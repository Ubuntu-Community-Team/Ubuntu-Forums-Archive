---
title: "Vmware Image &amp; writing to HDD"
date: 2006-11-25
forum: Server Platforms
---

### Post by ninocass on 2006-11-25
I have a VMware image of ubuntu server on my desktop (XP).

I have mounted a 250GB SATA drive for the server to store data to (torrentflux mainly)

Everything runs grand any my torrents download to the 250GB drive however i cannot seem to access these via the windows OS.

Im the VMware settings i have set up the HDD as:

Independant (disks are not effected by snapshots)
  *Changed are immediatly and permenantly written to disk

Do i need to restart the server and my XP machine to acees the downloaded files via windows?

Should i set up a samba/FTP share to access the files and pull them over the network?

Thanks for any help

Nino

---

### Post by stickboy2642 on 2006-11-26
I think you will have to set up a samba share on the VMware image.  The virtual file system is actually just a file inside of the vmware directory on the windows drive, so accessing files directly on the virtual machines is not possible from the host computer.  I have never done it, but setting up a samba share on the ubuntu computer should work fine and make the files accessible from the windows computer.

---

### Post by gRoberts on 2006-11-26
> **stickboy2642 said:**
> I think you will have to set up a samba share on the VMware image.  The virtual file system is actually just a file inside of the vmware directory on the windows drive, so accessing files directly on the virtual machines is not possible from the host computer.  I have never done it, but setting up a samba share on the ubuntu computer should work fine and make the files accessible from the windows computer.

You can setup a shared folder in VMWare that will appear in the UNC Path

\\.host

Then you can copy and paste files between the host and the hosted image.

If you goto the preferences there is a option for Shared Folders, simply click add, set a name and the path you want it to reflect.

I had to use this because I was about to reinstall edgy and my I didn't have write support on my ntfs backup drive. So I ended up loading my XP image and copying the files across like that.

---

