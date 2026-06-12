---
title: "[RANT] Why do we have to jump through hoops to update Virtualbox?"
date: 2023-02-15
forum: The Cafe
---

### Post by lsutiger on 2023-02-15
I see there is an update to VirtualBox 7.0, but the steps you have to go through just to update are tedious!
You have to uninstall 6.1 and the extension pack in order to update. Why can't we just have a clean update via apt update && apt upgrade?
Here is a tutorial on how to upgrade.
[https://kifarunix.com/upgrade-virtualbox-6-x-to-virtualbox-7-x-on-ubuntu-debian/](https://kifarunix.com/upgrade-virtualbox-6-x-to-virtualbox-7-x-on-ubuntu-debian/)
At the end it states "And that is how easy it is to upgrade VirtualBox 6.x to VirtualBox 7.x on Ubuntu/Debian."
LOL!

---

### Post by DuckHook on 2023-02-15
Thanks for the rant warning. Actually, as rants go, yours is pretty mild (and not without merit).

It's not really a help request, so I've moved it to the Cafe.

You've touched upon a topic that has vexed many people&#8212;both devs and users&#8212;since updates became a thing, which is pretty much since the dawn of computing: do we update with rolling releases or in discrete versions?

Ubuntu, for example, has chosen the version route: you get minor updates on a daily basis, but every six months, you have to make a conscious decision to upgrade to the next version. If you don't, you stay with the old version. This is done for purposes of stability and reliability. I'm still running Bionic on some old 32&#8209;bit HW. Perhaps Oracle has decided that major versions need to be treated in the same way. They've just gone one step further on the basis that if you do that major version upgrade, you've got to jump through this awkward hoop to ensure that you really mean it.

---

### Post by SeijiSensei on 2023-02-15
I just add the Oracle repository to my sources list as explained here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Then VB will update along with all the rest of the software when using apt.

These days I've switched from VirtualBox to the built-in virtual machine facility called KVM. I followed the steps here: [https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/). Since KVM resides in the Linux kernel, it updates when the kernel does.

---

### Post by QIII on 2023-02-15
Also bear in mind that the instructions you referenced appear to be for those who have done a one-time installation from Oracle rather than from the Ubuntu repos.

The repo can only have so much -- just the publicly available parts -- of Oracle products because Oracle is very jealous of its intellectual property.  Not only do you not get the nice details from Canonical's repo, you are also dealing with the fact that the repo may not have the latest releases because Ubuntu releases are "frozen" and new versions of software are not immediately available except for serious security updates.

If you do a one-off installation of VBox without adding the Oracle repo, you are left with uninstalling and re-installing.  As above, if you add their repo, you get their updates on their schedule -- generally.  There may be cases where you won't get an update because there is a dependency that does not exist in your Ubuntu release.

Your "rant" in this case may have provided the community with a bit of explanation about this.

By the way, I also use KVM.  It's native to the Linux kernel and it performs better without the "middle man".

---

### Post by DuckHook on 2023-02-15
Maybe I'm missing something here, but when I was still running VBox a few years ago, my experience was similar to lsutiger's: that is, even with Oracle's repo installed into my sources folder, I would get minor point upgrades automatically, but not major integer version upgrades. For those, I too had to do what lsutiger did—purge the old before installing the new.

Perhaps things have changed since then. I haven't used VBox for a couple of years now, so wouldn't know.

@lsutiger

I'm another proponent of switching from VBox to KVM: faster, cleaner, more reliable and native to Linux. In my not so humble opinion, a superior VM.

---

### Post by #&amp;thj^% on 2023-02-15
> **DuckHook said:**
> 
I'm another proponent of switching from VBox to KVM: faster, cleaner, more reliable and native to Linux. In my not so humble opinion, a superior VM.

Count me as 2.....the only way to VM :P

---

### Post by MAFoElffen on 2023-02-16
No comment on Oracle VirtualBox and the Repo Version, except...

I quit using VirtualBox about 8 years ago, unless I had to tutor someone else in using it, or help someone sort their VBox problems out. 

I've been using KVM (Like QIII, DuckHook, and 1fallen) for about 12 years. Fulfills all my needs.

---

### Post by SeijiSensei on 2023-02-16
> **QIII said:**
> Also bear in mind that the instructions you referenced appear to be for those who have done a one-time installation from Oracle rather than from the Ubuntu repos.

I've never needed to do that. You do have to remove any existing VB installation with "sudo apt remove virtualbox", though as I recall the installation script actually takes care of this for you.

The packaged versions from Oracle have names like "virtualbox-6.1" rather than simply "virtualbox," which the official Ubuntu repository uses, to avoid naming conflicts.

---

### Post by ajgreeny on 2023-02-16
Yes, KVM all the way as it is much faster, smoother and just overall better than VBox.

However, to answer your rant, VBox 6 will update automatically from the VBox repos mentioned above by DuckHook but only to the next VBox 6 version.
To move to VBox 7 you have to uninstallm 6 and install 7 from Oracle; unfortunately as things stand, at present VBox 7 is not available direct from the apt repos of Oracle so even when a new point version of 7 arrives you have to download and install using apt or dpkg, though you do not need to uninstall the current version 7 if it's already installed,

I imagine the VBox 7 versions will they will come eventually to their apt repos as happened when it moved from version 5 to 6.

---

### Post by Skaperen on 2023-02-20
does this mean we can have two different major versions of VB installed concurrently?

---

### Post by DuckHook on 2023-02-21
> **Skaperen said:**
> does this mean we can have two different major versions of VB installed concurrently?
I believe that I did that a few years ago when I still used VBox, but the old memory is failing so can't by sure.

I don't see why not. However, you must be aware that you can't *use* them concurrently; just have them installed side&#8209;by&#8209;side. Beware of the potential for breakage though: if one uses an incompatible library to the other, then you could run into dependency hell. So is it really worth the hassle?

---

### Post by ajgreeny on 2023-02-21
> **Skaperen said:**
> does this mean we can have two different major versions of VB installed concurrently?
No, you can not have both virtualbox-7.# and virtualbox-6.# direct from the repos together, in spite of what DuckHook says.

If you try to install version 7 you will quickly see that the version 6 is immediately removed in the installation activity, presumably to avoid conflicts between the files in the installations.
In my limited experience VBox 7 is working very well now though it was a bit flaky when it first appeared; now at 7.0.6 all appears good again.

Mostly I now use KVM, as I said in post #9 but I do like to have VBox available as well just to check how it's now doing in comparison, and of course, I never have a VM running in the two systems at the same time.

In spite of all these comments KVM is still my choice as the better system of the two, those two being the only ones I have used.

---

### Post by DuckHook on 2023-02-21
Thanks for the correction, ajgreeny.

This is true of the VBox from the repos. But I wonder if I can install VBox 6 in one container, then VBox 7 in another, and have them reside side&#8209;by&#8209;side? It would take a lot more than curiosity to get me to install VBox again, so I guess I will never really know.

---

### Post by ajgreeny on 2023-02-21
No, I've got no idea either.
I don't really **use** VBox other than simply running it, trying it out, as i find KVM  is so very much better.

The only situation in which VBox seems a bit simpler than KVM is the setting up of shared folders from host to guest but it is not too much bother in either.

---

### Post by TheFu on 2023-02-21
> **MAFoElffen said:**
>  I've been using KVM (Like QIII, DuckHook, and 1fallen) for about 12 years. Fulfills all my needs.

KVM/QEMU here too.  Was using virtualbox on Windows hosts and Xen on Ubuntu before the switch.  Also had a VMware ESXi and VMware Workstation setup. (VMware makes 6+ hypervisors, so always be specific).  KVM + libvirt is just as easy to use as virtualbox, but so much more capable, stable and faster for server-on-[desktop/server] virtualization.  There's only 1 trick to using it which seems to get non-techical people grief.  Setup a network bridge in the network settings, on the host system, completely unrelated to the virtualization before tying to do anything with creating any KVM VM.  Some people just can't get that working, though it isn't really very difficult - perhaps a 3 on a scale of 10.  By default, libvirt provides a NAT subnet for VMs, which means double-NAT or triple-NAT will be involved for most people.

With virtualbox, there is the hypervisor updates and the guest addition updates.  Those are paired and need to match.  That creates some added complexity.  With KVM, the can be client-side libraries, but those get updated automatically and don't seem to be as sensitive to version differences as virtualbox is.

Plus, libvirt makes using enterprise storage pools really easy, assuming you setup that sort of system. It isn't required, but it is really nice to have the capability.

---

### Post by bernard010 on 2023-03-18
I have had quite a struggle with Virtual Box over the last few years.
Either a new Kernel change, or a new version of Firefox.
Then nothing in Virtual Box works at all.
I start writing Bug reports to Bugzilla or Bugzilla Mozilla,
then posting the problem on Virtual Box Forum.
Surprisingly in a few days or a week update saves the day.
I only use the Oracle version from their site, it has its own
check for updates in the virtual box manager help tab.
The only reason I use their version, 
otherwise the package version is identical without that option.
I still use virtual box. :)

---

### Post by zebra2 on 2023-03-19
Because if there was no VirtualBox there would be a world wide glut of unused hoops.

---

