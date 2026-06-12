---
title: "[SOLVED] GRAPHICALLY connecting to a server (Via SSH) while on Xubuntu."
date: 2007-12-17
forum: Server Platforms
---

### Post by some_random_noob on 2007-12-17
Hi all, I want to connect into a server using SSH. I used to do this in Ubuntu via "connect to server" but now I'm running Xubuntu and there seems to be no such feature.

I really need the ability to drag'n'drop stuff onto the server (It saves so much time!). Can I somehow install the "connect to server" feature from Ubuntu? If not, then what other graphical tools are there to connect to a server using SSH?

Need a recommendation - Cheers! :)

---

### Post by maybeway36 on 2007-12-17
You could try installing Nautilus and typing in the Alt+F2 window:
```
nautilus --no-desktop sftp://username@server
```

---

### Post by cyberdork33 on 2007-12-17
most ftp clients now can connect via sftp.

---

### Post by some_random_noob on 2007-12-17
> **maybeway36 said:**
> You could try installing Nautilus and typing in the Alt+F2 window:
```
nautilus --no-desktop sftp://username@server
```
Yes, this is a possibility. However, if I have Nautilus AND Thunar then how the heck does that work out?

Also, thanks to cyberdork33. I might just end up using FTP. I think this will be my default choice if that is the case: [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

---

### Post by HermanAB on 2007-12-17
Nautilus, Konqueror, Filezilla and Gftp can all do graphical connections to sshd.

Cheers,

Herman

---

