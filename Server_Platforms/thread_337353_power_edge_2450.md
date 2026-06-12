---
title: "power edge 2450"
date: 2007-01-12
forum: Server Platforms
---

### Post by BillGod on 2007-01-12
Does anyone know if edgy server has drivers for a Dell 2450 server perc raid controller?  I am planning on ditching my AD server and going to Ubuntu server but I dont want to start the process until I know there are drivers for it.

---

### Post by Mike'sHardLinux on 2007-01-12
Hi. My 2450 says it has the Perc/3, I believe. Does that sound right? Anyway, Ubuntu sees the RAID 5, installs and runs on it fine. I just haven't yet found the software to monitor the array and do stuff like disable a drive to remove/replace it if needed.

---

### Post by BillGod on 2007-01-13
Sweet thanks ... on to the next project :)

---

### Post by jamesT0723 on 2007-10-05
I have also had the same problem. 
I have only successfully load Server 6.06 Alt to load.

Completely unable to run GUI on server after successfully installing 6.06.

I will be testing 7.1 beta, but I am not expecting good results.

I would be more than willing to work with any one that thinks they can help.

James

---

### Post by wirelessmonkey on 2007-10-06
Mike'sHardLinux - mdadm can monitor your array.

James - The server install does not have a gui.  You'll have to apt-get ubuntu-desktop, kubuntu-desktop, or other.

---

