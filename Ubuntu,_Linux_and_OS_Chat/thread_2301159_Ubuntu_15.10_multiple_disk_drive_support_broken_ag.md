---
title: "Ubuntu 15.10 multiple disk drive support broken again (still?)"
date: 2015-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by roland-logikalsolutions on 2015-10-31
It appears Ubuntu once again had difficulties correctly identifying boot drives. I thought they had it fixed, but perhaps they never fixed it and that is why I moved my machines to Mint so many years ago. At any rate...

6-core AMD 24G of RAM 250G SSD boot drive and 2TB ordinary drive with NVidia 384-core CUDA video card. Machine had been running Mint 17 64-bit KDE for years.

Client wanted me to test something with the new Ubuntu 15.10. Since I'm on satellite Internet connection and can really only download stuff between 2am-7:30am or something like that, been getting up really early pulling down ISOs and doing installs. 

First attempt: Booted 15.10 Gnome from DVD and went through install. Thought it odd that partitioning wanted to install on the 2TB drive instead of the boot device, but assumed that was due to free space being on the 2TB drive. Other than that, install seemed to proceed without oddities. Would not boot. Just left a tiny white underscore cursor in the upper left hand of screen. Thought, possibly bad burn of DVD or the fact I checked "download updates during installation" as it would not be the first time an update completely clocked an otherwise working Ubuntu distro.

Second attempt: Booted 15.10 Mate from DVD and went through install. Did not check "download updates during installation". It identified 15.10 as already being installed and I told it to erase and replace. Install seemed to proceed without a hitch. When attempting to boot I see the same cursor in upper left corner of screen.

Suddenly remember filing a bug about this __years__ ago. Remember getting argument from someone along the lines of "what we are doing is right and everybody else is wrong". Imagine bug report was closed the way 98.55% of all Linux bug reports, allowed to rot until version it was filed against had support dropped.

How do I know this?

I pulled out the 2TB data drive, grabbed the original 15.10 Gnome DVD and installed checking "download updates during installation" and it booted just fine.

Keep in mind Mint 17 is a YABU (Yet Another uBUntu). It installed perfectly on this machine with both drives in place and was still running that installation prior to yesterday morning's Ubuntu tests. Even Chakra [https://chakraos.org/](https://chakraos.org/) installed and booted correctly on this hardware configuration.

There are 2 work arounds.

1) give up your second drive (not cool for most) I did not need it for this particular task but will have to go back to Mint when this machine rotates back to main use.
2) open the case and randomly reconnect SATA cables to the motherboard until you magically find the order Ubuntu chooses to identify the drives in.

I would file a bug report, but given the rousing success and support received with the last one it will do far more good to post here. Given the falling prices on 250G SSD this will be a very common configuration. A small, incredibly fast boot drive and a second massive data drive. I mean BestBuy is listing 250Gig SSDs for $110 right now and they aren't usually the cheapest place on-line.

---

### Post by sudodus on 2015-10-31
I feel your frustration. I have felt like that too. But some of the bugs I have reported have been squashed. It is not enough to report the bug at Launchpad. It must be confirmed by at least one more person (the easy part). Sometimes you must also create an opinion, so that many people ask for the bug to be squashed.

Discussions here at the Ubuntu Forums will not reach the developers. You can reach them via the Ubuntu Quality mailing list or via the IRC channels about Ubuntu.

-o-

For this particular issue, I suggest that you try ***Something else*** at the partitioning window of the installer. This is manual partitioning and gives you much better control of what you are doing. I make partitions with gparted before starting the installer, and then select what I created via ***Something else***.

Remember to check that the bootloader will also be installed where you want it!

Unfortunately things get more complicated because of UEFI. You can find a lot of information at the following link and links from it.

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by roland-logikalsolutions on 2015-10-31
> **sudodus said:**
> I feel your frustration. I have felt like that too. But some of the bugs I have reported have been squashed. It is not enough to report the bug at Launchpad. It must be confirmed by at least one more person (the easy part). Sometimes you must also create an opinion, so that many people ask for the bug to be squashed.

Discussions here at the Ubuntu Forums will not reach the developers. You can reach them via the Ubuntu Quality mailing list or via the IRC channels about Ubuntu.

-o-

For this particular issue, I suggest that you try ***Something else*** at the partitioning window of the installer. This is manual partitioning and gives you much better control of what you are doing. I make partitions with gparted before starting the installer, and then select what I created via ***Something else***.

Remember to check that the bootloader will also be installed where you want it!

Unfortunately things get more complicated because of UEFI. You can find a lot of information at the following link and links from it.

