---
title: "Xubuntu 18.04 working well."
date: 2017-11-14
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2017-11-14
No particular problems to report but I have just created a new VM installation of Xubuntu 18.04 64 bit system using VBox 5.1.30, which is all working well.

The minor difficulties I have seen so far have been the same problems already reported in the default Ubuntu 18.04 system such as gdebi not being available from a right click -> open with in the file manager as discussed at [https://ubuntuforums.org/showthread.php?t=2377258](https://ubuntuforums.org/showthread.php?t=2377258) with the bug at [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1719746](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1719746).

Looking good so far though I'm aware there is a long way to go with both versions of 18.04, but I am very hopeful fpor them both as things stand at present.

---

### Post by Cavsfan on 2017-11-14
I've got 18.04 working pretty well too. I installed Ubuntu from an ISO yesterday and today I turned it (pretty much) into Xubuntu by installing all of the Xfce stuff from Synaptic.

I no longer have any problems with Synaptic and was able to install the Nvidia driver, Cairo Dock, Compiz along with the cube and everything is smooth as silk.

I installed Vivaldi, which is a lightweight browser an offshoot of Chrome. It uses much less resources than Firefox or any other browser I'm pretty sure.
You can add the stable deb to Ubuntu from here [https://vivaldi.com/](https://vivaldi.com/) either 32 or 64 bit. I use it everywhere even on Windows 10.

A couple of screenshots:

[[IMG]http://en.zimagez.com/miniature/screenshot2017-11-1416-42-04.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2017-11-1416-42-04.php")

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2017-11-1416-44-34.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2017-11-1416-44-34.php")

This may all blow up later since this is so early but, looking good for now.

---

### Post by Chanath on 2017-11-14
> **ajgreeny said:**
> No particular problems to report but I have just created a new VM installation of Xubuntu 18.04 64 bit system using VBox 5.1.30, which is all working well.

The minor difficulties I have seen so far have been the same problems already reported in the default Ubuntu 18.04 system such as gdebi not being available from a right click.

There is no problem of Gdebi working on right click in Xubuntu 18.04. Just install it in bare metal. Never had any problems with Xubuntu for few years. This edition would also be the same, trouble less use. :)

---

### Post by vasa1 on 2017-11-14
> **Chanath said:**
> There is no problem of Gdebi working on right click in Xubuntu 18.04. Just install it in bare metal. ...
I wonder why a virtual machine would not be able to do the job :???:

---

### Post by Chanath on 2017-11-15
> **vasa1 said:**
> I wonder why a virtual machine would not be able to do the job :???:

What the use of testing on a virtual machine?

---

### Post by slickymaster on 2017-11-15
> **Chanath said:**
> What the use of testing on a virtual machine?Using virtual machines in QA testing, allow testers to emulate different computers with different OS’s on a single physical computer or create a whole virtual lab, with several differently configured virtual machines. These virtual computers work independently from each other and you can launch two or more virtual platforms simultaneously on one computer, saving the cost of having to purchase more hardware just to run your QA tests. Applications running on a virtual machine behave as if they were running on their own physical system. This is very useful for testing applications and allows testers to test the software under various platforms using a single computer.

---

### Post by vasa1 on 2017-11-15
I thought that Chanath, in post #3, was implying that this particular feature (gdebi on right-click) would only work on bare metal and not in a VM.

As for "What the use of testing on a virtual machine?" there's [https://wiki.ubuntu.com/QATeam/DevelopmentSetup](https://wiki.ubuntu.com/QATeam/DevelopmentSetup)

---

### Post by ajgreeny on 2017-11-15
It is possible I was speaking too fast, stupid of me maybe, but having installed gdebi in Ubuntu 18.04 I also added it to Xubuntu 18.04 and immediately edited the gdebi.desktop file, adding the %U suffix to the Exec line, assuming it was going to be necessary; I know, I should not make assumptions, but I did, as we all have done sometimes.

Removing that %U suffix does not remove the ability of the file manager to find gdebi on a right click of a .deb package, as was the case in a standard Ubuntu installation, so perhaps Chanath is correct and thunar would have seen it without that edit to the .desktop file.

If I have time I may start again with another installation of Xubuntu 18.04 with a newer daily .iso to see if Chanath or I was correct. I will report back when and if I get time to do that.

None of this changes my comment that the system is working extremely well and is still looking very good.

---

### Post by Chanath on 2017-11-15
The installation works quite differently in virtual environment than in bare metal. If we are checking out a distro, the virtual environment is quite all right, but if we are testing, it should be on bare metal. You don't need much to install Xubuntu, just about 4GB partition. If anyone can spare at least 8GB, that's enough for testing. These days, laptops normally have 1TB, most have 500GB. An installation on bare metal gives you real results.

---

### Post by VMC on 2017-11-15
> **Chanath said:**
> The installation works quite differently in virtual environment than in bare metal. If we are checking out a distro, the virtual environment is quite all right, but if we are testing, it should be on bare metal. You don't need much to install Xubuntu, just about 4GB partition. If anyone can spare at least 8GB, that's enough for testing. These days, laptops normally have 1TB, most have 500GB. An installation on bare metal gives you real results.
+1. Also I find my graphics hardware are not fully tested. In the past, when all seems well using vm, then comes the release, then bare metal install. then the issues start. I never use vm since!

---

### Post by ajgreeny on 2017-11-15
I have now tested gdebi on a second installation of today's daily iso and Chanath was correct about that; gdebi works fine when installed with no need for the edit of its .desktop file as is required in Ubuntu 18.04.

I assume the difference is due to the different DE and file manager, but admit that I am no expert in gnome in any of its forms any more, so there may be more to it than that.

Regarding running in a virtual system; that is all I am prepared to do at present as I am not going to potentially damage my main installation by editing partitions on what is a critical system that I can not afford to mess up.  I know the likelihood of that is very small, but I am a little more careful these days with a UEFI system.

---

### Post by monkeybrain20122 on 2017-11-15
> **ajgreeny said:**
> 

Regarding running in a virtual system; that is all I am prepared to do at present as I am not going to potentially damage my main installation by editing partitions on what is a critical system that I can not afford to mess up.  I know the likelihood of that is very small, but I am a little more careful these days with a UEFI system.

I have a 500G external hd that I use for backups. Since I have a lot less data to backup I carved out several ext4 partitions in which I installed fully various Linux distros (right now I have Ubuntu18.04, Ubuntu-unity-edition 18.04, Fedora 27 and Kubuntu 17.10) I can boot them off different machines which is ideal for testing . Other than boot time I get the same performance as installing internally.

---

### Post by Chanath on 2017-11-15
When we are using Ubuntu, it is just as we are using a mixture of Debian Testing and Sid. So, we are always in a continuous development cycle, whether or not we are using the "stable" or the "development branch" releases. In the "stable" release the packages from Testing and Sid are frozen enough to be considered as stable, but not in Debian, where they come from. So, I don't ever use Ubuntu "stable" release, maybe few weeks until a new "repo" name is announced. I don't really know, if Ubuntu has thousands of maintainers for all those Testing/Sid packages, or they just sit there in the new repo, repackaged in to the Ubuntu deb way. But, it is exciting to be on the rolling. I have two Arch installs too.

For a long time, I am not that interested, if something would break. I keep all my data in a separate partition, so data is untouched. I can always reinstall the distro. As I do all updates and upgrades through a console, I keep an eye on what gets upgraded. I also never install an app from the Software store. On stability, I trust Kubuntu and Xubuntu. The Openbox install is the easiest one to maintain. I have Bionic Unity that refuses to break. I've moved the default Ubuntu to Vanilla-Gnome. I think Kubuntu is the most developed, most fully-fledged, most looked after distro in the Ubuntu family.

---

### Post by QIII on 2017-11-15
> **Chanath said:**
> The installation works quite differently in virtual environment than in bare metal. If we are checking out a distro, the virtual environment is quite all right, but if we are testing, it should be on bare metal. You don't need much to install Xubuntu, just about 4GB partition. If anyone can spare at least 8GB, that's enough for testing. These days, laptops normally have 1TB, most have 500GB. An installation on bare metal gives you real results.

Testing can most certainly be done in a VM and is done all the time.  All that is required when making a bug report is that the fact that a VM is used (and what type) is included in the report.  The developers will skip what appears to be a kernel issue if something like VBox, which taints the kernel, is used.  A KVM machine does not taint the kernel.

Please don't attempt to dictate the conditions of testing based on your opinion.  Testing "should be done" using whatever the tester has at hand.

---

### Post by Chanath on 2017-11-16
> **QIII said:**
> Testing can most certainly be done in a VM and is done all the time.  All that is required when making a bug report is that the fact that a VM is used (and what type) is included in the report.  The developers will skip what appears to be a kernel issue if something like VBox, which taints the kernel, is used.  A KVM machine does not taint the kernel.

Please don't attempt to dictate the conditions of testing based on your opinion.  Testing "should be done" using whatever the tester has at hand.

I don't think the developers make distros to be used on virtual environments. People use distros for real use in real hardware. For example, the Gdebi problem didn't happen in real hardware.

---

### Post by ajgreeny on 2017-11-16
> **Chanath said:**
> I don't think the developers make distros to be used on virtual environments. People use distros for real use in real hardware. For example, the Gdebi problem didn't happen in real hardware.

That may be what they would wish but surely it is the user's right to use the OS in whatever way works for them; not everybody has, or is prepared to make another partition in order to install a non-released version of *Ubuntu.

In spite of all this discussion about gdebi it is still a fact that the OS itself is working extremely well with no show-stoppers so far, so let's get back to the real reason for my starting this thread and leave the discussion of gdebi, and VMs vs hard metal installs for another time.

---

### Post by Chanath on 2017-11-16
> **ajgreeny said:**
> That may be what they would wish but surely it is the user's right to use the OS in whatever way works for them; not everybody has, or is prepared to make another partition in order to install a non-released version of *Ubuntu.

In spite of all this discussion about gdebi it is still a fact that the OS itself is working extremely well with no show-stoppers so far, so let's get back to the real reason for my starting this thread and leave the discussion of gdebi, and VMs vs hard metal installs for another time.

*Xubuntu 18.04 works extremely well in bare metal. *
No idea how it'd work in a virtual environment or any other Ubuntu 18.04 derivative. I don't use VMs for real distros, but to check out some exotic ones.  :)

---

### Post by ventrical on 2017-11-16
> **Chanath said:**
> *Xubuntu 18.04 works extremely well in bare metal. *
No idea how it'd work in a virtual environment or any other Ubuntu 18.04 derivative. I don't use VMs for real distros, but to check out some exotic ones.  :)

