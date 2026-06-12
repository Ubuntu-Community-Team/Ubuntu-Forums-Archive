---
title: "Port 21 open - wtf?"
date: 2006-07-07
forum: Server Platforms
---

### Post by uros678 on 2006-07-07
Hello fellow ubuntu users,

I just installed 6.06 server to try it out, and after trying nmap "serverIP" it showed port 21 open. This was from a remote location so it was an outsice nmap scan. 

when I ran nmap on the server, it showed port 25 and 3306 (smtp and  mysql) open, which I think is normal, but no port 21. Tried netstat and it said the same. I don't know... and no, I'm not runnign a ftp daemon.

Can anyone explain this to me please? 

Is there a problem with nmap (I'm using the latest stable from the official web page on the remote computer and the one from the repos on the server).

Thanks for the time,

Uros

---

### Post by Randomskk on 2006-07-07
You say you tried from an external point, is there a router with NAT in front of the server? If so, port 21 could be going to another computer.

---

### Post by lamego on 2006-07-07
The scenario explained by Randomskk is the most probable.
Anyway locally you can check whether you have some program listening on 21 with:
```
sudo netstat -lp | grep ftp
```

---

