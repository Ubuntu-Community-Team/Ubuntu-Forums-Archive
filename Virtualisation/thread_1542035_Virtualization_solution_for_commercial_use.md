---
title: "Virtualization solution for commercial use"
date: 2010-07-30
forum: Virtualisation
---

### Post by Simon Cropper on 2010-07-30
Hi,

I need a virtualization solution that allows me to use the VM in a commercial environment and have full access to the host system (especially USB connectivity).

I have been using VirtualBox (OSE) with XP Pro for a while but have encountered the ongoing problem that this product does not support USB connectivity. I would love to know why? Is the USB code proprietary?

Anyway, if you work through the treads on this forum you see that most suggest that you use VirtualBox (PUEL) but the license excludes use in a commercial environment (albeit there is only one person using the VM).

If you move to the other contender,VMWare, their license states "VMware Player is intended for your own personal non-commercial use only".

If I look at the MegaThread at the top of this forum and visit sites for alternatives you quickly see that most are designed for use with servers and are not really suitable for a host:guest | 1:1 | ubuntu-lucid:XPPro relationship.

Anyone have any suggestions about alternatives for use in a SOHO environment, where USB connectivity is available?

Simon

---

### Post by psavva on 2010-07-30
> **Simon Cropper said:**
> Hi,

I need a virtualization solution that allows me to use the VM in a commercial environment and have full access to the host system (especially USB connectivity).

I have been using VirtualBox (OSE) with XP Pro for a while but have encountered the ongoing problem that this product does not support USB connectivity. I would love to know why? Is the USB code proprietary?

Anyway, if you work through the treads on this forum you see that most suggest that you use VirtualBox (PUEL) but the license excludes use in a commercial environment (albeit there is only one person using the VM).

If you move to the other contender,VMWare, their license states "VMware Player is intended for your own personal non-commercial use only".

If I look at the MegaThread at the top of this forum and visit sites for alternatives you quickly see that most are designed for use with servers and are not really suitable for a host:guest | 1:1 | ubuntu-lucid:XPPro relationship.

Anyone have any suggestions about alternatives for use in a SOHO environment, where USB connectivity is available?

Simon

Hi Simon, 

I highly suggest you try XEN [http://www.xen.org/](http://www.xen.org/)

XEN is an open source virtualization layer.
You can actually download a live CD as to try it before actually going though the process of installing it in a production environment.

[http://wiki.xensource.com/xenwiki/LiveCD](http://wiki.xensource.com/xenwiki/LiveCD)

XEN is used as a basis for Citrix XEN Server, which is a commercial implementation of XEN, which offers support.

[http://www.citrix.com/English/ps2/products/product.asp?contentID=683148](http://www.citrix.com/English/ps2/products/product.asp?contentID=683148)


Good Luck!!!

---

### Post by Simon Cropper on 2010-07-30
Hi,

After further investigation I uncovered the following clarification on the VirtualBox Site under FAQ Licensing...

> 6. What exactly do you mean by personal use and academic use in the Personal Use and Evaluation License? 

Personal use is when you install the product on one or more PCs yourself and you make use of it (or even your friend, sister and grandmother). It doesn't matter whether you just use it for fun or run your multi-million euro business with it. Also, if you install it on your work PC at some large company, this is still personal use. However, if you are an administrator and want to deploy it to the 500 desktops in your company, this would no longer qualify as personal use.
[RIGHT][http://www.virtualbox.org/wiki/Licensing_FAQ]("http://www.virtualbox.org/wiki/Licensing_FAQ")[/RIGHT]


So it appears that although not specified as clearly as this in the licence, my personal circumstances (SOHO) would allow me to use the PUEL version of VirtualBox :).

---

