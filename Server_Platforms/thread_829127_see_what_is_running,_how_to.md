---
title: "see what is running, how to?"
date: 2008-06-14
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-06-14
Hi,

I'm encountering some problems with two programs/services: vsftpd and tomcat.
Both were working.
I added a new user and bam ... no tomcat and ftp fail. I get an error in the browser for both requests. 

When I start the ftp-service is says OK but when I stop it immediately Ubuntu says there is no service to be stopped.???

Is there a way to see if ubuntu has actually a surten service running or not? 

Mario

---

### Post by ajgreeny on 2008-06-14
In terminal use ```
top
```or open gnome-system-monitor System>>Administration>>System Monitor and look in the Processes tab.

---

### Post by prshah on 2008-06-14
> **MarioFromBelgium said:**
> 
Is there a way to see if ubuntu has actually a surten service running or not? 




Open a terminal (Applications-Accessories-Terminal), then give the following command ```

netstat -l

```

---

### Post by hyper_ch on 2008-06-14
```

ps aux

```

```

ps aux | grep KEYWORD

```
to filter it

---

### Post by MarioFromBelgium on 2008-06-18
tcp        0      0 *:ftp             *:*            LISTEN

The netstat -l command returns (amongst other lines) this line. I assume this means that there is a ftp-service listening???

(I got my tomcat back up   --  reboot ---) but the ftp-service is still not working.

---

