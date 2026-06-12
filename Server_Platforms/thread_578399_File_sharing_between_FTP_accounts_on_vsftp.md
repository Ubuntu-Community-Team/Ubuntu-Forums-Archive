---
title: "File sharing between FTP accounts on vsftp"
date: 2007-10-17
forum: Server Platforms
---

### Post by efriese on 2007-10-17
I'm using vsftp as the FTP server on my ubuntu box. I need to share a large amount of files between multiple ftp user accounts? I tried to create a symbolic link, but had permission problems. Does anyone know how to do this so I don't have to keep multiple copies of these files in each user's directory? Thanks!

---

### Post by efriese on 2007-10-17
Any thoughts?

---

### Post by nix4me on 2007-10-17
Just mount the same directories into each user home dir.  Or even better, make the ftp directory the home dir for each user.

nix4me

---

