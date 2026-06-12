---
title: "Exists chechsum for Ubuntu server.iso?"
date: 2011-11-08
forum: Server Platforms
---

### Post by dr_pompeii on 2011-11-08
Hello Guys

I just download through torrents the file **ubuntu-11.10-server-i386.iso**.

Is possible make a checksum with md5 or sha1? or is not necessary?
Seems not because on [**Alternative downloads**]("http://www.ubuntu.com/download/ubuntu/alternative-download") page, not appear something related with that

I am doing this question because for example on Fedora Core offer the option to do a checksum for a dvd .iso file downloaded with Torrents

Thanks in advanced

---

### Post by rubylaser on 2011-11-08
These are all the hashes for [Ubuntu]("https://help.ubuntu.com/community/UbuntuHashes"). Yours should be ```
881d188cb1ca5fb18e3d9132275dceda
```

Just run
```
md5sum ubuntu-11.10-server-i386.iso
``` to verify that it matches.

---

