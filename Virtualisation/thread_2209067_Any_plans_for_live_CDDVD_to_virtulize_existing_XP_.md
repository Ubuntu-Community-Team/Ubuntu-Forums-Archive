---
title: "Any plans for live CD/DVD to virtulize existing XP installs to work under Ubuntu?"
date: 2014-03-03
forum: Virtualisation
---

### Post by JohnInMableton on 2014-03-03
Hi;

(3/5/14 Edit for clarity: This is in reference to converting a legally owned XP installation to run virtualized on the same PC hardware it is already installed on. Not to clone XP for redistribution.  Thanks Fu!)

Win XP is coming up on its end of life support soon. I know I can (and will be) virtualizing my XP installs to run under Ubuntu. There are millions of non-tech savvy XP users out there and they don't know what they are going to do. And even if they knew what to do, they wouldn't know how.

So;
A. Any best practices/methods I can use to convert my own XP, Vista (or sure I run it) and Win 7 to run under Ubuntu?

B. Anybody know if there are any plans to develop a live CD/DVD to virtualize an existing XP install and run it under Ubuntu?  

Seems like it could be a nice way to expand the user base of Ubuntu. If not a live edition to automate the process perhaps a link on the front page of Ubuntu.com to a detailed article on how to do it with links to techs willing to assist freely or for a fee.

Thanks for any thoughts or assistance in advance!
John

---

### Post by TheFu on 2014-03-03
Out of support does NOT mean out of copyright. Redistrubuting XP would violate that. A "liveCD" would definitely be illegal in most countries across the world.

As to virtualization techniques - each VM hypervisor has a different method to handle this.  All have script-able "build VM" tools and if you need to move a VM from 1 machine to another (only running 1 place), then there is an export VM and an import VM feature in many of these tools.  VirtualBox has both vboxmanage CLI and export/import GUI features. 

When XP goes out of support, I'll be deleting it.  Not safe to use on ANY network that isn't highly, highly, highly controlled and NEVER connected to the internet.  Sometimes connected is still too risky.  There will be a huge set of viruses released that target XP. They've been held back the last 6 months waiting for E-O-S to happen. It is going to be ugly. [http://www.thewindowsclub.com/secure-windows-xp-after-end-of-support-april-2014](http://www.thewindowsclub.com/secure-windows-xp-after-end-of-support-april-2014)

I haven't converted from physical to virtual in ... 5+ yrs, but back in the old days, there were p2v tools which helped for many conversions, but not all. I don't expect those to work with Vista or later MS-Windows which are tied to hardware. The VM will **never** look like any real hardware close enough to make the license-checking parts work. Only a fresh install will work, if that is even allowed.  Heck, I have a Win7-retail VM that I'd like to move from an old version of KVM to a newer release and if always rejects the VM-hardware. This isn't going to get any better, since 99% of new Microsoft licenses sold with a PC are tied to that specific hardware and cannot be moved.

OTOH, a fresh install of Windows into a VM can be moved to a different VM server easily provided the underlying hardware appears to be the same - that usually means same hostOS and same VM hypervisor for everything to be good.

---

### Post by Simon_WM on 2014-03-05
IMO it would be better to drop XP completely, and move to Windows 7 Enterprise or 8.1 Professional. As there is more support, and you will get the latest Patches and such.

---

### Post by JohnInMableton on 2014-03-05
Hi Fu;

Thanks for the information Fu!  I was not referring to distribution of MS products.  I was referring to taking an existing XP installation and virtualizing it to run under Ubuntu.  Same hardware, same PC.  My understanding is that should anything happen to the virtualized XP, it can be dumped and reloaded to a fresh instance. In that way, protecting the end user from anything they may 'catch' malware or just plain XP crashing as usual. Though I haven't had a bad crash since service pack 3 but I seldom push on the software and hardware.

My other thought was to keep the virtualized XP off the internet etc., only feeding it files of whatever type to work on and save the results back to storage and out again through Ubuntu. 

So my game plan roughly would be (current XP) to an ISO and then run one or the other virtualized under Ubuntu.  

This is what I referring to about a live CD, to automate the process for current XP owners, never moving then off their current hardware. For a lot of people, they neither need nor desire updated hardware or software. But they will need protection and can afford to take a speed hit since their processing requirements are pretty low to begin with.  

Thanks again for responding!

---

### Post by JohnInMableton on 2014-03-05
Hi Simon;

For those that can afford to upgrade hardware and software, I totally agree with you. However, if one can't afford it, then virtualization may be good workaround.  Especially as Microsoft is pushing people to get new hardware for 8.1.  (Physical Address Extension (PAE), NX processor bit (NX), and Streaming  SIMD Extensions 2 (SSE2) are features of the processor, and they're  needed to run Windows 8.1.) 

So right now, I am running Ubuntu, XP, Vista (poor thing) and Win 7 multibooting on my old PC. I can't run Win 8 since it requires an updated processor. I don't play games much, and the current system suits all my needs.  I understand MS and Intell would love me to uprade but why on earth should I? Its not like I'm trying to run a business on this hardware.

As relates to the larger XP community, there are a lot of them in the same boat.  Besides, once we get them on Ubuntu, they will find less and less reason to go back to MS.

---

### Post by TheFu on 2014-03-05
Being on "the same hardware" makes what you want legal, but not easier.  The virtual machine hardware will NOT match the physical machine, so 90+% of WinXP licenses will fail to install at all. The change in motherboard, chipsets, sata/ide drivers inside the virtual machine will make it fail before getting to the license check. 
[http://www.zdnet.com/blog/berlind/windows-activation-trips-up-virtual-machine-clones-even-on-same-system/517](http://www.zdnet.com/blog/berlind/windows-activation-trips-up-virtual-machine-clones-even-on-same-system/517)

This is a well-known problem.

Plus don't forget that WinXP didn't come with SATA or Intel PRO/1000 drivers - which make a huge, huge, huge difference in performance. Be certain to grab those drivers from Intel before they are all pulled from the web (if it isn't already too late).

I think your goal is harder.  Sure, you could create a script to create a VM  ready to receive a WinXP install, but ... the install would still be necessary.  Much easier to install something that looks mostly like WinXP - Lubuntu - and move forward, IMHO.  The main issue with using Lubuntu is that support for each release is NOT as long as for other *buntu releases. I don't think there is a 5yr LTS release of Lubuntu planned. Hope I'm wrong.

---

### Post by JKyleOKC on 2014-03-05
If (and only if) the OP has a legal MS-generated CD for WinXP, he could slipstream it using any of several utilities available to create a new CD (actually an .iso file) of it, then install that into the virtualization package of his choice. I used a utility called nlite to create my iso file, with unnecessary drivers trimmed out and necessary ones added in together with all service packs and updates; it installs into VirtualBox VMs and works perfectly for my needs. This lets me keep a backup copy of the entire VM and restore everything in case of disaster. It might be a technical violation of an EULA, but so long as all other installations made from that original CD have been erased, and only one from the new CD is in existence, I believe it to be within the limits of "one backup copy" permitted by law.

However this won't work without the original CD since that's the starting point, and factory-installed versions of Windows are almost always keyed to the specific hardware of the original system, in addition to lacking a few critical items needed in the installation process.

---

### Post by JohnInMableton on 2014-03-05
Aha! Thanks again Fu and Kyle! My naivete is showing quite a bit. And with that, I think I shall mark the thread solved.  Thank you both for the information!

---

