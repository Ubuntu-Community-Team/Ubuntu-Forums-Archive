---
title: "Linux Device Driver Kit"
date: 2006-05-25
forum: The Cafe
---

### Post by newbie2 on 2006-05-25
> Have you ever felt teased when driver developers of other operating systems teased you about a lack of a "proper" driver development kit for Linux? Have you felt left out of the crowd when looking at the 36 cdrom package of documentation and example source code that other operating systems provide for their developers? Well feel ashamed no longer!
[http://www.kroah.com/log/2006/05/24/#ddk](http://www.kroah.com/log/2006/05/24/#ddk)
8)

---

### Post by Sef on 2006-05-25
SUSE (Novell) just released one too.

---

### Post by newbie2 on 2007-01-30
> schwaang writes "Linux Kernel hacker Greg Kroah-Hartman, author of Linux Kernel in a Nutshell has posted an epic announcement on his blog. This could portend increased device compatibility for Linux users, higher-quality drivers, and fewer non-free binary blobs." From the announcement: "[T]he Linux kernel community is offering all companies free Linux driver development... All that is needed is some kind of specification that describes how your device works, or the email address of an engineer that is willing to answer questions every once in a while. If your company is worried about NDA issues surrounding your device's specifications, we have arranged a program... in order to properly assure that all needed NDA requirements are fulfilled. Now your developers will have more time to work on drivers for all of the other operating systems out there, and you can add 'supported on Linux' to your product's marketing material."
[http://linux.slashdot.org/linux/07/01/30/044203.shtml](http://linux.slashdot.org/linux/07/01/30/044203.shtml)
[http://www.kroah.com/log/2007/01/29/#free_drivers](http://www.kroah.com/log/2007/01/29/#free_drivers)


> Linux Kernel in a Nutshell is now availble online, for free, from the kernel.org world-wide mirror systems (so that I really have no idea how many people download it, and that's fine with me.)
[http://www.kroah.com/log/2007/01/09/](http://www.kroah.com/log/2007/01/09/)

:biggrin:

---

### Post by newbie2 on 2007-02-01
> Jan. 31, 2007

Ask Linux users what they find most annoying about Linux, and many will complain about device drivers. While the vast majority of PC components and peripherals work with Linux, some don't work at all, and others are marginal. A leading Linux kernel developer has come up with a solution.

In a recent blog and email posting, kernel hacker Greg Kroah-Hartman wrote, "The Linux kernel community is offering all companies free Linux driver development. No longer do you have to suffer through all of the different examples in the Linux Device Driver Kit, or pick through the thousands of example drivers in the Linux kernel source tree trying to determine which one is the closest to what you need to do."

That's a significant point. While many hardware vendors don't want to open up their devices APIs (application programming interfaces) and ABIs (application binary interfaces) to the open-source community, it's often not because they have any real secret ingredient. No, it's just that they don't want a device driver out there that they haven't had a hand in making, and they also don't have the cash on hand to build it themselves. By enabling the equipment vendor to have some say in the matter, while not costing them a thin dime, Kroah-Hartman hopes that the hardware companies will work with open source developers.

Kroah-Hartman continued, "All that is needed is some kind of specification that describes how your device works, or the email address of an engineer that is willing to answer questions every once in a while. A few sample devices might be good to have so that debugging doesn't have to be done by email, but if necessary, that can be done."

And what will the hardware manufacturers get? "In return, you will receive a complete and working Linux driver that is added to the main Linux kernel source tree," Kroah-Hartman says.

"The driver will be written by some of the members of the Linux kernel developer community (over 1500 strong and growing). This driver will then be automatically included in all Linux distributions, including the 'enterprise' ones. It will be automatically kept up to date and working through all Linux kernel API changes."

Any device is fair-game for this new Linux project. "This offer is in effect for all different types of devices, from USB toys to PCI video devices to high-speed networking cards. If you manufacture it, we can get Linux drivers working for it."

Kroah-Hartman also gave vendors a marketing carrot: "This driver will work with all of the different CPU types supported by Linux, the largest number of CPU types supported by any operating system ever before in the history of computing."

Even for a hardware maker that thinks the Linux market for its product is small, the idea of having a driver that will let the equipment work on any architecture must be an attractive one. Later, Kroah-Hartman added, "Now your developers will have more time to work on drivers for all of the other operating systems out there, and you can add 'supported on Linux' to your product's marketing material" underlining that vendors can gain a lot with very little effort on their parts.

According to Kroah-Hartman, the vendor won't even need to worry about support. Both the community and enterprise Linux employee developers will take care of driver support.

What about a vendor that really doesn't want anyone peeking inside its firmware, or the like? Kroah-Hartman has an answer for that, too: "If your company is worried about NDA (non-disclosure agreement) issues surrounding your device's specifications, we have arranged a program with [the Linux Foundation's (the merged OSDL and the FSG's)] Tech Board to provide the legal framework where a company can interact with a member of the kernel community in order to properly assure that all needed NDA requirements are fulfilled."

The majority of the Linux kernel development community has rallied to Kroah-Hartman's call. A few, though, think he may have gone too far in his claims. Linux kernel developer Roland Dreier, for example, wrote on the LKML (Linux Kernel Mailing List): "I'm all for openness of device programming specs, but I think it's a bit disingenuous to suggest that all a company has to do to get a driver written and supported is throw some documentation over the wall. And it's crazy to suggest that the driver will work on every platform and be supported by enterprise distros."

Kroah-Hartman replied, and was seconded by many other LKML developers, that there was nothing crazy about it all since "We do that already today with the majority of drivers in Linux."

Others, such as Adrian Bunk, the maintainer of the 2.6.16 Linux Kernel, observed that while "Writing a driver for shiny new hardware is cool..., understanding and maintaining an already existing driver and working on bug reports for this driver is something not-so-cool." Bunk then asks, "Would someone from your long list of people e.g. be willing to maintain drivers/block/floppy.c? [the floppy disk driver]

"What? Throw a fresh-faced newbie instantly into the tar-pit of despair that floppy.c is? Do you want everyone just to run screaming from kernel development never to be seen again?," asked Kroah-Hartman in his humorous reply.

"Seriously, Kroah-Hartman continued, "if you need help with something like this, bring it up on the kernel-janitors list, there are lots of people there that are willing to help out with stuff like long-term maintenance and bug fixing but don't know where to start."

Will this plan work? Only time, the vendors, and the kernel developers will be able to tell, but the project is on its way. Kroah-Hartman invites vendors to email him at [email]greg@kroah.com[/email] to get their free open-source driver started.


-- Steven J. Vaughan-Nichols
[http://www.linux-watch.com/news/NS8802144045.html](http://www.linux-watch.com/news/NS8802144045.html)
:guitar:

---

