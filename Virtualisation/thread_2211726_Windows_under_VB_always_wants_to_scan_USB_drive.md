---
title: "Windows under VB always wants to scan USB drive"
date: 2014-03-17
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-03-17
I'm running Kubuntu 13.10 with Windows 7 Ultimate under VirtualBox.  I save all my work to thumb drives.  When I get into Win 7, I allow it access to a thumb drive and Windows says the drive needs to be scanned for errors.  I let it.  It works.  All is good.  I just wonder why it keeps happening.  The thumb drives, unfortunately, use FAT32 as their file system because I need both Kubuntu and Windows to be able to read them.  Is this the problem -- that yucky Microsoft file system that even Windows doesn't use to on hard drives anymore?  

Options I've considered: 
1. Use NTFS on the thumb drives instead.  Both Kubuntu and Windows can read Microsoft's better file system.  However, NTFS still isn't great, and there must be some reason why thumb drives come with FAT32 instead of NTFS.  I wonder if I'll open up a nightmare of file permission problems.  
2. Use Ext2 and install the driver into Windows that allows it to read an Ext2 drive.  Sounds like it should work, at least in theory.  I've never used the Ext2 driver for Windows.  Does it work well in Windows?  Or does Windows get buggy with it?   Will there be file permission hassles?  
3. Use Ext3 or Ext4 and the Windows driver for it.  Does it exist yet?  
4. Live with FAT32 and just keep letting Windows scan those drives every time I have to use one under Windows.  It does work.  I'm just getting sick of waiting for the thing to scan.

---

### Post by rollingthunderb on 2014-03-17
> **Tom_ZeCat said:**
> I'm running Kubuntu 13.10 with Windows 7 Ultimate under VirtualBox.  I save all my work to thumb drives.  When I get into Win 7, I allow it access to a thumb drive and Windows says the drive needs to be scanned for errors.  ... 

Options I've considered: 
1. Use NTFS on the thumb drives instead.  Both Kubuntu and Windows can read Microsoft's better file system.  However, NTFS still isn't great, and there must be some reason why thumb drives come with FAT32 instead of NTFS.  I wonder if I'll open up a nightmare of file permission problems. ...

I'm a big KDE fan, so I'm with you. While I have windows machines on physical installs, I still see this from time to time. 

Take a look here;


[http://social.technet.microsoft.com/Forums/windows/en-US/44941350-fd71-4a18-8b3f-f8882d4946ea/how-to-turn-off-scan-and-fix-dialog-when-inserting-usb-flash-disk?forum=itprovistasetup](http://social.technet.microsoft.com/Forums/windows/en-US/44941350-fd71-4a18-8b3f-f8882d4946ea/how-to-turn-off-scan-and-fix-dialog-when-inserting-usb-flash-disk?forum=itprovistasetup)


[http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/windows-7-usbflash-drive-if-i-click-scan-and-fix/f08c0dbd-f9c7-4286-a5e7-f61041014351](http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/windows-7-usbflash-drive-if-i-click-scan-and-fix/f08c0dbd-f9c7-4286-a5e7-f61041014351)

I know these are old, and one's even Vista related, yet I see the rogue trash and recycle stuff even though I use NTFS on my flash drives, I just don't get the pop ups you do. 

There could be a more official / technical answer, and I hope you find it. All the best.

---

