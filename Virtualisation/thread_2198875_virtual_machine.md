---
title: "virtual machine"
date: 2014-01-11
forum: Virtualisation
---

### Post by COKEDUDE on 2014-01-11
Can I please get some recommendations on virtual machine software? What do you think is the best software and why? I need a windows virtual machine to run some windows software. What do you think is the best Windows version to use and why (xp, vista, 7, 8, 8.1)? Is it hopefully possible to get some prebuilt iso's and if so where? I haven't used a virtual machine in a long time so a good tutorial would also be helpful.

---

### Post by nilla78ro on 2014-01-11
I'm using VirtualBox , if you don't have too much memory then use windows xp, otherwise i prefer win 7 ... it can be used as trial :) , you can google about "install windows on virtualbox" .
Thinking why you are not trying to run them with wine ?

---

### Post by ajgreeny on 2014-01-11
I also run XP on Virtualbox, the Oracle version as I need to be able to use it run Tomtom satnav update software, and I am not sure if the open source version from the repos can do that.  If you need the add-ons for USB etc etc, the Oracle version (free to use) is the way to go, I believe.

I use XP as I still have the DVD from many years ago, so I did not have to go looking for an iso to use, and have no idea where they can be found; presumably google is your friend for that.

It runs fairly well, though compared with my Xubuntu 12.04, is incredibly cumbersome and slow, and I had forgotten how long it takes to do things in Windows which I have not really used since 2005.  As the DVD was XP with the SP2 update package it took a very long time to fully update the OS to SP3, and I have to admit I am so pleased not to now be using Windows for anything other than this one Tomtom software package; it so frustratingly difficult to get my head around how to use it after 8 years.

---

### Post by TheFu on 2014-01-11
The cheapest, easiest, most open VM software to use is VirtualBox. Virtualbox is fine for desktop-on-desktop VMs.  I would NEVER deploy a server under virtualbox, however. Never, never, never.

"Best Windows" is none, but nobody should be using WinXP anymore. Support ends in a few months and every virus creater has been waiting for that the last year.  There will be hundreds of new viruses for WinXP and no patches.  Win7 is what I use for Windows, but I miss WinNT4 and OS/2 still.

Linux ISOs are available anywhere.  Asking for pre-built Windows ISOs is on the edge of being illegal and probably prohibited here.

Not really a tutorial, but it does help setup a VM for great performance: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)
Youtube has tutorials for almost everything these days. Search and you will fine.

---

### Post by JKyleOKC on 2014-01-11
> **TheFu said:**
> Linux ISOs are available anywhere.  Asking for pre-built Windows ISOs is on the edge of being illegal and probably prohibited here.

Not really a tutorial, but it does help setup a VM for great performance: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)I've seen some pre-built Vbox application packages, I believe on one of the true Microsoft sites, that include Win7 -- but I can't remember where, and haven't run across them again! I thought I had downloaded one of them in order to be able to support folk who use Win7, but haven't located my downloaded copy either...

Your blog musings are excellent! I've been using vbox for years now but had always just accepted its defaults when creating new VMs (and most of my VMs were created originally with vbox 2.x, then upgraded through 3.x to the current 4.3.6). I read your link for the first time yesterday, promptly changed a few of my VMs over to use virtio and SATA controllers per your recommendation, and responsiveness seemed to double! The only problem I encountered was with a Win2K VM -- it didn't like the SATA controllers so I had to switch that part back. I'll be changing the others over in the near future. My hosts are Xubuntu 12.04.4 (just changed from 12.04.3 and the only change was to the label itself); RAM on one host is 3 GB and the other is 4GB. I usually give each VM around 800 MB of RAM, and avoid having more than one VM active at any specific time, to avoid swapping as much as possible. I've also tweaked the swappiness setting on both hosts to reduce it, and seldom see more than 4K total used between restarts.

