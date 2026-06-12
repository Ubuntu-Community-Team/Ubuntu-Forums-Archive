---
title: "Anyone have experience running Ubuntu on Acer V5 laptop?"
date: 2013-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by velaxun on 2013-09-26
I recently purchased [this]("http://www.bestbuy.ca/en-CA/product/acer-acer-aspire-v5-14-laptop-iron-intel-core-i5-3337u-500gb-hdd-8gb-ram-windows-8-v5-472-6893/10254581.aspx?path=860f33b49c2c0e94fa3db9e8613a99cben02&SearchPageIndex=1") laptop, primarily for school, and was wondering if anyone around here has had any experience with it or a similar bit of hardware. Not a big fan of Windows 8 so I would like to toss Ubuntu on it if possible, so I was hoping someone around here would be able to give me any sort of heads-up about potential head aches associated with the switch, as I don't have a lot of free time to be mucking about with configurations and settings or fighting with the touch pad. Any help is good help, thanks guys.

---

### Post by oldfred on 2013-09-26
Some other Acer Threads:
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

See link in my signature for lots of general UEFI info.

---

### Post by velaxun on 2013-09-26
Eh... Seems like it might just be too much of a headache for me. I'll probably leave windows on there for this year and check back next release and see how much things of have changed. Thanks though man, saved me a day's worth of tension headaches.

---

### Post by Martin_Keaney on 2014-02-14
Hello, i have just installed ubuntu 13.04 on an acer aspire v5-571p. I read the links above and found them helpful. In the end i just selected and switched off the uefi option in the bios(?) and installed it imn a space i had made using windows drive mangement. I'm not too bothered about dual booting this machine as win 8 was such a drag, but by swapping the secure boot on or off i can log into either OS. There are problems with brightness(system settings work after adjustment) but no function key for the moment. Also having difficculty getting the launcher to unhide via touchscreen(works ok with the pad and possibly I'm just missing something). Wasn't too much stress, loads better now.

---

### Post by oldfred on 2014-02-14
You may do better with 13.10.
 
EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

But most of the improvements are related to UEFI and I do not think BIOS boot changed much if at all.

---

### Post by mips on 2014-02-14
> **velaxun said:**
> I recently purchased [this]("http://www.bestbuy.ca/en-CA/product/acer-acer-aspire-v5-14-laptop-iron-intel-core-i5-3337u-500gb-hdd-8gb-ram-windows-8-v5-472-6893/10254581.aspx?path=860f33b49c2c0e94fa3db9e8613a99cben02&SearchPageIndex=1") laptop...

That link does not work.

I booted ubuntu from a livecd on a V5 last year and everything was fine but I did not install it.

---

### Post by wn1ytw on 2014-02-15
I just took delivery of a v5-131 laptop that came with winderz 7 and have a USB  stick burned with 12.04 LTS ready to install as soon as a stack of DVD-rw disks arrive to make recovery disks of the present recovery. I'll be following this guide by Smallworld: [http://ubuntuforums.org/showthread.php?t=2188087](http://ubuntuforums.org/showthread.php?t=2188087) 

When 14.04 LTS is released I plane to upgrade all 3 of my laptops to that. Assuming I get a stable install of 12.04 LTS - should be a busy time next weekend.

scott

---

### Post by joaomfsantos on 2014-03-29
Hi guys. My experience with Ubuntu 13.04 and 14.04 beta 2:
Everything perfect except backlight not working with fn keys, bluetooth showing on/off but not detecting anything, sd card showing in devices but not reading anything I put in it.
Solutions for first 2 things:
1. To get the backlight working with fn keys AND the on screen display indicator just do this:
sudo nano /etc/default/grub
change line: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Then do:
sudo update-grub

Restart the laptop and it should be fine...

2. Solution for bluetooth:
sudo rfkill unblock all

---

