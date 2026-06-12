---
title: "LTSP_Server_Problem"
date: 2012-09-26
forum: Server Platforms
---

### Post by srtsuffer on 2012-09-26
hello,

I have a LTSP Server ubuntu 12.04 up and running and an Client who boots over the Network. My plan is that if the client boots up  after the Ubuntu loading screen a RDP session with rdesktop starts.

My Problem:
If I paste Rdesktop into the lts.config the client stops at the ubuntu loading screen and he doesn't go on.

lts.config:

[DEFAULT]

SCREEN_07 = rdesktop
RDP_SERVER = "192.168.2.58"

please help me

Thanks
SRTsuffer

---

### Post by lykwydchykyn on 2012-09-26
Is rdesktop installed on the server?

Can you remote desktop to the specified IP from the server directly?

---

### Post by srtsuffer on 2012-09-27
I have installed it with the comand:

sudo apt-get install rdesktop

:D

---

### Post by srtsuffer on 2012-09-27
But it doesn't work same effect as before

---

### Post by lykwydchykyn on 2012-09-27
Can you remote desktop to the IP directly from the server?

Have you checked /var/log/syslog for errors?

---

### Post by srtsuffer on 2012-09-27
If I remove the Rdesktop comand from the lts.config and the client starts normal and I log in, open a terminal and start rdesktop it works.

Syslog is empty

---

### Post by srtsuffer on 2012-09-27
What could it be that it doesn't work ?

---

### Post by lykwydchykyn on 2012-09-28
syslog is empty???  Like 0 bytes?  That's very odd, especially for a server.  There should be something in there.  You are looking at /var/log/syslog on the server, correct?

Go into your tftpboot directory (the one where lts.conf lives), go into the pxelinux.cfg director and open (as root) the "default" file.

Remove the words "quiet" and "splash" from the line that starts with "append".  Then boot your client.  This should give you some meaningful error output on the client's screen.

---

### Post by srtsuffer on 2012-09-30
Nothing the only thing that has changend is if I start the client there ist loading..... ready now, but then it stays at the ubuntu start screen :-(

---

