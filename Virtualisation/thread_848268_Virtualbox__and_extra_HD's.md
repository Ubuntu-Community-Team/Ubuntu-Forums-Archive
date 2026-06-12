---
title: "Virtualbox  and extra HD's"
date: 2008-07-03
forum: Virtualisation
---

### Post by jonwh25 on 2008-07-03
All,

I'm fairly new to Ubuntu and installed Virtualbox on 8.04. I then put XP Home on it and I am wondering if there is a way I can see my other Hard drives.

What I mean is that I have 1 SATA disk drive which is my primary disk which Ubuntu is on.

I then have 2 IDE disks which I had used for Windows NTFS storage when the SATA  disk was just a windows box. 

So I want to be able to access those disks inside Virtualbox... is that possible??

---

### Post by milosz.galazka on 2008-07-03
The answer is [here]("http://ubuntuforums.org/showthread.php?t=604000")

---

### Post by bodhi.zazen on 2008-07-03
IMO it is best to use a network protocol, ie samba, nfs, http, ftp, sshfs.

For example here is a how to samba: [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

It is for VMWare but could easily be adapted.

---

