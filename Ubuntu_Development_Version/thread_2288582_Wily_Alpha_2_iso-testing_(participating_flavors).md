---
title: "Wily Alpha 2 iso-testing (participating flavors)"
date: 2015-07-28
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-07-28
So far it looks like only Kubuntu, Ubuntu Kylin, and Ubuntu Mate are participating this time:

[http://iso.qa.ubuntu.com/qatracker/milestones/343/builds](http://iso.qa.ubuntu.com/qatracker/milestones/343/builds)

If you're so inclined jump right in and please report your results on the tracker :)

---

### Post by kansasnoob on 2015-07-28
Lubuntu has joined the party too :)

---

### Post by sudodus on 2015-07-28
Sure, we are joining the party :-)

---

### Post by ventrical on 2015-07-29
Yep .. just zsynced it. The first alpha had no probs . The '5 minute' install :)

---

### Post by sudodus on 2015-07-29
I think some of you boot from grub2 and ISO files during isotesting. I found a bug today, that affects this method specifically, and it is the automatic 'Install alongside and auto-resize' alternative.

See [this link (bug #1479405)](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1479405) for more details.

---

### Post by ventrical on 2015-07-30
> **sudodus said:**
> I think some of you boot from grub2 and ISO files during isotesting. I found a bug today, that affects this method specifically, and it is the automatic 'Install alongside and auto-resize' alternative.

See [this link (bug #1479405)]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1479405") for more details.

No auto-resize problem here. Lubuntu now is able to detect that it is being installed in UEFI mode and presents a warning (and option) to (Go back) at which point (when choosing Go back) will present all install options. So I didn't have to reboot!! This is awesome advance.

Regards..

---

### Post by sudodus on 2015-07-30
It works for me too, when I have created the boot drive in another way (instead of grub-n-iso), for example, mkusb. Then the auto-resize feature works. I agree that most things work well in Wily's installer.

-o-

ventrical, how did you create the boot drive?

---

### Post by ventrical on 2015-07-30
> **sudodus said:**
> It works for me too, when I have created the boot drive in another way (instead of grub-n-iso), for example, mkusb. Then the auto-resize feature works. I agree that most things work well in Wily's installer.

-o-

ventrical, how did you create the boot drive?

I just used 'Disks' on fully updated version of trusty on one of my more current machines. I haven't been experimenting with mkusb to much. It has been busy summer so far. :) Honestly, Disks is much faster and easier to use.

Regards..

---

### Post by ventrical on 2015-07-30
Rebooted into auto-resized install and works like a charm.

```

ventrical@ventrical-MS-7850:~$ uname -a
Linux ventrical-MS-7850 4.1.0-2-generic #2-Ubuntu SMP Wed Jul 22 18:19:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by sudodus on 2015-07-30
I think ***disks*** and ***mkusb*** do basically the same thing behind the curtain: copy/clone/flash the iso file into the pendrive. We find different favourites. You like disks. Actually I think both disks and mkusb could ***replace the startup disk creator***. I made mkusb to be easy to use and understand and ***safe***, but the safety checks (and extra windows) makes it slower than without those features. I still like the text mode version, now renamed to mkusb-nox. I think mkusb-nox is at least as fast as disks, and there are features to make it safe, for example the final warning.

I have been testing pendrives made with the 'grub-n-iso' method recently. I use a method, that works for almost all computers (BIOS and UEFI, 32-bit and 64-bit). Even 32-bit systems boot in UEFI mode. It does not work with secure boot, and I found out yesterday, the automatic selection, where auto-resize is one option, gets confused. Otherwise the 'grub-n-iso' method works well, and it is very convenient to upgrade the iso file in place in the pendrive. It need not be copied from a HDD to the pendrive, but of course, the pendrive must be rebooted after upgrading the iso file in order to run the new daily image.

[One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot ](http://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by ventrical on 2015-07-30
I left comment at your link.

Regards..

---

### Post by ventrical on 2015-07-30
> **sudodus said:**
> I think ***disks*** and ***mkusb*** do basically the same thing behind the curtain: copy/clone/flash the iso file into the pendrive. We find different favourites. You like disks. Actually I think both disks and mkusb could ***replace the startup disk creator***. 

I think we have all been been burned by how SDC is unreliable. It works sometimes, on some machines , on various installs.... so there are depend issues. 'Disks' does a clean and uninhibited rip .

Regards..

sorry for off topic..

---

### Post by kansasnoob on 2015-07-30
> **ventrical said:**
> I think we have all been been burned by how SDC is unreliable. It works sometimes, on some machines , on various installs.... so there are depend issues. 'Disks' does a clean and uninhibited rip .

Regards..

sorry for off topic..

I really wish they'd just scrap SDC. Not sure what to replace it with .................... I use Unetbootin but it could use a somewhat more user friendly UI.

---

### Post by ventrical on 2015-07-30
> **kansasnoob said:**
> I really wish they'd just scrap SDC. Not sure what to replace it with .................... I use Unetbootin but it could use a somewhat more user friendly UI.

I like mkusb but I get the jitters when it makes a call to terminal and asks me for my password rather than use the policy kit like other programs, especially with dev releases.

Regards..

---

### Post by sudodus on 2015-07-30
I replied to your comment at the link [One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot ](http://ubuntuforums.org/showthread.php?t=2259682)

Maybe it is better to discuss tools to make USB boot drives in a new thread (we have hijacked this thread too much already, sorry kansasnoob).

---

### Post by ventrical on 2015-07-30
+1 :)

---

