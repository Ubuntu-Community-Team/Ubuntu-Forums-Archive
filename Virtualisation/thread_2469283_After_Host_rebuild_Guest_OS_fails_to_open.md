---
title: "After Host rebuild Guest OS fails to open"
date: 2021-11-24
forum: Virtualisation
---

### Post by Jonners59 on 2021-11-24
I have been have a bit of a mare these past 3 days.  My host, xUbuntu  started playing up and needed an upgrade that resulted in a rebuild.   Now on 21.10 5.13.0-21-generic (64bit)

I am running Version 6.1.26_Ubuntu r145957 of VirtualBox

The Guest is Debian 9 specifically for running 3CX IP-PBX.

I  have two sepetrate partitions, one for VIRTUALBOX and the other for  .VIRTUALBOX and they both auto mount in Home/"user"/   That has been the  setup for the past 8 years and has worked flawlessly, even if I have  had to rebuild the machine.

The error message I am getting is
> [INDENT]Failed to open virtual machine located in /home/administration/VirtualBox/3cxServer/Debian/Debian.vbox.

Could not find an open hard disk with UUID {5cc89e6a-7588-4d58-8000-169b8d225531}.

Result Code: VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
Component: VirtualBoxWrap
Interface: IVirtualBox {d0a0163f-e254-4e5b-a1f2-011cf991c38d}

[/INDENT]

I  had to move "HOME" when rebuilding to allow for an EFI partition.   Could that be the cause, as it says partition number (UUID) has changed?   And if so how do I fix this?

---

### Post by lammert-nijhof on 2021-11-25
You have to change or add those partitions with the correct UUID in /etc/fstab

---

### Post by Jonners59 on 2021-11-25
> **lammert-nijhof said:**
> You have to change or add those partitions with the correct UUID in /etc/fstab

Thank you, but no, not virtual machines.  These are virtual.  I understand that one opens the VM's .vbox file in a text editor to find that hard disk file  with the UUID shown, then see where Virtualbox is looking for the file.  If you see only the disk file's name and no path, then the file should  go:

[LIST]
[*]in the VM folder with the VM's .vbox file, if the disk file name is a text name, probably named after the VM name.
[*]in the VM's Snapshots folder, if the name of the disk file is the UUID.
[/LIST]
Either  put it back where Virtualbox wants it, or -carefully- edit the .vbox  file to put the new absolute path to the file in the XML. You have to be  sure no Virtualbox processes are running before editing the .vbox file,  or your changes will be overwritten. Look at other VMs that have disk  files stored outside the VM's folder to see how an absolute path to a  disk file looks.

---

### Post by MAFoElffen on 2021-11-25
(FYI: People are here to try to help. trying not to assume that all things are known or not... If you want help, it may be helpful to not assume "that" people are talking down to you. That is most usually not the case, as a baseline. Just as Post #3 from you, in some respects could be interpreted by some as somewhat condescending. Just as I suspect, that was not your intent either. Just saying.... We are all here to help each other.)

Or... Sometimes easier... 

Recreate a new VM Guest using the existing VM disk image file, which will use the existing detail specifics without having to edit anything manually. But use any updated options in the new version and options of current version's VM Guest configuration file.  

Just another perspective or technique.

EDIT: It might sound like a bug now a-day's if you have to do that... But many years ago, that is exactly what you had to do when a VM Host updated. There was no automatic rebuilding or updating of VM Guest config files, you imported those into the new system. Archaic by today's standards right?

---

### Post by Jonners59 on 2021-11-26
> **MAFoElffen said:**
> (FYI: People are here to try to help. trying not to assume that all things are known or not... If you want help, it may be helpful to not assume "that" people are talking down to you. That is most usually not the case, as a baseline. Just as Post #3 from you, in some respects could be interpreted by some as somewhat condescending. Just as I suspect, that was not your intent either. Just saying.... We are all here to help each other.)

Or... Sometimes easier... [/QUOTE
Sorry, but it's not condescending at all.  It's a simple confirmation that the suggestion is incorrect and an explanation why - from help I am getting from Oracle VB forum, which incidentally I never took as condescending.  Then an answer to how to fix it, which would help anyone who has the same problem.  I am all too aware that this is people trying to help (as I too have done for 13 years) and the first to step on insults and patronising.  I am also very aware that these blogs are there to help others and tend to ramble on with no direction making them useless to others.  I think you misread my reply.


[QUOTE=MAFoElffen;14068656]Recreate a new VM Guest using the existing VM disk image file, which will use the existing detail specifics without having to edit anything manually. But use any updated options in the new version and options of current version's VM Guest configuration file.  

Just another perspective or technique.

EDIT: It might sound like a bug now a-day's if you have to do that... But many years ago, that is exactly what you had to do when a VM Host updated. There was no automatic rebuilding or updating of VM Guest config files, you imported those into the new system. Archaic by today's standards right?

Thank you, but I have tried that too, but it didn't work.   After trying to fix the problems with playing about  I then did a fresh install (xUbuntu) which required I move two partitions around and add a 3rd, which created the new error as above. And a new Guest also had errors.  And I've reinstalled again with Ubuntu distro and still have problems - no network on the guest.  I do believe that the latest builds have bugs.  I've had screen resolution issues on the host, no fix, and no network on the guest and no discs, so can't install updates and fixes to the guest os.

Stage I am at now is I have a new host installation of Ubuntu, and VBox.  I have no network share on the host regardless of samba.  I have no network on Guests and I can't see any attached devices, namely USB sticks on Guests.  If I can get over these, I'm back up again.

---

### Post by MAFoElffen on 2021-11-26
Whtat are the configuration settings of the VM Guest that are graphics related? What resolution was it before? What is it stuck at now?

When you say stuck... Do you mean that it does not show any other options in setting of the guest?

If you run the Forum's 'system-info' script in my signature line, let's see what hardware and settings information the VM Guest see's itself... That is the important thing.

---

### Post by Jonners59 on 2021-11-26
OK sorted.  I found that the MAC address had changed and I work on fixed.  Put the old address in and not only did the LAN work but so did the attached devices.

---

### Post by Jonners59 on 2021-11-26
> **MAFoElffen said:**
> Whtat are the configuration settings of the VM Guest that are graphics related? What resolution was it before? What is it stuck at now?

When you say stuck... Do you mean that it does not show any other options in setting of the guest?

If you run the Forum's 'system-info' script in my signature line, let's see what hardware and settings information the VM Guest see's itself... That is the important thing.
Thank you.  Seemed to not get your notification, so missed replying.

Graphics are still not as good, but that's an issue with the host as that is limited.  Better since moving back to Lightdm and being able to switch to xfce which allows a higher resolution and recognises the screen, but still no proprietary or additional drivers.  Never seen the like of it.

Anyway, a subject for a different query.

Thank you for your help.

---

### Post by MAFoElffen on 2021-11-26
For VBox 3D Graphics to work... You are right that the Host's Graphics need to work and be sorted out.

On the Host:
```

sudo lshw -C video
xrandr -q | egrep --color=never -e 'Screen' -e 'connected primary'

```

---

