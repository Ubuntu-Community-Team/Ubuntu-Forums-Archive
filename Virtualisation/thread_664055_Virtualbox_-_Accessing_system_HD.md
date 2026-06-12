---
title: "Virtualbox - Accessing system HD"
date: 2008-01-10
forum: Virtualisation
---

### Post by jmclein on 2008-01-10
I am wondering if any one knows how or if it is possible to access your system hard drive from within a visualized OS when running Virtualbox.  The virtual HD is great for system stuff but I really need to be able to access the files on my hard drive.

Thanks!

---

### Post by fjgaude on 2008-01-10
You do it through creating shares in Samba while in Ubuntu: System/Administration/Shared Folers menu in Gnome. Then you use Network in Windows to access the shares, the drives, folders you have declared as shares.

---

### Post by disturbed1 on 2008-01-10
You don't need samba enabled or system folder sharing for Virtual OS to see your system drive. It's as simple as the screen shot posted.

---

### Post by jmclein on 2008-01-10
> **disturbed1 said:**
> You don't need samba enabled or system folder sharing for Virtual OS to see your system drive. It's as simple as the screen shot posted.

Good stuff.  I figured there was probably a easy way to do it and I just didn't know how.  Thanks!

---

### Post by fjgaude on 2008-01-11
You do setup shares in Ubuntu? Yes/no.

---

### Post by disturbed1 on 2008-01-11
> **fjgaude said:**
> You do setup shares in Ubuntu? Yes/no.

I never have.

The files you set up to share in Virtual Box, will show up in Windows' Networking under "Entire Network\VirtualBox Shared Folders\" as documented in by the text tools in shared folder options, and section 4.4 of the help manual.

---

### Post by fjgaude on 2008-01-11
Thanks, man.

---

### Post by theZoid on 2008-01-12
> **disturbed1 said:**
> I never have.

The files you set up to share in Virtual Box, will show up in Windows' Networking under "Entire Network\VirtualBox Shared Folders\" as documented in by the text tools in shared folder options, and section 4.4 of the help manual.

If I can chime in on this, I've got that done, but my windows XP program can see the files I want, but can't read them, i.e. I get a program error message saying something like "can't read data"...is this because it's a Windows file sitting on a Linux ext3 partition?....any thoughts?  thanks!

Also, I'm the internet in the Virtual XP machine, but can't see my internal network, even when forcing the ip to be in range.  This would be a BIG help!

---

### Post by fjgaude on 2008-01-12
> **theZoid said:**
> If I can chime in on this, I've got that done, but my windows XP program can see the files I want, but can't read them, i.e. I get a program error message saying something like "can't read data"...is this because it's a Windows file sitting on a Linux ext3 partition?....any thoughts?  thanks!

Also, I'm the internet in the Virtual XP machine, but can't see my internal network, even when forcing the ip to be in range.  This would be a BIG help!

The only thing that might help is to be sure you have your Samba paasword in Ubuntu set:

```
sudo smbpasswd -a yourloginname
```

---

### Post by theZoid on 2008-01-12
> **fjgaude said:**
> The only thing that might help is to be sure you have your Samba paasword in Ubuntu set:

```
sudo smbpasswd -a yourloginname
```

Thanks Frank, I'll check that out.  This is a proprietary tax program, and I don't want to keep my whole life imprisoned in a single .vbi file, but outside the 'system' so I can sync it with my ext HD.

---

### Post by spur on 2008-01-14
> **disturbed1 said:**
> You don't need samba enabled or system folder sharing for Virtual OS to see your system drive. It's as simple as the screen shot posted.
What to do when this doesn't work? I have done this as shown and the folder apears in the folder icn at the bottom with the virtualxp running. I can't find the folder from xp . Its not any where in network folders.

---

### Post by disturbed1 on 2008-01-14
Did you install the guest additions in Windows?

---

### Post by spur on 2008-01-14
I tried but not sure if I did it right. I have installed the complete version of VB downloaded from the site and clicked on device/install guest additions and waited while the cdrom was active, then rebooted the xp and restarted the program to be sure.
Is this correct or do I need to download something or run another command. Reading the help file/manual would suggest I did it right but if it didn't work something went wrong or I did it wrong.

---

### Post by disturbed1 on 2008-01-14
You can tell if the additions are installed by the icon in the system tray next to the clock. If there's no icon, it did not install, icon there, it's fine.

There should have been an installation program pop up in windows with the next, next, next, I agree, yes you can have my first born, next, yes, install, reboot routine :D.

---

### Post by theZoid on 2008-01-14
I can see my files in Virtual XP, but my tax program can't read or write to them as it says the files are 'locked' by another user?  The are set for smb share in unbuntu...the directories that is....any ideas?  I'm beating my head against the wall over this one :D

thanks!

---

### Post by fjgaude on 2008-01-14
> **theZoid said:**
> I can see my files in Virtual XP, but my tax program can't read or write to them as it says the files are 'locked' by another user?  The are set for smb share in unbuntu...the directories that is....any ideas?  I'm beating my head against the wall over this one :D

