---
title: "How to share a folder in Thunar?"
date: 2016-02-20
forum: Ubuntu Studio
---

### Post by e-berlin.org on 2016-02-20
Hi, coming from Nautilus where things are so easy, but now on Ubuntu Studio 14 LTS (Xfce w/ Thunar) and utterly confused. I want to share a folder with another unix-like machine (a macbook), so should I use NFS or Samba? Could you paste some exemplary terminal commands for installing and setting up NFS/Samba, too? Thanks in advance.

---

### Post by QDR06VV9 on 2016-02-20
See if this helps: [http://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar](http://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar)

---

### Post by e-berlin.org on 2016-02-20
Hey, that was fast, thanks! Just one more thing: I know some users choose Samba just because of their Windows machines. Since I own only a linux and a mac machine, shouldn't I go for NFS?

---

### Post by QDR06VV9 on 2016-02-20
You know I don't have experience with Mac's so I am not much help there sorry..
But i have heard that samba is better now..
maybe you can share your experience with us here..
Regards

---

### Post by QDR06VV9 on 2016-02-20
Just found this [URL="http://apple.stackexchange.com/questions/19470/nfs-afp-smb-advantages-and-drawbacks-on-a-mac-os-system"]http://apple.stackexchange.com/questions/19470/nfs-afp-smb-advantages-and-drawbacks-on-a-mac-os-system

> [/URL] NFS is the recommended way to go. Five arguments, why NFS might be better in this situation:
  
[LIST]
[*]Fast installation and setup
[*]Simple/easy configuration of a "share"
[*]Simplet configuratio of security settings, e.g. host-based security
[*]Fast and reliable without the overhead of the SMB/CIFS protocol
[*]AFAIK, MAC OS supports NFS better than SMB/CIFS.
[/LIST]
  Only know that NFS can be confused when you are exporting a folder which is a bind mount. Youse fsid=xxx in /etc/exports then.
     
[URL="http://apple.stackexchange.com/questions/19470/nfs-afp-smb-advantages-and-drawbacks-on-a-mac-os-system"]
[/URL]

---

### Post by Morbius1 on 2016-02-20
Don't want to get into an argument about NFS vs Samba. This is just meant to be informational.

From: [https://support.apple.com/en-us/HT204445](https://support.apple.com/en-us/HT204445)
> When you connect from a Mac using OS X Mavericks or OS X Yosemite to  another computer using file sharing, your Mac automatically tries to use  the Service Message Block (SMB) protocol to communicate. If SMB is not  available, OS X tries to connect using Apple File Protocol (AFP).
Apple replaced it own afp protocol with it's own in-house implementation of SMB ( i.e., Samba ) starting with Mavericks.

---

### Post by QDR06VV9 on 2016-02-20
Hey Morbius1 Thanks this looks like very useful.

---

