---
title: "Performance of shared files in VirtualBox"
date: 2012-01-31
forum: Virtualisation
---

### Post by ofnuts on 2012-01-31
I'm running a VirtualBox 3.2.8 on Ubuntu 10.04. The performance of the box is fine but I need to share files with the Linux side. Ideally I would like to host most application files on the Linux side (makes backups easier among other things). 

But the performance of the built-in "shared folders" is abysmal. I get something better using a Samba mount: the performance is OK to move files across, but not good enough to use files directly.

Is there a better solution? Is performance better in later versions?

---

### Post by japzone on 2012-01-31
I'm running the Latest version of VB on Ubuntu 11.04(Classic UI) and have not encountered any bad performance with VB's Folder Sharing. However, you can't expect much since the File Transfer has to go through several layers of Virtualization. If you want a more "Direct" and speedy transfer then the only way is to use a USB Drive and transfer files using that or while the VM is comepletely Shutdown you can mount the VDI(Not Dynamic, only Fixed) in Ubuntu and copy files over that way(You can use this [**script**]("http://ubuntuforums.org/showthread.php?t=1904077") ). Other than that, there's no other way to access the files besides setting up an FTP server but that's hardly efficiant and speedy.

---

### Post by haqking on 2012-01-31
> **ofnuts said:**
> I'm running a VirtualBox 3.2.8 on Ubuntu 10.04. The performance of the box is fine but I need to share files with the Linux side. Ideally I would like to host most application files on the Linux side (makes backups easier among other things). 

But the performance of the built-in "shared folders" is abysmal. I get something better using a Samba mount: the performance is OK to move files across, but not good enough to use files directly.

Is there a better solution? Is performance better in later versions?

never had a performance issue with shared folders, it should be seemless.

However that being said you are running a old version.

Remove and install the latest (you will need to remove current install to install the latest)

You can get the .deb from Virtualbox or Oracle.

You also need the extensions pack

---

### Post by ofnuts on 2012-01-31
OK, thanks to both. I may get a new computer soon and be able to upgrade the whole lot. Will wait until then since there is some hop things will improve.

---

