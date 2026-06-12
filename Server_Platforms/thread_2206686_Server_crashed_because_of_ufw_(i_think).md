---
title: "Server crashed because of ufw (i think)"
date: 2014-02-20
forum: Server Platforms
---

### Post by adimate on 2014-02-20
Hello !

I am using Zimbra on a virtual machine with ubuntu server 12.04.4.
I have configured ufw to accept traffic only through ports used by zimbra, apache and ssh.
After a few days my server crashed (i had to manual restart my virtual machine)  with a lot of messages like the one below:

Feb 20 13:19:25 server kernel: [71821.868029] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:e0:81:b8:b8:79:08:00 SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2

This type of messages i received with cmd sudo tail -f /var/log/syslog.

What should i do to prevent another crashed ?

Thank you !

---

### Post by Lars Noodén on 2014-02-20
What were the messages right before the actual crash?  Or was that it?

---

### Post by nerdtron on 2014-02-20
What is the output of "sudo ufw status"? Have you consulted the zimbra community for the ports that should be open upon installation?

---

### Post by brokenhachi on 2014-02-20
I think we need some more information as to what exactly the crash was. can you post syslog from before the crash? Also, do you have kdump configured? [https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe)

---

### Post by adimate on 2014-02-21
Hello !

The output for ufw status is:

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
25                         ALLOW       Anywhere
80                         ALLOW       Anywhere
110                        ALLOW       Anywhere
143                        ALLOW       Anywhere
443                        ALLOW       Anywhere
465                        ALLOW       Anywhere
587                        ALLOW       Anywhere
993                        ALLOW       Anywhere
995                        ALLOW       Anywhere
7071                       ALLOW       Anywhere
123/udp                    ALLOW       Anywhere
389                        ALLOW       Anywhere
22                         ALLOW       Anywhere (v6)
25                         ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
110                        ALLOW       Anywhere (v6)
143                        ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)
465                        ALLOW       Anywhere (v6)
587                        ALLOW       Anywhere (v6)
993                        ALLOW       Anywhere (v6)
995                        ALLOW       Anywhere (v6)
7071                       ALLOW       Anywhere (v6)
123/udp                    ALLOW       Anywhere (v6)
389                        ALLOW       Anywhere (v6)

I am using the requested port for Zimbra, as i read in documentation.

This ip appears in every message: [COLOR=#000000]DST=224.0.0.1.
[/COLOR]What does it mean ?

Thank you !

---

