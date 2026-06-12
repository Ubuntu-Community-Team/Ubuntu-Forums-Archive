---
title: "loosing connection with server via ssh"
date: 2011-12-22
forum: Server Platforms
---

### Post by herbert tamayo on 2011-12-22
Hi, I'm using ssh to connect to the server, after some seconds of logon I'm loosing connectivity, I can't type any command even i can't logout, after 2 minutes the ssh tells, connection time-out. so my questions are:

1. ssh has some log file? where is it?
2. what other logs files should I check?
3. I've already checked the cable network with a fluke intellitone and it is ok, so in general way what do you think could be the problem?

regards

---

### Post by CharlesA on 2011-12-22
You can try using verbose mode to see if something strange happens before you get disconnected.

ssh -vvv user@ipaddy

Are you able to ping the host when ssh hangs?

---

### Post by herbert tamayo on 2011-12-23
no, i'm not able to ping the host when ssh hangs, i think it is not just a ssh issue but honestly i don't know where to look for, is there any log file for ssh?

---

### Post by CharlesA on 2011-12-23
There is only an auth.log that logs failed authentications, but you might have some luck by checking the syslog to see why networking is dropping, since you can't ping the host when ssh drops.

---

### Post by localhost8080 on 2011-12-23
> **CharlesA said:**
> There is only an auth.log that logs failed authentications, but you might have some luck by checking the syslog to see why networking is dropping, since you can't ping the host when ssh drops.

it could be a network issue, it could also be a 'keepalive' issue.

it sounds more like its a network issue, but its hard to diagnose.

'cat /var/log/messages | grep ssh'
'cat /var/log/messages | grep eth0' [or whatever device your network card is]

check on both your client and server

maybe even 'dmesg | grep ssh'

---

