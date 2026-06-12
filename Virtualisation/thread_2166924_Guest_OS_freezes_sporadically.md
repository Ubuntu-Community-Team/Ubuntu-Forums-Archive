---
title: "Guest OS freezes sporadically"
date: 2013-08-11
forum: Virtualisation
---

### Post by gwm on 2013-08-11
Hi,
](*,)
I have vBox running on 13.04 64 bit as host and Windows 7, 32 bit as guest. for the last month or so, Windows has been freezing when I close a window or close a program. The behaviour has improved a bit as the month progressed but continues to make ones life difficult. The only work around I have, is to pull the plug on the guest OS, restart it and try again. Maybe after a few tries, things get better and I can work normally.

The freeze is not total. Mouse movement is unaffected. Then, if one does something else on Ubuntu for 10 - 30 minutes, and comes back to the virtual machine, I find that the window has finally closed. Who wants to wait for that long though.

My feeling is that it is a vbox problem. Perhaps I should try vmware. I haven't heard much about it in this setting except that it may be slow.

Hopefully someone else had a similar problem and maybe even has a solution.

---

### Post by TheFu on 2013-08-13
5-6 yrs ago, I tried vbox on Ubuntu with a WinXP guest.  Doing nothing in the guest VM, just displaying, it would lock up after a few hours.  Not just the guestOS, but the hostOS too.  I tried a newer release of virtualbox - same, so I stopped pounding my head and switched to Xen and ESXi for my virtualization needs on Linux.

A few yrs ago, the VMware guys decided to screw around with their license model to shaft all their paying clients. We'd deployed ESX at a few clients, but the pricing had gone up more than they can stand.

Last year, after issues with Xen stability and ESX costs, I switched to KVM for Linux virtualization. Took about 6 months.  It has never locked up the client or the server and the costs are fantastic. However, I don't really do "desktop-on-desktop" virtualization.  I will load a desktop into a VM, but only access it remotely through FreeNX/nxclient interfaces.  RDP and VNC are too slow.