Xubuntu has most always worked well on bare metal.  When using a VM there is always a chance that the V-chip technology (hypervisor) which allows for concurrently run  kernels will fail to emulate a physical  IRQ and some apps  jockey for the same IRQ so if a concurrently run kernel is using that IRQ then often times it will not jockey the apps in. but for the most part to run test cases from QA/tracker  is an efficient way to test, so,in comes LXC containers. :) so one case is generic and the other case may be ortho-generic.

So I have an ortho-generic install of xubuntu 18.04 running soley on a Barracuda 80GB hdd being upgraded to the end of the cycle. When apport flags a bug I send it. 

regards..

---

### Post by monkeybrain20122 on 2017-11-17
VM testing will not work for graphic related issues.

---

### Post by ajgreeny on 2017-11-17
Having realised that I still had a redundant 21GB partition that had Trusty on it previously, and now having figured out how to change the OS which manages grub back to Xenial on my UEFI machine, I have now installed Xubuntu 18.04 as a "proper" bare metal install.

It is difficult to see any major differences between the VM and the bare metal system either in terms of their speed of booting and running, or in any obvious other ways such as the display/graphics.

Definitely looking good, though I accept there's a long way still to go.

---

### Post by Chanath on 2017-11-17
> **ajgreeny said:**
> Having realised that I still had a redundant 21GB partition that had Trusty on it previously, and now having figured out how to change the OS which manages grub back to Xenial on my UEFI machine, I have now installed Xubuntu 18.04 as a "proper" bare metal install.

