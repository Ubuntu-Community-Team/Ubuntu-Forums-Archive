---
title: "Very Strange problem with Virtualbox shared folders"
date: 2009-01-16
forum: Virtualisation
---

### Post by LightEngineer007 on 2009-01-16
I have run into a very strange problem with Ubuntu 8.10 Host and Virtualbox 2.0.x and 2.1.0. Windows XP is the guest. I have 3 different computers with similar setups doing the exact same thing. I have also been running this same setup on Ubuntu 7.10 and 8.04 for the last year with no problems like this. I can access my shared folders via the Virtualbox Shared folder method (faster but has the problem) or via Samba (slower but works as expected)

The problem is that the date and time modified on the files change when I copy the file using Windows Explorer. The new copy takes on the current time. Now the really strange thing happening is that the original files modified date is also changing to "May 9, 1913". If it were just the copy taking the new date I would normally think this was a Linux file or group ownership problem. But I have never seen the date of the original file change with this. 

Currently my username and my user group own the shares on the host. I have also tried changing the group ownership to "vboxusers" but still the same problem. 

I was also told by a friend of mine that the whole permissions structure changed first in Hardy then finished in Intrepid. I have not been able to find anything on this searching, but I have had problems with Samba permissions at first that I finally worked out. If anyone knows how all this permission stuff changed, please post me a link to some info on this so maybe it will give me a clue to this. 

Anyone with any ideas?? 

Thanks in Advance
Steve

---

### Post by LightEngineer007 on 2009-01-19
Bump.

---

### Post by sergio982 on 2009-01-21
Hi,
I had almost the same problem few days ago but now I have found a solution to usage VirtualBox shared folders methods in the same way as Samba(shared folder) methods. The problem only persist in combination host Ubuntu and guest Windows XP.

I have Ubuntu 8.10 as Host and VirtualBox 2.x.x. Windows XP (SP3 with latest updates) is the guest. 
I can access my shared folders via the VirtualBox Shared folder method (faster but here was a problem) or via Samba (slower but works as expected).
In VirualBox I run guest OS. Windows XP.  With Windows Explorer I can access my shared folders and inside folder I can create new folders and files. But problem persists when I want to delete them. So I thought that might be permission problem. 
And I check:
$ ls -l /dev/vboxdrv
crw-rw---- 1 root root 10, 62 2007-10-08 13:27 /dev/vboxdrv

Maybe here is the problem. I try to change the group root to vboxusers:
$ sudo chgrp vboxusers /dev/vboxdrv
$ sudo rmmod vboxdrv

$ sudo modprobe vboxdrv

but unsuccessfully. Then I check the rules:
$ dpkg -L virtualbox-ose | grep rules
$ cat /etc/udev/rules.d/50-virtualbox-ose.rules
KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", MODE="0660"

and I see the group is missing. So I modify this line to
KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="vboxusers", MODE="0660"

An restart the session and system and I get the same result:
$ ls -l /dev/vboxdrv
crw-rw---- 1 root root 10, 62 2007-10-08 13:27 /dev/vboxdrv

To bad. Then I try install new version of VirtualBox 2.1.x and check the
$ ls -l /dev/vboxdrv
crw-rw---- 1 root vboxusers 10, 62 2007-10-08 13:27 /dev/vboxdrv

Finally.
I install new version of guest Virtual Additions on WindowsXP (guest OS). And I try manage shared folders with Windows Explorer. And I see strange things (unable to delete folders) that make me realise that are not permission problems. Then I try to use shareware program Total Commander inside Windows XP and manage shared folders via the VirtualBox Shared folder method. Amazing! with this application I get no problems to manage (create, delete and  edit) folders and files shared via the VirtualBox Shared folder method.  
In my case I see only problem with Windows Explorer and VirtualBox Shared folder method. So I use alternative program to manage folders and files. And their response time is quite fast.
I post this report because this interest me and I would like to know if anybody find the same problem.

---

### Post by bearTM on 2009-02-05
I'm experiencing exactly the same issue with Windows XP SP3 (latest) under the latest VirtualBox 2.1.2.

Copy, edit, create - all fast and without issue ... try to delete a file, and explorer locks up ... eventually times out, and then I simply receive the following error:

Cannot delete file: Cannot read from the source file or disk
(screencap attached)

Then the disk/drive is unusable for another timeout period - and afterwards, everything comes right again ... files can be copied, created, edited ... but not deleted through explorer.

I've also tried a 3rd party tool (Teracopy) for dealing with files, but even this application doesn't always work 100%.

Deleting the same files from Nautilus works instantly and without issue, reflected in the shared drive (almost) instantly.

---

### Post by Ng Oon-Ee on 2009-02-05
I've heard noises about VMs which are on NTFS drives (meaning the vmdk is stored on an NTFS drive) having some issues, could this be it?

---

### Post by bearTM on 2009-02-08
I'm using a VDI, which happens to be NTFS (needed for the work I'm doing), but the issue is not with the NTFS drive, but with the shared folder - so I think the fact that the OS is on an NTFS drive is irrelevant.

The shared folder is on an ext3 partition - no issues with the drive under Ubuntu/Nautilus = only from the VM.

Any other ideas?

---

### Post by Ng Oon-Ee on 2009-02-08
Nope, sorry, I have 2.1 working here, I can delete, save, everything.

But I HAVE noticed slow-ness in file transfer. All-in-all I don't know enough about file-systems and the like to say what its about, though.

---

### Post by awest_swe on 2009-08-04
Deleting the network drive mapping and making a new one in XP solved this problem for me. The problem was still there after an upgrade of VBox (to 3.0.2) and guest addons.

---

