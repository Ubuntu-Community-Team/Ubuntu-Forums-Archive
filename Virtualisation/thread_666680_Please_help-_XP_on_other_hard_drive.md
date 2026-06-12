---
title: "Please help- XP on other hard drive"
date: 2008-01-13
forum: Virtualisation
---

### Post by davesbrain on 2008-01-13
How would I 'boot up' XP in Ubuntu?  I already have XP installed to my master on IDE.  Ubuntu is installed to the slave drive.   Each use the entire partition on thier own drive respectively and I use the bios to switch when rebooting.  
(Also note: when I first installed Ubuntu I disconnected the XP drive and jumper'ed slave as master temporarily to avoid confusion. I then plugged my XP drive back in and set the jumpers on the Ubuntu drive to slave, and just use the bios to switch as mentioned above.)
So I now have:    masterC XP(uses entire partition)
                                        slaveD Ubuntu(uses entire partition)

---

### Post by fjgaude on 2008-01-13
I'm not sure if you are wishing dual-boot or running Windows in a virtual mode under Ubuntu.

You can dual boot, leaving your BIOS pointing to the Ubuntu drive, by adding something like this to your /boot/grub/menu.lst file:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

You have to first determine what the drive is called, if /dev/hda1 or /hdb1, from which you boot Ubuntu. Do this by entering in a terminal this command:

```
sudo fdisk -l
```

From there you'll see if Ubuntu's drive is hdb or not. I don't use Master, Slave PATA drives anymore.

Now if you wish to actually have XP inside of Ubuntu you have to install VMware Server and then re-install XP in the Server. That's the way I run my main box and laptop. This HOW-To might be of help:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

Good luck but do let us know how you are doing.

---

### Post by davesbrain on 2008-01-13
Hmmm....I was wanting to run the Windows XP thats already installed on the other hard drive within Ubuntu.
By the way, I am really liking this Ubuntu Linux.

---

### Post by yottabit on 2008-01-14
You should be able to boot your XP installation from VMware Server by choosing "Advanced" when setting up the new VM. Choose to use a physical hard disk instead of a virtual disk, and point it to your XP drive.

You will need to boot XP natively first and create a new hardware profile, and then choose this profile when booting XP in the VM. Otherwise you will get the BSOD because XP will not be able to access the hard disk due to the native driver loaded, which is different than the VM driver. Choose a new hardware profile will force XP to load the low-performance Standard IDE driver and re-detect all hardware once in the VM. Don't forget to install the VMware Tools in the guest, and turn on Clock Sync option in VMware Tools!

If you get a message saying "NTLDR compressed" when trying to boot XP in the VM, just let me know and I'll tell you how to work around it.

J

---

### Post by fjgaude on 2008-01-14
> **yottabit said:**
> You should be able to boot your XP installation from VMware Server by choosing "Advanced" when setting up the new VM. Choose to use a physical hard disk instead of a virtual disk, and point it to your XP drive.
[...]
J

You mean "Custom" first then later "Advanced"?

---

### Post by yottabit on 2008-01-14
> **fjgaude said:**
> You mean "Custom"?

Yup! ;)

---

### Post by davesbrain on 2008-01-14
Perhaps someone could walk me through the VM server wizard.  
XP is on hda1, and thats what I want to load/boot within Ubuntu.  Overall I would like to have it be in a fullscreen window on another 'workspace' desktop in Ubuntu.   I have the Compiz cube going on and I would like to flip it over to a desktop that has my XP from master or hda1.  Anyways, thanx in advance for the help and support.  
My fdisc reads as follows:
(note: the scsi drive at the bottom(sda1) is used for backups/junk only)

Disk /dev/hda: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc77ec77e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1867    14996646    7  HPFS/NTFS

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c2de3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1744    14008648+  83  Linux
/dev/hdb2            1745        1826      658665    5  Extended
/dev/hdb5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7864361e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2231    17920476    7  HPFS/NTFS

---

### Post by yottabit on 2008-01-14
File -> New Virtual Machine... -> Next -> Custom -> Next -> blah blah -> (Disk) Use a physical disk -> /dev/hda -> blah blah -> Finish.

When you boot the VM you'll see your GRUB menu where you should be able to select Windows XP. Be careful never to select your Ubuntu in this menu or you will have some issues trying to boot your OS twice!! haha.

Also remember that before you attempt to load XP in the VM, you need to boot it natively and create a new Hardware Profile. You'll then get the opportunity to select this Profile when XP is loading. I named my XP profiles "Native" and "Virtual" to make it obvious. ;)

J

---

### Post by davesbrain on 2008-01-14
I did create a new hardware profile in XP, however it is second on the list(not sure if this effects anything)
Rebooted, bios switch over to my Ubuntu drive...and fired up Ubuntu.

In the VMware(v1.0.4 build-56528) I click new...the wizard opens
click next
I chose custom
click next
I chose Windows XP Pro (thats what it is)
click next
The next window has Name: Windows XP Pro and Location:/var/lib/vmware-server/Virtual Machines/Windows XP Professional  (with a browse button next to it)
click next
Number of processors one or two( I have one)
click next
Access Rights:  Make this virtual machine private check or not(tried both)
Memory: it suggests 192 or 276 max.  
click next
Network connection:  I chose "Do not use network connection"
click next
Ide Atapi:
click next
Disk:  choises are Creat new virtual disc, use existing virtual disk and use physical disc.  I chose use physical disc
click next
Select physical disc:  I chose hda and use entire disk
click next
Specify Disc File:  has "Windows XP Professional.vmdk" in the field. 
click finish
And I get the following error...."Unable to complete wizard, Insufficient permission to access file"

---

### Post by yottabit on 2008-01-14
okay you need to create the vmx file in your homedir instead of wherever VMware wants to put it by default, which you apparently do not have the permissions to access. Alternative you can run the vmware console in superuser mode, by doing "gksudo vmware-console" or whatever the vmware executable is called... that may or may not work to give you the perms you need... if you do use this method you must make sure you don't set the VM to private or you won't be able to access the vmx file as your normal user... Another approach is to go to the console and change the permissions on the dir (and all subdirs) that are being used by default by vmware... something like this "sudo chown -R :usergroup VMware_directory; sudo chmod -R g+rwX".

J

---

### Post by davesbrain on 2008-01-14
Thanks for all the help folks.  But I think I need to put this on hold as I seem to be having an issue with my quit/shutdown button.  It freezes everything for a couple of minutes before displaying the restart/shutdown/hibernate/etc.. window.

---

### Post by davesbrain on 2008-01-15
Fixed it.  Turns out it was the gnome power management under the session window was disabled.  Thanks again for the help.  I'm sure I'll be back.

---

### Post by davesbrain on 2008-01-19
To those who were helping before...I'm giving it another go.  I got past the wizard and it starts to load Windows, then abruptly blue screens.
I did create a new hardware profile named 'VMware', and within that profile I updated the ide channel drivers to "standard" as recomended on squidoo website.  now stuck.

---

### Post by davesbrain on 2008-01-19
Never mind...I got it all working.   Thank you for the help though.  :)

---

