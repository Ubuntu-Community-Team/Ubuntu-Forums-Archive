---
title: "Cannot connect to ftp server via WAN-ip"
date: 2006-12-13
forum: Server Platforms
---

### Post by Micra on 2006-12-13
Hi everyone
I'm very new to linux, but I decided to set ubuntu 6.06 up as a server (i have no server experience)

Everything worked out just fine installing xampp, but i have problems connecting to my server via ftp. I'm able to connect using my LAN-ip but as soon as i use the WAN-ip it stops halfway during the connection. The last message gFTP displays is:
```
227 Entering Passive Mode (xx,xx,xx,xx,xx,xx)
```
So i went into options in gFTP and unchecked "passive file transfers" hoping that it would run in active mode then. It still stops halfway but its a different message it displays before freasing:
```
200 PORT command successful
LIST -aL
```

Some of my friends tried to connect aswell and they COULD connect via WAN-ip with filezilla (but they had to turn passive mode off). And through /system32/ftp.exe on a windows pc.

My questions to you is:
Why am I unable to connect via gFTP (even with passive mode: off), when some of my friends can connect via another ftp-client. Has it anything to do with my ftp-client? And why is passive mode not working for anyone? Has it anything to do with the router of the server? Which ports should be forwarded?

I would really appreciate some answers, I'm very confused
Thanks!

---

