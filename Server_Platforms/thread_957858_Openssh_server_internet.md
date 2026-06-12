---
title: "Openssh server internet"
date: 2008-10-24
forum: Server Platforms
---

### Post by alex1996arm on 2008-10-24
hello,
i have a server running Ubuntu server edition 8.04
i installed open ssh
i can access it from network i just put 192.168.0.101
but how do i assess from other computer on the internet

---

### Post by PilotJLR on 2008-10-24
192.168.X.X is a private IP address. You need to forward port 22 from your router to your server, then access the server via your public IP adress.

To find your public address:  [http://www.whatismyip.com](http://www.whatismyip.com)

---

### Post by alex1996arm on 2008-10-25
thank you very much:guitar:

---

