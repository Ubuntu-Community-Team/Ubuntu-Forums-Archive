---
title: "characters problem"
date: 2005-05-25
forum: Server Platforms
---

### Post by Gandalf on 2005-05-25
Hello,
i use ubuntu hoary as a server on my server box, there's some characters problems,
when i mported the database to mysql all french characters ( é, è, à, ç, ê, € etc...) are all showing like this "?", but when someone post on the forum those characters they are showing correctly,
again when i upload files via FTP all those characters are ? and no way to repair them since pico type a square,
i have installed: language-pack-fr language-pack-fr-base language-support-fr but it didn't solve my problem, on debian sarge i haven't this problem, do you have any idea on how to solve it????

thanks

---

### Post by LordHunter317 on 2005-05-25
You likely have a locale issue.  What locale is the MySQL database set to?

---

### Post by Gandalf on 2005-05-25
[QUOTE=LordHunter317]You likely have a locale issue.  What locale is the MySQL database set to?[/QUOTE]
 i'm not having mysql locale problem, but system, ftp or apache maybe

---

