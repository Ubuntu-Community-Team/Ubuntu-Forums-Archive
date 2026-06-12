---
title: "Boot existing Ubuntu installation on Vmware"
date: 2008-06-11
forum: Virtualisation
---

### Post by tsikis on 2008-06-11
Hello there i have a dual boot (Ubuntu,Winxp) and i have a vmware to boot the existing winxp installation when i am at Ubuntu but i have to boot Winxp sometimes for my work but i need to be able to run some appz of my Ubuntu installation so i need a way to do the opposite meaning to run my existing Ubuntu installation to a vmware in Winxp.
Anyone can help i would be grateful 
Thanks

---

### Post by bmwman on 2008-06-12
I'm doing the same thing. I can boot XP inside VMWare in Ubuntu.When I'm in windows(native) i boot a virtual Ubuntu but it's a whole new set up. I have no idea if you can use/convert existing Ubuntu inside VMware. The other way around - convert windows in VMware in Ubuntu is pretty easy.

---

### Post by iamkrazee on 2008-06-12
This works with Hardy for sure. Just the thing is that my windows and linux drives are completely different. So the usual naming convention maintains under kubuntu's kernel load via VMWare. What I did was to use the cr4cked version of VMWare, use "entire physical disk" and then it just boots.

I'd tried this back when latest kernel out there was 2.15, the one where harddisks were named /dev/hda if PATA and /sda if SATA. It made a disaster when I tried that. But the newer kernels work differently. Noticably, hardy mounts drives using their UUIDs (see /etc/fstab and appropriate locations in /dev/disk). So I'm pretty sure that if you directly make use of the "use entire physical disk" option when selecting partition for the virtual machine, it would work out JUST fine. You could also keep a separate 50~100MB boot drive exclusively for your virtual machine boot up purpose.

---

### Post by tsikis on 2008-06-15
I will try this and report any results.
I hope it will work

---

### Post by iamkrazee on 2008-07-08
So did you get it to work?

---

### Post by philinux on 2008-07-15
I'd like to know if this worked, and how.

---

