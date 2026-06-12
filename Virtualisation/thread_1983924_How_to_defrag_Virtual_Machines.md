---
title: "How to defrag Virtual Machines"
date: 2012-05-21
forum: Virtualisation
---

### Post by Rebelli0us on 2012-05-21
Virtual Machines are large files where your Guest OS resides. The “filefrag” command is built into my Ubuntu, so checking fragmentation of my Windows 7 VM:

```
filefrag /home/boo12/VirtualBox\ VMs/w7/w7.vdi 
/home/boo12/VirtualBox VMs/w7/w7.vdi: **147 extents found**

```

That’s **147 fragments**! On the other hand, VMs on NTFS partitions can be defraged using Sysinternals’ “contig” utility.

How do you de-fragment files on ext4 system?

---

### Post by wilee-nilee on 2012-05-21
[http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html)

---

### Post by Rebelli0us on 2012-05-21
> **wilee-nilee said:**
> [http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html)

Thank you, there’s no mention of defrag there. I’m looking for something like:

```
defrag /home/boo12/VirtualBox\ VMs/w7/w7.vdi
```

or even better:

```
filefrag /dev/sdb4
```

Is there such thing?


..

---

### Post by CharlesA on 2012-05-23
Are you using dynamic or fixed disks?

---

### Post by Rebelli0us on 2012-05-24
> **CharlesA said:**
> Are you using dynamic or fixed disks?

I'm using the default "dynamically allocated storage".

---

### Post by CharlesA on 2012-05-24
Ah. the only way I have found to actually "defrag" on ext4 is to copy the file to a different file name, then rename it back to the original.

---

### Post by matt_symes on 2012-05-24
Hi

There is now a defrag tool for ext4 filing systems (the default filing system in new installs of Ubuntu) in the newest version of Ubuntu (12.04) in the package e2fsprogs. 

```
man e4defrag
```

I cannot comment on it though as i have not used it.

Kind regards

---

### Post by CharlesA on 2012-05-24
Thanks for the info, Matt!

