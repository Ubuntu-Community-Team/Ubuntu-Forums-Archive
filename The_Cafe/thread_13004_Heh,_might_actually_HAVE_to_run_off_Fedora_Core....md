---
title: "Heh, might actually HAVE to run off Fedora Core...."
date: 2005-01-28
forum: The Cafe
---

### Post by jdong on 2005-01-28
As you guys may have heard, user Renegade has generously donated 4 hard drives to me, and I intend on setting up a RAID5, to speed up the backporting process and give me more space (and reliability) to work!

However, after cruising around on the net doing research, I've came to the following scary conclusion:
**1.   Fedora Core does RAID+LVM perfectly on the root filesystem**
**2.   Debian-Installer requires a 6-page installation "hack" to even CONSIDER getting RAID+LVM to work on the root filesystem**


As I've said, I'm quite busy this year, and don't have the time to spend 12 hours hacking RAID+LVM on Hoary (though it would be extremely interesting).

When the drives arrive, I'll give Hoary's installer a whirl, and if it doesn't work within 3 hours or so, then I'm moving to FC3 and setting Hoary/Warty chroots from there.... Depending on how well their Xen project is going, I may be able to actually virtualize many Ubuntu systems!!





P.S. I'm installing FC3 now, on a 10GB side partition, just to get accustomed. Dealing with that monster called "yum" right now.

---

### Post by Juergen on 2005-01-28
How do the FC people do that?
At boot time there is no kernel with appropriate modules running, so, hmm, does their bootloader understand LVM and RAID or what?  :smile:

---

### Post by jdong on 2005-01-28
[QUOTE=Juergen]How do the FC people do that?
At boot time there is no kernel with appropriate modules running, so, hmm, does their bootloader understand LVM and RAID or what?  :smile:[/QUOTE]

No, you still have to have /boot separate (which will contain GRUB), but the initrd will be able to set up RAID/LVM.

---

### Post by jdong on 2005-01-28
Ok, first day in FC3.... It's actually going surprisingly smoothly -- I got my desktop tweaked just the way I want....

The last time I tried FC3... if I would've let the system prelink itself... maybe it would've been running as fast as it is now. Could you imagine that?? ;)

---

### Post by jdong on 2005-01-28
Ok, currently have a beautifully set up FC... (Too bad I'll have to reformat next week! LOL)

Just starting to play around with SELinux, execshield. (Purposefully making holes in Apache, trying the PHP backticks) (Exec-shield, trying little buffer-overflow games)

---

### Post by jdong on 2005-01-28
Man, there's updates virtually by the hour!! LOL

Oh well, time to create an update CRON job!

---

### Post by az on 2005-01-28
With all respect, instead of the hourly postings, what about dropping a note to Hoary Devel mailing list?

You seem to know exactly what to ask for.  Perharps the 6-page installation "hack" can be packaged.

If not Hoary devel, how about Debian boot?

If you don't ask, you shall not receive.

---

### Post by TravisNewman on 2005-01-28
[QUOTE=jdong]Depending on how well their Xen project is going, I may be able to actually virtualize many Ubuntu systems!![/QUOTE]

OK, this is slightly off topic, but when you say "their" Xen project, do you mean that Fedora is incorporating Xen into the distribution? I've heard about Xen but I didn't know that Fedora was utilizing it at all.

---

### Post by jdong on 2005-01-28
They're integrating the (independent) Xen project into FC4... It's pretty certain to be there! That's what I meant by their project.

---

### Post by jdong on 2005-01-28
[QUOTE=azz]With all respect, instead of the hourly postings, what about dropping a note to Hoary Devel mailing list?

You seem to know exactly what to ask for.  Perharps the 6-page installation "hack" can be packaged.

If not Hoary devel, how about Debian boot?

If you don't ask, you shall not receive.[/QUOTE]
This "hack" was posted on the Debian mailing lists, with many developers interacting. From what I've heard in addition, Debian hasn't fixed it yet.

---

### Post by TravisNewman on 2005-01-28
aaahhh ok that makes sense. I've been looking into Xen because (as you know) chroot isn't doing it for me, and UML is  **s l o w.** About as slow as VMWare. I don't think I'd mind running a barebones Fedora system as the backend for different virtual machines if Xen works much better in Fedora than it does in Debian/Ubuntu

Anyway, good to know that Fedora is going better for you this time, but it sucks that RAID isn't supported well in Debian.

BUT here's an idea for a backport for the extras section. Compile that 6 page hack into a deb somehow so that it'll be much easier for others to set up RAID ;) OK no, not really.

---

