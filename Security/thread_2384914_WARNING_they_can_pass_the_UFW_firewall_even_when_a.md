---
title: "WARNING: they can pass the UFW firewall even when all incoming blocked except http(s)"
date: 2018-02-14
forum: Security
---

### Post by xenon3 on 2018-02-14
They can change my user password from outside (incoming) with maybe they retrieved by CCTV camera's, ore have hacked it with password crackers (but then they cracked a 20 characters strong password within a couple of hours)

---

### Post by wildmanne39 on 2018-02-14
Do you have a question?

---

### Post by xenon3 on 2018-02-14
no want general discussion on firewall security

---

### Post by wyliecoyoteuk on 2018-02-14
Strongly advise the use of hardening tools on any server exposed to the internet.
For example:
Lynis will give you a lot of useful tips for hardening
Fail2ban makes password cracking a lot less likely
Relevant tools for your http server, redirect http to https
certificates for ssh login, etc.

A really determined hacker will keep trying, but if you make it hard, they will probably move on.

Keep all IOTs (e.g.network cameras, wifi sockets or lamps etc) on a seperate subnet with different security credentials.

---

