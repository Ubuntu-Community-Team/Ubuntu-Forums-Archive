---
title: "Grub issue in 13.04"
date: 2013-03-15
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-03-15
I was experimenting with Gnome 3.6 13.04, when I decided to install 'ubuntu-gnome-desktop' and 'ubuntu-gnome-default-settings', to further enhance my experience. Using synaptic to do so, all went smoothly. Closed out of the app, then proceeded to reboot my PC. 

My PC screen went darker, and after a few moments I was re-offered the option to restart my PC. I chose yes, then waited a few more moments and nothing happened. So I did a manual switch off.

Now, when I restart, I get this message:

[COLOR="#000080"]GNU GRUB version 2.00-13ubuntu2

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>[/COLOR]

What do I do next to get this booting properly again??

Cheers.

---

### Post by oldfred on 2013-03-15
You may have switched off too soon. Always remember the elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

You may need to run chkdsk.
      
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Then try Boot-Repair or post link to BootInfo report.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Baldrick_NZ on 2013-03-16
Thanks! Worked a treat.

How does one mark the thread as solved now? The option seems to have been taken out of 'Thread Tools' now.

---

### Post by cariboo on 2013-03-16
> **Baldrick_NZ said:**
> Thanks! Worked a treat.

How does one mark the thread as solved now? The option seems to have been taken out of 'Thread Tools' now.

I marked the thread as solved for you, but in the future, just edit your first post, and change the prefix to solved.

---

### Post by Baldrick_NZ on 2013-03-16
Very cool. Thanks guys!

---