[Installation/FromUSBStick#UEFI]("https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI")


Thank you for your response.

I actually did try "something else" and got the same result. The last time I went down this particular rabbit hole I seem to remember Ubuntu was using its own code to identify drives instead of communicating with the BIOS (this machine is still BIOS based) and that was causing it to identify drives in the wrong order.

Yes, I do realize "some" bugs do get squashed. Some actually get fixed and others simply see the tool/package which has them get replaced by another package with different bugs. Once I'm done with the testing I needed to do using 15.10 I will put a new Mint release or some other release on that machine. I have determined 15.10 Gnome won't run BOINC correctly so it cannot be left with my standard "idle" software. When machines aren't currently in use I have them run BOINC so they don't suffer that mysterious "shelf death" heavy use machines are notorious for. Shelf Death: Use a machine heavy for months then power it off and put on a shelf. When you take it off the shelf it won't power up/boot/run again. Had that happen to too many machines over the years. Now all my spares run BOINC so they are always good to go.

Both the standard driver chosen by Ubuntu and the various NVidia drivers for this card seem to cause Xorg to crash and file automated bug reports. As a result the CUDA cores are not usable by BOINC. This means some of the projects I participate in cannot send work to me.

Thanks again for trying to help.

---

### Post by sudodus on 2015-10-31
It is too bad that Ubuntu 15.10 does not work for you. I'm glad that Linux Mint works, that you have a working solution with linux.

---

### Post by buzzingrobot on 2015-10-31
> **sudodus said:**
> 

For this particular issue, I suggest that you try ***Something else***...


Only option I ever use...:D 

FWIW, I've seen Debian's netinst/minimal installers frequently (usually) misidentify drives, at least from my perspective. E.g., if I boot off a USB stick the installer's partitioner will call it /dev/sda, while I think of it, say, as /dev/sdc or /dev/sdd.  Meanwhile, of course, the real /dev/sda is the device where I want the bootloader to go, but it's tagged /dev/sdb or whatever. Left to its own devices (boo!), the installer will do exactly that, which means it will happily put the bootloader on what it thinks is /dev/sda, which is the USB stick. The install completes, you reboot, pull out the USB stick... and you're DOA.

If any of this code survives in Ubuntu's installer, it's gonna produce the same result.

---

### Post by roland-logikalsolutions on 2015-10-31
> **sudodus said:**
> It is too bad that Ubuntu 15.10 does not work for you. I'm glad that Linux Mint works, that you have a working solution with linux.

The few tasks it pulled down will be done tomorrow some time. Mint 17.3 is supposed to be released today so I will probably wait until I can pull down 17.3.

It is sad though, the Gnome version actually looked almost acceptable. It will be interesting to see what Cinnamon looks like.

---

### Post by oldfred on 2015-10-31
Ubuntu/grub do not identify drive order. BIOS or UEFI does and reports that to grub/Ubuntu.

I found that with my older BIOS system it was SATA port order. And I had skipped a port and flash drive that would be sdg on reboot becomes sdb. So I had to then be very careful with any task using device like /dev/sdd, not UUIDs.

My new UEFI system did the same thing. So I went back in and changed SATA port order.

---

### Post by roland-logikalsolutions on 2015-10-31
> **oldfred said:**
> Ubuntu/grub do not identify drive order. BIOS or UEFI does and reports that to grub/Ubuntu.

I found that with my older BIOS system it was SATA port order. And I had skipped a port and flash drive that would be sdg on reboot becomes sdb. So I had to then be very careful with any task using device like /dev/sdd, not UUIDs.

My new UEFI system did the same thing. So I went back in and changed SATA port order.

That doesn't make it any less broken. What you describe is a bug. They are getting the device order from the BIOS/UEFI, but either ignoring which is supposed to be the boot device, also contained in the BIOS/UEFI. Instead an assumption is made that it will always be the "first" device.

---

### Post by buzzingrobot on 2015-11-01
On my installs -- 3 drives plus the USB stick -- the boot drive is always identified correctly, with the option to change the drive/partition where the bootloader is written.

---

### Post by roland-logikalsolutions on 2015-11-01
> **buzzingrobot said:**
> On my installs -- 3 drives plus the USB stick -- the boot drive is always identified correctly, with the option to change the drive/partition where the bootloader is written.

Even if you change the boot drive in the BIOS? The problem seems to be when the boot drive isn't the first physically identified drive. As stated before one must either re-arrange the cables to boot from the first physically identified drive or remove the other drive(s).

---

