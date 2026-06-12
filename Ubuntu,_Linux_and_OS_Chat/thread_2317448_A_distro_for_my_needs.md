---
title: "A distro for my needs?"
date: 2016-03-16
forum: Ubuntu, Linux and OS Chat
---

### Post by UDroidie626 on 2016-03-16
Hello,
I am looking for a distro to suit my needs, I have hopped around a few distros like Arch, OpenSUSE, CentOS/Fedora, Ubuntu/Debian/Elementary.
I simply cannot find one that sits well with me for some reason.
Anyways my usage is going to be mostly Virtualization for a Windows 7 machine I will be building, I will more then likely be using either VBox or KVM, it also must have good multi-monitor support.
I would also like to use Openbox+Tint2 as I have recently heard about ricing and I always like to make things look good on Linux.

The laptops specs are as follows.
i5 2520m
8GB RAM (Upgrade to 16GB soon)
500GB SSD

Any suggestions towards such a distro?

Thanks

---

### Post by HermanAB on 2016-03-16
Since you want to keep resources for the virtualizer, I'd suggest Xubuntu, Fedora Xfce spin or PC-BSD.

---

### Post by 1clue on 2016-03-16
What exactly do you think is missing from these distros?

How much effort are you willing to put into this?

kvm is in the kernel. Every distro supports it.  QEMU and other tools necessary for this are present in every distro I've heard of.  This part is not a barrier for you.

All Linux distros use 99% of the same software.  Most distros do some sort of customization which may or may not be used by some other distro.  The fallout of that is that most of the differences between distros are all about customization and what options were compiled into the packages built.

You could take almost any distro and get a large degree of customization from it.  If that doesn't work for you you may need to go through some more effort.

If you have a pretty quick box and you don't mind getting your hands dirty, you can get almost anything you want by using Gentoo.  Gentoo is a source-based distro, meaning everything on your box is compiled from source code, on your box.  There are exceptions available for bigger packages, but in general you configure your system for the options you want present and then build your system to suit.

There are other source-based distros. They're fine too, I use Gentoo because it offers a good balance between flexibility of building everything just the way I want without having to configure every package separately.

[https://gentoo.org/](https://gentoo.org/)
[https://wiki.installgentoo.com/index.php/GNU/Linux_ricing](https://wiki.installgentoo.com/index.php/GNU/Linux_ricing)

---

### Post by Frogs Hair on 2016-03-16
Moved to *Ubuntu Linux & OS Chat*

---

### Post by PaulW2U on 2016-03-16
> **1clue said:**
> All Linux distros use 99% of the same software.  Most distros do some sort of customization which may or may not be used by some other distro.  The fallout of that is that most of the differences between distros are all about customization and what options were compiled into the packages built.
Agreed. Which is why I've always found Ubuntu and its various flavours so much easier to use and install.

---

### Post by 1clue on 2016-03-16
> **PaulW2U said:**
> Agreed. Which is why I've always found Ubuntu and its various flavours so much easier to use and install.

I manage a lot of equipment.  I use whatever distro works best for the current use case for the box. There are extenuating circumstances for each distro.  

Ubuntu, for example, is sponsored by Canonical who created the distro in order to be a stable commercially viable platform on which its non-free products can be used.  I use Ubuntu on the workstation I am currently typing on, and I use Ubuntu Server for a whole lot of VMs, both for personal use and for professional use, on my own hardware and on hardware related to work.  Other distros are community-based and have a different appeal. Some have better desktop configurations, others have better forum support or WIKIs. 

I use Gentoo anywhere I need something custom.  I don't bother tweaking other distros beyond a certain point.  I'll add or remove software from some non-source distro, but I don't bother recompiling anything or get crazy about tweaking.  If it gets to that point I find it much better to use Gentoo. Gentoo has fantastic documentation, as does Arch. Gentoo forum, like Ubuntu forum, is helpful and chatty.  Arch forum is, in my opinion, less tolerant of that. While I've installed Arch and am on their forum, I've never posted there.

CentOS, RHEL, Suse and a few others are in there too, mostly because of some specific product (Oracle database wants CentOS for example) that is supported only for that specific distro.


I strongly encourage people to try several distros.  There is no need to uninstall one and install the other these days, almost every semi-modern computer has built-in virtualization hardware support and hard disks and RAM are cheap.

If I want another distro on the metal I simply add another hard drive, remove my existing drive(s) and install fresh on the new drive with the new distro.  If that doesn't pan out I pull that drive and re-install the other drive(s) and I'm exactly the way I was.  There is no risk of trashing something good this way.

---

### Post by UDroidie626 on 2016-03-17
> **1clue said:**
> I manage a lot of equipment.  I use whatever distro works best for the current use case for the box. There are extenuating circumstances for each distro.  

Ubuntu, for example, is sponsored by Canonical who created the distro in order to be a stable commercially viable platform on which its non-free products can be used.  I use Ubuntu on the workstation I am currently typing on, and I use Ubuntu Server for a whole lot of VMs, both for personal use and for professional use, on my own hardware and on hardware related to work.  Other distros are community-based and have a different appeal. Some have better desktop configurations, others have better forum support or WIKIs. 

I use Gentoo anywhere I need something custom.  I don't bother tweaking other distros beyond a certain point.  I'll add or remove software from some non-source distro, but I don't bother recompiling anything or get crazy about tweaking.  If it gets to that point I find it much better to use Gentoo. Gentoo has fantastic documentation, as does Arch. Gentoo forum, like Ubuntu forum, is helpful and chatty.  Arch forum is, in my opinion, less tolerant of that. While I've installed Arch and am on their forum, I've never posted there.

CentOS, RHEL, Suse and a few others are in there too, mostly because of some specific product (Oracle database wants CentOS for example) that is supported only for that specific distro.


I strongly encourage people to try several distros.  There is no need to uninstall one and install the other these days, almost every semi-modern computer has built-in virtualization hardware support and hard disks and RAM are cheap.

If I want another distro on the metal I simply add another hard drive, remove my existing drive(s) and install fresh on the new drive with the new distro.  If that doesn't pan out I pull that drive and re-install the other drive(s) and I'm exactly the way I was.  There is no risk of trashing something good this way.

I have used a lot of distros over my time, thing is I just cant seem to find one that fits what I need as it is for work, I need the stability of RHEL but with a newer kernel something like 4.4LTS.
Another good reason I suppose for RHEL (CentOS specifically) is the resource usage, as its a dam fast and light OS, plus I believe Red Hat actively maintains KVM no? although I am hearing good things about Xen, which maybe more fitting as we use Cirtrix receiver for remote.

---

### Post by 1clue on 2016-03-17
Maybe you need to write down your needs on paper and prioritize them.  It may be some are mutually exclusive.  Then list the distros you try, and rate them for each requirement.

"Newer kernel" and "stability" are very possibly mutually exclusive.  Newer kernel means you will be regularly replacing/recompiling the kernel, which means you either have a really good script to check for required features or you miss things every now and then. Also the LTS distros decide on a kernel and then only provide stability and security patches, ignoring all others. You could do that manually, but in order to ensure stability you'll have to do a lot of patching and testing on other hardware.

---

### Post by Bucky Ball on 2016-03-17
> **1clue said:**
> Maybe you need to write down your needs on paper and prioritize them.

Excellent suggestion and good starting point. It helps to get it out on a mud map on paper where you can see it and make changes rather than having some idea of what you're after in your head where it is open to infinite interpretation (at least in mine).

Lock it in time then tweak your plan.

---

