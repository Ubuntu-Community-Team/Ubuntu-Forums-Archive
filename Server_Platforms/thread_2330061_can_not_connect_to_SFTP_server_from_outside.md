---
title: "can not connect to SFTP server from outside"
date: 2016-07-07
forum: Server Platforms
---

### Post by max.schollen on 2016-07-07
Dear people !
I have built a SFTP server for my files
He is running on a raspberry pi 3 with ubuntu mate
But I can not connect to the server from the outside (4G)
I have the router Zte H369A 
Could someone help me please ?
Max Schollen

---

### Post by darkod on 2016-07-07
In the internet router option forward port 22 to the Pi private IP. Then use the router public IP to connect to SFTP. It will forward the traffic to the Pi.

---

### Post by max.schollen on 2016-07-07
Its working 
Thank you ferry much 
You are my hero !

---

### Post by darkod on 2016-07-07
You are welcome. Please mark the thread as SOLVED. You can do that in Thread Tools above the first post.

---

### Post by mastablasta on 2016-07-09
+ make sure you installed fail2ban or similar software and that you use keys (not passwords) for authentication. attacks on your Pi will begin within hours of opening the port.

---

