---
title: "UFW blocks https"
date: 2019-06-28
forum: Server Platforms
---

### Post by knight69 on 2019-06-28
I am setting up a new Ubuntu 18.04 Mate server with a LEMP stack.  Everything was working perfectly until I set up ufw. After setting it up to allow http and https for nginx, http requests are allowed but https requests are blocked.  When I installed ufw, version 0.36 was installed automatically.  When it failed to pass https requests, I replaced version 0.36 with version 0.35-5 as prescribed in Ubuntu wiki without any effect.  Nginx access log shows that http requests were processed successfully but there is no indication that any https request was accepted, denied or even received.  Dmesg reports

[13721.758846] [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:20:c0:47:13:01:15:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=35955 DF PROTO=2 

In the middle of many of these statements there are these 3 statements:

[12837.112813] audit: type=1400 audit(1561742822.856:38): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/wayne/.cache/mesa_shader_cache/index" pid=7671 comm="soffice.bin" requested_mask="wrc" denied_mask="wrc" fsuid=1000 ouid=1000
[12841.715035] audit: type=1400 audit(1561742827.456:39): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/wayne/.mozilla/firefox/6jljrto3.default/cert8.db" pid=7670 comm="soffice.bin" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
[12841.715826] audit: type=1400 audit(1561742827.456:40): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/wayne/.mozilla/firefox/6jljrto3.default/key3.db" pid=7670 comm="soffice.bin" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=1000

I am new to this security stuff and at this point, I am stuck. Any help will be appreciated.

---

### Post by TheFu on 2019-06-29
I'm inclined to think it is an nginx config or HTTPS/cert or ufw config problem, not a ufw bug.
```
$ sudo nginx -t
```
to see if there are issues with the nginx config.

```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Nginx Full                 ALLOW       Anywhere                  
3000/tcp                   ALLOW       Anywhere

$ sudo ufw app info "Nginx Full"
Profile: Nginx Full
Title: Web Server (Nginx, HTTP + HTTPS)
Description: Small, but very powerful and efficient web server

Ports:
  80,443/tcp    
```
is working here on 16.04.6.  This is on a reverse proxy nginx server as a front end to about 20 virtual websites. Some are single static files and some are complex webapps running both local and on other systems.

The libreoffice lines aren't connected at all.  soffice is from Star Office, which was pre-OpenOffice, which was pre-LibreOffice.

BTW, I wouldn't run a public web server on a desktop.  Just too many risks.

Did you setup https stuff correctly?  Where did the cert come from?

---

### Post by knight69 on 2019-07-04
:pSOLVED!

There were two problems. The first was two enabled server blocks with the same domain name. (I had started to set up a new one for my website, but then when I ran into problems, I went back and modified the default server block and forgot to remove the link to the new one.)

The second problem was not getting rid of the snippet that pointed to the "snakeoil" certificate that really is snakeoil.  After I got rid of that and put in the proper location for my real certificate, all went well.

---

### Post by TheFu on 2019-07-04
Thanks for explaining the issues. No way could anyone here know that from the information provided.  BTW, please use the "thread tools" button near the top to mark this thread as SOLVED to help the community so people don't waste time.

---

