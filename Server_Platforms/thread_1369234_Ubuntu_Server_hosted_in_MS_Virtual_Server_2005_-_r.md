---
title: "Ubuntu Server hosted in MS Virtual Server 2005 - random lockups..."
date: 2009-12-31
forum: Server Platforms
---

### Post by lord_farfig on 2009-12-31
Hi all,

I've been having an odd problem with an instance of Ubuntu Server 8.04 LTS running in a virtual machine under MS Virtual Server 2005.

There were a bunch of hoops to jump through just to get Ubuntu to install into VS2005.  It's been running for a few weeks now, and now (almost every other day) I have to go into the VS2005 console and "hard" reboot the Ubuntu Server.  It just stops responding. :confused:

I did notice one time the screen had an error on it "CPU#0 SOFT LOCK" or something along those lines.

It is being tested for use with Nagios for monitoring our other Windows servers, and I cannot figure out the cause of these lock-ups.  I for one would rather ditch the Windows host and VS2005 and just run Ubuntu Server on that physical machine and have Nagios do it's thing that way to see if it's Nagios related.

I was just curious to know if anyone else has run into an issue such as this, since I was unable to find one searching...

After the reboot the system is great... so I don't know if maybe it's a VS2005 configuration issue or an Ubuntu not playing nice with VS2005 and Nagios eating up the RAM.


I can provide more details if needed, I just want to get to the bottom of this issue.


Thanks!

---

### Post by Vegan on 2009-12-31
I am surprised you were able to get Ubuntu to run in Virtual Server.

I have heard a lot of attempts have had all manor of problems. Try using bare metal and see if that helps.

---

### Post by Cheesemill on 2009-12-31
As far as I know Virtual Server doesn't support any type of Linux as a guest OS.
You would be much better off using either VMware Server or VirtualBox as your VM solution.

---

### Post by sylvester_0 on 2010-01-01
Just a shot in the dark, but is there any way you can enable/disable ACPI on the VM? I was receiving that error on a machine with Hardy and it turned out that the chipset was too new to be fully supported by the Hardy kernel. I had to boot with the noacpi kernel option (you could try this too) but this introduced its own clock problems with KVM.

---

### Post by lord_farfig on 2010-01-05
> **Vegan said:**
> I am surprised you were able to get Ubuntu to run in Virtual Server.

I have heard a lot of attempts have had all manor of problems. Try using bare metal and see if that helps.

I was too.  I came across a different forum with someone who wanted to virtualize Ubuntu, and they posted their solution which worked for me.  However, it included a lot of hoops to jump through, but in the end it did work.

> **Cheesemill said:**
> As far as I know Virtual Server doesn't support any type of Linux as a guest OS.
You would be much better off using either VMware Server or VirtualBox as your VM solution.

VS2005 doesn't officially support Ubuntu, but there are a handful of other *nix distro's that are supported.  And with the help of the previously mentioned forum, I was able to get Ubuntu to install into a Virtual Environment.

> **sylvester_0 said:**
> Just a shot in the dark, but is there any way you can enable/disable ACPI on the VM? I was receiving that error on a machine with Hardy and it turned out that the chipset was too new to be fully supported by the Hardy kernel. I had to boot with the noacpi kernel option (you could try this too) but this introduced its own clock problems with KVM.

Hmm.... I will have to try this and report back!


Thanks everyone!

---

