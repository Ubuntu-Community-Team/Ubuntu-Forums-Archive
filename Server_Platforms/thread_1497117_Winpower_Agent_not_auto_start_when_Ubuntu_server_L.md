---
title: "Winpower Agent not auto start when Ubuntu server Linux system start"
date: 2010-05-30
forum: Server Platforms
---

### Post by dalitso on 2010-05-30
I have bought a Mecer ME-1000BK UPS and installed winpower on my Ubuntu 8.04 server box that its connected to via serial connection. I used the cd that it came with.
Everything went well and is running fine but I have noticed that the winpower agent is not starting automatically when the system boots. I have to manually start it all the time with this code
```
cd /opt/upspilot
./agent start
```

Please help me with a way I can make it start when the system boots

---

### Post by dalitso on 2010-09-25
Adding the below to /etc/rc.local (before the exit 0 line) worked

cd /opt/upspilot
./agent start

---

