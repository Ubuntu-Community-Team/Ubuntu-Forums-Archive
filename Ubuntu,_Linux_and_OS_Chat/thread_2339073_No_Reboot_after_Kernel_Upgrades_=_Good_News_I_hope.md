---
title: "No Reboot after Kernel Upgrades = Good News I hope with &quot;kpatch&quot;"
date: 2016-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by markackerman8@gmail.com on 2016-10-04
WooHoo - I hope

I just found it - "kpatch" - (needs "universe" enabled obviously) in Synaptic Package Manager. I was wondering why it is not enabled by default in Ubuntu.   (less than a 10 MB Install)

I will say that in my crusade to turn people onto Linux, this would be/is a HUGE advantage taking one step further to stop the need for ... 
... Windows 3-8 Minute startups (not including shutdown) when there are updates involved.
To make my point, 1 year getting a neighbour/friend to use Linux (he is loving ElementaryOS - I don't though), and just last week on his 3rd Distro change, I said watch how fast it reboots - not like Windows.  He said stop bashing Windows/LOL, "It never takes that long.  I said with updates it does.  And Ironically there had been an update 3 days before for his dual boot Windows 10.  So I said, lets start up your Windows.

10 MINUTES LATER we stopped the timer.  His quote, oh we do this at 3 am, hmmmm I guess my poi9nt was made.

Get it together Linux, a sure fire way to turn more people onto Linux, with technology already available, just a little effort, and some extra space.

Make no rebooting with kernel updates.

I hope to reply to this with a successful functioning "kpatch", but will need to wait for obvious reasons, (probably only a day or two for a kernel update - TO MAKE MY POINT!

Cheers, and Up-vote this to get the attention of Ubuntu, PLEASE.

Mark
p.s. I just had my first kernel update less than 10 minutes later and so far NO "PLEASE RESTART YOUR COMPUTER"  -- WOOHOO :)

---

### Post by Bucky Ball on 2016-10-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not support.

---

### Post by markackerman8@gmail.com on 2016-10-04
Woohoo, on another install and working fine - Linux Mint Cinnamon.  Add that to Ubuntu-Gnome.

Awesome. :)

---

### Post by jeremy31 on 2016-10-04
This works with the normal kernel updates?  If it does that would be great news

---

### Post by markackerman8@gmail.com on 2016-10-04
It seems to be, ... I will update either way, and I looked into the size of the file ... less than 100 kB in size or less than 1/2 a MB for all 4 packages.  Wow should be implemented.
:)

---

### Post by him610 on 2016-10-04
I hope you read this...
> WARNING: Use with caution! Kernel crashes, spontaneous reboots, and data loss may occur!
RE: [https://github.com/dynup/kpatch]("https://github.com/dynup/kpatch")

---

### Post by DuckHook on 2016-10-04
> **him610 said:**
> I hope you read this...him610 beat me to it. kpatch should really be treated as beta software. I read about it a couple of years ago when Red Hat first developed it. At this point, RHEL seem to have the most robust implementation of it. Linux has certainly moved in that direction because the necessary system calls have been accepted into the kernel by Linus and company. But I don't believe that Ubuntu has tested it much and certainly not  with the thoroughness needed for something that monkeys around with the kernel. That's the reason it is not part of a default install.

I'm also worried about the security aspects of a service that allows bits of a running kernel to be replaced or modified. Sounds like a rootkit's dream. Like most new technology, I don't believe that the security ramifications of this technology have been thought out with the required rigour.

Personal paranoia aside, it would be a welcome technology especially for backend boxes in which constant uptime is very important.

---

