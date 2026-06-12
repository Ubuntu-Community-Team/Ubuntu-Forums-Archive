---
title: "Errors with duplicity and backblaze b2"
date: 2018-08-25
forum: Server Platforms
---

### Post by timsmit1997 on 2018-08-25
Hi,

I am completely new to ubuntu server and need some help. 

I have been trying to backup the files on my server (Ubuntu server 18.04) to my BackBlaze B2 account using duplicity. I followed this guide [https://help.backblaze.com/hc/en-us/articles/115001518354-How-to-configure-Backblaze-B2-with-Duplicity-on-Linux](https://help.backblaze.com/hc/en-us/articles/115001518354-How-to-configure-Backblaze-B2-with-Duplicity-on-Linux).

The installation went fine, but when I tried by first backup I got a long list of errors that do not help me diagnose the problem.[ATTACH=CONFIG]280843[/ATTACH]

Hopefully someone can help.

Kind regards,

Tim

---

### Post by timsmit1997 on 2018-08-25
Solved it by using Restic instead of duplicity

[https://help.backblaze.com/hc/en-us/articles/115002880514-How-to-configure-Backblaze-B2-with-Restic-on-Linux](https://help.backblaze.com/hc/en-us/articles/115002880514-How-to-configure-Backblaze-B2-with-Restic-on-Linux)

---

