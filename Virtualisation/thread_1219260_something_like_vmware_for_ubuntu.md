---
title: "something like vmware for ubuntu?"
date: 2009-07-21
forum: Virtualisation
---

### Post by krtek80 on 2009-07-21
Hello,

does someone know if it's possible to install something like vmware virtual machine on ubuntu to enable function of windows programmes ?

Please let me know on [EMAIL="hrdlicka.milan@gmail.com"]hrdlicka.milan@gmail.com[/EMAIL]

Thanks a lot.

Milan

---

### Post by ajgreeny on 2009-07-21
VirtualBox is available either from the repos or direct from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).  Go for the second as it will allow certain extras to work not available on the repository version, which is the open source version.

It is very easy to use, many say easier than vmware, but I've never used vmware, so can't compare, but I have used VirtualBox with ease.

---

### Post by bacil on 2009-07-21
There is couple of products:

1. VirtualBox - open source or closed source developed by Sun 
2. qemu - brilliant tool that can emulate spectrum of different cpu and platforms (eg you can emulate sparc on x86)
3. kvm
4. xen - default in SUSE and RH

so you have nice selection of products, and i have mentioned only most important ones :-) and if ia ma not mistaken you can get free vmware server on linux aswel

---

### Post by bodhi.zazen on 2009-07-21
Sometimes people find the stickies are informative. It is hard to see them as they are right on the top of the forum and it is easy to over look them 

**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[The Virtualization Mega-Thread]("http://ubuntuforums.org/showthread.php?t=973756")

---

### Post by doas777 on 2009-07-21
> **bodhi.zazen said:**
> Sometimes people find the stickies are informative. It is hard to see them as they are right on the top of the forum and it is easy to over look them 

**[B]Sticky:**[/B]                                      [COLOR=#008c00]**[all variants]**[/COLOR]                          [The Virtualization Mega-Thread]("http://ubuntuforums.org/showthread.php?t=973756")

I never see stickies. they are not on the search page, and I never end up in any of the categories, just the "New Posts" and "Find all My Posts" lists.

your point is well taken however. always google and search the forum before posting.

---

### Post by Sxeptomaniac on 2009-07-21
I think it might be good to point out that you don't even necessarily have to use something *like* VMware, as there is a Linux version of that software available, too.  There's a good variety of virtualization options available for Linux, so it's up to you to decide what's best.

---

### Post by nmaster on 2009-07-21
i like virtualbox, but i've never tried anything else.  these are really good for getting started:

[http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox](http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox)

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by bodhi.zazen on 2009-07-21
> **doas777 said:**
> I never see stickies.

As I said, they are hard to see =)

Sometime the best place to hide something is out in the open.

---

### Post by Lem on 2009-07-23
In fact it is possible to install something exactly like vmware in Ubuntu.

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

---

### Post by rbishop on 2009-07-23
I currently use VMware server on my Ubuntu Servers.  It does involve a lot of command line setup, but it is very easily managed via the web.

I used the following guide:

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04)

---

### Post by juancarlospaco on 2009-07-23
[Use Convirt]("http://www.tecnicoslinux.com.ar/livecd/auto-repo-cnvrt_1_all.deb"), and your servers can run without web servers running, it only needs SSH, no X needed.

Live Migration *(two-ways)* with Drag&Drop, nice GUI, Snapshots, Backups, Templates, opensource.

---

