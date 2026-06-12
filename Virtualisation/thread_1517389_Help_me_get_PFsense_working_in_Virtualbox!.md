---
title: "Help me get PFsense working in Virtualbox!"
date: 2010-06-25
forum: Virtualisation
---

### Post by em3raldxiii on 2010-06-25
As the title suggests, I am intrigued by PFsense, and I would like to try it out with Virtualbox.  I am a 100% new to Virtualbox, and I am also 100% new to PFsense.  On top of that, I am a bit fuzzy with the whole networking thing to begin with, often having to muddle with my own router in the past, eventually getting it working correctly only through tenacity.  -- As an aside, why is it that most router firmware/software seems so counter-intuitive; as if it was translated 3 times before they actually got to English?

Anyway, I have done a fair bit of Googling, and so far I have not found a tutorial or how-to that gets me all the way there.  I have been able to get VBox installed, and I have a PFsense iso image successfully loaded (and installed, I think).  But then the various tutorials seem to skip something between that point, and the point where you make changes to the system via web configurator.

So up to this point, here is my arrangement:

Ubuntu 9.10 32bit
AMD Phenom Quadcore
8GB high-performance RAM
1x onboard networking (currently directly connected to the ISP, not thru a router)
1x WiFi networking (configured, and working in Ubuntu)
TONS of HD space


[LIST]
[*]I installed VirtualBox using the Ubuntu Software Center
[*]downloaded the PFsense Live Install CD (and unpacked the ISO)
[*]fired up VirtualBox
[*]Created a new Machine with these specs:
[LIST]
[*]Name PFsense02 (my first attempt was epic fail)
[*]HD 512MB
[*]RAM 312
[*]Adapter 1:  PCnet-PCI II (NAT)
[*]Adapter 2:  PCnet-PCI II (Internal)
[/LIST]
 
[*]Mounted the ISO image, booted the virtual machine, and installed PFsense from the Live installer with only 64MB for the swap memory ... not sure if it needed more.  Everything else was default.
[*]Restarted the Virtual Machine, whereupon it asked me a few questions that I didn't really know how to answer.
[LIST]
[*]Set up VLan?  NO
[*]LAN Adapter?  le1 (which I guess corresponds to the "internal" adapter.
[*]WAN Adapter?  le0 (which I guess corresponds to the NAT adapter.
[/LIST]
 
[*]Am now staring at a black screen with 15 menu options (0-14), not sure where to go from here.
[/LIST]

What do I want to do with this?  Well, my wireless router was fried in a lightning storm a couple of days ago (well, not fried per se, but it won't boot correctly and I suspect the power supply has gone kaput).  I have a new wireless router on order, and it should arrive in a few days, but I would absolutely LOVE to get PFsense working and use it in place of my wireless router.  The host computer would be directly connected to the Internet (doesn't specifically need to be routed through PFsense for it's own internet access, whichever way is easier).  All other devices would be wireless.

I guess before we dive into configuring this, is my hardware sufficient, or do I need additional network adapters (wireless or not) in order to function as described?

Where do I go from here?  I am at an absolute stand still, not knowing what to even look at.  How do I access the web configuration utility now for PFsense?  Did I configure my "virtual" network adapters correctly?  How do I point *something* to my wireless network adapter in the host machine?  Once that's done, how do I connect additional wireless devices to it (ie, must I manually configure their IPs etc?)

Any help would be great.  Also, since there seems to be fuzzy (and often far too technical) information and guides, I welcome additional questions.  I will try to help others where I can with setting up this far.  Finally, please try to keep this as simple as possible ... if we get into technical lingo, we need to try to put in explanations so that other people (especially newbies and non-techies) can figure this stuff out too.

I look forward to getting somewhere with this!!

Mike  :guitar:

---

