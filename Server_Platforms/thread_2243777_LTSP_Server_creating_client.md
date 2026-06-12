---
title: "LTSP Server creating client"
date: 2014-09-11
forum: Server Platforms
---

### Post by aor2 on 2014-09-11
Hi, anybody can help me with my problem, Im in a stage of learning ubunbtu server application

I have installed ltsp server from a scratch running in ubuntu 14.04 LTS, my problem is I cant get client to log in, or perhaps i have a wrong method of creating clients,my client username resides in this location /opt/ltsp/amd64/home/

Here is my command in creating the client user, thus if i will log in using server account it can log in.
ltsp-chroot -c -p -d
adduser USERNAME
then back to server root and perform ltsp-update-image.


Please help me,
Thanks.

---

