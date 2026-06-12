---
title: "Xen with Ubuntu intrepid"
date: 2008-10-14
forum: Virtualisation
---

### Post by denoc on 2008-10-14
Hi,

I'm currently trying to get Xen work on interprid-amd64. I installed a basic system, and than installed the ubuntu-xen-server package. Everthing seems to be installed - without a xen-kernel? I searched the repository for one, but i do not find any xenkernel.

Does someone has a Idea how to get Xen working on Ubuntu Intrepid?


Thanks,

Maik

---

### Post by atoponce on 2008-10-14
Xen is installed into grub, and looks like a linux kernel. You may have to configure grub to tell it to use the Xen kernel as the default, and not a Linux kernel.

However, unless this is a production system, I'd recommend KVM over Xen. Xen is going the way of the Dodo, and KVM is the new way to virtualize Linux.

---

### Post by agent8131 on 2008-10-19
My understanding is that there are no plans to support Xen Dom0's in Intrepid.  I am also finding that DomU support is not currently present either, which is a bigger problem.  There is an effort to get Xen 3.3 backported to Hardy which will be the best setup for using Xen on Ubuntu.  It also may be that Xen users might just ditch Ubuntu and Debian in favor of server oriented distros such as CentOS and SLES.

Yes, KVM is a newer way to do virtualization.  And by newer, I could write "immature".  Don't expect Xen to ever be replaced by KVM.  KVM may work well on the desktop eventually but for servers a hypervisor makes a huge difference in performance.  The only question is which distros want to be used in server environments and which ones are only good for the desktop.  Ubuntu may well be the latter.

---

### Post by bettlebrox on 2009-03-06
This is a bummer for Ubuntu Xen fans, but Ubuntu will be following Red Hat and using KVM in the future. If you want a version of Ubuntu that support Xen you'll have use Hardy. Alternatively, you can build your own [kernel]("http://www.howtoforge.com/installing-xen-3.3-with-kernel-2.6.27-on-ubuntu-8.10-x86_64") or try and use the [Debian packages]("http://www.chrisk.de/blog/2008/12/how-to-run-xen-in-ubuntu-intrepid-without-compiling-a-kernel-by-yourself/")

I'm working on building my own packages using Debian's 2.6.28 source code (patched with Xen). If your interested and I get it to work I'll write it up on my blog.

---

### Post by bedge on 2009-03-07
> **bettlebrox said:**
> 

I'm working on building my own packages using Debian's 2.6.28 source code (patched with Xen). If your interested and I get it to work I'll write it up on my blog.

I'm definitely interested. Let us know when you get it working.

---

### Post by bettlebrox on 2009-03-07
It's a lot of work, I think I'm just going to reuse the debian kernels that support Xen. There available somewhere on [http://kernel-archive.buildserver.net/](http://kernel-archive.buildserver.net/)

---

### Post by pierce_ on 2009-03-12
I love kvm as much as the next guy (I have used it almost daily for about 2 years) but is there anything even close to XenServer that functions as an enterprise virtualization solution that uses kvm?

From what I can see, VMware is the defacto standard for enterprise virtualization, and XenServer from citrix is VMware's only linux based competitor.

We are working on setting up a XenServer instance where I am working, so I thought it should be pretty simple to set up xen on my laptop so I can work on tweaking images, and then migrate them over to the server.

So I started following the Xen installation guide ([https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)), and nothing was working right.  dpkg -L was showing that most of those packages were just installing documentation.  xen-create-image worked just fine, but no kernel image was created.

Is it really possible that ubuntu has completely dropped support for xen?  Why doesn't it mention this at all in the ubuntu documentation?  Why are the packages even still in the repositories if all they do is install documentation?  Can anyone explain to me who made these decisions, and why they were made?  Am I missing something here?

I would love to suggest a kvm based alternative to ESX and XenServer, but does such a thing even exist?

---

### Post by feedbeef on 2009-03-26
There are lots of organizations that use xen and this decision is a total killer. 

HVM on x86 are slower then "binary translation" technique based VMs (for references search portal.acm.org)...

Xen offers lots of useful features, a really important one is Live Migration...

---

### Post by FrankT-Qc on 2009-03-26
I'm a big fan of Xen myself and KVM is still a little young in some situations... But about the live migration, you might want to have a look at this page :

[http://www.linux-kvm.org/page/Migration](http://www.linux-kvm.org/page/Migration)

Have a nice read
François

---

### Post by FrankT-Qc on 2009-03-26
Me again.

Newcommer in Ubuntu, but not to the world... Here's one to boost up on KVM acceptation AND to raise a flag to those ready to ditch Xen.

First, if you have "desktop needs" (and the hardware for it) you might consider giving KVM a try, it's actually impressive and so easy that if you try it and still don't like it, well it shouldn't take you more than an hour or two learning something !

Alright, let's say your were to give it a try... If you're already confortable with Xen, don't bother using virt-manager (while it's an excellent starting point for the basics), start with "kvm --help | less", read through the thing and after ten minutes you'll feel like a pro. Actually virt-manager just lacks flexibility (like the abitily to add your personnal switches...) and tosses in a bunch of stuff (dns, dhcp tun/tap... come on, this is Linux, tune it yourself !!!). You might consider using Qemulator (KVM and QEMU smell pretty much the same) and add a new architecture called KVM that would run using the command "kvm". After you reboot QEMU, just add a virtual machine of type KVM (which you just created) and you're off to the KVM virtual world.

Still, the kvm command is pretty simple (either kvm --help or man qemu, once again, kvm (command) works like qemu (command)). Nothing beats a few good scripts... You like xentop ? Did you know that you can provite top with the pid you want to monitor (pgrep kvm + top = pretty much xentop) ?... Anyway, we're drafting away there.


Device virtualization is the feature you're missing ? Well go spend a few minutes to linux-kvm.org ... It's already quite advanced in this direction and there's even a virtual ethernet driver for Windows XP... (while you could, of course, just emulate a normal ethernet card, but hey, don't you like tweaking !)

