---
title: "Another Linux security question (re: Linux.com)"
date: 2006-03-18
forum: The Cafe
---

### Post by Jucato on 2006-03-18
Well, this has been nagging my curiosity for quite some time now. One of Linux's selling point (emphasis of "one of") is it's stability and security. I'm led to think that Linux has less security vulnerabilities/problems than your leading OS (you know what I mean). And that if ever there are vulnerabilities, they are fixed/patched right away. 

But then I've noticed that [Linux.com](http://www.linux.com) releases Security Advisory weekly, some of which affect Ubuntu. My two questions would be:

1. Are there that many security vulnerabilities/flaws/issues in Linux that you have a weekly Security Advisory? I hope I'm wrong that there are security issues discovered every week. :o

2. How do I apply these patches in Ubuntu? or does Ubuntu develop their own patch for issues posted on the advisory?

This is basically a security newb question, so please pardon my ignorance. :D

---

### Post by Virogenesis on 2006-03-18
Linux is the kernel not the application that sit on top of linux.

ubuntu has a good track record of fixing security issues I believe patches are made by those outside ubuntu I'm not 100% certain and nothing is totaly secure even openbsd has probs which is meant to be the most secure os around.

sudo apt-get update will patch your system unless you used programs outside the ubuntu repos.

---

### Post by Jucato on 2006-03-18
Oh I see. so the security patches in Linux.com mostly involve non-kernel stuff? So when people say that Linux is more secure, they mean that the Linux kernel is more secure, but the Linux OS as a whole (meaning apps included) are open to as much vulnerabilities as the other OS'es?

(Nevermind on how to patch the security advisory from Linux.com. I realized those involving Ubuntu directly are linked back here).

---

### Post by DaMasta on 2006-03-18
There are kernel vulnerabilies and then there are application vulnerabilities.

---

### Post by TLE on 2006-03-18
I know this is not exactly what you asked but I think it is still relevant because it has to do with the power of open source and the pertaining commuty. If one compares problems in browsers a pretty clear picture reveals itself. Try and open these two links next to each other in tabs in your firefox browser ;)  and compare the statistics:
[Mozilla Firefox 1.x]("http://secunia.com/product/4227/")
[Microsoft Internet Explorer 6.x]("http://secunia.com/product/11/")
What I think is important to notice here is, that although the shear number of problems aren't as low (in Firefox) as one could hope for, there are a world of difference in the severity and most importantly in the fixtime. (Can sort of be extrapolated from solution status graph) so if this is a general tendency in the open source commuty I'd say we are very well secured.
Regards TLE

---

### Post by mstlyevil on 2006-03-18
Linux permission systems are what give the various Linux based operating systems their better security. Also most applications are installed to the home folder and not to the root of the operating system. Linux has it's vulnerabilities but they usually are not as severe as that other operating system.

You should always practice a good security policy no matter what operating system you use. Windows can be locked down to be as safe and secure as Ubuntu. And Ubuntu can be as unsecure as Windows if you throw good security out the window and run as root. It is up to you how secure your system is.

---

### Post by Lovechild on 2006-03-18
I check all the released security updates for Fedora and I read Linux Weekly News in it's entirety (lwn.net). 

That covers me pretty well in terms of getting hot naked and covered in oil.. I mean up to date on security.

---

