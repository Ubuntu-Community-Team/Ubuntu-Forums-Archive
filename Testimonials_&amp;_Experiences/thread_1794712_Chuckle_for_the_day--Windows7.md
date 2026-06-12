---
title: "Chuckle for the day--Windows7"
date: 2011-07-01
forum: Testimonials &amp; Experiences
---

### Post by walt.smith1960 on 2011-07-01
I found a way to download a legal win7 iso file.  I've not used Win7 and was curious so I downloaded, burned and installed.  Installation went OK; seemed slow but OK.  I can switch between IDE and AHCI disk access.  I have XP installed and didn't install the AHCI drivers so I'm running IDE as default.  With Ubuntu if I want to use AHCI no problem, make the change in BIOS, reboot and be happy.  Windows7-problem.  It won't start using AHCI and tries to repair.  Note the word "tries".  Win7 tries for a few minutes and gives up.  I sure am glad that Windows7 handles hardware better than Ubuntu:popcorn:.  Oh, and finds and installs WiFI network drivers?  Ah, no.

---

### Post by johnnybgoode83 on 2011-07-01
Any version of Windows I have used have always needed a few extra steps to get my hardware funtioning properly and to get Wireless connectivity working. 
 
Compare that with every version of Ubuntu where both have worked flawlessly out of the box.  I love it

---

### Post by Jerry N on 2011-07-01
I wonder just how good that "legal" Win 7 ISO download is.  I haven't had any problem at all with Win 7 hardware recognition and I have done several installs.  OTH I have had quite a bit of trouble with Linux recognizing a GT-430 video board and I haven't had a Linux laptop install yet that didn't require a wired ethernet connection to download the wireless drivers.  

I haven't done a Win 7 install that required wireless drivers so I can't comment on that.  

Oh - I paid for my Windows 7 copies.

Jerry

---

### Post by nmaster on 2011-07-01
> **Jerry N said:**
> I wonder just how good that "legal" Win 7 ISO download is. 
...
Oh - I paid for my Windows 7 copies.

Jerry

just so you know, there are legal ways of downloading a Windows 7 iso.  for example, [http://msdn.microsoft.com/en-us/academic/bb250591](http://msdn.microsoft.com/en-us/academic/bb250591)

---

### Post by varunendra on 2011-07-01
> **Jerry N said:**
> I wonder just how good that "legal" Win 7 ISO download is
If only meant for trial.. then how about 90 days trial version of fully functional Win7: [http://technet.microsoft.com/hi-in/evalcenter/cc442495](http://technet.microsoft.com/hi-in/evalcenter/cc442495)

Although there's an 'activation within 10 days' and some more restrictions associated with it.. but 10 days are more than enough for just experiencing it.

---

### Post by walt.smith1960 on 2011-07-01
> **varunendra said:**
> If only meant for trial.. then how about 90 days trial version of fully functional Win7: [http://technet.microsoft.com/hi-in/evalcenter/cc442495](http://technet.microsoft.com/hi-in/evalcenter/cc442495)

Although there's an 'activation within 10 days' and some more restrictions associated with it.. but 10 days are more than enough for just experiencing it.

That's what this appears to be although there's no "you must activate this blah...blah....blah" yet.    I expect to buy keys if I keep it installed which is fine.  OTOH I may just continue to use XP for the infrequent times I need it until 2014. Mostly I just wanted to see if my existing Windows software would run on the latest & greatest.  WordPerfect Office X3 seems to install okay and does the basics.  That was my primary concern; I have some Quattro Pro files that aren't recognized in LibreOffice.  

I just thought it was funny that Ubuntu will switch between AHCI and IDE without a hair getting out of place and Windows 7 would require a reinstall.

---

### Post by lancest on 2011-07-01
> **walt.smith1960 said:**
> 
I just thought it was funny that Ubuntu will switch between AHCI and IDE without a hair getting out of place and Windows 7 would require a reinstall.

People are often amazed about this kind of thing with Linux. 

Last week I switched drives on my desktop machines without needing to reinstall Ubuntu. The hardware is completely different too- AMD/Intel.

Windows: Life with Walls.

---

### Post by freebeer on 2011-07-01
Yeah.  I once replaced a mother board - same processor manufacturer, but different family and different video and sound.  Turned on the machine and Ubuntu booted up just fine.  No re-install like you'd have to do with Windows.

---

### Post by christopher.wortman on 2011-07-02
> **walt.smith1960 said:**
> I found a way to download a legal win7 iso file.  I've not used Win7 and was curious so I downloaded, burned and installed.  Installation went OK; seemed slow but OK.  I can switch between IDE and AHCI disk access.  I have XP installed and didn't install the AHCI drivers so I'm running IDE as default.  With Ubuntu if I want to use AHCI no problem, make the change in BIOS, reboot and be happy.  Windows7-problem.  It won't start using AHCI and tries to repair.  Note the word "tries".  Win7 tries for a few minutes and gives up.  I sure am glad that Windows7 handles hardware better than Ubuntu:popcorn:.  Oh, and finds and installs WiFI network drivers?  Ah, no.

I must be a wizard or something, I just tried the AHCI-IDE switch and back and had 0 issues with Windows 7 SP1. You need the drivers installed. Windows 7 using Windows update finds all Windows drivers they have in their signed database and installs them, you must be using some obscure off-brand wifi card that doesn't provide signed drivers. Obvious troll smells obvious. Moving on...

---

### Post by walt.smith1960 on 2011-07-02
> **christopher.wortman said:**
> I must be a wizard or something, I just tried the AHCI-IDE switch and back and had 0 issues with Windows 7 SP1. You need the drivers installed. Windows 7 using Windows update finds all Windows drivers they have in their signed database and installs them, you must be using some obscure off-brand wifi card that doesn't provide signed drivers. Obvious troll smells obvious. Moving on...

[B]you must be using some obscure off-brand wifi card that doesn't provide signed drivers.

[/B]If a Netgear WNA1100 from Staples is an obscure off-brand, that's probably the problem.

It seems like the problem is that the AHCI drivers are not present when first installed and updates run.  I'm sure they would be downloaded----if Windows could boot.  I'm curious why yours worked and mine didn't but not curious enough to spend any time on it.

---

### Post by 3rdalbum on 2011-07-02
Windows 7 isn't bad for finding drivers that it needs and installing them. I'm surprised by how often it works, compared to how it never worked on Vista.

However, Windows 7 still has that stupid habit of assuming that it needs specific drivers for every USB device plugged in. Plug in a mouse and be prepared to wait ten seconds while Windows looks to find a driver for Model MSM-1024A USB Mouse; a driver that works precisely as well as the standard one that was already loaded into RAM. It might have been quicker to shut down, swap the mice, and boot up again.

---

### Post by prodigy_ on 2011-07-03
> **freebeer said:**
> Yeah.  I once replaced a mother board - same processor manufacturer, but different family and different video and sound.  Turned on the machine and Ubuntu booted up just fine.  No re-install like you'd have to do with Windows.
Vista and 7 don't require reinstallation if you move to a different chipset. Moreover, it was possible to move earlier versions. Basically you just needed to add some registry keys so that Windows could load proper drivers for the new HDD controller.

---

