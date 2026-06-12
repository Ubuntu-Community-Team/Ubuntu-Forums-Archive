---
title: "FTP server problem"
date: 2009-07-17
forum: Server Platforms
---

### Post by note32 on 2009-07-17
im using VSFTPD as my server

anyway so i set it up and everything and it works just fine. BUT! when you login to the server it shows everything of mine my photos music movies ect.... pretty much everything in my home folder i just want there to be one "shareing folder" for me and my bro

---

### Post by jonobr on 2009-07-17
Hello


I think in your vsftpd.conf file
you need an entry that will change you to the right directory

the entry you need is
local_root
and give the full path of where you are placed after you log in

---

