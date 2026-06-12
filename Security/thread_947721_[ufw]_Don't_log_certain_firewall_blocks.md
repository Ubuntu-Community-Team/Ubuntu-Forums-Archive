---
title: "[ufw] Don't log certain firewall blocks"
date: 2008-10-14
forum: Security
---

### Post by drewtown on 2008-10-14
I have UFW setup to block everything but 80 from anybody and 22 from local machines.  There are 2 devices on our network that broadcast junk all the time and our syslog captures all of them since they are blocked on the firewall.  Is there any way to not log events triggered by these two machines?

example:
Oct 14 07:53:54 ubuntu-server kernel: [1539740.414254] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:4a:29:21:40:08:00 SRC=192.168.1.* DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=47809 PROTO=UDP SPT=1025 DPT=53862 LEN=58
x infinity

---

