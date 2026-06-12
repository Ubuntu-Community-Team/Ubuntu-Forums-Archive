---
title: "Recommended virtualization choice to run Windows apps?"
date: 2016-06-07
forum: Virtualisation
---

### Post by jub2 on 2016-06-07
I've got a single boot laptop running Xubuntu 16.04 64-bit. I'd like to run several Windows apps in a virtual machine. It's part of an experiment to see if I can switch my main machine over from Windows to Ubuntu and still run the Windows apps I need to run. I could dual boot, but that's such a hassle.

This is not part of any server operation. Just an individual who wants to be able to run Windows apps on a virtual machine. Looking for ease of use (from the perspective of someone coming from Windows) and robustness. I wish to run Windows 7 - is there any particular flavor of Windows 7 that works better than other flavors as a guest operating system? I'm guessing Home Premium would use less resources than Professional or Ultimate.

To help narrow down the options:
1. must be able to run Windows 7 as guest OS
2. free
3. ability to clone VM, so that once I've got it set up the way I want it, I can make a backup copy
4. ability to run multiple Windows virtual machines, though not simultaneously. I just want to have 2 or 3 Windows virtual machines, each with a different package of apps running on it. 

Which virtualization option would you suggest?

---

### Post by DuckHook on 2016-06-08
The big three "free" VMs out there are:

[LIST=1]
[*]VirtualBox (owned by Oracle)
[*]Xen (open source - community developed)
[*]KVM (open source - community developed)
[/LIST]
All of them can do what you require.

VBox is partially open source but to be really useful (USB support, integrated mouse/keyboard) you must install proprietary package called Extension Pack which is "free" as in beer, but non-free as in speech. However, it is considered the easiest one to use.

Xen is obscure and arcane, but very powerful. It was the first to permit VGA passthrough which will allow a guest GPU to operate at near-bare metal speeds. This is important for gamers, graphics artists, computer assisted drafting, etc. Because it is copy-lefted, it can be (and indeed is) part of the standard Ubuntu kernel. However, it is the most difficult to use.

KVM is somewhere in between. I've heard that it now permits VGA passthrough, though not as efficiently as Xen. However, it is more user-friendly because it is not as obscure or arcane. Also a copy-left project, so also already a part of the standard Ubuntu kernel. Ease of use is somewhere between Vbox and Xen.