BUUUUUTTT No mather how I love Ubuntu, if you're a Xen master (sounds cool, doesn' it !) then you will soon miss a few things from Xen (You might want to know that XenServer is now free). Well it might be time for you to go shopping for a while...Debian ?  Fedora ? CentOS ? Hey... Diversity exists for a reason !!! 

At my place, I have Xen on two servers with Debian(ish) Dom0 where more and more DomU are Ubuntu and it's pure gold... But on my desktop, KVM's the new king... Would my cheap server support it, I I would probably swith it to Ubuntu/KVM just to keep the pace, taking into acount that it holds my less critical services. (Actually, that would also force me to swith my desktop back to Xen to still have a test bench and that's not gonna happen. I'm keeping KVM there and... Ubuntu is just so sweet, I'd miss it too much !)

By the way, just to be fair with virt-manager, while the current version left me a little cold (as it did under Xen), a new version has come out that is quite promising. You might want to keep an eye on the repos and give it a chance when it shows up.

So, Xen, KVM ... The answer : Both... Who the hell has decided that there isn't room for two (thinking this way, we'd be using Windows) 

Why is Xen not supported by Intrepid ? Well maybe if Xen would hit it mainstream in the kernel... Time being short, they have decided to focus on KVM but who said that you had to focus on Ubuntu ? After all, if you're going to add five or six extra guests on your machine because your extra lean Xen installation allows you, your sacrificing one Ubuntu dom0 for potentially a few Ubuntu domU !!! Everyone's a winner !

Pushing KVM up is one, pushing Xen down is a huge loss (like biodiversity... geekodiversity)

Pffieeew... My longest post ever... I need sugar !

Have fun,
François

---

### Post by erlguta on 2009-04-22
I am totally surprised too.
Who the hell took this decision.
Ok KVM for desktops, and for play with it for normal users. It is nice and blah, blah, blah... But there is people who works in large enterprise with a LOT of critical servers deployed it in Xen with very important services (yes lots of $$$$$$$, not for play).

And now with the new Jaunty server announcing the cloud with "Eucalyptus" (in that so stupidly sensationalism way that only knows how to make ubuntu), which ONLY works with Xen....:confused:

Extracted from: [http://eucalyptus.cs.ucsb.edu/wiki/FAQ](http://eucalyptus.cs.ucsb.edu/wiki/FAQ)
> 
What software environments are supported?

Eucalyptus targets Linux systems that use Xen (versions 3.*) for virtualization. We provide binary RPMs for i386 and x86_64 RPM-based systems and also offer a source package as well for installation on other common Linux distributions. 


It is going to be supported again?
This is a joke?
Who the hell is understand something?
How is going to be Ubuntu serious in the enterprise market with this decisions?.

---

### Post by erlguta on 2009-04-22
As you can see here:
[http://www.workswithu.com/2009/04/10/cloud-computing-what-can-it-do-for-ubuntu/](http://www.workswithu.com/2009/04/10/cloud-computing-what-can-it-do-for-ubuntu/)

> 
Given that Eucalyptus requires the Xen hypervisor, it would seem that work needs to be done on a Xen kernel image for Karmic’s release, something that has been missing from Ubuntu releases for nearly 18 months since the decision was made to drop Xen in favour of KVM as the supported virtualisation solution.


So..it is true?
I see in ubuntu-packages that there is not one xen linux-image

---

### Post by digi123 on 2009-11-07
Hi, 
i have trying to install xen in ubuntu intrepid  .. please if any one can tell me solution 
reply asap

digvijay@digvijay-desktop:~$ sudo apt-get -f install
[sudo] password for digvijay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xen-utils-3.3
The following NEW packages will be installed:
  xen-utils-3.3
0 upgraded, 1 newly installed, 0 to remove and 465 not upgraded.
1 not fully installed or removed.
Need to get 0B/868kB of archives.
After this operation, 2650kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 347381 files and directories currently installed.)
Unpacking xen-utils-3.3 (from .../xen-utils-3.3_3.3.0-1ubuntu7.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xen-utils-3.3_3.3.0-1ubuntu7.1_i386.deb (--unpack):
 trying to overwrite `/usr/sbin/xend', which is also in package xen-utils-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xen-utils-3.3_3.3.0-1ubuntu7.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

