Channel Analytics Battle

Channel Analytics Battle คือ Web Application สำหรับเปรียบเทียบและวิเคราะห์สถิติช่อง YouTube แบบเจาะลึก (Deep Analytics) โดยเน้นการใช้ข้อมูลจริง (Data-Driven) เพื่อวางกลยุทธ์คอนเทนต์ แตกต่างจาก Dashboard ทั่วไปตรงที่มีการผสานพลังของ Generative AI (Gemini) เข้ามาช่วยวิเคราะห์พฤติกรรมคนดูและแนะนำแนวทางปรับปรุงช่องเสมือนมี Producer ส่วนตัว

ฟีเจอร์หลัก (Key Features)

Multi-Channel Comparison: เปรียบเทียบสถิติช่อง Youtube ได้หลายช่องพร้อมกัน (Views, Likes, Engagement Rate)

Heatmap Golden Hour: วิเคราะห์ช่วงเวลาที่ดีที่สุดในการลงคลิป (Day & Hour) จากประวัติยอดวิว

3D Content Matrix: กราฟ 3 มิติแสดงความสัมพันธ์ระหว่าง ความยาวคลิป, Engagement, และยอดวิว เพื่อหา "Sweet Spot" ของคอนเทนต์

AI Analyst (Powered by Gemini): ระบบผู้ช่วยอัจฉริยะที่วิเคราะห์ข้อมูลและให้คำแนะนำเชิงกลยุทธ์ 3 ด้าน:

Content Structure: โครงสร้างการเล่าเรื่อง

Audience Behavior: พฤติกรรมคนดู

Optimization (CTR/SEO): การตั้งชื่อและทำปก

Dynamic Dashboard: กราฟวงกลมและแท่งที่ปรับเปลี่ยนตามข้อมูลที่เลือกได้ทันที



สถาปัตยกรรมระบบ (System Architecture)

ระบบทำงานแบบ Serverless โดยใช้ n8n เป็นตัวขับเคลื่อนข้อมูลหลัก:

Data Ingestion (n8n): Workflow อัตโนมัติดึงข้อมูลจาก YouTube Data API v3

Data Storage (Google Sheets): เก็บข้อมูลแบบ Data Warehouse ขนาดย่อม

dim_videos_update: เก็บ Metadata ล่าสุดของคลิป (Upsert)

fact_video_stats: เก็บ History ของยอดวิวตามเวลา (Append)

Visualization (Frontend): Web App (React) ดึงข้อมูล CSV จาก Google Sheets มาแสดงผลและส่งต่อให้ AI


Tech Stack

Frontend: HTML5, React 18 (CDN), Tailwind CSS

Visualization: Recharts, Plotly.js (3D)

Automation: n8n, Google Sheets API

AI Model: Google Gemini 1.5 Flash (via API)


วิธีการใช้งาน (How to Run)

เนื่องจากโปรเจกต์นี้เป็นแบบ Single File HTML ที่รวมทุกอย่างไว้ในไฟล์เดียว จึงไม่ต้องติดตั้ง Node.js หรือ build step ใดๆ

ดาวน์โหลดไฟล์ index.html

เปิดไฟล์ด้วย Web Browser (Chrome, Edge, Safari)

ใช้งานได้ทันที! (ข้อมูลจะดึงจาก Google Sheets ที่ตั้งค่าไว้)


การตั้งค่าข้อมูล (Data Setup)

หากต้องการเปลี่ยนแหล่งข้อมูลเป็นของคุณเอง:

แก้ไข URL ในฟังก์ชัน fetchData ในไฟล์ index.html:

const SHEET_ID = 'YOUR_GOOGLE_SHEET_ID'; const CSV_URL = https://docs.google.com/spreadsheets/d/${SHEET_ID}/export?format=csv&gid=YOUR_GID;

ตรวจสอบให้แน่ใจว่า Google Sheet เปิดแชร์แบบ "Anyone with the link can view"



โปรเจกต์นี้จัดทำขึ้นเพื่อการศึกษาและการวิเคราะห์ข้อมูลเบื้องต้น หากต้องการพัฒนาต่อยอด สามารถ Fork และส่ง Pull Request ได้เลยครับ

Thitikorn Sapanguen(SDA), Natpaphon Nukhunthod(DS)
