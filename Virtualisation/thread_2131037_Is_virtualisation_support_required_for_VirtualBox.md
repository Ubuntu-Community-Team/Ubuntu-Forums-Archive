---
title: "Is virtualisation support required for VirtualBox??"
date: 2013-03-31
forum: Virtualisation
---

### Post by arunb on 2013-03-31
Hi,

The laptop that I intend to buy has this kind of processor./[http://ark.intel.com/products/69669/]("http://ark.intel.com/products/69669/")

This processor does not have Virtualisation and Hyperthreading..see above link.

My question will I be able to run VirtualBox on the laptop? The main OS will be Ubuntu 12.04 and the VirtualBox will run Windows 7, or Windows XP.

I read in the internet that Virtualisation is needed to run VirtualBox...

Please enlighten me...

thanks
a

---

### Post by haqking on 2013-03-31
> **arunb said:**
> Hi,

The laptop that I intend to buy has this kind of processor./[http://ark.intel.com/products/69669/](http://ark.intel.com/products/69669/)

This processor does not have Virtualisation and Hyperthreading..see above link.

My question will I be able to run VirtualBox on the laptop? The main OS will be Ubuntu 12.04 and the VirtualBox will run Windows 7, or Windows XP.

I read in the internet that Virtualisation is needed to run VirtualBox...

Please enlighten me...

thanks
a

[http://www.virtualbox.org/manual/ch10.html#hwvirt](http://www.virtualbox.org/manual/ch10.html#hwvirt)

---

### Post by sudodus on 2013-03-31
Are you thinking about

Intel® Virtualization Technology (VT-x) and Intel® Virtualization Technology for Directed I/O (VT-d)?

I recently tried to run a 64 bit system in VirtualBox in a new computer, and had to switch on VT-x in a BIOS menu to succeed. But I'm pretty sure it works for 32 bit systems without it, because I have 32 bit guest systems in an old computer (this one I'm using now) both with and without VT-x activated in the virtual machines for 32 bit systems (and they work).

---

### Post by arunb on 2013-03-31
I am planning to buy a laptop with a Pentium Dual Core (2nd Generation) processor. The laptop would run on Ubuntu 12.04 (64 Bit), and the virtualbox will run Windows 7, Windows XP, Ubuntu 10.04 (32 Bit).

The processor details are...

Pentium Dual Core (2nd generation)
Variant: B980
RAM: 8 GB (Max.) DDR3 1333Mhz Speed: 2.4 Ghz
2MB Cache

Will the above processor work ??

According to the support page for this processor...[http://ark.intel.com/products/69669/]("http://ark.intel.com/products/69669/")

There is no support for hardware virtualization, also no hyper threading support.

Is it possible to run VirtualBox without this support ??

Please do be correct as this info is very crucial to me since I have not yet bought the laptop...

thanks
a

---

### Post by sudodus on 2013-03-31
Please read the replies in your previous thead!

As far as I understand the support for 64 bit guest systems needs virtualisation, but you can run 32 bit guest systems without it. What do you want and need? The better you explain to us, the better advice we can give to you.
Finally you should know that we (who help at the Ubuntu Forums) are volunteers. We get no money, so we cannot give any guarantees, only advice based on our experience. The advice is almost always correct, but no guarantee.

---

### Post by arunb on 2013-03-31
yes sudodus thats what I have in mind...

These two technologies are not supported in the processor. As I haven't yet bought the laptop I wanted to be sure...

@haqking..

I read the link you posted..It says VirtualBox can run on old systems which have no hardware virtualisation technology, but is it possible to run Windows 7 (64bit) ?? 

thanks
a

---

### Post by arunb on 2013-03-31
I need to run Windows 7 (64Bit) for some Windows based programs, the other OSes (ubuntu 10.04, windows XP) are all 32 bit.

I have read your replies in the older thread...

Sorry for the double post, I did not realise that I had posted the same question in two different forums.

It seem I should buy a system which has support for hardware virtualisation technology..

thanks
a

---

### Post by sudodus on 2013-03-31
My experience is that I cannot run 64 bit guest systems in Virtualbox without VT-x. So if I would like to run Windows 7 (64bit) as a guest system, I would get another computer. The computer where I run 64 bit guest systems has an intel i5 cpu

[[COLOR=#ff0000]http://ark.intel.com/products/53452/[/COLOR]]("http://ark.intel.com/products/53452/")

It came with a computer that I bought 'second-hand'.

---

### Post by QIII on 2013-03-31
[I]Threads [B]merged.


[/B][/I]Please do not start duplicate threads.

Thanks!

---

### Post by Cheesemill on 2013-03-31
> **arunb said:**
> I read the link you posted..It says VirtualBox can run on old systems which have no hardware virtualisation technology, but is it possible to run Windows 7 (64bit) ??

No.

If your CPU *or* motherboard don't support VT-x or AMD-V then you can only run 32-bit guest OS's.
Your VM's will also be much slower than the same VM running on a machine that does support hardware virtualization.

---

### Post by arunb on 2013-03-31
is Intel Virtualization Technology for directed I/O (VT-d) also required to run a 64 bit OS in VirtualBox ??

---

### Post by sudodus on 2013-03-31
> **arunb said:**
> is Intel Virtualization Technology for directed I/O (VT-d) also required to run a 64 bit OS in VirtualBox ??
I don't know (I never heard anything about it in connection to VirtualBox).

---

### Post by Cheesemill on 2013-04-01
> **arunb said:**
> is Intel Virtualization Technology for directed I/O (VT-d) also required to run a 64 bit OS in VirtualBox ??

No, it isn't.

---

### Post by afz12 on 2013-04-15
This notebook (hp dv6 i4 quad core) runs Virtualbox from Mint Cinnamon and (now) Ubuntu 13.04 Beta host OS's. It runs other VM's whether they are 32 bit or 64 bit, no problem. However I checked the BIOS and it has an option for virtualization, checked active by default, but no refernece to any VT-*type etc. I suspect the other posters are correct - however your best bet may be to test the computer you intend to buy in the shop by booting into BIOS (perhaps press escape key). If it has not option, or if the shop staff are unhelpful I would be reticent in buying the device. FYI, I tried disabling the BIOS virtualization option on this notebook some time ago and Virtualbox definitely did not work!

If you need to be sure, I suggest you look for a computer / notebook / tablet etc that provides evidence of being virtualization ready. There seem to be a wide range of excellent models these days, if I bother to upgrade I would not consider anything less than i7, quad core, 8 GB RAM, 2 GB graphics, 1 TB hard drive, USB3 support etc etc. Good luck!

---

