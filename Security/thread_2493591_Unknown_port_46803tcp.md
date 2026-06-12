---
title: "Unknown port 46803/tcp"
date: 2023-12-19
forum: Security
---

### Post by exceptcar37 on 2023-12-19
Hello I did a nmap scan of my network recently to see everything was as  it should be and this unknown port showed up could someone please tell  me what it is?

I tried "sudo netstat -lntp" but the port did not show up. The nmap  output seems to trying to tell me it have something to d with Kerberos  but I don't wish for this to be running, i am using Ubuntu 23.10.

---

### Post by exceptcar37 on 2023-12-19
to reproduce you can run this "sudo nmap -sC -sV -p- $ip" replace $ip with your ubuntu machines ip

---

