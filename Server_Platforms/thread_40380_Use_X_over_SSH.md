---
title: "Use X over SSH"
date: 2005-06-08
forum: Server Platforms
---

### Post by Trickyphillips on 2005-06-08
Hello,

My website is on a VPS that I have full SSH access to, and I plan on doing some major changes. I don't want to use FTP, as I'll have to keep downloading/uploading while I make changes, so I'd like to use gedit on my own machine (I'm not a fan of Terminal-based text editors, like nano).

Is there any way I can use X and Gedit on my own machine to modify files remotely?

Thanks,
Ron

---

### Post by diebels on 2005-06-08
In gedit press ctrl+o, ctrl+l,
type in "sftp://yourservername"
type in password and browse to file you want to open.

You can also do this in nautilus.

For different users login:
"sftp://someuser@yourservername"

---

### Post by Trickyphillips on 2005-06-08
[QUOTE=diebels]In gedit press ctrl+o, ctrl+l,
type in "sftp://yourservername"
type in password and browse to file you want to open.

You can also do this in nautilus.

For different users login:
"sftp://someuser@yourservername"[/QUOTE]

Thanks for the help, diebels. :)

---

