---
title: "Site Every Night goes down..."
date: 2020-12-18
forum: Server Platforms
---

### Post by deezywonder on 2020-12-18
Hello friends. I found the forum on Google and decided to come here for help, because I still haven't found any solution!


I have a VPS with Ubuntu 20.04 that serves to host a Wordpress website.


But, every day something bizarre happens... Every day at 8,45 - 8,50pm my site is unavailable to access, and only returns after 22pm... I go to the logs and it seems that there is nothing wrong.


I will leave the logs below, if someone can help me thank you. I'm a newbie and the logs seem normal to me...

Syslog:
```

Dec 18 20:39:01 vps-d4d2562a CRON[141268]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Dec 18 20:39:04 vps-d4d2562a systemd[1]: Starting Clean php session files...
Dec 18 20:39:04 vps-d4d2562a systemd[1]: phpsessionclean.service: Succeeded.
Dec 18 20:39:04 vps-d4d2562a systemd[1]: Finished Clean php session files.
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Created slice User Slice of UID 1000.
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Starting User Runtime Directory /run/user/1000...
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Finished User Runtime Directory /run/user/1000.
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Starting User Manager for UID 1000...
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Reached target Paths.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Reached target Timers.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Starting D-Bus User Message Bus Socket.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on GnuPG network certificate management daemon.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on GnuPG cryptographic agent and passphrase cache.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on debconf communication socket.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on REST API socket for snapd user session agent.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Listening on D-Bus User Message Bus Socket.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Reached target Sockets.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Reached target Basic System.
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Started User Manager for UID 1000.
Dec 18 20:48:39 vps-d4d2562a systemd[1]: Started Session 562 of user ubuntu.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Reached target Main User Target.
Dec 18 20:48:39 vps-d4d2562a systemd[141772]: Startup finished in 125ms.
Dec 18 20:48:48 vps-d4d2562a kernel: [602377.147448] [UFW BLOCK] IN=ens3 OUT= MAC=fa:16:3e:f0:f9:ba:d6:17:fc:7e:52:23:08:00 SRC=194.26.27.109 DST=51.91.57.249 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40377 PROTO=TCP SPT=40405 DPT=14741 WINDOW=1024 RES=0x00 SYN URGP=0 
Dec 18 20:48:55 vps-d4d2562a kernel: [602384.162267] [UFW BLOCK] IN=ens3 OUT= MAC=fa:16:3e:f0:f9:ba:d6:17:fc:7e:52:23:08:00 SRC=64.227.64.219 DST=51.91.57.249 LEN=40 TOS=0x00 PREC=0x00 TTL=241 ID=0 PROTO=TCP SPT=2678 DPT=30005 WINDOW=14600 RES=0x00 SYN URGP=0 

```

---

### Post by TheFu on 2020-12-18
Are either of those blocked IPs yours?
How long do you block attacking IPs? 1 hour? 3600 seconds?  
That would be from 20:48  - 21:48 in the logs above.

Do you block all ports or just the specific port they attacks appear to be on?

What do the web server and reverse-proxy or load-balancer logs show?

---

### Post by QIII on 2020-12-18
Moved to ***Server Platforms***

---

### Post by deezywonder on 2020-12-18
> **TheFu said:**
> Are either of those blocked IPs yours?
How long do you block attacking IPs? 1 hour? 3600 seconds?  
That would be from 20:48  - 21:48 in the logs above.

Do you block all ports or just the specific port they attacks appear to be on?

What do the web server and reverse-proxy or load-balancer logs show?

Hey buddy,
None of these IP's is mine. I don't know how long it blocks IP's, but there are many UFW logs... I didn't configure much this part, so I have no idea.

UFW Status:
```

80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
22                         ALLOW       Anywhere
80/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)

```

Where do I find the reverse-proxy or load-balancer logs? I don't find anything about that.

---

### Post by TheFu on 2020-12-19
If you didn't setup either a load balancer or revere proxy, then almost certainly aren't using any.
If you didn't setup dynamic blocking, then you don't have it either.

I am a little worried that ssh is on the default port and available to anyone in the world. Please say you have at least fall2ban working for some ssh protection.

Enough information hasn't been provided to guess the original problem. The relevant  logs matter.

---

