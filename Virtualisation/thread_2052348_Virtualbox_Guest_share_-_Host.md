---
title: "Virtualbox Guest share - Host"
date: 2012-09-03
forum: Virtualisation
---

### Post by manuleka on 2012-09-03
Platforms:
Host - Kubuntu 12.04.1
Guest - Windows XP Pro
Virtulabox - Version 4.1.12


I'm trying to enable sharing files/folders between a VirtualBox Guest Windows XP Pro with my Kubuntu 12.04.1 Host

Now i've installed samba, enabled a few shared folders on Kubuntu, I've also enabled sharing a few folders on the Windows XP Guest (VirtualXP)...

Under VirtualXP i can't see any of the shared folders from host...

I did the same setup with LinuxMint KDE 13 on a friends machine and after enabling share i can view the shares on host from guest immediately

help please

---

### Post by opensshd on 2012-09-03
Have you configured smb.conf (samba's conf file?)

Interesting link here, might help: [http://blog.fekw.de/2008/07/13/vmware-shared-folders-using-samba-server/](http://blog.fekw.de/2008/07/13/vmware-shared-folders-using-samba-server/)

---

### Post by manuleka on 2012-09-03
> **opensshd said:**
> Have you configured smb.conf (samba's conf file?)

Interesting link here, might help: [http://blog.fekw.de/2008/07/13/vmware-shared-folders-using-samba-server/](http://blog.fekw.de/2008/07/13/vmware-shared-folders-using-samba-server/)

thanks i needed to create an account on samba so i can use it for accessing from the vm... 

maybe mint automatically sets this up

---

### Post by opensshd on 2012-09-04
:) \o/

---

### Post by Dedoimedo on 2012-09-04
Did you install guest additions?
Dedoimedo

---

### Post by manuleka on 2012-09-04
> **Dedoimedo said:**
> Did you install guest additions?
Dedoimedo

yes guest addition has been installed

---

### Post by Dedoimedo on 2012-09-06
Did you try to manually mount the shared folder?
Perhaps they are simply not automounted.
Dedoimedo

---

