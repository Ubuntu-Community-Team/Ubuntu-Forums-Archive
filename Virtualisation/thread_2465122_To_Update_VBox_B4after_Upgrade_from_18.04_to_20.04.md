---
title: "To Update VBox B4/after Upgrade from 18.04 to 20.04 -or- Switch to KVM"
date: 2021-07-22
forum: Virtualisation
---

### Post by Rick St. George on 2021-07-22
Have UbuntuStudio v18.04 installed on SSD drive, with VirtualBox v6.0 installed.  See that an update is available.
But in Synaptic Pkg Mgr it doesn't show it installed, but does show several version including 6.1.
My VM is on another Hard Drive I connect ONLY when using VBox (have Kingswin Switcher). 

So, should I uninstall via Gdebi Pkg Installer? Then install fresh v6.1 - or - upon install will the install process see a current version and update it?

Want to do this before upgrading System from v18.04 to v20.04. OR, perhaps wait to FRESH install v20.04 before installing Virtual Box?!?!

Also see notes that QEMU-KVM is better than Vbox. Can I export my VM to be compatible with KVM? Or would I have to start all over building a new VM?
(see this post [https://ubuntuforums.org/showthread.php?t=2464211]("https://ubuntuforums.org/showthread.php?t=2464211")

I use charting software and would hate to start over, as I have tons of Data on Stocks, Futures, ETFs using MetaStock with all kinds  of extra Indicators etc. add ons. I need an easy but safe way to upgrade my system while keeping my existing VM safe and usable after an Upgrade to 20.04.

Any thoughts would be very appreciated!

OH ... FYI - SYSTEM INFO:

Mobo:
MSI 990FXA-GD65 v2R

CPU:
AMD FX-8320 Vishera 8 core ... with a Cooler Master GeminII S524 Version 2 CPU Air Cooler with 120 mm 
Silenx FP Fan, 2 more Fans - 1 Front, 1 Rear (70 CFM)

RAM:
2 x 8GB Corsair Vengence DDR3 1600 Mhz (PC3 12800)

GPU:
ASUS GT610 w/2GB DDR3 Ram (running 2 monitors)

PSU:
Enermax ENP450AST 450 Watt

SSD: Samsung 840 EVO 250GB SATA III

OS:
UbuntuStudio-64 v18.04 LTS


Thanks

---

### Post by ajgreeny on 2021-07-22
You can not run a Virtualbox vdi VM machine directly in KVM/QEMU but it is fairly simple to export any VBox VM to an ova file, convert the vmdk file within the ova file to qcow2 in order to import it into KVM; I did this for all my VMs including Windows 10 and Windows 7 when I moved from VBox to KVM a long time ago.

All details are shown in detail at [https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2](https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2)

It is a bit time consuming converting the ova file and very easy, but importing the qcow2 into KVM using virt-manager is quick and simple, and once done I can certainly confirm that KVM runs much better and faster in my experience than VBox.

---

### Post by monkeybrain20122 on 2021-07-22
> **Rick St. George said:**
> 
Want to do this before upgrading System from v18.04 to v20.04. OR, perhaps wait to FRESH install v20.04 before installing Virtual Box?!?!

Also see notes that QEMU-KVM is better than Vbox. Can I export my VM to be compatible with KVM? Or would I have to start all over building a new VM?
(see this post [https://ubuntuforums.org/showthread.php?t=2464211](https://ubuntuforums.org/showthread.php?t=2464211)



For first question I would update the OS first, besides, if you go the "upgrade" route (not recommended. a fresh install is much more problem free) you should remove all third party software and ppa anyway, including Oracle's for VB. 

Second question, yes, you have to convert the VB image to kvm image first.

e.g if you have a .vdi
```

qemu-img -f vdi -0 qcow2 /path/to/vdi /path/to/qcow2

```
/path/to/vdi is your input .vdi file and /path/to/qcow2 is where you want to place your converted image (.qcow2)

Then you just create a new vm from the output .qcow2 with say virt-manager. the qcow2 can be anywhere in your system, doesn't have to be in the default location /var/lib/libvirt/images. I have a old windows vda which I have converted and put the qcow2 in my home.

---

### Post by MAFoElffen on 2021-07-22
You mentioned in another thread that you had installed it much time ago straight from Oracle. That is why you don't see it as installed in Synaptic.I was going to mention there that the drawback to that (from Oracle) is that keeping it up to date is then on the user...

Note that in the other thread, he was having vbox / Video problems on an update... I did think that thread would have worked got more exposure here.

You have the hardware for KVM. Performance wise, I think you would be very happy with KVM.

I am not familiar with what application you are using for your charting... So it would depend on what it requires for video. You said it requires 3D acceleration right?

If you convert your VB VM to KVM, then use virtio driver of video, then select 3D acceleration... 

Well... You can have both installed until you get it working. Costs nothing to try to make it work.

---

### Post by monkeybrain20122 on 2021-07-22
> **MAFoElffen said:**
> 
If you convert your VB VM to KVM, then use virtio driver of video, then select 3D acceleration... 
.

I could be wrong but AFAIK there is no [working way]("https://wiki.archlinux.org/title/QEMU/Guest_graphics_acceleration") to enable 3d acceleration for Windows guests without GPU passthrough. Probably the most straight forward thing you can do without passthrough is [https://github.com/pal1000/mesa-dist-win/releases](https://github.com/pal1000/mesa-dist-win/releases). Download the archive in the Win guest and click the .run file to install then reboot. It will update the opengl version so you can run some programs which otherwise won't run, but that's about it, no performance boost to speak of.

As for Linux guest, I find virgl incredibly amazing, but stock qemu from Ubuntu's repository doesn't support it, so you have to either compile it yourself or install the [snap]("https://www.dedoimedo.com/computers/qemu-virgil.html"). There is also a ppa with virgl capable qemu for Ubuntu 18.04 and a very old version qemu. 
I managed to get it working with latest qemu 6 but I can't get it to work with virt-manager. Will post a more detailed thread when I sort my thoughts out.

---

### Post by Rick St. George on 2021-07-22
Thanks guys! AJ, I am assuming conversion can be made after install of "qemu-utils", as it is one of the dependencies for "qemu-kvm" to install?

If so, 

1. I will EXPORT to an .ova (on another HDD)

2. I'll wait until upgrade to 20.04 goes OK, 

3. then Install "qemu-kvm", run the conversion to import my Vbox VM into KVM.

Got it. Will report back and close thread.

---

### Post by monkeybrain20122 on 2021-07-22
> **Rick St. George said:**
> Thanks guys! AJ, I am assuming conversion can be made after install of "qemu-utils", as it is one of the dependencies for "qemu-kvm" to install?

If so, 

1. I will EXPORT to an .ova (on another HDD)

2. I'll wait until upgrade to 20.04 goes OK, 

3. then Install "qemu-kvm", run the conversion to import my Vbox VM into KVM.

Got it. Will report back and close thread.

You don't need to export to .ova first if you use my command.

---

### Post by MAFoElffen on 2021-07-22
I did not realize it was a Windows guest... And as I very rarely do Windows Guests in KVM... LOL

---

### Post by scorp123 on 2021-07-23
> **Rick St. George said:**
>  But in Synaptic Pkg Mgr it doesn't show it installed, but does show several version including 6.1. 

You perhaps installed it manually via downloading the software directly from Oracle?

There's one big difference between Ubuntu 18.04 and 20.04 when it comes to Virtualbox: Virtualbox 6.1.x is directly available from the Ubuntu 20.04 "multiverse" repositories. In 20.04 you don't need PPA's or any manual downloads for it.

Because of this I'd recommend this approach:

[LIST]
[*]remove your manual installation of Virtualbox...
[*]upgrade your Ubuntu 18.04 to 20.04
[*]reinstall Virtualbox from the Ubuntu 20.04 "multiverse" repositories, packages: "virtualbox" and "virtualbox-ext-pack"
[/LIST]


Output from my system:

```

> apt show virtualbox

Package: virtualbox
Version: 6.1.16-dfsg-6~ubuntu1.20.04.2
Priority: optional
[COLOR="#FF0000"]Section: multiverse/misc
Origin: Ubuntu[/COLOR]
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Virtualbox Team <team+debian-virtualbox@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 112 MB
Depends: adduser, iproute2, procps, virtualbox-dkms (>= 6.1.16-dfsg-6~ubuntu1.20.04.2) | virtualbox-source (>= 6.1.16-dfsg-6~ubuntu1.20.04.2) | virtualbox-modules, python3 (<< 3.9), python3 (>= 3.8~), python3.8, 
python3:any, libc6 (>= 2.29), libcurl3-gnutls (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.97), libgcc-s1 (>= 3.0), libgl1, libgsoap-2.8.91, liblzf1 (>= 1.5), libopus0 (>= 1.1), libpng16-16 (>= 1.6.2-1), 
libpython3.8 (>= 3.8.2), libsdl1.2debian (>= 1.2.11), libssl1.1 (>= 1.1.1), libstdc++6 (>= 5.2), libvncserver1 (>= 0.9.10), libvpx6 (>= 1.6.0), libx11-6, libxcursor1 (>> 1.1.2), libxml2 (>= 2.7.4), libxt6, zlib1g (>= 1:1.1.4)
Recommends: virtualbox-qt (= 6.1.16-dfsg-6~ubuntu1.20.04.2), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5opengl5 (>= 5.0.2), libqt5widgets5 (>= 5.0.2), libxcb1, libxext6
Suggests: vde2, virtualbox-guest-additions-iso
Conflicts: virtualbox-2.0, virtualbox-2.1, virtualbox-2.2, virtualbox-3.0, virtualbox-3.1, virtualbox-3.2, virtualbox-4.0, virtualbox-4.1, virtualbox-4.2, virtualbox-4.3, virtualbox-5.0, virtualbox-5.1, virtualbox-5.2, 
virtualbox-6.0, virtualbox-6.1
Homepage: https://www.virtualbox.org
Download-Size: 21.5 MB
APT-Manual-Installed: yes
APT-Sources: http://ch.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages
Description: x86 virtualization solution - base binaries
 VirtualBox is a free x86 virtualization solution allowing a wide range
 of x86 operating systems such as Windows, DOS, BSD or Linux to run on a
 Linux system.
 .
 This package provides the binaries for VirtualBox. Either the virtualbox-dkms
 or the virtualbox-source package is also required in order to compile the
 kernel modules needed for virtualbox. A graphical user interface for
 VirtualBox is provided by the package virtualbox-qt.

```

---

### Post by monkeybrain20122 on 2021-07-23
> **scorp123 said:**
> You perhaps installed it manually via downloading the software directly from Oracle?

There's one big difference between Ubuntu 18.04 and 20.04 when it comes to Virtualbox: Virtualbox 6.1.x is directly available from the Ubuntu 20.04 "multiverse" repositories. In 20.04 you don't need PPA's or any manual downloads for it.

Because of this I'd recommend this approach:

[LIST]
[*]remove your manual installation of Virtualbox... 
[*]upgrade your Ubuntu 18.04 to 20.04 
[*]reinstall Virtualbox from the Ubuntu 20.04 "multiverse" repositories, packages: "virtualbox" and "virtualbox-ext-pack" 
[/LIST]


Output from my system:

```

> apt show virtualbox

Package: virtualbox
Version: 6.1.16-dfsg-6~ubuntu1.20.04.2
Priority: optional
[COLOR=#FF0000]Section: multiverse/misc
Origin: Ubuntu[/COLOR]
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Virtualbox Team <team+debian-virtualbox@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 112 MB
Depends: adduser, iproute2, procps, virtualbox-dkms (>= 6.1.16-dfsg-6~ubuntu1.20.04.2) | virtualbox-source (>= 6.1.16-dfsg-6~ubuntu1.20.04.2) | virtualbox-modules, python3 (<< 3.9), python3 (>= 3.8~), python3.8, 
python3:any, libc6 (>= 2.29), libcurl3-gnutls (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.97), libgcc-s1 (>= 3.0), libgl1, libgsoap-2.8.91, liblzf1 (>= 1.5), libopus0 (>= 1.1), libpng16-16 (>= 1.6.2-1), 
libpython3.8 (>= 3.8.2), libsdl1.2debian (>= 1.2.11), libssl1.1 (>= 1.1.1), libstdc++6 (>= 5.2), libvncserver1 (>= 0.9.10), libvpx6 (>= 1.6.0), libx11-6, libxcursor1 (>> 1.1.2), libxml2 (>= 2.7.4), libxt6, zlib1g (>= 1:1.1.4)
Recommends: virtualbox-qt (= 6.1.16-dfsg-6~ubuntu1.20.04.2), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5opengl5 (>= 5.0.2), libqt5widgets5 (>= 5.0.2), libxcb1, libxext6
Suggests: vde2, virtualbox-guest-additions-iso
Conflicts: virtualbox-2.0, virtualbox-2.1, virtualbox-2.2, virtualbox-3.0, virtualbox-3.1, virtualbox-3.2, virtualbox-4.0, virtualbox-4.1, virtualbox-4.2, virtualbox-4.3, virtualbox-5.0, virtualbox-5.1, virtualbox-5.2, 
virtualbox-6.0, virtualbox-6.1
Homepage: https://www.virtualbox.org
Download-Size: 21.5 MB
APT-Manual-Installed: yes
APT-Sources: http://ch.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages
Description: x86 virtualization solution - base binaries
 VirtualBox is a free x86 virtualization solution allowing a wide range
 of x86 operating systems such as Windows, DOS, BSD or Linux to run on a
 Linux system.
 .
 This package provides the binaries for VirtualBox. Either the virtualbox-dkms
 or the virtualbox-source package is also required in order to compile the
 kernel modules needed for virtualbox. A graphical user interface for
 VirtualBox is provided by the package virtualbox-qt.

```


I think the version from the repo is a "community edition" which are missing some features, kind of like Chromium vs Chrome  (Debian would not maintain "proprietary" stuff). When you download from Oracle you can enable its repository instead of just installing the .deb,then it will be upgraded when a new version is available. See the part about [adding keys and repository]("https://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by scorp123 on 2021-07-23
> **monkeybrain20122 said:**
> I think the version from the repo is a "community edition" which are missing some features

**virtualbox-ext-pack** is there in the repositories as well. You install that and you get everything.

---

### Post by MAFoElffen on 2021-07-23
Backup. Everyone think. Please do not cause this person extra work...

I don't believe that the edition in the repo's is a community edition. Maybe from Oracle, upstream, but not as from Ubuntu. It is still upstream from Oracle. What he has is just older. It's just like other 3rd Party package editions of software versus the Editions of software in the new SnapCraft Store... On Ubuntu Repo editions of 3rd Party, it's repackage by an Ubuntu maintainer for a specific Ubuntu Release version, and if you are on that Ubuntu Version, say 20.04 LTS, then you are locked into that mated version of the application for the life of when you are on that release of Ubuntu... Even when the application vendor came out with a newer version There's pro's and cons to that... (not discussed here) But does receive upstream patches.

On installed versions of VB form Oracle, there's two scenario's... either it got installed as a stand-alone Deb package (which I think the OP mentioned in 1 of his two threads) and got installed manually. In that scenario, the application is standalone and receives no updates, nor patches...

Or the what we will call scenario 2, where you add the oracle repo... where it gets patches and upgrades...
[U]
The OP's primary goal is to upgrade to 20.04, with continued access with his VM. [/U]

He doesn't have to uninstall VB to upgrade releases. There is really not reason to do that. The only reason he had issues before with this was issues related to 3D acceleration, related to his host system's video driver, during an 18.04 video driver update...
RE: [https://ubuntuforums.org/showthread.php?t=2465112](https://ubuntuforums.org/showthread.php?t=2465112)

Now that that is resolved, that shouldn't prevent him from upgrading his release to 20.04... He should be able to now upgrade his release of Ubuntu and deal with VB when he does that. Since that VM is important to him, I would at least backup that VM, before doing that, at a minimum,,, He didn't receive any updates to VB, so I don't think he installed the Oracle repo...

If he had, then he would have to disable that repo, any other 3rd party repo's (such as Google Chrome's) and any PPA's before doiing the release upgrade.

Before he upgrades VB, before he does anything... He needs to uninstall VB guest additions... that is tied to the VB version. if he does do that first, he's going to l9se acces to that VM right? Then he can do whatever...

What I remember from VB OVAs between the Ubuntu repo versions and the Oracle versions is that you needed to pay attention to the application version numbers... you can go to the same or higher... easily. Backwards is, well... I don't think he's going to run into that.

Then you all can go back to discussiing personal preferences, right? LOL Just saying...

---

### Post by scorp123 on 2021-07-23
> **MAFoElffen said:**
>  He doesn't have to uninstall VB to upgrade releases. 

I did. And it worked pretty well. Advantage of getting your Virtualbox and the Extension pack from the Ubuntu 20.04 repositories: It also automagically works with all Kernel updates you receive, thanks to some automatic "dkms" magic happening in the background. In other words: No suddenly broken Virtualbox after a kernel update, no Extension pack mismatch after a Virtualbox update, and so on. It all gets updated by "apt" like the rest of the system. Since everything is coming from the Ubuntu maintainers it all "just works".

Removing Virtualbox should not delete your personal settings stored in **"~/.config/Virtualbox"** or your virtual machines stored in **"~/VirtualBox\ VMs"** ... so once the OS is upgraded to Ubuntu 20.04 and the **"virtualbox"** and **"virtualbox-ext-pack"** packages are installed again, this new Virtualbox installation should easily be able to find the configuration settings and load the stored VM's again.

At least that was the case for me.

---

### Post by MAFoElffen on 2021-07-23
Agreed with Scorp123 on changing to a repo version. Is less problems on both VB and on your NVidia card drivers from the Ubuntu repo versions. As he said, the biggest problems with both of those (not just VBox) is when Ubuntu does a Kernel Update. The VBox modules are compiled and added to Kernel. They need to work with that Kernel. Just as NVidia drivers and DKMS do, with kernel updates.

Both NVidia and Oracle, don't tie their versions to a specific Distro, and have no idea when a Distro is going to do a kernel update... So when Ubuntu does an Update, which usually on Kernel, then all of a sudden, users of manually installed versions have problems. That is one of the perc's of the Ubuntu Repo versions of both those. 

AND you just experienced a taste of that with your NVidia video driver. This is one "more" of the Pro's that I didn't discuss above.

---

### Post by ajgreeny on 2021-07-24
Just to offer the other side of this Oracle-repository vs Ubuntu-repository version of VirtualBox, in the time that I used VirtualBox it was always the Oracle version straight from their repos which were added to my software sources, so VBox was upgraded each time a new version appeared in exactly the same way as every other installed package.

I never had any difficulties when a new kernel version appeared in the upgrades though I did have to upgrade the Guest Additions when I opened the upgraded VBox-manager window for the first time, a dialogue box appearing with link to get the new Guest Additions and install them.  Everything worked seamlessly though I must add a caveat that I do not and have never used an nvidia graphic card which others seem to be saying can cause problems.

---

### Post by rsteinmetz70112 on 2021-07-24
My two cents. Unless you have identified a specific need for something you know you need that is not in the repro version always use the repro version.,It's easier to update and less likely to cause a problem.  If you have a problem you are more likely to find help here than anywhere else since so many users are using the same version on the same distro. In the past I've gone to software specific sources and after explaining my issue had the problem blamed on the distro not the packages in question.

---

### Post by monkeybrain20122 on 2021-07-24
When I used VB I always use Oracle's repo, I have never had any upgrade problem. As ajgreeny said after each update there is a popup with link to download the matching guest-additions. Yes I do have a Nvidia card (not sure what the relation is anyway)

But I suppose if you do distro upgrade you need to remove the repo first, I don't really know since I don't do distro upgrade which I find problematic for other reasons. I always backup my data and do a fresh install.

I stopped using VB in Ubuntu 20.04 and moved to kvm because it installs python-is-python2 as a dependency which sets the default python to python2 which makes no sense and can potentially mess up my other python applications. I think that happens regardless whether you install from Oracle's or Ubuntu's repo

---

### Post by MAFoElffen on 2021-07-24
Just FYI-

The NVidia issue is not just NVidia, but includes AMD video also... It is from the past. If you installed vendor binaries instead of the Ubuntu Repo's 3rd party drivers, then a kernel update would cause problems,.. because the install scripts built the modules off of what kernel it was installed with. Some of those problems aren't as common now, because of a lot of inclusions in Kernel now, which one is that dkms is part of a kernel update now. But it still happens on some Kernel updates.

I used to support high end graphics in the Linux Graphics Layer, so had lots of test machines with both Vendor's cards. I don't know how many times there would be a kernel update, and on a reboot, there would be no graphics at all. I would repeatedly have to boot as text only, and in command line, have to uninstall and reinstall the graphics drivers manually.Even when the drivers were the same version, just to recompile the kernel modules to the newer kernel version.No normal user should have to go through that, again and again. That's why I steer user's away from the Vendor binaries now. Much easier to use the packaged drivers from the Repo.

VirtualBox, it you just install only the deb file, instead adding their repo, then it doe's the same, compiles the binaries with the current Kernel for their "4" kernel modules... and on a Kernel update where certain features changed... well...

VBox 3d Acceleration uses DRM and DKMS from the Video Card's driver modules. So if there is a problem with those in an update, then VBox loses it in guest with 3D enabled. If you use the Ubuntu Repo 3rd Party video drivers, they get updated for kernels and have *less* problems with that... 

I personally stopped using VBox on 14.04... But I still had to support Computer Science college students until recently, who had to use that, because their equipment couldn't run Type 1 Hypervisors. For example, some of them could only afford ChromeBooks. What else were they going to run VM's on. LOL

That is the background on that.

---

### Post by monkeybrain20122 on 2021-07-24
> **MAFoElffen said:**
> Just FYI-

The NVidia issue is not just NVidia, but includes AMD video also... It is from the past. If you installed vendor binaries instead of the Ubuntu Repo's 3rd party drivers, then a kernel update would cause problems,.. because the install scripts built the modules off of what kernel it was installed with. Some of those problems aren't as common now, because of a lot of inclusions in Kernel now, which one is that dkms is part of a kernel update now. But it still happens on some Kernel updates.





Most people know about the headache of installing Nvidia driver with the .run file, but  Nvidia actually has a .deb repository for its drivers except it is not called that, it is the cuda repo and is accessed through the cuda download page instead of the graphic drivers download page. You can just install the driver without the cuda stuffs just with sudo apt install nvidia-xxx

The problem is the drivers included in that repo are missing 32 bit support (32 bit support removed from the drivers packaged in the cuda repo since cuda 10.0, though Nvidia still supports it if you install the drivers other ways) so if you use it for steam, for example you are out of luck. I use cuda but I prefer to install a local version myself and install the driver from the graphic driver ppa (you can install cuda in your $HOME with Nvidia's script without installing the driver) since cuda updates often break backward compatibility I would rather I control the version rather than let it be updated by Nvidia.

---

