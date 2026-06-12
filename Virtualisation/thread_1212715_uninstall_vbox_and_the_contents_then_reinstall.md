---
title: "uninstall vbox and the contents then reinstall"
date: 2009-07-14
forum: Virtualisation
---

### Post by Mia1990 on 2009-07-14
Ok i need to uninstall windows xp from virtual box 3 and start all over how could i do this?

---

### Post by aesis05401 on 2009-07-14
Not sure what you mean by start all over..

If you are looking to kill everything in your .vdi so you can reinstall from scratch into the existing virtual hard drive then do the following:
1. Download the GParted livecd .iso (or another livecd utility distro)
2. Go to the VBox main screen while no VM is running, select your XP install, and point the cdrom to the GParted .iso image. 
3. Turn the VM on - it should boot into the GParted livecd where you can blow away/reformat the disk space. 
4. Turn off VM.
5. Unmount Gparted iso livecd
6. Point XP VM to Windows install .iso
7. Turn VM back on to begin installation.

Does this help?

---

### Post by Mia1990 on 2009-07-14
Maybe i am trying to do a fresh install of everything.Deleting virtual hard drive and all.

---

### Post by aesis05401 on 2009-07-14
> **Mia1990 said:**
> Maybe i am trying to do a fresh install of everything.Deleting virtual hard drive and all.

Alright.  Virtualbox has a 'Virtual Media Manager' that should be listed in the 'File' menu.  Provided your VM is not running you will be able to select the virtual drive and 'Release' it to remove the association linking the virtual drive with the virtual machine.  

Once this is done the 'Remove' button will become active (no longer grayed out).  Clicking 'remove' should kill the .vdi altogether. 

As a guy who uses a lot of virtualization, let me suggest looking into keeping separate data partitions within each of your virtual harddrives.  This makes thing very easy when you want to kill a VM but keep all the files you were using.  

Yes, there are other ways to do this, but I find moving whole partition images around to be much simpler than other backup alternatives. 

Post back if you have problems.

---

### Post by Mia1990 on 2009-07-15
> **aesis05401 said:**
> Alright.  Virtualbox has a 'Virtual Media Manager' that should be listed in the 'File' menu.  Provided your VM is not running you will be able to select the virtual drive and 'Release' it to remove the association linking the virtual drive with the virtual machine.  

Once this is done the 'Remove' button will become active (no longer grayed out).  Clicking 'remove' should kill the .vdi altogether. 

As a guy who uses a lot of virtualization, let me suggest looking into keeping separate data partitions within each of your virtual harddrives.  This makes thing very easy when you want to kill a VM but keep all the files you were using.  

Yes, there are other ways to do this, but I find moving whole partition images around to be much simpler than other backup alternatives. 

Post back if you have problems.

Thank you sooo much that worked perfect now if i could find a way to get usb working when i reinstall everything i will be ready when the college year startes

---

### Post by aesis05401 on 2009-07-15
> **Mia1990 said:**
> Thank you sooo much that worked perfect now if i could find a way to get usb working when i reinstall everything i will be ready when the college year startes

Hmmm.  Make sure you are using the closed source version, not VirtualBox OSE.

Here is the explanation of differences between versions.  Both are free, but the open source edition (OSE) excludes USB and a couple other things.

Link:[http://www.virtualbox.org/wiki/Editions]("http://www.virtualbox.org/wiki/Editions")

Best of luck.

---

### Post by Mia1990 on 2009-07-15
ok i have free for personal use version or the closed source version downloaded i need to get usb working on it and i have had no luck can anyone help i'll be installing win xp pro on it

---

### Post by aesis05401 on 2009-07-15
> **Mia1990 said:**
> ok i have free for personal use version or the closed source version downloaded i need to get usb working on it and i have had no luck can anyone help i'll be installing win xp pro on it

Is USB working on your host install?

---

### Post by Mia1990 on 2009-07-15
no i cant get my printer to work on it and my mp3 player says mtp device but it does not install the driver for it someone please help i at least need to get my printer to work.

---

### Post by aesis05401 on 2009-07-16
> **Mia1990 said:**
> no i cant get my printer to work on it and my mp3 player says mtp device but it does not install the driver for it someone please help i at least need to get my printer to work.

Hey, to get the fastest response on those issues you should start new threads with descriptive titles.  I could try to walk you through those things, but I don't have personal experience with any of that. 

I'm sure someone will be able to help you out. Good luck.

---

### Post by Mia1990 on 2009-07-16
thank you I'll start a new one as i really need to get this to work in a few weeks

---

### Post by tacantara on 2009-07-16
Once you install the Guest Additions in VB, you should find that the USB support will be in place.  The Guest Additions also allow you to run in seamless mode, and do a bunch of other neat things.  To activate the Guest Additions, start your virtual machine then click Devices > Install Guest Additions.

---

