---
title: "VirtualBox 2.0.2 -  Sun Microsystems"
date: 2008-09-28
forum: Virtualisation
---

### Post by transmeta on 2008-09-28
Turn your PC into an easy-to-use virtualization platform with Sun xVM VirtualBox, the free and open source software that runs on all major operating systems and eliminates the need for tradeoffs or multiple hardware systems.

[http://www.sun.com/software/products/virtualbox/](http://www.sun.com/software/products/virtualbox/)

Transmeta

---

### Post by Coombabah on 2008-09-28
> **transmeta said:**
> Turn your PC into an easy-to-use virtualization platform with Sun xVM VirtualBox, the free and open source software that runs on all major operating systems and eliminates the need for tradeoffs or multiple hardware systems.

[http://www.sun.com/software/products/virtualbox/](http://www.sun.com/software/products/virtualbox/)

Transmeta

If anyone uses VirtualBox please take the time to read the VirtualBox license as you may unwittingly be violating the license agreement.

I went to the link above clicked the "Get It" tab and saw the following.

> 
Get Sun xVM VirtualBox

Download free and open source Sun xVM VirtualBox and use one platform to write software to any operating system in the datacenter.
Download Sun xVM VirtualBox

Run multiple operating systems at the same time with this award winning, easy to use, no cost desktop virtualzation product.

	 
Download Sun xVM VirtualBox Open Source Edition

VirtualBox Open Source Edition is the source code, licensed under GPLv2, and useful to developers who want to compile and build their own product.



This is where it gets confusing as both download links go to the same download page.

I selected the "Download Sun xVM VirtualBox Open Source Edition" option and then downloaded the hardy version expecting it to be "Free" not evaluation or personal use with limitations.

Although the page heading says "Free and Open Source" this is the start of the virtualbox license conditions you have to agree to during it's installation.

Unfortunately even some of the features I currently use with the free Vmware Server would violate the free VirtualBox license even for personal use :(


> 
VirtualBox Personal Use and Evaluation License (PUEL)

License version 6, July 28, 2008

Sun Microsystems, Inc. (“Sun”) grants you the right to use the software product as defined in § 1 according to the following provisions. If you do not agree to all conditions set forth by this license, you may not use the product, because only Sun as the product’s owner can give you permission to use it.

§ 1 Subject of license. “Product”, as referred to in this License, shall be the binary software package “VirtualBox”, which allows for creating multiple virtual computers, each with different operating systems (“Guest Computers”), on a physical computer with a specific operating system (“Host Computer”), to allow for installing and executing these Guest Computers simultaneously. The Product consists of executable files in machine code for the Windows, Mac OS X, Linux and Solaris operating systems as well as other data files as required by the executable files at run-time and documentation in electronic form.

§ 2 Grant of license. (1) Sun grants you a personal right to install and execute the Product on a Host Computer for Personal Use or Educational Use or for Evaluation. “Personal Use” requires that you use the product on the same Host Computer where you installed it yourself and that no more than one client connect to that Host Computer at a time for the purpose of displaying Guest Computers remotely. “Educational use” is any use in an academic institution (schools, colleges and universities, by teachers and students). “Evaluation” means testing the product for a reasonable period (that is, normally for a few weeks); after expiry of that term, you are no longer permitted to evaluate the Product...

I realise Sun also have an open source version where you can download the source code and compile it yourself but it is probably a cut down version like before and more suited to developers than end users.
Both the free and the open source links on their "Get It" page actually go to the same download page. Most of the links on that page are actually for the closed source restrictive license version. The second last link has the source tar file VirtualBox-2.0.2-OSE.tar.bz2 if you are looking for the Open Source Edition.

This is disappointing as if I recommended VirtualBox to friends and colleagues they'd probably end up downloading and using it illegally and not realise it.

It looks like the free VMWare Player and Server is still safer to recommend to friends and colleagues if you don't want to encourage the illegal use of software.

Does anyone know if Sun plan on changing the VirtualBox license to make the versions most people will download a bit more like the free and open source version that is promoted?

---

### Post by markba on 2008-09-29
Licensing in VirtualBox is indeed tricky, confusing, etc. But if you use the OSE version from the Ubuntu repo (2.0.2 is included in Intrepid), it's absolutely free (as in freedom) to use. It goes without saying that the version in the repo is precompiled, so there's no need to do this yourself. There are also no EULA's to sign or accept.

The OSE version does not have USB support and a VRDP server.

---

