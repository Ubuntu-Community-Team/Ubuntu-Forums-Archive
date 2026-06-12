---
title: "Does 12.04 Support hybrid graphics cards?"
date: 2012-03-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jlmatthews on 2012-03-07
I could not install the last Ubuntu on my laptop due to this, wondering if any improvements have been made?

---

### Post by raja.genupula on 2012-03-07
I think you have to read this 
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by jlmatthews on 2012-03-07
I do not have the AMD/Intel graphics, I have a [COLOR=#0066cc][COLOR=black]HP[/COLOR] [/COLOR][COLOR=black]dv6-6135dx, with two Radeon cards. I am new to Linux and just want it to work.[/COLOR]

---

### Post by raja.genupula on 2012-03-07
yup! my friend , here we go 
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by oldos2er on 2012-03-07
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by grahammechanical on 2012-03-07
Support for various types of graphic cards does not come from Ubuntu but from various projects developing drivers for videos cards.

In some cases the drivers are provided by the manufacturer. In other cases open source drivers are being developed. The usefulness of any of these drivers depends upon the extent of their development and not with Ubuntu's development.

To give you an example of the work being done I post this link

[https://wiki.ubuntu.com/Kernel/PowerManagementRC6]("https://wiki.ubuntu.com/Kernel/PowerManagementRC6")

I do not think that it applies to your situation.

The simplest way to find the answer to your question is, in my opinion, to download the beta 1 version and create a live Cd from and test it out yourself.

You do not explain the issues that you had the last time. So, how do we know if things have improved?

Here are two links

[https://wiki.ubuntu.com/HardwareSupport/]("https://wiki.ubuntu.com/HardwareSupport/")

[https://help.ubuntu.com/8.04/switching/preparing-hardware.html]("https://help.ubuntu.com/8.04/switching/preparing-hardware.html")

I do think that it is too early to know what computers work with 12.04 and which have problems as 12.04 is still under development. In fact testers are needed to test the 12.04 beta live CD operations.

But somebody has to be the first.

Regards.

---

### Post by Mark Phelps on 2012-03-07
Being new here, you may not know this, but Beta releases are inherently unstable -- and are intended for Developers and Testers, not for the general population.

Unless you are willing to deal with bugs on a daily basis, you should not be installing a pre-release version of Ubuntu.

Also, the Hybrid Graphics "problem" is a video drivers issue, not a Linux kernel issue, so it's unlikely to be fixed in a newer version of Ubuntu.

And finally, I have read claims that AMD has "fixed" the Hybrid Graphics problem in version 12.x of their Catalyst Drivers.  But these are brand new and may not work with the Linux kernel version present in Ubuntu 12.04.

---

