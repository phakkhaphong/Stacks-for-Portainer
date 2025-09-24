# 🚀 My Stacks Repository

Repo นี้รวมหลาย **Docker Compose Stacks** ที่สามารถใช้งานผ่าน **Portainer** ได้ โดยแต่ละ Stack แยกอยู่ในโฟลเดอร์ของตัวเอง  

---

## 📂 โครงสร้าง Repo
```
automation-stack/
  ├── docker-compose.yml
  ├── .env.example
cloudflare-stack/
  ├── docker-compose.yml
  ├── .env.example
smart-home-stack/
  ├── docker-compose.yml
  ├── .env.example
  ├── homeassistant_config/
  ├── mosquitto_config/
  └── zigbee2mqtt/
.gitignore
README.md
```

---

## 📦 Stacks ที่มีอยู่

### 1. **Automation Stack**
- สำหรับระบบ Automation (ตัวอย่าง: n8n, scheduler ฯลฯ)
- ไฟล์สำคัญ: `docker-compose.yml`, `.env.example`

### 2. **Cloudflare Stack**
- สำหรับเชื่อมต่อกับ **Cloudflare Tunnel**
- ใช้เพื่อให้เข้าถึง Service ต่าง ๆ ผ่าน HTTPS ฟรี
- ไฟล์สำคัญ: `docker-compose.yml`, `.env.example`

### 3. **Smart Home Stack**
- สำหรับระบบ Smart Home
  - **Home Assistant**
  - **Mosquitto MQTT Broker**
  - **Zigbee2MQTT**
- มีโฟลเดอร์ config แยกไว้แล้ว
- ไฟล์สำคัญ: `docker-compose.yml`, `.env.example`, `configuration.yaml`

---

## ⚙️ การตั้งค่า `.env`

แต่ละ Stack จะมีไฟล์ `.env.example` → ให้ copy เป็น `.env` แล้วแก้ค่าตามระบบของคุณ  

```bash
cp automation-stack/.env.example automation-stack/.env
cp cloudflare-stack/.env.example cloudflare-stack/.env
cp smart-home-stack/.env.example smart-home-stack/.env
```

แก้ไขไฟล์ `.env` ตามที่ต้องการ เช่น รหัสผ่าน, Token, หรือ Port ที่ต้องการใช้  

📸 **ตัวอย่างไฟล์ `.env`**  
![env-example](docs/images/placeholder.png)

---

## 🚀 Deploy บน Portainer

1. เปิด **Portainer Web UI**  
   ![portainer-home](docs/images/placeholder.png)

2. ไปที่ **Stacks → Add Stack → Git repository**  
   ![add-stack](docs/images/placeholder.png)

3. กรอกข้อมูล:  
   - Repository URL:  
     ```
     https://github.com/<your-username>/<your-repo>.git
     ```
   - Compose Path:  
     - `automation-stack/docker-compose.yml`
     - `cloudflare-stack/docker-compose.yml`
     - `smart-home-stack/docker-compose.yml`
   - (ถ้า Repo เป็น Private ให้ใส่ GitHub Token)  
   ![git-stack](docs/images/placeholder.png)

4. กด **Deploy the stack**  
   ![deploy-stack](docs/images/placeholder.png)

---

## 🌐 การเชื่อมต่อกับ Cloudflare

- ใช้ **Cloudflare Tunnel** จาก `cloudflare-stack`  
- ต้องนำ Token จาก Cloudflare Zero Trust มาใส่ใน `.env`  
- Subdomain ต่าง ๆ สามารถตั้งค่าได้ เช่น  
  - `https://n8n.mydomain.com`  
  - `https://ha.mydomain.com`  

📸 **ตัวอย่าง Cloudflare Tunnel Dashboard**  
![cloudflare-tunnel](docs/images/placeholder.png)

---

## 🛡️ ความปลอดภัย

- **.env** จะถูก ignore ไม่ถูก push ขึ้น GitHub  
- ตัวอย่างค่า config อยู่ใน `.env.example` เท่านั้น  

---

## 📖 คู่มือเพิ่มเติม
- [Docker Documentation](https://docs.docker.com/)  
- [Portainer Documentation](https://docs.portainer.io/)  
- [Cloudflare Tunnel Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)  
