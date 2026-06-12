---
title: "How-To: Transfer files from Ubuntu to VMware OS"
date: 2008-03-04
forum: Virtualisation
---

### Post by boeing777 on 2008-03-04
I've been trying to find a solution to transfer files from my Ubuntu to guest OS Windows XP under VMware.  I just get a USB key, put all the files in it and then transfer it to the VMware Windows XP.

---

### Post by dcstar on 2008-03-05
> **boeing777 said:**
> I've been trying to find a solution to transfer files from my Ubuntu to guest OS Windows XP under VMware.  I just get a USB key, put all the files in it and then transfer it to the VMware Windows XP.

Yep, or set up Samba on the server and share whatever folders you need to.

---

### Post by adityakavoor on 2008-03-07
Did your  guest XP recognise the USB key ?

---

### Post by HermanAB on 2008-03-08
I use FileZilla on Windoze and Proftpd on Linux.  This is much less hassle than getting Samba to work.

---

### Post by fjgaude on 2008-03-08
Ever since Feisty I've had no trouble getting Samba Shares to work through the gnome menu: System/Administration/Shared Folders. From there set the shares you wish. This is not rocket science.

Then in WinXP go to Network, Entire Network, Windows Network, Workgroup, and there you are seeing your Ubuntu shares. In Ubuntu you had to set the group name. I have always used Workgroup since the late 1980s, so that is what I do now.

Then at the command line you add your password to Samba's:

```
sudo smbpasswd -a yourloginname
```

Nothing more need be done. All the Windows programs can access the shares that way.

---

