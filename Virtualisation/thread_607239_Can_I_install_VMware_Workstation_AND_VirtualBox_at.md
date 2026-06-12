---
title: "Can I install VMware Workstation AND VirtualBox at the same time"
date: 2007-11-08
forum: Virtualisation
---

### Post by peterx14 on 2007-11-08
Can I install VMware Workstation and VirtualBox at the same time?

I'm sure it's fine, but since keeping my VMwared Windows running is rather important to me at present, I though I'd check before I go and break it by installing VirtualBox!

A couple of  secondary questions are, does the open-source version of VirtualBox (1). work with the parallel printer port, and (2). can it be booted headless?

---

### Post by gb64 on 2007-11-08
In the past, I ran both VMware workstation and VirtualBox together on a XP  host machine.  There was no conflict. Later, I removed VirtualBox since I didn't really need it at the time.

The latest VirtualBox manual shows no options for connecting to parallel ports ( they are now obsolete, even though there are many older devices still in use ). Neither does the VMware documentation. However, the now free VMware Server 1.04 shows a section on establishing a parallel connection. You could download the manual from the VMware site, and then perhaps download the free server. If you register, they will give you a serial key, no charge.

I regret I cannot answer the headless question. I know what you mean, but don' t have an answer at the moment. Good luck.

---

### Post by peterx14 on 2007-11-08
Thanks for you reply! I'm currently reading the VirtualBox documentation (I was being lazy before!) and it all looks good on the headless front.

As for the printer port, I currently have it working fine in VMware workstation, but I'd like to move the printer to a file server. So my intent was to install VirtualBox here (on my machine) to configure a Windows guest with suitable printer driver, and then move that VM over to the headless server once it's all working.

But [things in LPT land on VirtualBox are not looking so rosey!](http://forums.virtualbox.org/viewtopic.php?t=320&highlight=lpt). I'll dig around a bit more yet, but otherwise I'll have to figure out how I can run a free version of VMware headless.

Anyway... thanks once again!! :D

---

### Post by gb64 on 2007-11-08
Just found this thread on the VirtualBox forums confirming no parallel support, but being requested by several posters:
[http://forums.virtualbox.org/viewtopic.php?t=320&start=0](http://forums.virtualbox.org/viewtopic.php?t=320&start=0)

Edit: Sorry, see now that is the link you also provided.

---

### Post by FrankVdb on 2007-11-09
I have found this on the VMware support site:
[http://pubs.vmware.com/esx254/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=esx25admin_running.5.36.html](http://pubs.vmware.com/esx254/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=esx25admin_running.5.36.html)
(posted it to the VirtualBox forum as well)

The VirtualBox people say it is relatively easy to add parallel port support, the requirement seems to be that enough people should be asking for it...

BTW, it is simply untrue that parallel ports are obsolete. 

A lot of older printers are using it (do you expect people to throw a working printer in the bin?) and for another group the parallel port is important because they are using dongles to get professional software to work.

---