I do differ with you on one point: I set the CPU cap for all my VMs at 90% instead of 100%, to make sure that none of them totally hog the CPU when they're in tight loops dealing with network traffic. It seems to make a significant difference; the guests' audio stutters occasionally, but I don't see any other ill effects.

---

### Post by 1clue on 2014-01-11
Downloading a Windows ISO is not even sort of illegal.  Get it from Microsoft and absolutely nowhere else.  Go to microsoft.com and search on windows 7 iso.  Or windows <your version> iso.  If you get it anywhere else it's almost certainly tampered with.  ***Edit:** You don't have to log in, you don't have to give an email address.*

After you install it you have 30 days to get a license.  If you don't put one in it will say "non-genuine Windows" on the lower right corner but it will still run.

Likewise, you can search microsoft.com for authorized license vendors to be sure you're getting the real thing.

There are multiple license terms for pretty much any Microsoft product.  You can buy one that fits your application best.  At one point I got one for my work that was specifically aimed at VMs, it let me change the CPU type and memory and all that without freaking out.

You can call a number from the Microsoft site to help you choose which version might work best for you.  Only you know your circumstances (student, vm on linux, software-development-only, etc), and the number you get the guys won't even sell you a license so they'll never know what you wind up with.  They're there only for advice.  Be absolutely honest no matter how crazy your intended application is.  Remember that if you call that number, they know you're at least TRYING to be legal.  If you can't do what you want, they'll tell you that and probably tell you what's pretty close to that.

Here's a bit of anti-FUD about Microsoft:  Anyone who tries to be legitimate gets all sorts of help.  They don't want to hamper your business, so they offer ISOs online.  You can set up your computer as soon as you finish the download, you can configure it and get it up to get your business (or your home) going.  Buy now, pay later.  Some of the licenses are crazy expensive (sql server enterprise for example) and others are unbelievably cheap, like student or non-profit licenses.

They also KNOW about virtualization.  There's not a single fortune 500 business that doesn't make heavy use of virtualization.  That's speculation on my part but I'd put money on it.  They know that you could be using Linux as your host, they know about cores and sockets, they know better than most of us how it all works.  It's OK.

You might not like the need to purchase some varieties of software, but the fact is that if you use it, you're required to follow the terms of use.  As evil as that sounds on a Linux forum, chances are the real facts are a lot less frightening than what you might read on this forum.  Commercial software and Open Source can exist rather nicely.  You have to pay attention to licenses and avoid some scenarios, but that's usually a minor problem.

---

### Post by 1clue on 2014-01-11
Sorry about the rant.

What virtualization software depends on how you want to use it.  I advise that you install a Linux image in whatever virtualization software first and use that for awhile.  That way you know when you've picked the right one.

If you want your Windows to boot when your Linux boots, then don't use VirtualBox or VMware Player.  I use KVM/QEMU but that's because I have a BUNCH of vms, most of which start at system boot.

There are lots of really good choices, but keep in mind that everyone has their own priorities.  Which is why I recommend you install a free OS and make sure your setup works for you before you install a Windows license.

---

### Post by PJs Ronin on 2014-01-11
I use VBox because it's simple and it was the first one I tried.   My needs are also very simple... I need a Win VM to run some game software and iTunes; that is all.   I have Win7 Pro in a VM and that does the game software easy peasy but there's a bug with iTunes that prevents connection to my phone.   To get around this, I dug out an old Win XP Home iso (from a time long ago when you got a real iso and not a 'restore' partition on a HD) and one of half a dozen or so certs of authenticity I have laying around and built an XP VM.   iTunes (32 bit) works fine in this VM and I can update my iPhone.

None of my VMs do anything other than those two specific tasks.   I do not run browsers or anything else in them.   All my data is on a separate Linux partition (hint: never keep data in a VM).   I run standard Microsoft anti-virus software in each VM... I keep a weekly backup of every VM, and have absolutely no hesitation blowing away a VM if I think it has been compromised and build afresh.   Is not rocket science and VBox fills the bill.

---

