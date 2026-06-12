---
title: "Is PAE required"
date: 2012-05-01
forum: Server Platforms
---

### Post by thnewguy on 2012-05-01
I have an old 32-bit server box running Ubuntu Server 11.10. I'd like to upgrade it to 12.04, but I've heard Ubuntu has dropped support for non-PAE processors.

Was the PAE issue just regarding the Desktop edition or is the Server edition also affected? I read the release notes and the notes on the Server edition didn't mention PAE one way or the other.

---

### Post by arrrghhh on 2012-05-01
So you know your processor architecture doesn't support PAE?

I thought PAE was just if you wanted to run more than 4gb of RAM on a 32-bit system...  Would this really result in a non-booting system?  I doubt it - but I can't say for sure.

Also, if you have old hardware - I would recommend staying on 10.04 until 12.04 has reached .1 or .2...  It's still supported to 2015!  (On the Server platform...)

---

### Post by jerrrys on 2012-05-01
I don't know about the server, but you can still do non PAE with the mini iso.

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

You shouldn't notice a performance difference if you run the PAE kernek and less than 4G of ram.  Over 4G there is a lite performance hit as compared to 64 bit.

---

### Post by bab1 on 2012-05-02
> **arrrghhh said:**
> So you know your processor architecture doesn't support PAE?
I believe all Intel CPU's from Pentium on (e.g. Pentium, P2, P3, P4, etc.) can use PAE.   > 

I thought PAE was just if you wanted to run more than 4gb of RAM on a 32-bit system...  Would this really result in a non-booting system?  I doubt it - but I can't say for sure.

Also, if you have old hardware - I would recommend staying on 10.04 until 12.04 has reached .1 or .2...  It's still supported to 2015!  (On the Server platform...)
I would not worry about using a PAE enabled kernel.  Just because you have the ability to map > 4GB PAM doesn't mean you have to have that much RAM installed.

---

### Post by asus701user on 2012-05-02
I am trying to boot/instal from a usb having downloaded the latest Ubuntu iso. I get the message:

```
This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU.
```That is not a very helpful message. Where can I get an 'appropriate' kernel. I cannot see any option on the Ubuntu download page?

---

