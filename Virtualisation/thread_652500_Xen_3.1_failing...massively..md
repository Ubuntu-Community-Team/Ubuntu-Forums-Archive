---
title: "Xen 3.1 failing...massively."
date: 2007-12-28
forum: Virtualisation
---

### Post by soltanis on 2007-12-28
VMWare crashes and I find it generally annoying, and Wine doesn't meet my needs (games), so my friend suggested I use Xen, or paravirtualization.

Fair enough...finding Xen was hard enough (it took me a while to realize that it was open-source, and that I didn't have to pay for it) and there were no .deb packages, so I installed from a tarball using a manual install script for precompiled binaries (I tried compiling my own, but it took 36 minutes, and then failed out with an error).

Once I got through that, setting the thing up was hard--had to edit /boot/grub/menu.lst, etc, a bunch of the files were listed wrong in the readme, et cetera.

Once I got through all that, I tried booting Xen, it seemed to work, but then it said something like
```

FATAL: could not open /modules/(stuff)

```
and then hanged on a message saying
```

Waiting for root filesystem...

```

Has anyone used Xen and/or run into this problem, and does anyone know how to fix it?

---

### Post by fjgaude on 2007-12-29
I've been waiting for Xen to mature for me to try to use it. VMware has worded so well I've sorta lost interest in Xen, at least until Ubuntu has it in a user-friendly form.

When I do a Search of Xen in Synaptic we find headers that are not current, so...

---

### Post by soltanis on 2007-12-29
I don't know...Xen is so weird about the way it works. I don't understand why I should have to boot into it instead of just running it like a program--because Xen isn't an operating system, it still is supposed to boot Ubuntu...

And the readme was horribly outdated, and their documentation was similarly bad. I had to figure it all the way to here just by guessing what each of the files it put in the /boot/ directory did, so I probably did that wrong.

That being said, if anyone has gotten it to work, could you post how you managed that and /boot/grub/menu.lst? Thanks a lot.

---

### Post by mclk on 2007-12-31
Hi, could you post some more details about your ...
* ubuntu version,
* hardware platform,
* kernel version, please?
Xen 3.1 is available via apt / synaptic for 7.10 at least (switch on community-based repository "universe" at least and reload (synaptic or apt-get - depends on what you're using).
My "uname -a" says:
Linux <pc-name> 2.6.22-14-xen #1 SMP Tue Dec 18 09:31:59 UTC 2007 i686 GNU/Linux
As you can see - up-to-date xen-kernel (pre-packaged xen-version often have a lower version number compared to current generic kernel-versions).

---

### Post by fjgaude on 2007-12-31
Wow, I take it you have Xen running with 2.6.22-14 kernel?

---

### Post by mclk on 2008-01-01
My answer is not as convenient as I would have liked it: I installed all packages on a Asus Z53 laptop (intel T7200 dual-core, 2GB RAM). Yesterday I worked near all night to get a vm with ReactOS running but failed (causing various complete system freezes) - obviously due to ioemu issues (according some forum threads I found). 
A PC with AMD64 X2 3800 processors I bought for s.b. else in Dec 2006 did work nicely with a win2k installation including webaccess etc.  - after ca. 1h reading installation guides. 
Now I most likely have to come back to what soltanis did - get xen 3.1 source and configure & compile from scratch. 
fjgaude seems to have the right platform for all this. 
Well - lets see ....

---

### Post by mclk on 2008-01-05
via "gksu synaptic" I chose the server kernels replacing the generic ones. 
I failed with that (kernel does not even start, xen-server kernel causes extremely slow reaction on user input or froze graphic desktop - keyboard worked).
On other forums I found that one needs to check if the BIOS supports INTEL- / AMD-virtualization features: 
e.g. see ... [http://kb.xensource.com/servlet/KbServlet/download/411-102-28/XenSource_4_0_Product_FAQ.pdf](http://kb.xensource.com/servlet/KbServlet/download/411-102-28/XenSource_4_0_Product_FAQ.pdf)
That means one must contact the hardware manufacturer (ASUS in my case, Sony in soltanis' case). 

fjgaude - you shouldn't have any problems with this I guess? I wrote soltanis in a private message that apt-get install xen doe not work because of a xen version mismatch of all xen related packages the apt database contains. 
One must choose the relevant packages manually (via "gksu synaptic" or else way) to make sure only xen 3.1 related packages are installed. If not done so the installation fails.

---

### Post by fjgaude on 2008-01-05
Thanks for the input... we will be thinking about all this as time goes by. I would like to change over to Xen from VMware but don't wish to go through too many hassles.

Thanks again, and do keep us informed as you learn.

---

