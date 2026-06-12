---
title: "Newbie-ish VMWare Server Question"
date: 2008-03-08
forum: Virtualisation
---

### Post by toddk111 on 2008-03-08
If I install Win2kPro on VMWare server in Ubuntu 7.10 and I want to transfer files between the host and guest do I have to set up SAMBA shares or is there an easier way?
Thanks,
Todd

---

### Post by HermanAB on 2008-03-08
FileZilla.

---

### Post by scottro on 2008-03-08
Doesn't filezilla require an ftp server?  I've found winscp to be quite handy for quick transfers.  (t creates an ssh session between Windows and Unix or Unix like machines.)

---

### Post by fjgaude on 2008-03-08
Samba is easy to setup, almost automatic using the System/Administration/Shared Folders menu of Gnome.

Then in WinXP in Explorer set the drive as a share.

Then you can access the shares from either side, host to guest, guest to host.

---

### Post by atentik on 2008-03-08
Can you provide the procedure for setting up this?

---

### Post by toddk111 on 2008-03-09
Thanks everyone!

---

### Post by adityakavoor on 2008-03-09
[Here]("http://www.youtube.com/watch?v=Ad17kma8rNM") is an awesome guide to setup samba

---

