---
title: "Linux Kernel Long Term Support Extended to 6 Years"
date: 2017-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by sonicwind on 2017-09-29
[Linux.com]("https://www.linux.com/news/linux-kernel-long-term-support-extended-6-years-project-treble") is reporting that the long term support for the Linux kernel will be extended to 6 years, starting with Linux kernel 4.4.

"This is a great change for everybody in the Linux community as it  will not only apply to Android but to Linux on the desktop and more  importantly to Linux servers. It will be interesting to see what  companies like Ubuntu and Red Hat now do with the LTS versions of their  distributions."

So... what will Ubuntu do?

---

### Post by TheFu on 2017-09-29
Redhat already provides about 10 yrs of support for a line of distros, so nothing will change.

The kernel is a relatively minor part of the total "support" effort - because by the time 5 yrs is done, there aren't many security issues that don't effect ALL kernels, not just that single line.  The real support effort comes from all the core applications and testing of all the different released platforms.

I ran a software development team for years.  We supported 12 platforms, but usually just 1 release on each platform based on the customers.  Supporting 2 releases - say Solaris 8 and Solaris 9 was next to impossible for us due to the cost of the hardware and all the effort to test things.  Even with automatic testing, that helps greatly in a stable area, but not for any new features.  

From a business perspective, 5 yrs is sufficiently long to get the best from an LTS, but not so long (like Microsoft does) as to effectively trap a business into running unsupported systems because the people who deployed it initially have all retired.  Forcing an OS upgrade every 4-5 yrs really is the best deal for businesses.  

I should also mention that I've seen businesses trapped. They'd be forced to run 30+ yr old equipment for which there were no replacements until they died. This was well after all the used-equipment market had run out.  I've had to order equipment from eBay for stuff that hadn't been made in 15+ yrs.

IMHO.

---

### Post by mastablasta on 2017-10-02
i don't think MS traps them in that respect. they just make them lazy. they could just as well upgrade every 3 or 4 years when new OS come out. we have a change of PC hardware aboiut every 5 or 6 year and with the change we also replace the OS. the only one that was skipped was Vista, but that is because the apps we use and need worked well on XP and they also worked well on 7 later on.

the porblme are companies that do not have any dedicated IT staff, or dont' want to pay for outside help. but that is kind of their own fault. not taking the IT operation costs into account.

---

### Post by TheFu on 2017-10-02
Tiny companies are more likely to change the OS with each new HW purchase. 

That isn't how large companies do it.  They have a very different agreement - generally pay MSFT separately for the OS and have the PC vendor pre-load the company's base image onto any HW that will be shipped to them.  I worked at a place that ran WinXP until 2010 - 8 yrs of support.  They moved normal desktops to Win7 and it was painful, but 40K employees couldn't be moved due to specialized hardware that only worked with XP.  It wasn't "lazy" of the companies.  The HW vendors simply refused to provide the necessary programs AND drivers that would work under Win7.  The driver model changed drastically with Win7.  Those vendors wanted to milk the old software/drivers for as long as possible.  I left that company, but heard they moved to Win7 around 2010 for those machines.  This time, hopefully, they added requirements that supporting the currently popular Windows OS 5 yrs later or 2 yrs prior to Win7 EOL was mandatory 

Anyways, converting OSes isn't just about the OS, it is about the HW support and the ability to complete tasks using the entire setup. Some industry-specific applications simply are not ported to every OS and due to driver limitations, do not work.  On those specialized machines, we had 20 different softwares like that and 15 different HW drivers of concern.

Migrating a typical business office between OSes really is trivial compared to migrating OSes for computers that have specialized interfaces for hardware to highly specialized industrial equipment.

BTW, I have printers/scanners that aren't supported by Win7+ because the vendors didn't want to migrate the drivers.  Thankfully, the specific models I have were popular enough that F/LOSS drivers were created which worked and those machines - 12+ yrs old and still working - thanks to Linux.  Industrial companies have 10+ yr old HW that needs drivers and supported software too.  But this HW isn't a $60 printer. For many, even buying brand new hardware today requires running WinXP still.

---

