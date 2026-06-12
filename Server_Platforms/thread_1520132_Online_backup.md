---
title: "Online backup"
date: 2010-06-29
forum: Server Platforms
---

### Post by damo12 on 2010-06-29
[FONT="Comic Sans MS"]I support a small business which uses an Ubuntu server (10.04 32 bit) as a file server which is access from Windows machines.  The server is headless and is accessed through Webmin.

Can anyone recommend an automated online backup solution.  I have looked at Carbonite and Livedrive but they only seem to work on Windows machines and will not backup network drives.  As there is around 500Gb of data on the server and money is an important factor I would rather not go down the route of Amazon S3 or equivalent as the costs will be prohibitively high.

Thanks in advance for your help.[/FONT]

---

### Post by HermanAB on 2010-06-29
Rsync over SSH to another PC is the best bet.

---

### Post by damo12 on 2010-06-30
[FONT="Comic Sans MS"]Thanks for the reply, was hoping to not have to invest in another server but am starting to think that could be the only option[/FONT]

---

