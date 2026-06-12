---
title: "VMWare won't recognize usb hard drive"
date: 2008-09-28
forum: Virtualisation
---

### Post by Roundel on 2008-09-28
Hi,

I'm running Windows XP on VMWare Server 1.06 with Hardy 8.04 as my host.  VMWare will not recognize my USB harddrives (I have 2, one FAT32 the other NTFS, and both are recognized by Hardy).  I've tried the fix using the fstab file, etc, but the only thing that seems to work is manually making a new drive as detailed [here]("http://ubuntuforums.org/showthread.php?t=700029&highlight=usb+hard+drive").

Can anyone help me find a way to get VMWare to recognize the drives automatically so I can add them to the Windows "My Computer" area?  It's a pain to have to manually add them...

Thanks!

* Uppdate:I read somewhere that allowing a hard drive to be mounted by both ubuntu and the XP virtual machine can hurt the hard drive.  Is this true?

---

### Post by fjgaude on 2008-09-28
Well, I use a raid5 array under both Ubuntu and VMware WinXP. Remember when you are on the Windows side you are actually in NTFS and that can't read ext3 Linux. So we use Samba to convert going and coming.

Setup **Samba** in Ubuntu, issue the password for your login, and make sure you have a workgroup setup. Then after a reboot, you should be able to go into the Windows network, using Filemanager, i.e, **Explorer**, and see the drive.

Although I can't see why the USB drive isn't recongized in the VM tab, Removeable Devices/USB Devices, if you have done all that has been shown to setup USB support, especially adding this line in /etc/fstab:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That should permit USB devices of all kinds to show.

---

### Post by Roundel on 2008-09-29
Thanks for your help!  Yeah, I haven't tried Samba yet so I'll look into that and see if it's a good solution.  

I've added that line to my fstab but I'm still running into problems on the VMWare recognition.  Its been a while since my last reformat, so I'm thinking about just doing that (or at least uninstalling VMWare) and trying VM 2.0 on my next install (the new version of 2.0 looks fairly stable).  I'll let you know if I still run into problems.

Thanks again.

---

### Post by fjgaude on 2008-09-29
Okay, keep us informed if you success with your efforts.

---

