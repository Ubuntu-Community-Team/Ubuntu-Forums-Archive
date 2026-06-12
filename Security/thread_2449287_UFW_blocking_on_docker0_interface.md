---
title: "UFW blocking on docker0 interface"
date: 2020-08-24
forum: Security
---

### Post by MangoPapaya on 2020-08-24
Hi, I just configured ufw on a xenial instance. In the logs I find lots of messages like

[UFW BLOCK] IN=**docker0** OUT= PHYSIN=vetha8c6d2e MAC=02:42:6b:48:be:a8:02:42:ac:11:00:04:08:00 SRC=**172.17.0.4** DST=**172.17.0.1** LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=54509 DF PROTO=TCP SPT=80 DPT=40092 WINDOW=0 RES=0x00 RST URGP=0

I created some rules on interface and IP ranges but those block messages are still there. Here is current status.

Status: active
To                         Action      From
--                         ------      ----
Anywhere on **docker0        **ALLOW       Anywhere
**172.17.0.0**/16              ALLOW       **172.17.0.0**/16
Anywhere                   ALLOW OUT   Anywhere on **docker0**
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on docker0

I suppose I'm missing something, but I have no idea what it is... Any ideas?
Thanks

---

### Post by EuclideanCoffee on 2020-08-24
This is a common problem with UFW and docker iptables.

The community recommends disabling docker's iptables like this:

DOCKER_OPTS="--iptables=false"

Or simply running it as such as an argument.

You can also add it to your configuration file to include iptables options.

[https://docs.docker.com/network/iptables/](https://docs.docker.com/network/iptables/)

Reboot your services UFW and docker or restart the computer to resolve the issue.

[https://github.com/docker/for-linux/issues/690](https://github.com/docker/for-linux/issues/690)

[https://stackoverflow.com/questions/30383845/what-is-the-best-practice-of-docker-ufw-under-ubuntu](https://stackoverflow.com/questions/30383845/what-is-the-best-practice-of-docker-ufw-under-ubuntu)

---

### Post by MangoPapaya on 2020-08-25
Thank you for the pointers. It seems it is not a "do this and resolve" type of problem, each solution has it's own pros and cons.
Didn't expect such a mess for two of the most used Linux products.
I'll start experimenting, thanks.

---