thanks!

You aren't accessing these files first in Ubuntu and then trying to do the same in virtual Windows?

These files are for Windows only use?

Did you install the program that runs these tax files in Windows?

If these files are on a Ubuntu partition, you can make sure the ower is you, using the chown command.

You do have your samba password installed in Ubuntu, yes?

---

### Post by theZoid on 2008-01-14
> **fjgaude said:**
> You aren't accessing these files first in Ubuntu and then trying to do the same in virtual Windows?

**No, these are standalone tax data files that are only accessed in Windows, the XP Virtual Machine**.

These files are for Windows only use?
[B]
Yes[/B]

Did you install the program that runs these tax files in Windows?

**Yes, it installed and runs fine.**

If these files are on a Ubuntu partition, you can make sure the ower is you, using the chown command.

**Yes, they are on a ubuntu ext3 /home partition.  I have their parent directory like 04data, 05data, etc marked for read/write samba sharing.  I have NOT done ownership...how do I do the chown command?**

You do have your samba password installed in Ubuntu, yes?

**I have done a set smbpasswd to "username", me, but that didn't work?**


Please see above....thanks much!

---

### Post by disturbed1 on 2008-01-15
If you're attempting to set up samba, this is completely different than Virtual Box shared folders. Are you attempting to read/write to a directory you actually have read/write permissions to?

[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

^^ See that for samba configuration. Once you have samba set up, the folder will then be shared through samba, and not Virtual Box. So, instead of attempting to mount the network share under Virtual Box Shared folders, the share would then be under Windows Networking\ Your-Workgroup\ Your Share.

As seen by the screen shot I have No Samba Shares, I have Virtual Box shares ;) Perhaps you should head over to the Virtual Box forums, where they can better walk you through the setup.

---

### Post by theZoid on 2008-01-15
> **disturbed1 said:**
> If you're attempting to set up samba, this is completely different than Virtual Box shared folders. Are you attempting to read/write to a directory you actually have read/write permissions to?

[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

^^ See that for samba configuration. Once you have samba set up, the folder will then be shared through samba, and not Virtual Box. So, instead of attempting to mount the network share under Virtual Box Shared folders, the share would then be under Windows Networking\ Your-Workgroup\ Your Share.

As seen by the screen shot I have No Samba Shares, I have Virtual Box shares ;) Perhaps you should head over to the Virtual Box forums, where they can better walk you through the setup.

Yep, that's a goog idea too I guess ;)  I can see the folders like that, just can't read or write to them.  Last time I had this set up in Ubuntu (previous install) I could though....that's why I thought i've got someting set wrong with the folders in ubuntu.

---

### Post by disturbed1 on 2008-01-15
What directory are you attempting to share? Right click on that folder in Linux and check the permissions. **USER** need to have read and write permission. Since **USER** is running Virtual Box, these permissions are inherited. 

**USER** is of course the user name of the Linux User currently logged in an running Virtual Box.

Also, there is a Linux group now called vboxusers. Make sure you are a member of that group. System -> Administration -> Users and Groups. Click on manage groups, find vboxusers, click properties, and make sure your name is checked as being in the group. You have to log out then back in for this to take effect.

---

### Post by theZoid on 2008-01-15
> **disturbed1 said:**
> What directory are you attempting to share? Right click on that folder in Linux and check the permissions. **USER** need to have read and write permission. Since **USER** is running Virtual Box, these permissions are inherited. 

**USER** is of course the user name of the Linux User currently logged in an running Virtual Box.

Also, there is a Linux group now called vboxusers. Make sure you are a member of that group. System -> Administration -> Users and Groups. Click on manage groups, find vboxusers, click properties, and make sure your name is checked as being in the group. You have to log out then back in for this to take effect.

thanks disturbed1....I checking all that out now.....thanks!  I'll 'port back for future generations....:D

---

### Post by theZoid on 2008-01-15
Disturbed.....I set my permissions for owner and user to read and write, same problem....however, I think the program itself might be stopping me because it sees the files as on a network, and I only paid for the standalone version.  However, maybe not....Ill try to open a .doc file for something else and see what happens and report back...because I can't remember, but I think I had the same problem trying to open a .txt file with notepad a while back.

in the meantime I've been reading and writing to a usb drive to get the data files out of that .vbi file.

---

### Post by theZoid on 2008-01-17
[SOLVED]  Duh on me....don't throw anything at my avatar guys.  All I had to do was map the shared linux folder containing all the data folders I needed in my XP Virtual Machine, at which time they showed up in explorer as drive Z. The I merely turned on sharing for that drive in the XP Virtual Machine,  Tech support for my tax software helped, as the guy happened to a linux/VM user :D  My tax program needed full control to use the ifles.  Now everything is reading and writing back and forth through the 'virtual wall'.

---

### Post by eagledrc on 2008-03-11
I need help on something related...
[http://ubuntuforums.org/showthread.php?t=718060](http://ubuntuforums.org/showthread.php?t=718060)
Thanks!

---

