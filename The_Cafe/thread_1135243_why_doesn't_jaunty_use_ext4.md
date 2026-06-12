---
title: "why doesn't jaunty use ext4?"
date: 2009-04-24
forum: The Cafe
---

### Post by daverich on 2009-04-24
I've done a clean install and jaunty seems to default to ext3?

I thought it was supposed to use ext4?

Kind regards

Dave Rich

---

### Post by swoll1980 on 2009-04-24
> **daverich said:**
> I've done a clean install and jaunty seems to default to ext3?

I thought it was supposed to use ext4?

Kind regards

Dave Rich

You can choose ext4, but it's not the default. They wanted more testing, and some issues to be resolved before they make it the default.

---

### Post by 4th guy on 2009-04-24
> **daverich said:**
> I've done a clean install and jaunty seems to default to ext3?

I thought it was supposed to use ext4?

Kind regards

Dave Rich
It's there, just not selected by default.

---

### Post by JohnFH on 2009-04-24
You've answered your own question.  Jaunty 'defaults' to use ext3 but you can choose to use ext4 if you want.  Just choose manual partition at install time.

---

### Post by reprobus on 2009-04-24
From what I have heard ext4 needs to be tested a little more and will be the default in the next release. You can install ext4 in Jaunty by manually partitioning your hard drive. I am using ext4 on Jaunty now and I haven't had any problems thus far.

---

### Post by Wiebelhaus on 2009-04-24
> **swoll1980 said:**
> You can choose ext4, but it's not the default. They wanted more testing, and some issues to be resolved before they make it the default.

Which I can certainly appreciate.

---

### Post by bikeboy on 2009-04-24
For more detail, you can check the official statements - [http://www.ubuntu.com/getubuntu/releasenotes/904overview](http://www.ubuntu.com/getubuntu/releasenotes/904overview) and [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by daverich on 2009-04-24
hmm

fair enough.

I was under the mistaken impression it was all good.

I'm all for having a stable default over ext4 - I just wondered why it was hyped around that jaunty would be running on ext4 and then it installed ext3.

Kind regards

Dave Rich

---

### Post by samjh on 2009-04-25
> **daverich said:**
> hmm

fair enough.

I was under the mistaken impression it was all good.

I'm all for having a stable default over ext4 - I just wondered why it was hyped around that jaunty would be running on ext4 and then it installed ext3.

Kind regards

Dave Rich

Jaunty's inclusion of ext4 was hyped as it's the only distro which supports ext4 on the boot partition.  So far, other distros don't support ext4 on the boot partition, because grub doesn't support ext4 yet.  Jaunty had to use a backported patch for grub to make it work.

---

### Post by SomeGuyDude on 2009-04-25
> **samjh said:**
> Jaunty's inclusion of ext4 was hyped as it's the only distro which supports ext4 on the boot partition.  So far, other distros don't support ext4 on the boot partition, because grub doesn't support ext4 yet.  Jaunty had to use a backported patch for grub to make it work.

I'd love to know what kind of a difference that makes.

---

### Post by cariboo on 2009-04-25
Ext4 really makes a difference to boot time I went form 30 seconds to 20 seconds from grub to desktop. Disk checking is a lot faster too, it takes less than 5 seconds to check my 250Gb hard drive.

---

### Post by Saint Angeles on 2009-04-25
my jaunty uses ext4... what a misleading thread title!

jeez!

---

### Post by samjh on 2009-04-25
> **SomeGuyDude said:**
> I'd love to know what kind of a difference that makes.

Sorry, I'll try to explain in the simplest terms...

Grub is a piece of software which reads what operating system you have installed on your computer, and boots into the selected operating system.  For most of us, that operating system will be a version of Linux.

At the time when Jaunty was being developed, Grub could not read ext4 disk partitions.  So if your disk partition with boot information was in ext4 format, then grub will not work, therefore your computer can't boot!  At the time, your boot partition had to be in one of the formats grub could work with: eg. ext3, JFS, XFS, ReiserFS, etc.

For example, in Fedora 9 and 10 they supported ext4.  But because ext4 was not yet compatible with grub, users could not use ext4 on a partition if they wanted to use that partition to boot their computer.

For Jaunty, developers adapted a patch for grub which will allow grub to read ext4 partitions, allowing Jaunty users to format their boot partition in ext4.  As far as I know, Jaunty was the first distribution to do this.

---

### Post by wolfen69 on 2009-04-25
> **SomeGuyDude said:**
> I'd love to know what kind of a difference that makes.

i notice a HUGE difference in speed. ext4+64bit=blazing speed.

---

### Post by celthunder on 2009-04-25
> **samjh said:**
> Jaunty's inclusion of ext4 was hyped as it's the only distro which supports ext4 on the boot partition.  So far, other distros don't support ext4 on the boot partition, because grub doesn't support ext4 yet.  Jaunty had to use a backported patch for grub to make it work.

archlinux lets you use ext4...has for a while.

---

### Post by Simian Man on 2009-05-23
> **wolfen69 said:**
> i notice a HUGE difference in speed. ext4+64bit=blazing speed.

He was asking what difference having /boot as ext3 makes.  I am almost certain that /boot hardly matters since it just holds the boot loader and only needs to be a few hundred megabytes large.  It is just a little simpler not to need it.

---

### Post by MikeTheC on 2009-05-24
It's deceiving, as far as I'm concerned.

I don't manually partition my system (well, ok, I do inasmuch as I do a partition resize for the NTFS WinVista install) but you have to go into completely manually partitioning, and I really am not comfortable with that because I'm never certain what the optimal size or placement of the SWAP partition is.

However, I'm running ext4 and the performance difference to me is amazing.

---