Definitely looking good, though I accept there's a long way still to go.

You won't find much (any) problems with Xubuntu 18.04.

---

### Post by flocculant on 2017-11-17
> **Chanath said:**
> You won't find much (any) problems with Xubuntu 18.04.

Shortly we will be sorting out a ppa with 'stuff' we want to bring to the LTS, some updates to apps, some gtk3 updates, we've already got changes to panel plugins on the daily - so it's likely to change.

All that aside - not many from the Xubuntu team look here regularly - it's much too non-Ubuntu aimed for it to be much use to us as place to use. That said slicky<tab> and I **do** check here. Xubuntu's work does tend to be more irc and ml based.

All efforts by those frequenting this small place in the interwebs helping to keep a small part of the freedom going is much appreciated.

---

### Post by Chanath on 2017-11-18
> **flocculant said:**
> Shortly we will be sorting out a ppa with 'stuff' we want to bring to the LTS, some updates to apps, some gtk3 updates, we've already got changes to panel plugins on the daily - so it's likely to change.

All efforts by those frequenting this small place in the interwebs helping to keep a small part of the freedom going is much appreciated.

How to install (or from where to get) libxfconf-0-dev  4.13.0 or xfconf 4.13+ ?
I have Exo 0.11.4 installed, but can't install xfce4-settings-4.13.1

