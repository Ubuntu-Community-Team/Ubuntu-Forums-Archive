---
title: "What do you do if..."
date: 2009-10-03
forum: Security
---

### Post by Roasted on 2009-10-03
Say someone hacks my Ubuntu system and changes my password.

Now, at this point, I have an Ubuntu system, 1 account, and an unknown password.

What can I do to reset my password to take control of my PC again?

---

### Post by Roasted on 2009-10-03
So, I think I found the answer. I booted into recovery mode with my most recent kernel. When it loaded I selected root login or something like that and typed passwd roasted, and reset it. Bam!

---

### Post by gnudoc on 2009-10-04
Yep, generally if you have physical access to the computer, you can do something about this sort of problem.

So if someone had stopped you from using the recovery mode route, e.g. by setting up grub to force a password before you can change the grub option, then you could take the hard drive out of the computer, put it into a 2nd computer and boot into some other partition on that 2nd computer. You could then, at the very least, take all your data off the disc, put it back into your 1st computer and reinstall your OS. If you were lucky and skilful, you might even chroot into your own partition using the 2nd computer and actually fix your password issue.

This all becomes much much harder if the data is encrypted, but even then there is a theoretical way out.

---

### Post by Roasted on 2009-10-04
Is there a way to do what you described from a LiveCD? In terms of changing the Grub options?

---

### Post by Marlonsm on 2009-10-04
> **Roasted said:**
> Is there a way to do what you described from a LiveCD? In terms of changing the Grub options?

I think so.

You'd need to edit the grub menu file: /boot/grub/menu.lst
I've never done that myself, but I think a possible way would be the open the terminal and run:
```
gksu nautilus
```
It'll open nautlus in root mode (be extremely careful when running nautilus as root) then you can open the HD (that is seen as a media disk by the LiveCD) and browse to that file, editing it as you need.
You'll need to add something like this to the file:
```
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		8773284e-e9dc-4e73-acc6-30d5591c328f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8773284e-e9dc-4e73-acc6-30d5591c328f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic
```
The next time you reboot you'll see the recovery mode option.

---

### Post by cariboo on 2009-10-04
Startupmanager will also allow you to set a grub password. Startupmanager is in the repositories.

---

### Post by undecim on 2009-10-04
the recovery option will only work if the root password hasn't been set (which most attackers will do, as well as put up other methods to maintain access)

You can change a password from a live cd as well, using chroot. From a terminal in your live cd, with the root partion mounted to /media/disk (and any other partitions you need to work with under /media/disk/[path]; you will only need to work with the /etc directory though...) use this line:

```

for k in {dev,proc,sys}; do sudo mount --bind /$k /media/disk/$k; done; sudo chroot /media/disk

```

then you will have root access to that drive, and you can use passwd to change your password back (and also look for other access maintenances)

---

### Post by gnudoc on 2009-10-06
undecim - I can't believe I've been mounting everything one at a time for a chroot environment all this time! Funny how you don't think of some obvious things until someone points them out!

Roasted, we should also note that, to be honest, if you had evidence of a genuine attack with someone working to maintain root access on your system as opposed to a silly prank (I don't know about you but I've worked in places where changing someone's password was considered a friendly prank...), then the safest (perhaps the only safe) thing to do is assume a rootkit with elements that you've not detected.

Under such circumstances, I would mount the drive in a safe environment (i.e. an operating system that you trust has not been taken over and is run by someone you trust), not connected to the internet, and copy off any data that you *absolutely* cannot live without. Hopefully you've been keeping regular backups on a separate drive that's not connected to the computer normally, so this shouldnt be very many data files. I would then completely wipe that harddrive and any others in the hacked system (or, depending on the situation, give it to the IT department/police/whatever)

cheers,
gnudoc

---

