---
title: "I may have a problem - incorrect machine size"
date: 2011-04-10
forum: Virtualisation
---

### Post by mcai8sh4 on 2011-04-10
So I decided to have a play around with 11.04 beta, I backed everything up on a NAS server, played around and I'm quite happy.

So I decided to put my virtual machines back on.

I installed VirtualBox, then set my machines copying across. (copied 'VirtualBox VMs' directory into my home dir)

The problem arrived when something went wrong (thats betas!) and I had to reboot.

I have a 50gb XP machine, but it stopped copying at ~30gb - so the file 'XP.vdi' is only 30.5gb

It boots ok, and everything works fine - but I'm concerned that I may have problems in the future if I use more than 30gb on that virt machine.

Has anyone got any info on this situation? I'd rather not copy the vdi across again, as it takes a long time. But I'd rather do that than find an issue in a few months time.

The virtual machine still reads 50gb.

Any thoughts? (could I expand the vdi, as the missing space is empty?)
 
Many thanks, Steve

---

### Post by CharlesA on 2011-04-10
If you told it to use a dynamic sized virtual drive, then the VHD will only be as big as how much data you have on it.

Also note: You will have to copy the ~/.VirtualBox folder as well, since that contains the config for VirtualBox. If you don't do that, you'll have a hell of a time getting your VMs set back up without creating new virtual machines (and attaching the old vhds)

---

### Post by mcai8sh4 on 2011-04-11
CharlesA, thank you for the response. unfortunately I didn't use the dynamic size option, I wanted to limit myself. I have copied the entire dir structure, and everything *seems* ok at the minute.

The size of the vdi on my backup is 50gb, but the copy only got up to 30.5gb.

I might just re copy the dir structure across again tonight to ease my concerns.

Thanks again.

---

### Post by CharlesA on 2011-04-11
Have you verified the file size on the host machine?

---

### Post by mcai8sh4 on 2011-04-11
I've booted the vm and xp thinks it's partition is 50gb, virtual box thinks it's 50gb, but the vdi on my hdd is only 30. 

Its a strange one, and everything seems to work perfectly, I just have a doubt in my mind.

Thanks for the help.

-s

---

### Post by CharlesA on 2011-04-11
Strange indeed.

The other thing you could try is just exporting the VM and then importing it again.

---

