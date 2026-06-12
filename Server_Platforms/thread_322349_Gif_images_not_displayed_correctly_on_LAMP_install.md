---
title: "Gif images not displayed correctly on LAMP install"
date: 2006-12-20
forum: Server Platforms
---

### Post by kkroese on 2006-12-20
Hi

This is my first day with Ubuntu (linux).  I am moving windows hosted websites over to an LAMP install of Ubuntu.  Everything is working fine except  the gif images on my hosted sites are not displaying correctly when served by my LAMP server.

Any ideas? I don't know where to start.

***********************************************
It seems like the gif files got corrupted in some way during the FTP process.  I have copied the gif files over via my windows PC and it works fine now.  Now to figure out why the gif files got corrupted during my ftp.
***********************************************

---

### Post by ArtechnikA on 2006-12-20
a standard thing to check first is case sensitivity.
Windows (IIS) doesn't much care about case - *nix does.
make sure the filenames are *exactly* what you're asking for.
(BTDT)

---

### Post by ArtechnikA on 2006-12-20
> **kkroese said:**
> It seems like the gif files got corrupted in some way during the FTP process.  I have copied the gif files over via my windows PC and it works fine now.  Now to figure out why the gif files got corrupted during my ftp.

editing the original post rather than adding a reply makes continuing the thread with context quotes a bit of a challenge...

you know (I presume) that gif files are binary and ftp won't transfer them correctly when it's in ASCII mode.  an FTP tutorial is beyond the scope of this forum if for no other reason than I am not qualified to give one and good ones already exist...  However - before you start using 'put' or 'mput' to transfer your files, make sure you're in binary transfer mode by using the 'bin' command.  it'll tell you the current mode after you do this.  then try again.  good luck.

---

