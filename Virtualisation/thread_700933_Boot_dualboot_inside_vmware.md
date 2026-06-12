---
title: "Boot dualboot inside vmware"
date: 2008-02-18
forum: Virtualisation
---

### Post by Lanrat on 2008-02-18
Hi, I have a dual boot system with vista.

I would go to linux completely but vista does still run my games a LOT better than wine. And for work I need to use Dreamweaver and some other windows only apps. I have tried them all in wine but for example Dreamweaver runs really slow.

I want to from inside linux boot up my vista partition inside vmware. This way when I need to do work I can just fire up the vm and do what i need to do. And when I want to play A game I can re-boot into windows and it will run just fine.

I like this way because it will have all of my windows apps and windows files only once on my hd instead of once in the dualboot and again inside another vm.

I have found several guides that talk about this, such as these
[http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware](http://gentoo-wiki.com/HOWTO_Configure_a_dual_boot_windows_linux_to_be_able_to_open_each_os_in_vmware)
[http://www.vmware.com/support/ws45/doc/disks_dualboot_ws.html](http://www.vmware.com/support/ws45/doc/disks_dualboot_ws.html)

But they all talk about windows XP. I am running vista. And going back to XP isn't an option for me. (Iv already tried, there really are a lot of missing drivers for it)

So when I boot the vm I get the little windows loading bar, and before it can even get across 1/2 way I get a bsod. (screenshot attached)

So im guessing that it is because vista does not support hardware profiles and once it boots it looks for my SATA drive instead of the virtual drive to load the rest of the data off of. Is this correct?

So, How do I get this to work? I am using Vista Ultimate so there wont be any EULA issues.  :)

---

### Post by deejross on 2008-02-19
I'm not VM expert, but maybe I can help somewhat. You're not gonna want to hear this, but the only **safe** way to do what you want is to split it up. Keep your gaming on Vista (dual-boot) and your work stuff on a newly created VM (XP, if you can, otherwise Vista).

The reason you wouldn't want to use the same Windows partition in a dual-boot and a VM is because you would have to swap out all the system drivers whenever you switched between VM and dual-boot. Which is the reason you are getting the blue screen, because you actual partition is looking for your hard drive on a SATA interface, while your VM would be looking in the same place, but would actually be on a virtual IDE device. That is just one driver. You would have to do it for the CPU, all the motherboard devices, video, audio, etc.

Hardware profiles might help with most of the stuff, but in the end, it's the hard drive location that's killing you. On XP, the only way to change the interface of your hard drive without a wipe and reinstall is a Windows Repair. I'm guessing Vista is the same way.

Besides, doing this would run the risk of crashing your Vista partition altogether, so I think it would be best to what you can in a VM and leaving the gaming for dual-boot. I'm sure it's not what you wanted to hear, but hope it help anyways.

Ross

---

### Post by Lanrat on 2008-02-19
I was kinda already aware of that but i still want to give it a try. I know in XP with Hardware profiles you can specify which drivers to load. But M$ took that out in vista :mad: If you had hardware profiles in XP when you boot it would let you select which hardware profile to use before it actually started loading.

So is there any way to do this in vista? Is there some hack I can do to make it work?

If I tryed the idea of repairing it inside vmware to make it boot would it still boot on the real hardware or just the vm?

Thanks.

---

### Post by deejross on 2008-02-19
I don't really know about the hardware profiles thing in Vista. However, doing a repair in the VM while connected to an actual partition, will almost certainly hose your Vista partition the next time you dual boot. And a Windows Repair is really a last resort. It can mess things up, as it removes all the Windows updates you've installed since installing Vista. I usually tell people that doing a repair is like putting a bandaid on a broken bone. It will last long enough to get anything important off of it, but after a few days, it will eventually fall apart.

About 6 months ago, I did a little research into doing something to what you want to do and decided against it because it's simply too unstable and too much of a hassle. So, I left my XP partition for games, and made a new virtual machine for everything else. Though it seemed less than perfect at the time, I'm really glad I did it. Having gaming on its own partition and my work apps on a VM in Ubuntu is rather convenient simply because I don't have to reboot, and because I could mess around with my gaming partition, knowing that if I screwed it up, no big deal. Just reinstall the games, but if the work stuff got screwed, I'd be in real trouble.

So, bottom line, unless you're willing to format and reinstall Vista, **don't** try it. In my opinion, it's just not worth it unless everything on your hard drive (including Vista and Ubuntu) is disposable.

Hope this info helps you.

---

### Post by Lanrat on 2008-02-19
> **deejross said:**
> 
So, bottom line, unless you're willing to format and reinstall Vista, **don't** try it. In my opinion, it's just not worth it unless everything on your hard drive (including Vista and Ubuntu) is disposable.


I am willing to reinstall if I could get this working. ;)

---

### Post by kool_kat_os on 2008-02-19
AHH.!!! The blue screen of death!!!! Get it away.!!!!!

---

### Post by deejross on 2008-02-19
Well, if you're willing to give it a go, I'm sure there are many that would like to know the end result. So if you go through with it, let us know how it went.

---

### Post by Lanrat on 2008-02-21
I will try this after I make a backup of everything and when I have time to re-install (incase things go horribly wrong)

But in the meantime i also found this. [http://yousefourabi.com/virtualization/vmware-running-native-xp-on-sata-disk](http://yousefourabi.com/virtualization/vmware-running-native-xp-on-sata-disk)

Again its for XP and it uses hardware profiles, but ill try it.

---

### Post by Shazaam on 2008-02-22
Lanrat....
Before you start this project do a COMPLETE backup (or image/snapshot) of your drive(s). This way when it (your project) goes south all you need to do is reload and your back in business.

---

### Post by Lanrat on 2008-03-01
Well, I just tried both methods. Adding the drivers and doing a system repair. Both had no affect. Is there any other way to do this?

If not I guess I will need to just make a XP VM. But I REALLY don't want to do that. (I have a vary small HD and want to save space (having windows on it twice)

Thanks.

---

### Post by perrodin on 2008-03-13
I am having the same troubles, except I am using trying to load a preinstalled version of XP x64. I am getting the blue screen on each load. 
I was unable to install the scsi driver which places say to do, windows gives an error each time. I figured this was the problem, but I am not sure how to fix it.

---