I found this too:
[http://ubuntuforums.org/showthread.php?t=1902253](http://ubuntuforums.org/showthread.php?t=1902253)

---

### Post by Rebelli0us on 2012-05-24
> **matt_symes said:**
> Hi

There is now a defrag tool for ext4 filing systems (the default filing system in new installs of Ubuntu) in the newest version of Ubuntu (12.04) in the package e2fsprogs. 

```
man e4defrag
```

I cannot comment on it though as i have not used it.

Kind regards


Thank you, I can&#8217;t do anything in Ubuntu 12.04, it looks like somebody tried to copy Windows 8... and failed. The floating scrollbars are the icing on the cake.

---

### Post by matt_symes on 2012-05-24
Hi

> **Rebelli0us said:**
> Thank you, I can’t do anything in Ubuntu 12.04, it looks like somebody tried to copy Windows 8... and failed. 

If you know how then install your preferred DE. There are many tutorials on the net for this.

> The floating scrollbars are the icing on the cake.

This functionality can be disabled using dconf editor in Unity.

Kind regards

---

### Post by Rebelli0us on 2012-05-24
> **matt_symes said:**
> Hi



If you know how then install your preferred DE. There are many tutorials on the net for this.



This functionality can be disabled using dconf editor in Unity.

Kind regards

Thank you. I have Ubuntu 12.04 in a VM, I boot it occasionally out of curiosity as a former UI designer. I noticed the startup options -- Ubu or Gnome Classic, and I also installed xfce shell. I don&#8217;t enjoy tinkering or feeling lost and having to re-learn computing, but I dislike the MS monopoly even more. Lets hope Linux will be king in mobile devices.

---

### Post by Haneef Mubarak on 2012-05-25
Actually floating sidebars have been in various projects a while before even Vista. Not stable, mind you, but still there...

---

### Post by drs305 on 2012-05-25
Over time my vdi's increase in size. I don't know if this technically defrag's the VM, but I use VirtualBox's compact command in confjuction with zerofree and it reduces the size by quite a bit.

For an Ubuntu VM:

I first do the normal housekeeping within the VM - cleaning out the apt archives, emptying the Trash (including root's), etc.

In the VM, add the Ubuntu ISO and make it the first boot priority in System.
[LIST=1]
[*]Reboot to LiveCD Desktop within the VM.
[*]Enable the universe repository
[*]Install zerofree 
[*]sudo zerofree /dev/sda1  # This is actually the VM's partition w/i VB
[LIST]
[*]Will take 3-5 minutes, no feedback.
[/LIST][*]Close VB
[*]```
VBoxManage modifyhd -compact <vdi location>
```
[/LIST]

---

### Post by Rebelli0us on 2012-05-25
> **drs305 said:**
> Over time my vdi's increase in size. I don't know if this technically defrag's the VM, but I use VirtualBox's compact command in confjuction with zerofree and it reduces the size by quite a bit.

For an Ubuntu VM:

I first do the normal housekeeping within the VM - cleaning out the apt archives, emptying the Trash (including root's), etc.

In the VM, add the Ubuntu ISO and make it the first boot priority in System.
[LIST=1]
[*]Reboot to LiveCD Desktop within the VM.
[*]Enable the universe repository
[*]Install zerofree 
[*]sudo zerofree /dev/sda1  # This is actually the VM's partition w/i VB
[LIST]
[*]Will take 3-5 minutes, no feedback.
[/LIST][*]Close VB
[*]```
VBoxManage modifyhd -compact <vdi location>
```
[/LIST]

Thank you. Compacting VDIs is different from OS-level fragmentation. VirtualBox is unaware of file fragmentation, correct?  That’s an OS file-system isssue.

I simply moved VMs to an NTFS partition, then defragment partition or individual file(s):

Contig.exe -v -s  “C:\...\VirtualBox VMs\*.vdi”


BTW: I noticed that somebody is editing my posts above and issuing subtle warnings. Does this forum have a language police or grammar enforcement?

---

### Post by CharlesA on 2012-05-25
> **Rebelli0us said:**
> Thank you. Compacting VDIs is different from OS-level fragmentation. VirtualBox is unaware of file fragmentation, correct?  That’s an OS file-system isssue.

I simply moved VMs to an NTFS partition, then defragment partition or individual file(s):

Contig.exe -v -s  “C:\...\VirtualBox VMs\*.vdi”

Did you move them back after running contig?


> BTW: I noticed that somebody is editing my posts above and issuing subtle warnings. Does this forum have a language police or grammar enforcement?

Language police, no, but [from the CoC]("http://ubuntuforums.org/index.php?page=policy"):

> Attacks and derogatory terms of any kind are not welcome. This includes references to other operating systems and the companies that produce them.

---

### Post by drs305 on 2012-05-25
> **Rebelli0us said:**
> BTW: I noticed that somebody is editing my posts above and issuing subtle warnings. Does this forum have a language police or grammar enforcement?

You can read who edited and why it was done at the bottom of the post (if the user added a comment as to why the edit was made).

Normal users cannot edit another's post but moderators and forum staff can. In this case, a moderator altered your reference to Microsoft Windows to reflect forum policy. His edit is explained in the 'editing comments' section. If a moderator changes a post a PM is sometimes sent explaining the reason; in this case this may or may not have been done since the explanation is in the post comment itself.

---

### Post by Rebelli0us on 2012-05-28
> **CharlesA said:**
> Did you move them back after running contig?




Language police, no, but [from the CoC]("http://ubuntuforums.org/index.php?page=policy"):

No, VMs run just fine on NTFS partitions, plus you can defrag them as well.



Regarding the censorship issue above. I typed <snip>. Is it really worth your time correcting trivia like that? Wouldn't you rather volunteer to help with global warming?

---

### Post by Iowan on 2012-05-28
I am helping with global warming - but CoC violations will still be corrected.

---

