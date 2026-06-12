---
title: "rkhunter warning"
date: 2009-11-30
forum: Security
---

### Post by saltydog on 2009-11-30
This morning, on my 8.04LTS server, I got this warning message from rkhunter:

```
Warning: Network TCP port 6667 is being used by /usr/bin/python2.5. Possible rootkit: Possible rogue IRC bot
         Use the 'lsof -i' or 'netstat -an' command to check this.
```


Checking with netstat -an, I had this result:

```
tcp        0      0 <server_IP_address>:41318    213.92.8.4:6667         ESTABLISHED

```

Should I be scared?
Thanks for any suggestion

Fabio

---

### Post by saltydog on 2009-11-30
Sorry it was my fault: I forgot to have a supybot installed...

---