It is not possible to suggest which one you should use. Only you know your use-case (eg must have VGA passthrough? Then Vbox won't do. Ease of use trumps everything else, then consider VBox), but the above info should help.

There are other VMs. [Here]("https://help.ubuntu.com/community/Virtualisation") is the Ubuntu community Wiki page listing and linking to them.

Please note, that your plan to run separate Windows guests may put you offside of MS licensing provisions. It may even be against their licensing provisions for you to run Windows in a VM. You will have to read your license for the details yourself. I haven't used Windows in years so my comments are just an alert.

---

### Post by T.J. on 2016-06-08
While Duckhook's points are all perfectly valid ones, I support KVM over VirtualBox because VirtualBox's guest drivers are less than stellar and can have unforeseen side effects if you try to do anything that requires any form of video or GPU acceleration. I also prefer KVM over Xen, because KVM is kept in sync with the Linux kernel, which means you probably won't need extra patches, and it will generally work out of the box without extra software. A big plus is that most distributions, like Ubuntu come with Virt-Manager included in the repository.  It is a reasonably working GUI for KVM to get you started.

It should also be said that "VGA passthrough" (regardless of the VM you chose) requires mainboard support for IOMMU and a second GPU.

As far as I know,  Microsoft allows for Windows to be virtualized as long as you have a separate license for each virtual machine, and the licenses are not OEM/System Builder licenses. Chances are you cannot use the license that came with your PC, as almost all of them are an  OEM/System Builder license.  OEM/System Builder licenses are one time  licenses tied to the original hardware motherboard and cannot be reinstalled or reused for any other purpose, including virtualization.  You are not even allowed to use an OEM license on your own DIY PC.  They are specifically for resale to third parties, where you are the business selling the computer and OS as a package.

[FONT=Verdana]**Q.** [COLOR=#00309C]_Can I use OEM system builder software that I purchase and install myself?_[/COLOR][/FONT]
[FONT=Verdana][COLOR=#333333]**A.** If you are building a PC for your personal use or installing an additional operating system in a virtual machine, you will need to purchase Windows 8 software or a Microsoft retail version of Windows 8.1 software. Windows 8.1 system builder software does not permit personal use, and is intended only for preinstallation on customer systems that will be sold to end users.[/COLOR]
([https://www.microsoft.com/OEM/en/Pages/support-faq.aspx](https://www.microsoft.com/OEM/en/Pages/support-faq.aspx))

[/FONT]So in order to virtualize Windows legally, you will need a corporate license (Enterprise/VAR), a developer's license (MSDN) or pay at about $100-150 USD per copy for Retail use license.  My advice to you is that if you discover that you are using an OEM copy, you are better off sticking with dual-booting. Microsoft uses telemetry for license enforcement.  (I can't find the official Microsoft page to prove it to you, but I know it existed, and from experience that even Windows 7 contacts Microsoft on a regular basis to verify your license when possible.)

Being a programmer and not wanting to pay about $1500 USD per year for an MSDN, I went with two Retail copies.  You might be able to get one cheap from Ebay, but don't accept ones that do not sell the original disc, or do not specifically have a Retail key, as they are probably selling keys by violating the EULA (which in some jurisdictions is probably illegal).

---

### Post by jub2 on 2016-06-08
Thanks for all the info. I might start with VirtualBox for ease of use and if I find I need better performance, I'll invest the time to learn to use KVM. I'm not doing anything graphics intense, so keeping it simple might work out fine.

On the point of Windows licensing, Microsoft does offer Windows for free for certain virtualization platforms: [https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/windows/](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/windows/)

---

### Post by T.J. on 2016-06-08
True, but developer licenses have restricted use, that is software development or testing only.  No personal use of any kind is permitted, games, email, etc.  I know this because I used to be on MSDN.  Microsoft is specific about it, even if they do not say so outright on the download page.

---

### Post by DuckHook on 2016-06-08
> **jub2 said:**
> ...Microsoft does offer Windows for free for certain virtualization platforms: [https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/windows/](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/windows/)Interesting offer. They are testing-images that expire after 90 days, but even MS encourages you to roll back to a snapshot, essentially giving you unlimited usage. There may be other restrictions like running only IE or Edge, but I wouldn't know because I have no desire to test them out. Altogether, it seems quite constraining to me, but this might be all that you want or need.

At any rate, I think that your choice of VM will work for your circumstances. There are two ways to install VBox: through the Ubuntu repositories or via Oracle's VBox PPA, instructions [here]("https://www.virtualbox.org/wiki/Linux_Downloads"). If you are starting out and want to keep things simple, I recommend the Ubuntu repositories. The PPA will install the latest version and then keep it updated, but this is actually sometimes a pain because it requires you to keep updating the extension pack as well, which then necessitates updating the vbox additions in each of your VMs. The version from the repositories is relatively current and has been vetted by Ubuntu, so it is stable and safe.

---

### Post by SeijiSensei on 2016-06-08
I prefer to install from the Oracle repository myself.  See [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) for details.  Updating the Extension Pack might be a pain if you have lots of VMs, but for just one VM, it's not that much effort.

I run Win7 in a VirtualBox for things like Microsoft Access and tax-preparation software.  There isn't much else I need Windows for except gaming.  For that, I have a dual-boot installation as well.  I recommend giving a Windows VM at least 2 GB of memory for decent performance.  You should also check if your BIOS has a switch for VT-x virtualization, which you'll need to enable for 64-bit guests.

---

### Post by kurt18947 on 2016-06-08
Another option though I've done very little with it:  GNOME boxes. It's really a front end for various open source VMs. I believe my default is QEMU. I haven't tried Windows as a guest, I have installed MX15. It was REALLY easy though it doesn't use quite the whole screen.  Here's a blurb from FedoraProject.org:
[INDENT][URL="https://wiki.gnome.org/Apps/Boxes"]
GNOME Boxes[/URL] is a  front-end management interface to the libvirt/QEMU/KVM stack.  It is  intended to replace virt-manager for end users who desire a simpler  interface which doesn't bother to present features unlikely to be used  or desired by this class of end user.  GNOME Boxes relies on libvirt  which has the ability to manage a variety of hypervisors (though  Virtualbox isn't one of them), but my understanding is that GNOME Boxes,  at this stage in its development, [solely employs KVM for its hypervisor]("https://help.gnome.org/users/gnome-boxes/stable/supported-protocols.html.en").
[/INDENT]

I also have Virtualbox running and once the add-ons are installed (extensions & guest additions for the appropriate guests) it works well too. After some clicking VirtualBox will fill the screen of an Intel powered Thinkpad. I haven't spent time with Boxes because I'm not losing much screen real estate to worry about it. I'm not certain Boxes is available with Xubuntu but it should be simple enough to check the repositories. I'm running it on Ubuntu-Gnome 16.04 64 bit.

[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by jub2 on 2016-06-08
> **DuckHook said:**
> At any rate, I think that your choice of VM will work for your circumstances. There are two ways to install VBox: through the Ubuntu repositories or via Oracle's VBox PPA, instructions [here]("https://www.virtualbox.org/wiki/Linux_Downloads"). If you are starting out and want to keep things simple, I recommend the Ubuntu repositories. The PPA will install the latest version and then keep it updated, but this is actually sometimes a pain because it requires you to keep updating the extension pack as well, which then necessitates updating the vbox additions in each of your VMs. The version from the repositories is relatively current and has been vetted by Ubuntu, so it is stable and safe.I went ahead and installed using the instructions on the VirtualBox Linux downloads page; was relatively easy, even for me.

> **SeijiSensei said:**
> I prefer to install from the Oracle repository myself.  See [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) for details.  Updating the Extension Pack might be a pain if you have lots of VMs, but for just one VM, it's not that much effort.

I run Win7 in a VirtualBox for things like Microsoft Access and tax-preparation software.  There isn't much else I need Windows for except gaming.  For that, I have a dual-boot installation as well.  I recommend giving a Windows VM at least 2 GB of memory for decent performance.  You should also check if your BIOS has a switch for VT-x virtualization, which you'll need to enable for 64-bit guests.There were a couple of virtualization options in the BIOS and I enabled them. 

> **kurt18947 said:**
> Another option though I've done very little with it:  GNOME boxes. It's really a front end for various open source VMs. I believe my default is QEMU. I haven't tried Windows as a guest, I have installed MX15. It was REALLY easy though it doesn't use quite the whole screen.  Here's a blurb from FedoraProject.org:[INDENT][URL="https://wiki.gnome.org/Apps/Boxes"]
GNOME Boxes[/URL] is a  front-end management interface to the libvirt/QEMU/KVM stack.  It is  intended to replace virt-manager for end users who desire a simpler  interface which doesn't bother to present features unlikely to be used  or desired by this class of end user.  GNOME Boxes relies on libvirt  which has the ability to manage a variety of hypervisors (though  Virtualbox isn't one of them), but my understanding is that GNOME Boxes,  at this stage in its development, [solely employs KVM for its hypervisor]("https://help.gnome.org/users/gnome-boxes/stable/supported-protocols.html.en").
[/INDENT]

I also have Virtualbox running and once the add-ons are installed (extensions & guest additions for the appropriate guests) it works well too. After some clicking VirtualBox will fill the screen of an Intel powered Thinkpad. I haven't spent time with Boxes because I'm not losing much screen real estate to worry about it. I'm not certain Boxes is available with Xubuntu but it should be simple enough to check the repositories. I'm running it on Ubuntu-Gnome 16.04 64 bit.
Thanks for the info on GNOME Boxes. Seems like an even easier way to get into KVM should the need arise.

---

### Post by jub2 on 2016-06-08
So now that I've got Windows 7 up and running in a VirtualBox virtual machine on a Ubuntu (Xubuntu) host, do I really need firewall and an antivirus? While the virtual machine will need to connect to the internet for certain data services, I won't be browsing the web from the vm. The host has a firewall as does my router, and I'll make backups of the vm, so if it does get infected, I'll just replace the infected vm with a backup vm.

Though I suppose that leaves open the question of how I'd even know it was infected if the symptoms weren't obvious. I guess I'm thinking risk of infection is rather low in this situation.

Trying to avoid the additional overhead of a firewall and antivirus on the vm . . . but if that's really stupid even for this setup/usage, then I'll use both.

---

### Post by QIII on 2016-06-08
Best practice is that you should treat that VM exactly like a real machine.  Don't develop bad habits.  Your host may not be compromised, but the guest certainly could be.

---

### Post by DuckHook on 2016-06-08
When it comes to Windows, I would not even breathe without a firewall and antivirus. It's very likely my paranoia talking, but Windows is such a malware gravity pit that it needs every protection it can get, every moment of every hour of every day. Not surfing on it will go a long way, but there are so many APIs, RPCs, DLLs, OCXs, COMs, and an alphabet soup of unbound, full-of-holes, opaque "stuff" built into the guts of Windows that one simply cannot take anything for granted.

---

### Post by DuckHook on 2016-06-08
> **QIII said:**
> Best practice is that you should treat that VM exactly like a real machine.  Don't develop bad habits.  Your host may not be compromised, but the guest certainly could be.+1

Additionally, the host *can* be compromised, sometimes in ways that we don't even understand, so that it never occurs to us to take measures to guard against. For example, lots of people will give their VMs access to a network file server, or a printer connected to the host, or a set of USB ports, or make use of the convenient "Public" folder that can be used to pass files back and forth from guest to host, etc. Many of these "features" create security holes that can theoretically be exploited by crackers, though they would admittedly have to be quite knowledgeable and very dedicated to cracking you. Now I *am* being paranoid.

---

### Post by T.J. on 2016-06-10
> **DuckHook said:**
> When it comes to Windows, I would not even breathe without a firewall and antivirus. It's very likely my paranoia talking, but Windows is such a malware gravity pit that it needs every protection it can get, every moment of every hour of every day. Not surfing on it will go a long way, but there are so many APIs, RPCs, DLLs, OCXs, COMs, and an alphabet soup of unbound, full-of-holes, opaque "stuff" built into the guts of Windows that one simply cannot take anything for granted.

7/10ths of those problems can be solved by simply not using Microsoft browsers or Office crapware. =)

As far as a VM is concerned, in my opinion, you are better off taking a snapshot after installing the OS, and then restoring it on a regular basis. Running antivirus will just add more overhead to the process that your host OS has to manage, and wastes energy.

It's just a personal view, but a firewall is a device that acts as a bridge between two networks and that is where they are most effective.  Anything else named a "firewall" is usually a waste of time.  Software "firewalls" have their uses on servers for packet management and unwanted connections, but on desktop operating systems like Windows, they are basically a very bad joke.  Windows "firewalls" can cause more crashes and errors than most viruses.  Not to mention that fact that most home Internet users are effectively firewalled by their ISPs, whose connections are significantly "one-way" only.  Incoming connections that did not originate from a request you make are usually blocked unless you have a business class connection.

Windows "anti-virus"/"anti-malware" are a waste of processors and battery life/AC.  

In my experience, a high priced Windows anti-whatever has about a 50% chance to remove something, IF it even catches it all. Out of the times your anti-software does catch something, the "cleaning" process will often damage software or the OS so that you end up reinstalling anyway.  You are better off just restoring from a clean backup.  Instead of wasting hours scanning and cleaning, a restore only takes 30 minutes.  I consider "anti-programs" the 21st Century equivalent of "snake oil." They give you a false sense of security that doesn't exist while costing you money and time. 

When someone says "virus" I respond with "wipe it" after collecting necessary data. A complete wipe and restore from an image guarantees a clean system.  That is something an anti-virus can't do. Anything else is a waste of labor, and drives up service costs. 

Even Symantec, the company that basically invented anti-virus admits that that anti-virus approach is useless in today's world.  You can't prevent attacks 100% of the time.  The approaches that are advocated now are methods of expedient recovery and minimizing the damage.  Microsoft recognizes this to some degree, Windows 10 has the option to restore the system files.

Leave the anti-virus/anti-malware as tools for the IT departments and techies to use as part of disaster recovery.  They are usually the only ones who can understand false positives or do a decent cleanup, anyway.

---

### Post by squirrel3 on 2016-06-11
I have used VMware Pro in Ubuntu before. VirtualBox is a good platform. VMware offers a free virtual machine player for personal use, of which I tried also. I found that both platforms can run certain programs better than the other.

---

### Post by kurt18947 on 2016-06-14
I've been playing around with VM software just for grins. I've been playing with a 3rd option recently - Gnome Boxes, a front end for QEMU (by default). I haven't tried Windows as a guest yet - other linux distros but itseems *really*  easy to use. I'm certain it's not as capable or customizable as VMware or Virtualbox but for hobby use it seems fairly functional. In addition to gnome-shell I have it running in Xubuntu 16.04 and what little use I've given it seems functional for desktop use.

---

### Post by jub2 on 2016-06-14
As a followup, I went with VirtualBox and it's been working great so far. Very easy to set up and lots of useful features once the Windows Guest Additions were installed.

Appreciate the antivirus and firewall discussion. I haven't bothered setting either up yet. Once I've got the vm set up with all the apps I want, I'll see how responsive it is, then take a snapshot, turn on Windows built-in firewall and antivirus, and see how responsive it is. If it bogs down the vm too much, I'm going to try to live without it. As I mentioned, there will be no web surfing from the vm, and I have the benefit of both my ISP's firewall and my router's firewall.

And maybe I'll use a bootable usb with an antivirus app to periodically scan the vm.

---

