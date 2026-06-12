---
title: "Ubuntu Studio ISO Boot Problems"
date: 2020-03-31
forum: Ubuntu Development Version
---

### Post by dbergst on 2020-03-31
I was just checking out the current boot ISO and its predecessor, both of which have a problem finding /casper/vmlinuz when trying to boot from the main menu.  Can someone from the Ubuntu Studio team check to see what the issue is?

PS:   This issue was discovered in the cd images dated 20200329 and 20200328.

---

### Post by sudodus on 2020-03-31
Are you talking about booting from grub into an iso file? In that case you are affected by a known bug:

[Bug report #1851311: Grub 2.04 Out of memory error, No server error](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)

Please mark that it *affects you too* to add heat to the bug report.

---

### Post by dbergst on 2020-03-31
> **sudodus said:**
> Are you talking about booting from grub into an iso file? In that case you are affected by a known bug:

[Bug report #1851311: Grub 2.04 Out of memory error, No server error]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311")

Please mark that it *affects you too* to add heat to the bug report.

No, this is against the ISO itself.  For convenience here is a link to the bug I filed on launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/1869928](https://bugs.launchpad.net/ubuntu/+bug/1869928)

---

### Post by sudodus on 2020-03-31
I zsynced the current iso file and yes, it affects me too, so I confirmed the bug.

---

### Post by dbergst on 2020-03-31
Unfortunately since this bug is against the daily ISO, it has been marked invalid.  A workaround is to edit the grub command line and change the instances of vmlinuz and initrd to vmlinuz-lowlatency and initrd-lowlatency, respectively.

---

### Post by sudodus on 2020-04-01
I have added comments to the bug report and reported it also in the [qa iso tracker](http://iso.qa.ubuntu.com/qatracker/milestones/411/builds/209968/testcases)

---

### Post by sudodus on 2020-04-01
[This bug](https://bugs.launchpad.net/ubuntu/+bug/1869928) is squashed in an updated beta version of Ubuntu Studio :-)

---

