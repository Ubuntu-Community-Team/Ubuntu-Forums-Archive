---
title: "PPTPd Ubuntu 12.04 anon fatal[get_ip_address:pptp.c:437]: getaddrinfo():"
date: 2013-10-22
forum: Server Platforms
---

### Post by Dominic--- on 2013-10-22
Hi guys,

I have installed PPTPd and followed this instruction: [https://www.digitalocean.com/community/articles/how-to-setup-your-own-vpn-with-pptp](https://www.digitalocean.com/community/articles/how-to-setup-your-own-vpn-with-pptp)

When the instruction says to run this command: pptp call pptpserver, I receive the message:
anon fatal[get_ip_address:pptp.c:437]: getaddrinfo(): No address associated with hostname

What is causing this error?

/etc/pptpd.conf:
# (Recommended)
localip 85.**.*1.**8
remoteip 192.168.0.234-238

What can cause this error and where should I look for the problem? I have seriously no clue where this is going wrong.
My DNS is functioning properly.

---

### Post by Dominic--- on 2013-10-22
Anyone?

---