### Post by sudodus on 2012-05-02
I have an IBM thinkpad t41 with a pentium m cpu without pae. The new Lubuntu and Xubuntu desktop flavours of 12.04 are delivered with non-pae kernels, and work with that old laptop. There is also an i386 non-PAE mini-iso file to download from
[[COLOR="RoyalBlue"]_http://cdimage.ubuntu.com/netboot/precise/_[/COLOR]]("http://cdimage.ubuntu.com/netboot/precise/")

I don't know about the server flavour, but I doubt that it is delivered with a non-pae kernel, so if you want to run a server on a computer with a cpu without pae, start with the mini-iso, or run Ubuntu server 10.04 LTS which is supported for five years (until April 2015). If you want to run a desktop or laptop with a cpu without pae, you can install Lubuntu or Xubuntu 12.04.

*Nota bene*, only the server specific program packages are supported that long. If you install other programs or packages, they are supported according to the their category: Ubuntu desktop packages have three years support, Lubuntu packages have only 1,5 years support, so LXDE for 10.04 is no longer supported with security updates, and LXDE for 12.04 will be supported only until October 2013. So run your server with a command line interface, and you will avoid some problems!

---

### Post by thnewguy on 2012-05-02
> **bab1 said:**
> I believe all Intel CPU's from Pentium on (e.g. Pentium, P2, P3, P4, etc.) can use PAE.
I would not worry about using a PAE enabled kernel.  Just because you have the ability to map > 4GB PAM doesn't mean you have to have that much RAM installed.

No, there are more modern machines which do not support PAE. Further, CPUs without PAE support cannot boot using kernels with PAE enabled. It has nothing to do with how much RAM is installed on the machine, but what features are available to the CPU. Since my server box doesn't support PAE I need to make sure the 12.04 Server kernel is non-PAE or otherwise the OS won't boot.

I suppose I could downgrade to 10.04 to get longer support, but I'd rather move up to 12.04, if it supports my hardware. Does anyone here have 12.04 Server edition installed? Does it use the PAE-enabled kernel?

---

### Post by bab1 on 2012-05-02
> **thnewguy said:**
> No, there are more modern machines which do not support PAE. Further, CPUs without PAE support cannot boot using kernels with PAE enabled. It has nothing to do with how much RAM is installed on the machine, but what features are available to the CPU. Since my server box doesn't support PAE I need to make sure the 12.04 Server kernel is non-PAE or otherwise the OS won't boot.

I suppose I could downgrade to 10.04 to get longer support, but I'd rather move up to 12.04, if it supports my hardware. Does anyone here have 12.04 Server edition installed? Does it use the PAE-enabled kernel?

Wouldn't that be an architecture issue, not a PAE (alone) issue?  What specific CPU are you referring to?

---

### Post by thnewguy on 2012-05-02
> **bab1 said:**
> Wouldn't that be an architecture issue, not a PAE (alone) issue?  What specific CPU are you referring to?

No, it's a PAE issue. You might find this article helpful for better understanding PAE support. [https://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](https://en.wikipedia.org/wiki/Physical_Address_Extension#Linux)

---

### Post by Cheesemill on 2012-05-02
As sudodus mentioned above, just install using the non-PAE mini ISO.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

---

### Post by bab1 on 2012-05-02
> **thnewguy said:**
> No, it's a PAE issue. You might find this article helpful for better understanding PAE support. [https://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](https://en.wikipedia.org/wiki/Physical_Address_Extension#Linux)
I read that last week when 12.04 came out.  I have several P3 servers that I maintain.  This is what I take away from Wikipedia: *"PAE is provided by Intel Pentium Pro (and above) CPUs - including all later Pentium-series processors **except the 400 MHz bus versions of the Pentium M,** as well as by other processors such as the AMD Athlon and later AMD processor models with similar or more advanced versions of the same architecture."*

This sure looks like CPU Architecture to me.

---

### Post by hawkmage on 2012-05-02
In the Wikipedia page on PAE it mentions:
> PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except the 400 MHz-bus versions of the Pentium M).
So you either have a the mentioned Pentium M or really old CPU in the system.  Or for some reason this feature is being masked by the chip set of the system.

From the 12.04 release notes:
> The Ubuntu 12.04 installation image does not include support for old  computers that do not support PAE. If your computer is affected, you can  either first install Ubuntu 10.04 or 11.10 and upgrade to 12.04 or you  can use the Lubuntu or Xubuntu images. The non-PAE version of the Linux  kernel will be dropped completely following the 12.04 release.

So you should be OK to do an in place version upgrade without and issue.

---

### Post by sudodus on 2012-05-02
*kansasnoob* has managed to convince the Ubuntu development team to include a non-pae kernel in some of the 12.04 flavours. And as stated before in this thread, you can also download a non-pae mini-iso file and build your system from that starting point.

Read more about kansasnoob's efforts in the following links

[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1938684_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1938684")
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1951653_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1951653")

---

### Post by thnewguy on 2012-05-02
I decided to bite the bullet and download the 12.04 version of Ubuntu Server to see if it would work. As it turns out, the new Server edition _does_ require a CPU with PAE. CPUs which do not support PAE will not work with Ubuntu Server 12.04.

---

### Post by thnewguy on 2012-05-02
> **bab1 said:**
> I read that last week when 12.04 came out.  I have several P3 servers that I maintain.  This is what I take away from Wikipedia: *"PAE is provided by Intel Pentium Pro (and above) CPUs - including all later Pentium-series processors **except the 400 MHz bus versions of the Pentium M,** as well as by other processors such as the AMD Athlon and later AMD processor models with similar or more advanced versions of the same architecture."*

This sure looks like CPU Architecture to me.

You're confusing architecture with CPU features. Re-read the last line you quoted "processor models with similar or more advanced versions of the **same architecture**". This isn't an i368 vs i686 vs x86_64 type of issue.

---

