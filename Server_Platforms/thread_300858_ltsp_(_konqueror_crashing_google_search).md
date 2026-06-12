---
title: "ltsp ( konqueror crashing google search)"
date: 2006-11-16
forum: Server Platforms
---

### Post by oly on 2006-11-16
i just got a edgy ltsp server setup, very nippy works perfectly except for konqueror which crashs when on almost every website, i can not even do a simple search. it closes instantly with a fatal error message.

anyway i can find out the cause it works perfectly on standard kde on edgy, and firefox works excellently the server is to server a class of students looks bad if i have to say don't use konqueror because it crashs anyone seen any thing similar ??

---

### Post by fnjordy on 2006-11-18
Try using Konqueror on the server desktop, if that works fine you have a problem with memory on the client.  Usually this is video memory size being incorrectly guessed, explicitly set it in /opt/ltsp/i386/etc/lts.conf via "X_VIDEO_RAM = 2048" or similar.  Also try bumping up the NBD swap space by changing the default 32MB to 128MB in /usr/sbin/nbdswapd

---

### Post by oly on 2006-12-08
thanks for the suggestion a reboot fixed it in the end

---