2 yrs ago, I loaded VirtualBox on a Core i7 with plenty of RAM for Mom (80 yrs old then).  Loaded WinXP inside a VM, setup printing, networking, all the minimal stuff for Quicken to work ... (Quicken wasn't cooperating in WINE at the time).  Mom ran that for 2 yrs happily. She passed away about a month ago (sniff, sniff), but virtualbox was very stable on her hardware.

I cannot ever recommend anything from VMware anymore due to their corporate history with screwing customers. If you are in business and performing QA or testing, then VMware Workstation is worth the money. It works - well and has features the other options do not which will make any QA or tester more productive.

Anyway - when you talk about "VMware" - be certain you include the product name, since they have like ... 6 different virtualization products. End the confusion.

KVM is built into the Linux kernel, so it gets tested just like the rest of the kernel. Use virt-manager to setup and manage the VMs and you'll probably be plenty happy for desktop productivity apps.  Don't expect music or videos to work great, since you will be accessing it over a remote desktop protocol.

Sorry, no real solution, just an option and some stories.

---

### Post by gwm on 2013-08-14
Thanks for the feedback TheFu.

Since no one else seems to be having this grief, I suspect that it must be either a bad download of Vbox at the last update or something happened to my guest Windows 7 before I last backed up the vdi file.

I suppose I could try making a second vm client and install Win7 on it as well (when I can get the time) and see if the problem is there too. If so, I could then try reinstalling vbox from scratch or wait for the next major update and see if the problem goes away.

---

### Post by TheFu on 2013-08-15
> **gwm said:**
> Thanks for the feedback TheFu.

Since no one else seems to be having this grief, I suspect that it must be either a bad download of Vbox at the last update or something happened to my guest Windows 7 before I last backed up the vdi file.

I suppose I could try making a second vm client and install Win7 on it as well (when I can get the time) and see if the problem is there too. If so, I could then try reinstalling vbox from scratch or wait for the next major update and see if the problem goes away.

It could be a kernel module didn't get rebuilt.  I'd try reinstalling vbox on the host.
BTW, where in SA are you?  I gave a talk to the Cape Town LUG in May on VirtualBox. Did we happen to meet there?

---

### Post by gwm on 2013-08-21
FIXED! (I Think).
I've just installed the latest updates and have a new kernel. I can't remember how to find the kernel level so I have to identify it by date. It is the one released on Wednesday, 2013-08-21. The problem seems to have gone away!

Of course, to get vbox to work again, I had to perform the usual install / rebuild magic trick
> sudo apt-get install linux-headers-$(uname -r)
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

It is so nice to be able to go in there even when I'm rushing, without having to worry whether I'll actually get what I want done in time.

:guitar:

ps for TheFu,
I'm in the Johannesburg area so we wouldn't have met in Capetown. Would have been good to hear the talk though.

---

### Post by TheFu on 2013-08-22
> **gwm said:**
> FIXED! (I Think).
Great!, but I think it is only fixed for now. The next kernel install will bring back a similar issue.

> **gwm said:**
> Of course, to get vbox to work again, I had to perform the usual install / rebuild magic trick

No need to remove/install .... just "install --reinstall" instead.
Also, the way you specified the headers, means that you'll have to manually install new headers with every new kernel. There is a meta-package for kernel headers that will keep you current. Much easier. [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) explains which package you want ... search on the page for the "Guest Addition Dependencies" section. 

> **gwm said:**
> ps for TheFu,
I'm in the Johannesburg area so we wouldn't have met in Capetown. Would have been good to hear the talk though.

J-burg was too scary for us. We were afraid to leave the airport with all the reported kidnappings of tourist on the road and by fake taxis. 
Still, had a great time in Cape Town, didn't get to do everything I wanted that trip, so I'll try to get back sometime.  It is a great FF mileage run, for people who like to do that sort of thing. The airfare was almost a steal, it was so cheap. Actually met a few other couples who did the exact same travel we did on the exact same days because it was so very cheap.

---

### Post by gwm on 2013-09-02
Once again, Thanks for the feedback.
I started another thread about the headers thing. The responders there have also been making suggestions.
> Also, the way you specified the headers, means that you'll have to manually install new headers with every new kernel.
I simply copied that code from someone else's solution to my problem.
> sudo apt-get install linux-headers-$(uname -r)
My experiments seem to indicate that apt-get replaces $(uname -r) with the current installed version of the kernel.
How else might one specify the headers?
Does dkms or build essential go looking for some other text string when deciding what to do?

Once again, Thanks for the feedback.
I started another thread about the headers thing. The responders there have also been making suggestions.
> Also, the way you specified the headers, means that you'll have to manually install new headers with every new kernel.
I simply copied that code from someone else's solution to my problem.
> sudo apt-get install linux-headers-$(uname -r)
My experiments seem to indicate that apt-get replaces $(uname -r) with the current installed version of the kernel.
How else might one specify the headers?
Does dkms or build essential go looking for some other text string when deciding what to do?

---

### Post by TheFu on 2013-09-02
The link provided above explains which meta-package you need to install for your kernel type. 

There is a short-term solution - using the uname -r
and
there is the long-term solution described in that link.

Your choice,

---

### Post by gwm on 2013-09-02
Sorry for double posting that reply.
I have now checked the link you gave me and I believe it answers the question I asked.
It seems that what I need is just plain> apt-get install linux-headers-generic
I will modify my little text file containing these instructions that I keep with my vms accordingly and after the next update I probably won't need the file again.
Thank you for your help!

Message for TheFu!
> 
FIXED! (I Think).

Great!, but I think it is only fixed for now. The next kernel install will bring back a similar issue.

The next kernel update has come and I have installed it.
The lock up remains fixed, so this thread remains SOLVED!
And the vbox rebuild seems to have happened automatically.
My subjective impression is that the client OS is running better than ever.
:guitar:

---

