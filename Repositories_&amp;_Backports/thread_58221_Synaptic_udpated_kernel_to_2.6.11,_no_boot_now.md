---
title: "Synaptic udpated kernel to 2.6.11, no boot now"
date: 2005-08-19
forum: Repositories &amp; Backports
---

### Post by crxgames on 2005-08-19
Synaptic notified me that there was new updates today, kernel updates. So I downloaded, installed and rebooted. 

Grub's menu.lst hasn't been edited, and I can't get the old kernel to boot.(manually typing them in grub's console). I

I type this in to boot the old 2.6.10 kernel:
grub> root (hd0,0)
grub> kernel /vmlinuz.old root=/dev/hde6 ro quiet splash
grub> initrd /initrd.img.old
grub> boot

The kernel starts to boot then says:
Uncompressing Linux... OK, booting the kernel.
audit(1124461878): initialized
Starting Ubuntu...
pivot_root: no such file or directory
/sbin/init: 428: Cannot open /dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

Any help would be greatly appreciated, because I really don't want to take the time to reinstall/update/install my tools again. :(

---

### Post by Kapre on 2005-08-22
[QUOTE=crxgames]Synaptic notified me that there was new updates today, kernel updates. So I downloaded, installed and rebooted. 

Grub's menu.lst hasn't been edited, and I can't get the old kernel to boot.(manually typing them in grub's console). I

I type this in to boot the old 2.6.10 kernel:
grub> root (hd0,0)
grub> kernel /vmlinuz.old root=/dev/hde6 ro quiet splash
grub> initrd /initrd.img.old
grub> boot

The kernel starts to boot then says:
Uncompressing Linux... OK, booting the kernel.
audit(1124461878): initialized
Starting Ubuntu...
pivot_root: no such file or directory
/sbin/init: 428: Cannot open /dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

Any help would be greatly appreciated, because I really don't want to take the time to reinstall/update/install my tools again. :([/QUOTE]

crxgames - try using the recovery mode (3rd option on the grub menu). BTW, have you upgraded to Breezy?

K

---

### Post by crxgames on 2005-08-23
[QUOTE=Kapre]crxgames - try using the recovery mode (3rd option on the grub menu). BTW, have you upgraded to Breezy?

K[/QUOTE]
 I just did a complete reinstall, didn't feel like fixing., but I didn't think of trying recovery mode. :/
This was a Hoary install.

---

### Post by joaovicente on 2005-09-01
[QUOTE=Kapre]crxgames - try using the recovery mode (3rd option on the grub menu). BTW, have you upgraded to Breezy?

K[/QUOTE]
I have the same problem in the exact same situation.
I tried the recovery mode and the result is the same...  ](*,) 
The boot sequence is correct against that described on the file "menu.lst"
What should i do to not loose every thing that i have in my system?

BTW, I have mounted the /boot in a separeted partition with ext3. 
My root "/" partition is mounted in another partition with jfs.

Any help would be greatly appreciated too...

João Vicente

---

### Post by alloydog on 2005-09-02
No, you should not lose anything.

When a new kernel is installed, the process should just add a new entry to GRUB.

The original kernel should still be usable.

When you first boot the PC, you should see a couple of lines saying GRUB is starting, then you get a 3 second countdown.  Hit **Esc**  during this countdwon to get the full list of bootable options.

Your working original kernel should still be there.

---

### Post by joaovicente on 2005-09-02
[QUOTE=alloydog]No, you should not lose anything.

When a new kernel is installed, the process should just add a new entry to GRUB.

The original kernel should still be usable.

When you first boot the PC, you should see a couple of lines saying GRUB is starting, then you get a 3 second countdown.  Hit **Esc**  during this countdwon to get the full list of bootable options.

Your working original kernel should still be there.[/QUOTE]
 Unfortunately, it's not so easy... 

The new kernel (2.6.11) is not there and the old one (2.6.10-5) is not booting...

After that, i tried editing some options in the grub menu, but still not working.

Thanks anyway.

---

### Post by Mephist0 on 2005-09-24
I have exactly the same problem as the ppl above.. I have run the update tool and saw a kernel there.. I installed all the new packages as i always do.. and now when i did reboot i get this problem..

I get to the grub> prompt.. Guys in the irc channel helped me to what i shall type.. i tried it and i get the same problem as the poster.. kernel panic...

and 

grub> kernel /boot/ 
possible files are: config-2.6.10-5-686 memtest86+.bit grub vmlinuz-2.6.10-5-686 System.map-2.6.10-5-686 initrd.img-2.6.10-5-686

someone plz help! :(

This is the settings i used when trying to boot with grub> when the system did not reboot ..

grub> root
(hd0,0): Filesystem type is ext2fs, partition type 0x83

grub> kernel /boot/vmlinuz-2.6.10-5-686
grub> initrd /initrd.img   (also tried initrd /boot/initrd.img-2.6.10-5-686)
grub> boot

after that i got exactly the same error message as the first poster to this thread..

---

### Post by Pippen101 on 2005-09-28
[QUOTE=Mephist0]I have exactly the same problem as the ppl above.. I have run the update tool and saw a kernel there.. I installed all the new packages as i always do.. and now when i did reboot i get this problem..

I get to the grub> prompt.. Guys in the irc channel helped me to what i shall type.. i tried it and i get the same problem as the poster.. kernel panic...

and 

grub> kernel /boot/ 
possible files are: config-2.6.10-5-686 memtest86+.bit grub vmlinuz-2.6.10-5-686 System.map-2.6.10-5-686 initrd.img-2.6.10-5-686

someone plz help! :(

This is the settings i used when trying to boot with grub> when the system did not reboot ..

grub> root
(hd0,0): Filesystem type is ext2fs, partition type 0x83

grub> kernel /boot/vmlinuz-2.6.10-5-686
grub> initrd /initrd.img   (also tried initrd /boot/initrd.img-2.6.10-5-686)
grub> boot

after that i got exactly the same error message as the first poster to this thread..[/QUOTE]
Figured this needed a bump because i have just experienced it with Hoary. I DID make a change to my menu.lst...added nolapic and something else

---

### Post by chunk on 2005-09-29
Same problem here. Using ubuntu Hoary and allowed synatic to do a standard ubuntu update (no universe, multiverse, or any of that crap....only the sources enabled by default). I believe the update included something about the kernel, but I didn't look closely.

I really need to get back into ubuntu. All the grub/kernel files are in place and there were no changes made to grubs menu.lst. As far as I can tell there aren't even any new kernels hanging around. I can't imagine what the update might have screwed up. Anyone have a fix for this problem?

---

### Post by Scio on 2005-09-29
Now I got this problem too, after booting due power shutdown. Recovery mode does not help. Any help?

---

### Post by adictojuego on 2005-09-29
Try booting Live CD, mounting / partition, and installing the old kernel. I had a similar problem a month ago, and that did the trick for me.

---

### Post by chunk on 2005-09-29
Here is my exact error message when trying to boot for any kind soul who has a solution:
```
audit(1127997162.082:0):initialized
Kernel Panic- not syncing:VFS:Unable to mount root fs on unknown -block(0,0)
```

And before anyone goes blaming grub, my other distro (on hda5) boots just fine. (ubuntu is on hda6)

---

