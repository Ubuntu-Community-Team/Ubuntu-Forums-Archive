---
title: "VirtualBox - yes or no?"
date: 2008-04-10
forum: Virtualisation
---

### Post by DexterLB on 2008-04-10
I haven't used VirtualBox, but I need to emulate some Windows programs and they don't work under WINE. But will virtualbox make my PC slower? does it take a lot CPU when it's not running (I see it's a kernel module)? :confused:

---

### Post by kpkeerthi on 2008-04-10
It will make your PC slower **only when it is running**. I have not experienced any slow downs otherwise. The kernel module however might take a very little (negligibe) of your RAM but not CPU when it is not in use.

---

### Post by The Cog on 2008-04-10
^^ What he said. I use VBox for just that - occasional use of winblows only apps. When it's not running, it has no impact. I am not aware of the kernel module being there.

---

### Post by Tom--d on 2008-04-10
I do see, when a list of things start up, VirtualBox pop up now and then.

---

### Post by The Cog on 2008-04-10
No. The vboxdrv driver sits there unused and doing nothing unless you launch the VirtualBox application.

If you launch VirtualBox and boot windows inside of it, then it will sit there sapping your CPU the way windows does until you shut windows down again. Forget the driver. Its no more important than say, your TV tuner driver which does nothing until you start using your tv tuner to watch telly.

---

### Post by Chame_Wizard on 2008-04-10
aHAHAHHA*JUST INSTALLED vBOX*

---

### Post by DexterLB on 2008-04-11
OK I am dual-booting with winXP, BUT I messed it up and it doesn't work. I'll upgrade to the new 8.04 ubuntu after 2 weeks and format the winxp's partition to ext3 and put a virtualBox virtual HD file on it. Then I'll install winXP on the virtual machine and ready. :popcorn:

---

### Post by insane_alien on 2008-04-11
you can also have virtual box integrate with your ubuntu desktop, i have it set up like that, works great if you have a dualcore. plenty of RAM helps too.

i have XP integrate with 8.04 on an intel quad core with 8GB of RAM, it rocks. though XP does occasionally get a virus or two. its also limited to one core. don't experience any slowdown really.

---

### Post by DexterLB on 2008-04-11
> **insane_alien said:**
> you can also have virtual box integrate with your ubuntu desktop, i have it set up like that, works great if you have a dualcore. plenty of RAM helps too.

i have XP integrate with 8.04 on an intel quad core with 8GB of RAM, it rocks. though XP does occasionally get a virus or two. its also limited to one core. don't experience any slowdown really.
but... I don't have a dual-core, my CPU is ~2000MHz and I only have 1gig ram

---

### Post by fmonjaraz on 2008-04-11
I think its just easier if  you dual-boot..I hate windows but I only use it for itunes and games...I use the VM to use solaris, fedora, open-suse, and mandriva...just to check them out and see how they compare to ubuntu

---

### Post by fmonjaraz on 2008-04-11
P.S.  sweeet machine Alien

---

