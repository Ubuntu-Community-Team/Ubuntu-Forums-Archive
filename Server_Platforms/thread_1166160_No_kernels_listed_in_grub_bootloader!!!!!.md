---
title: "No kernels listed in grub bootloader!!!?!?!"
date: 2009-05-21
forum: Server Platforms
---

### Post by chinbo99 on 2009-05-21
Hi all,

Not sure if anyone can help me with this as it quite complicated. I am pretty new to linux so apologies for this not being the most technical description!!!

Basically this is what happened. I have Ubuntu 8.10 Server installed on an old IBM Pentium 4 system and it has been working fine for some time. I earlier shutdown the server (the proper way using the shutdown command and no errors were reported) and installed a second hard drive to just use as more storage alongside the server system on the primary drive. I checked the jumper settings to set a master and slave drive, and the bios picked the primary and new drive up correctly. On reboot, I received a large list of faults, but the main worry was many "segmentation faults". The boot sequence then just stopped at "Starting kernel log daemon".

So I had to reboot again and tried the recovery mode from the GRUB bootloader. I wasn't able to get a command prompt, as for some reason Ubuntu has forgotten the root password I set up??!?! So I tried the "dpkg - repair broken packages option". It searched around for a bit and came back with some available kernel updates and restricted modules packages, and some other packages to fix the broken packages problem. I let it download these and try to install them, but once again I got dpkg errors for these packages and they weren't installed properly. When I then rebooted again, the GRUB bootloader had lost all kernel options from its menu, leaving the only option as a memtest!!

I tried the repair broken system option on the original CD, and have looked at the disk with the shell option, and it appears the kernel files are still all there. I then tried to re-install the GRUB, and it failed, which the caused problems with the shell option!! So I am now unable to get a shell command prompt from the CD, and I have no kernels listed in the bootloader so I think I'm pretty stuffed.

Can anyone give me any advice as to where I can go from here. Stupidly, being relatively new to linux, I don't have any backups of anything. I have quite a lot of stuff running on the machine that has taken me some time to setup, and I could really do with not having to give up and start again. Is there any way I can get a working kernel re-installed, or if nothing else, get access to the disk to get all my config files off of it, so at least I won't have to start completely from scratch if I'm forced to start again?

I know that description is pretty washy, but without having access to any logs, I can't really be any more specific as I can't remember the exact fault descriptions, codes etc.

Any help would be much appreciated!

Chinbo99

---

### Post by Alekz_ on 2009-05-21
Hi Chinbo99!

I'll sugest you to remove the new disk you setted up and boot from a live CD.

If you're able to start the system through the live CD, you can read de menu.lst file (/boot/grub/menu.lst).

If you know the file, verify if there is nothing wrong.. else, post the content of the file here and we'll see if there's something to do!

[]'s

Alekz_

---

### Post by chinbo99 on 2009-05-21
Thanks for your reply Alekz.
 
I'll give it a try when I'm home later, at work now unfortunately!!
 
I'm not sure if I will be able to though as when I tried earlier to get to the shell prompt from the Live Cd rescue section it came back with an error! This was after I had tried to re-install the GRUB bootloader, which also failed! So not too sure what thats all about.
 
If all else fails, would I be able to install a fresh server install on the new hard drive, then mount the bad drive, and copy across any files I need. I'm thinking mainly things like Samba, Postfix, Courier etc config files that are pretty long and gave me a lot of agro setting up in the first place!!! And also a farily large MySQL setup which included multiple databases??
 
Thanks again.

---

### Post by Alekz_ on 2009-05-21
Well.. You "have" to be able to boot from a live CD becouse your HD doesn't make any difference when you're booting from a live CD!

You can use any Linux Dist. Live CD (yeah! even desktop releases), and.. Well, when you have your system up, you can backup what you want! :)

PS.: You don't have to use any "rescue" session of the CD... Boot your system normaly, as if you're starting to use first time!

---

### Post by chinbo99 on 2009-05-21
Right, I see what you mean now, boot from the CD itself. I take it I can then mount the hard drive and look at it that way.
 
Thanks for the help, I'll try that when I get home and see what I can do.

---

### Post by Alekz_ on 2009-05-21
Yeah! That's it!

Any problem, tell us! :)

---

