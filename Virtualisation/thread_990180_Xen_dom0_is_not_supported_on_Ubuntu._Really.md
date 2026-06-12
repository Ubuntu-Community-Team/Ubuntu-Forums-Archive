---
title: "Xen dom0 is not supported on Ubuntu. Really?"
date: 2008-11-22
forum: Virtualisation
---

### Post by pmorch on 2008-11-22
It looks like Xen dom0 isn't supported in the newest Ubuntu Interpid release. And that it apparently is a policy decision. I can't believe that is true. So for now, I've been forced to go back and use Debian again. Yes, I know I can use KVM, VirtualBox or whatever, but please, let **me** decide whether to use Xen or not. And I'd *much* prefer to use Ubuntu...

Is there somewhere an official Ubuntu statement about the decision not to support Xen at all?

The "Community Ubuntu Documentation" (wiki) didn't mention that, so I've changed it:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

Please, if you've been able to run Xen with standard Ubuntu packages, please let us all know. Because these resources all seem to indicate it isn't possible:

CNET's "Ubuntu picks KVM over Xen for virtualization"
[http://news.cnet.com/8301-13580_3-9867657-39.html](http://news.cnet.com/8301-13580_3-9867657-39.html)
does say that this is an official Ubuntu position, but not that Xen wouldn't be supported at all...

[http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization) says:
Running a Xen host (Dom0) on Ubuntu still requires a community maintained kernel in universe. (In the following requests about where to find that kernel have gone unanswered)

"The Virtualization Mega-Thread"
[http://ubuntuforums.org/showthread.php?t=973756&highlight=xen](http://ubuntuforums.org/showthread.php?t=973756&highlight=xen)
Closed, sticky thread under Virualization on Ubuntu forums says:
It appears Xen will no longer be maintained server side (Dom0 / Host) in Ubuntu. Client side (DomU / Guest) is supported.

"Xen dom0 support"
Thread mentioning asking what kernel to use. No good responses.
[http://ubuntuforums.org/showthread.php?t=963625&highlight=xen](http://ubuntuforums.org/showthread.php?t=963625&highlight=xen)
One comment says:
"it's a pity that cannonical don't support xen dom0 in ubuntu 8.10"

Xen with Ubuntu intrepid
[http://ubuntuforums.org/showthread.php?t=947391&highlight=xen](http://ubuntuforums.org/showthread.php?t=947391&highlight=xen)
has this comment:
"My understanding is that there are no plans to support Xen Dom0's in
Intrepid."

Also, "installing Xen and setup"
[http://ubuntuforums.org/showthread.php?t=941649&highlight=xen](http://ubuntuforums.org/showthread.php?t=941649&highlight=xen)

---

### Post by bodhi.zazen on 2008-11-22
The "community' wiki pages are not "official" ubuntu documentation, they are community maintained.

With that said, it seems Xen is not maintained on Intrepid.

I suggest you post on Launchpad.

It appears Openvz and Xen are maintained on LTS (8.04) and not intrepid (8.10). This in a way makes sense.

---

### Post by pmorch on 2008-11-22
You are quite right. My bad. I've edited the original post to say "Community Ubuntu Documention".

Xen maintained in Hardy but not in Intrepid does not really make sense to me. 

If Xen isn't supported intrepid, then why is the ubuntu-xen-server package available?

> **bodhi.zazen said:**
> ...**it seems** Xen is not maintained on Intrepid.

I suggest you post on Launchpad.

**It appears** Openvz and Xen are maintained on LTS (8.04) and not intrepid (8.10). This in a way makes sense.
(bold emphasis mine)

Thanks, bodhi.zazen, for your efforts in this forum. It helps!

I created a bug report in launchpad as you suggested.
[https://bugs.launchpad.net/ubuntu/+bug/301102](https://bugs.launchpad.net/ubuntu/+bug/301102)

But I'm still a little puzzled by the fact that you, an Ubuntu employee, the poster/maintainer of the only sticky thread in the virutalization forum, "The Virtualization Mega-Thread" also don't seem to have an official Ubuntu stand on whether Xen is maintained or not, but have to resort to soft phrases like "it seems" and "it appears". Or is this something that happens by accident without conscious decision by anybody?

And is it an official Ubuntu policy that certain packages are only maintained in LTS releases? Is there a list of packages for whom support is dropped / will be dropped in future stable releases?

Btw, from what I seem to be reading here and there, it is not a walk in the park to get Xen to work on Hardy either...

Peter

---

### Post by bodhi.zazen on 2008-11-22
LOL, I am not an employee of Ubuntu, I am a volunteer. 

Virtualization is complex and we are trying to keep the number of stickies to a minimum, thus a single mega thread rather the multiple stickies.

I have not head a definitive word from the developers either (I posted on Launchpad re OpenVZ).

Well, it makes sense in that (in theory) one wishes to use Xen / OpenVZ on a stable platform that will be maintained as long as  possible == LTS.

Xen has always been easier, to my knowledge, on Fedora. I am not all *that* familiar with Xen, but the project has undergone changes as well.

---

### Post by pmorch on 2008-11-22
Hi again,

> **bodhi.zazen said:**
> LOL, I am not an employee of Ubuntu, I am a volunteer. 


Ok, I just thought that because it says "Ubuntu Forum Staff" under your name, that you were an employee.

However, in the meantime, I have succeeded in getting xen working under intrepid by following this guide:

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

Especially it suggests getting a kernel from [http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/](http://www.il.is.s.u-tokyo.ac.jp/~hiranotaka/). Here is what I did:

```
wget http://www.il.is.s.u-tokyo.ac.jp/%7Ehiranotaka/linux-image-2.6.24-19-xen_2.6.24-19.33~zng1_i386.deb
dpkg -i linux-image-2.6.24-19-xen_2.6.24-19.33~zng1_i386.deb

```

Then, following the rest of that guide I got a xen dom0 and domU working. Network and everything. Only did 5 minutes of testing so far, though.

Peter

---

### Post by bodhi.zazen on 2008-11-22
OK, cool. I will update the mega sticky.

Thank you very much for the information.

---

### Post by Lampi on 2008-12-02
Hi Peter

> **pmorch said:**
> Here is what I did:

```
wget http://www.il.is.s.u-tokyo.ac.jp/%7Ehiranotaka/linux-image-2.6.24-19-xen_2.6.24-19.33~zng1_i386.deb
dpkg -i linux-image-2.6.24-19-xen_2.6.24-19.33~zng1_i386.deb

```

Then, following the rest of that guide I got a xen dom0 and domU working. Network and everything. Only did 5 minutes of testing so far
I'm having the same problem with Intrepid. It can be partly solved by using the mentioned kernel image, but it's always the same deal with workarounds like that: most stuff will work, some stuff won't. If it weren't for pci card handling (which xen provides pretty good by now) I would change to the new solution ubuntu provides (kvm). From what I read this one will be able to handle pci cards **in the near future**, is that correct? Cuz I need pci card handling in my VM to get the linux vdr up and running with those buggy hdtv drivers. I wouldn't dare to run those on my server just like that. So I need a VM with pci card handling, preferably with the kernel ubuntu-server already provides. Looks like I'm stuck with kvm and have to wait, or I change back to etch or hardy 8.04 using xen.

---

### Post by pmorch on 2008-12-03
> **Lampi said:**
> From what I read this one will be able to handle pci cards **in the near future**, is that correct?

Sorry, have no idea about that. BTW, where did you read this? Links are always helpful for the next guy...

When I discovered that xen won't run with the nvidia X drivers and also that VMware workstation won't run in a dom0 [I've pretty much given up on xen for now]("http://www.morch.com/2008/11/24/xen/").

---

### Post by pmorch on 2008-12-03
> **Lampi said:**
> But it's always the same deal with workarounds like that: most stuff will work, some stuff won't.

Do you say this because there is stuff you *know* doesn't work, or because this is your assumption. Could you let us know what works and what doesn't?

I don't see how a community maintained kernel necessarily has to be worse than an official Ubuntu one, although that often is the case, I grant you that!

Peter

---

### Post by Lampi on 2008-12-03
> **pmorch said:**
> Do you say this because there is stuff you *know* doesn't work, or because this is your assumption. Could you let us know what works and what doesn't?
powernowd for starters (would bump up with never ending complaints about beeing unable to step down the core voltages), onboard lan would get an ip, but dns resolving for a simple ping to google host wouldn't work. Plus tons of error messages during boot up I didn't get in detail... so that's where I stopped - don't see it working on Ibex without heavily customizing the kernel, since this xen kernel is clearly designed for hardy and so has patches and stuff for hardy.

> **pmorch said:**
> 
I don't see how a community maintained kernel necessarily has to be worse than an official Ubuntu one, although that often is the case, I grant you that!

As you've read in the howto: kernel's designed for hardy, so you will have to design one on your own. As far as I'm concerned I don't know how to do that. (Do you?)

Sorry about the missing links on kvm pci handling: this sounds promissing to me, since pci handling will work if you use [kvm version 79 or later]("http://www.linux-kvm.com/content/kvm-79-released-pci-device-assignment-pci-device-hot-plug") The releavnt patch to the kernel module can be found in the [linux kernel Mailing List]("http://lkml.org/lkml/2008/9/23/175")

I assume with release date of mid-september this patch couldn't have made it into Ibex on time, so the next step will be trying to rebuild the kernel module on your own, witch could be easier than rebuilding a whole xen kernel (so it that really suits all your needs). But I'm trying to figure this out since it is metioned n the article on kvm.com you will nedd a newer kernel anyway to get kvm working with pci handling (2.6.28 they say, we got 2.6.27 on ibex)

I just HATE it - don't know what to do by now since going back to Hardy was clearly not what I had in mind... at least not before they backport the non-working stuff from ibex to hardy (working power management, propper raid haddling, server installer scripts)

I'm up for suggestions though - generally I like Ubuntu, just don't see it working in a little more complex server environement

---

### Post by Xepra on 2008-12-17
If you guys want a bit more updated dom0 kernel:

[http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html](http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html)

I also posted a bit more in other threads.

If I get around to learning how to package a deb I might try.

-----------

Hiranotaka++ -- he released a xen kernel to solve the networking problem in the amd64 hardy xen kernel that worked perfectly for me.

---

### Post by Lampi on 2008-12-27
Thanks for letting us know Xepra - great Howto. I might try this one if in need.

as for me i went back to use etch(n'half) again on the server, ibex now runs on the client only

---

### Post by stevegt on 2009-05-04
Evan Broder has provided better information about Ubuntu Xen support -- it's not deprecated, it's basically just waiting for Xen to get into the mainstream kernel.  Meanwhile the Xen userland and hypervisor continue to be supported in Ubuntu, including Intrepid:

[http://bugs.launchpad.net/ubuntu/+source/xen-3.3/+bug/301102](http://bugs.launchpad.net/ubuntu/+source/xen-3.3/+bug/301102)

Workaround:  Use the Xen 3.3 hypervisor and userland that are already in Intrepid, and then use a dom0 kernel from, say, Debian:

[http://www.chrisk.de/blog/2008/12/how-to-run-xen-in-ubuntu-intrepid-without-compiling-a-kernel-by-yourself/](http://www.chrisk.de/blog/2008/12/how-to-run-xen-in-ubuntu-intrepid-without-compiling-a-kernel-by-yourself/)

I'll also update [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) to reflect this.

---

### Post by nebosphere on 2009-05-11
stevegt, do you have idea if this would allow for the install of Microsoft's Linux Integration Components?  They are technically only supporting configs with Xen under SUSE.... I have an Intrepid fileserver that I would love to be able to run efficiently (read: use the synthetic SCSI adapter) under Hyper-V.

---

### Post by bedge on 2010-05-04
No activity in over a year on this Xen support thread and the official docs all point to a HOWTO that starts with a rant:

[INDENT]...then noticed that Canonical has dropped Xen Dom0 support. Great! Why the heck did they drop Xen? Because KVM is cooler? Or because they didn’t want to blame themselves by releasing another totally buggy self-patched Dom0 kernel?  I mean they didn’t even manage to provide a working one later on so the community had to…and thats a LTS release? WTF?
[/INDENT]

Is there _any_ word from Canonical on this? 
"Waiting for mainstream kernel support" is a ridiculous statement. It might as well say "given up until someone else does it for us".
Why can't Canonical just port the upstream debian dom0 kernel? The work is already done, they need to bless & repackage it. What's wrong with the debian kernel?

Also, the howtos that state "just use the debian kernel" are all out of date as of 10.04 as it no longer installs because of a missing "linux-base" dependency so that's no longer even an option unless you want to dpkg -x it on top of /. 

With the current focus on virtualization, this is very bad policy. What are the ubuntu server guys thinking?

---

### Post by bodhi.zazen on 2010-05-04
Support for Xen is no longer available , even RHEL (which means Centos) is dropping support from Xen

[http://ostatic.com/blog/xen-cut-from-rhel-6](http://ostatic.com/blog/xen-cut-from-rhel-6)

For Xen support go here : [http://www.xen.org/](http://www.xen.org/)

---

