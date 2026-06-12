---
title: "How do I switch default bootloader?"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by iClouseau88 on 2012-04-03
Hello,

I have a multiboot system in which the default bootloader is legacy Grub.  From the Grub menu I can boot into opensuse 12.1 (legacy Grub), Windows 7 or Ubuntu 12.04 (Grub2), etc.

During today's updating of Ubuntu, the screen says:

> 
Writing Grub(2) to boot device (/dev/sda7) failed.  Continue?

So I had no choice but to check the dev/sda box and hit Forward.

Now when I reboot, I only see the Grub 2 menu. Obviously I unknowingly chose Grub2 as the default bootloader.

How do I change the default bootloader from Grub2 back to legacy Grub as I have before?

Thanks in advance for your help.

:confused:

---

### Post by Skaperen on 2012-04-03
You decide which bootloader you want to use, and leave/have that installed.  Changing back depends on how the old one was installed.  Under the old distro, uninstall its bootloader package, then install again.  There may be faster more direct options, but this suggestion is more likely to accomplish this under a wider range of distros and their versions.  You then add the boot entries into whichever boot loader you want to use.

---

### Post by kc1di on 2012-04-03
you might want to take a look at esay BCD. 

[http://easybcd.en.softonic.com/]("http://easybcd.en.softonic.com/")

---

### Post by oldfred on 2012-04-03
Your grub2 should present you with all three systems, in Ubuntu run this if it does not:

sudo update-grub 

There was a bug.
It just changed to fix released:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972250](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972250)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411)

---

### Post by Baldrick_NZ on 2012-04-03
The other win for Grub2 is that you can customise it to look more to your liking. 

Find more about it here: [http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html](http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html)

---

### Post by Baldrick_NZ on 2012-04-03
The other win for Grub2 is that you can customise it to look more to your liking. Including which O/S you want to make boot default.

Find more about it here: [http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html](http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html)

---

### Post by iClouseau88 on 2012-04-03
Hello kc1di,

Thanks for your reply.  I did look at easyBCD, but have not found the right way to boot _several_ Linux distros along with Windows.  I did see one blog on the web but it's for booting one Linux distro only.

---

### Post by iClouseau88 on 2012-04-03
Hi everyone,

I found the solution to reinstall legacy grub from an old note courtesy of caf4926 in opensuseforums:

1. Boot into opensuse > Terminal
2. grub
3. find /boot/grub/menu.lst
4. Terminal shows for example: (hd0,1)
5. root (hd0,1)
6. setup (hd0)
7. quit
8. reboot

:D

---

### Post by kc1di on 2012-04-03
> **iClouseau88 said:**
> Hi everyone,

I found the solution to reinstall legacy grub from an old note courtesy of caf4926 in opensuseforums:

1. Boot into opensuse > Terminal
2. grub
3. find /boot/grub/menu.lst
4. Terminal shows for example: (hd0,1)
5. root (hd0,1)
6. setup (hd0)
7. quit
8. reboot

:D
Glad you got it sorted out :)

---