---

### Post by ventrical on 2017-11-18
> **ajgreeny said:**
> Having realised that I still had a redundant 21GB partition that had Trusty on it previously, and now having figured out how to change the OS which manages grub back to Xenial on my UEFI machine, I have now installed Xubuntu 18.04 as a "proper" bare metal install.

It is difficult to see any major differences between the VM and the bare metal system either in terms of their speed of booting and running, or in any obvious other ways such as the display/graphics.

Definitely looking good, though I accept there's a long way still to go.

The log-out still does not work  but that's a small bug.. maybe something I did or didn't do :) Iv'e seen cycles where xubuntu has went south with breakage. Yes, there are ways to recover if you want to sit for hours doing google searches but it is much easier doing a fresh install. I find that the breakage happens on all flavors when trying out ppas or off apps (meaning apps from other flavor software centers) so there is always the chance that a slippery depend is going or be added or removed.

---

### Post by ajgreeny on 2017-11-18
I have no PPAs enabled when testing a dev version, though I do have some on my main full installation of 16.04.

It seems a bit unfair to add a PPA to an OS that is still in development and which I want to give as fair a test as is possible.

---

### Post by ventrical on 2017-11-18
> **ajgreeny said:**
> I have no PPAs enabled when testing a dev version, though I do have some on my main full installation of 16.04.

It seems a bit unfair to add a PPA to an OS that is still in development and which I want to give as fair a test as is possible.
+1

---

### Post by Chanath on 2017-11-18
> **ajgreeny said:**
> I have no PPAs enabled when testing a dev version, though I do have some on my main full installation of 16.04.

It seems a bit unfair to add a PPA to an OS that is still in development and which I want to give as fair a test as is possible.

But, we can test a little, can't we? Have a read here, [https://smdavis.us/](https://smdavis.us/)

---

### Post by flocculant on 2017-11-19
> **ajgreeny said:**
> I have no PPAs enabled when testing a dev version, though I do have some on my main full installation of 16.04.

It seems a bit unfair to add a PPA to an OS that is still in development and which I want to give as fair a test as is possible.

These particular ppa's are there to test xfce packages (for the most part) which are intended to land during the cycle. They're not set up by some random user, but by the Xubuntu devs.

---

### Post by slickymaster on 2017-11-19
> **flocculant said:**
> These particular ppa's are there to test xfce packages (for the most part) which are intended to land during the cycle. They're not set up by some random user, but by the Xubuntu devs.And some fearless testers ;)

---

### Post by ajgreeny on 2017-11-19
> **flocculant said:**
> These particular ppa's are there to test xfce packages (for the most part) which are intended to land during the cycle. They're not set up by some random user, but by the Xubuntu devs.
I did not know thatso thanks for the info.

---

### Post by flocculant on 2017-11-19
> **ajgreeny said:**
> I did not know thatso thanks for the info.

np - I thought that was the case :)

I'd not talk about ppa's for xubuntu testing as a general rule, the ones I use are a bit different. The Xubuntu Team ppa's are listed on [https://launchpad.net/~xubuntu-dev](https://launchpad.net/~xubuntu-dev) if you're interested. 

Also included in those are the packages which are currently being moved to Gtk3.

---

### Post by Cavsfan on 2017-11-20
The only ppa I've added is for [Vivaldi]("https://vivaldi.com").
So, much less resources required than any other browser I've seen.

That was one of the first things I did.

---

