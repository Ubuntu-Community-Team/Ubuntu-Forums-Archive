---
title: "Viewing NTFS partitions in VirtualBox"
date: 2008-05-01
forum: Virtualisation
---

### Post by stesosaso on 2008-05-01
My computer set-up is as follow :
4 HD. Hd0,0 contains Win Xp Pro. the 3 other partitions on this HD are SWAP, / (ext3) and /home (ext3). The 3 other HD are NTFS partitions.

I installed on my XP machine, about a month ago, Ubuntu with a Grub Dual Boot.

on 24th of April I installed Hardy Heron in replacement of Gusty Gibbon, by starting from scratch the Linux partitions as described above.

Found the virtualization software VirtualBox, installed it without any problem, USB is running, printer, anything, just I cannot get in touch with my other NTFS drives on my machine...

I have tried via samba, but apparently it is impossible to share a total partition, just folders can be shared via samba...

I have tryed to find a solution via IPs... 
virtualbox : 10.0.2.2 , 10.0.2.15
ubuntu : 192.168.1.0 , 192.168.1.100(dhcp adress of my computer on LAN), 127.0.0.1
no luck at all...

maybe you can help me, finding a solution so that I can read/write on my NTFS drives via an Xp Pro virtualized in VirtualBox (this  virtualized XP is a New installation, ie. I have 2 XPs on my machine, one in dual boot, and the virtualized one)

__________________________________________________________
My knowledge on terminal commands is really limited, My English is maybe not at best too (I am French), So I would appreciate if you could be as precise as possible with the terminal commands and other explanations, as I would like to really understand what I am doing instead of just copy/paste a solution.

My computer knowledge is about 20 years on DOS/Windows, 1 year on OSX leopard, 1 Month on Ubuntu Gusty Gibbon, 1 week on Hardy Heron.

My feelings about ubuntu : that's just great, I love this OS !
and as one of my friends sayed "Solidarity and share are the secrets of LINUX"

---

### Post by stesosaso on 2008-05-04
Nobody has a little idea ?

---

### Post by OldTimeTech on 2008-05-04
Have you tried loading ntfs-3g from Synaptic Package Manager?  It's suppose to let you read all ntfs drives.

---

### Post by stesosaso on 2008-05-05
Thanks for your answer OldTimeTech, but the ntfs-3g lib is installed in standard for the Ubuntu 8.04 Hardy Heron.

Maybe the solution is within samba...

---

### Post by Lord_Phoenix on 2008-05-05
Have you tried using a shared folder ?

I am using the proprietary virtualbox, so if you're going witht the OSE it might not work, but for me shared folders work just fine.

Just define the share on VirtualBox to point to the "Mount" folder on Ubuntu; for me this is */media/disk?* where ? is the disk number.

Then on the Guest OS just Map a Network Drive for each and everyone, actually with Virtualbox the shares should show under Network Neighbourhood, so just right click and select "Map Network Drive".

NOTE: This requires Guest Additions (or whatever they're called) to be installed!

---

### Post by stesosaso on 2008-05-05
> **Lord_Phoenix said:**
> Have you tried using a shared folder ?

I am using the proprietary virtualbox, so if you're going witht the OSE it might not work, but for me shared folders work just fine.

Just define the share on VirtualBox to point to the "Mount" folder on Ubuntu; for me this is */media/disk?* where ? is the disk number.

Then on the Guest OS just Map a Network Drive for each and everyone, actually with Virtualbox the shares should show under Network Neighbourhood, so just right click and select "Map Network Drive".

NOTE: This requires Guest Additions (or whatever they're called) to be installed!

Yes  I have tryed, but in my opinion the problem comme from that the drives are actually NTFS drives and not ubuntu drives...
I am running the proprietary version as my USB is working well in Virtualbox. and the Guest additions are also installed.

I'll give a second try and let you know, thanks for your reply.

---

### Post by Lord_Phoenix on 2008-05-06
> **stesosaso said:**
> Yes  I have tryed, but in my opinion the problem comme from that the drives are actually NTFS drives and not ubuntu drives...
I am running the proprietary version as my USB is working well in Virtualbox. and the Guest additions are also installed.

I'll give a second try and let you know, thanks for your reply.

My PC has 3 Internal Hard-Disks and 1 External (USB 2.0)

With the exception of the one used for Ubuntu, they're all NTFS.
I did install a utility some time ago, a NTFS manager of some kind that allows me to have all my NTFS HDs use ntfs-3g instead of fuseblk (the default) and also makes sure they're all properly mounted at logon (some of them would only get mounted after I selected them under the 'Places' menu).

Maybe that makes a diference ?
I am not currently at home, and I don't remember what it was that I installed, but I can check and let you know, assuming the Shared Folder technique still doesn't work.

BTW, to get this to work on Windows Vista I had to first disable Vista's UAC management.

---

### Post by stesosaso on 2008-05-06
Many thanks **Lord_Phoenix !**
You were right, as soon as my NTFS drives were correctly mounted within Ubuntu, they became accessible within the virtualized XP with the command :

Connect a new Lan drive : path= \\vboxsvr\the name given in the fstab.

I can now close this thread and point it as solved

---

