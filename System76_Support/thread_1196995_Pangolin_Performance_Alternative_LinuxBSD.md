---
title: "Pangolin Performance: Alternative Linux/BSD"
date: 2009-06-25
forum: System76 Support
---

### Post by slackwidow on 2009-06-25
A quick note to those wishing to run another version of Linux on their System76 machine. Mine is:

1 x Pangolin Performance (PAN-P5) = $1,068.00
       Bluetooth Bluetooth
       Car AC Adapter no car AC adapter
       Display Resolution 15.4" WSXGA+ Super Clear Glossy LCD (1680 x 1050)
       Extra AC Adapter no extra AC adapter
       Extra Battery no extra battery
       Hard Drive 320 GB 7200 RPM SATA II
       Hardware Warranty 1 Yr. Ltd. Warranty and 1 Yr. Technical Support
       Laptop Bag no bag
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Operating System Ubuntu 9.04 (Jaunty Jackalope) 64 Bit Linux
       Optical Drive CD-RW / DVD-RW
       Processor Core 2 Duo P8700 2.53 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Wireless Intel Wi-Fi Link 5100 - 802.11A/B/G/N Up to 300 Mbps

--------------------
OpenBSD

OpenBSD 4.5 installs but does not boot successfully from the stock kernels (/bsd, /bsd.mp). There appears to be no work-around at this time.

The same boot error occurs with BSDAnywhere, which is based on OpenBSD. It is a LiveCD with a similar or identical to the current release of OpenBSD, which suggests the kernel itself is to blame. Guess we'll just have to wait for the next release of OpenBSD, which generally runs more reliably on older hardware (according to its website).

------------------
Paldo Linux

Paldo Linux ("pure adaptable linux distribution": paldo.org/index-section-about.html), latest stable version 1.18, runs just fine with a Gnome desktop. Kernel is based on Linux 2.6.29.5.

It's thoroughly reliable (though nfs mounts may cause some process hangs), looks great and is MUCH FASTER than current Ubuntu (9.04). In particular, web browsing is a lot faster than on Ubuntu, surprising considering that the Paldo's Firefox is based on the same release (3.0.11) as the latest Ubuntu.

All multimedia works fine but 64-bit Flash must be downloaded from adobe.com and installed in /lib/mozilla/plugins/, e.g. as /lib/mozilla/plugins/libflashplayer.so.

Suspend works out of the box, but only if network connection is terminated by hand prior to suspend.

---

### Post by slackwidow on 2009-07-07
[QUOTE=slackwidow;7516963]A quick note to those wishing to run another version of Linux on their System76 machine. Mine is:

1 x Pangolin Performance (PAN-P5) = $1,068.00
       Bluetooth Bluetooth
       Car AC Adapter no car AC adapter
       Display Resolution 15.4" WSXGA+ Super Clear Glossy LCD (1680 x 1050)
       Extra AC Adapter no extra AC adapter
       Extra Battery no extra battery
       Hard Drive 320 GB 7200 RPM SATA II
       Hardware Warranty 1 Yr. Ltd. Warranty and 1 Yr. Technical Support
       Laptop Bag no bag
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Operating System Ubuntu 9.04 (Jaunty Jackalope) 64 Bit Linux
       Optical Drive CD-RW / DVD-RW
       Processor Core 2 Duo P8700 2.53 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Wireless Intel Wi-Fi Link 5100 - 802.11A/B/G/N Up to 300 Mbps

--------------------

Good news for the adventurous! 

FreeBSD 7.2 installs and boots without a hitch on my Pangolin. Bootstrapping X was a problem, but that's my problem,not BSD's.

Slackware64-13.0-RC1 installs to an ext4 filesystem and runs alright. However advanced power management (suspend from KDE, the poweroff/telinit 0 commands) does not work out-of-the-box. Also there was a problem with wireless configuration. From a root console ' iwconfig essid "my_network" ' and 'dhclient wlan0' worked fine. Once a normal user was created and 'startx' run as the normal user, even with proper sudoers configuration 'sudo dhclient' could not be run successfully from  the command line, nor could KDE be coaxed to configure a wireless connection properly.

Another problem with Slackware64, as it stands, is 32-bit library compatibility missing, which means (AFAIK) no easy install of OpenOffice without first creating a *.tgz file from available Linux64 RPM or DEB package.
----------------

With all that, let it be said that the stock image of Ubuntu 9.04 that is shipping on system76 machines (and particularly the Pangolin) is still the best OS overall. Everything except the webcam worked right out of the box, though it is a bit slow due to certain kernel issues that are supposed to be fixed before too long.

---

### Post by bill516 on 2009-07-07
I am dual-booting Ubuntu 8.10 and Sidux Ouranos 64-bit on my Pangolin with no problems at all.

Sidux requires some configuration work but the reward is a really fast distro hotrod!

I may or may not keep it on, but it is fun I must say.

---

### Post by miniyak on 2009-07-07
im curious what the battery performance looks like on other distros, has it been any different? better/worst? 

ill post for puppy here when i get the time to try it out

---

### Post by slackwidow on 2009-07-08
> **miniyak said:**
> im curious what the battery performance looks like on other distros, has it been any different? better/worst? 

ill post for puppy here when i get the time to try it out


Slackware64 can't tell when the Pangolin's plugged in so it assumes you're on battery power and outputs a constant flow of error messages to that effect on tty1. I can't say if it's better than Ubuntu or not.

Paldo Linux manages power quit well. If you're off wireless expect 3+ hours on the Pangolin. Unlike Slackware Paldo manages well with Suspend -- I'm scared to try Hibernate with any distro at this point, I've never once seen it work on any machine of mine.

In my experience generally the only way to fully optimize power consumption is to learn to use the appropriate command-line tools and/or write/edit config files for hdparm and k8-powernow or whatever tools apply to your architecture. Gnome and KDE take care of display timeouts & sleep, but as far as power is concerned, that's only half the problem. Hard drive PM and CPU throttling are the other half and window managers usually can't do those as well as a human, if at all.

---

### Post by slackwidow on 2009-07-08
> **bill516 said:**
> I am dual-booting Ubuntu 8.10 and Sidux Ouranos 64-bit on my Pangolin with no problems at all.

Sidux requires some configuration work but the reward is a really fast distro hotrod!

I may or may not keep it on, but it is fun I must say.

Does Sidux do power management? What sort of configuration does it need?

---

### Post by slackwidow on 2009-08-28
> **slackwidow said:**
> A quick note to those wishing to run another version of Linux on their System76 machine. Mine is:

1 x Pangolin Performance (PAN-P5) = $1,068.00
       Bluetooth Bluetooth
       Car AC Adapter no car AC adapter
       Display Resolution 15.4" WSXGA+ Super Clear Glossy LCD (1680 x 1050)
       Extra AC Adapter no extra AC adapter
       Extra Battery no extra battery
       Hard Drive 320 GB 7200 RPM SATA II
       Hardware Warranty 1 Yr. Ltd. Warranty and 1 Yr. Technical Support
       Laptop Bag no bag
       Memory 4 GB - DDR2 800 MHz - 2 DIMMs
       Operating System Ubuntu 9.04 (Jaunty Jackalope) 64 Bit Linux
       Optical Drive CD-RW / DVD-RW
       Processor Core 2 Duo P8700 2.53 GHz 1066 MHz FSB 3 MB L2 (25 Watt)
       Wireless Intel Wi-Fi Link 5100 - 802.11A/B/G/N Up to 300 Mbps

--------------------
OpenBSD

OpenBSD 4.5 installs but does not boot successfully from the stock kernels (/bsd, /bsd.mp). There appears to be no work-around at this time.

The same boot error occurs with BSDAnywhere, which is based on OpenBSD. It is a LiveCD with a similar or identical to the current release of OpenBSD, which suggests the kernel itself is to blame. Guess we'll just have to wait for the next release of OpenBSD, which generally runs more reliably on older hardware (according to its website).


I am happy to say that OpenBSD -current (future release 4.6) installs and configures successfully on my Pangolin Performance. Using the Packages system, it also downloads and *automatically compiles from source* most popular desktop programs and window managers, including (supposedly) KDE and OpenOffice. So far I've used Packages to compile Fluxbox, which went off without a hitch.

For security and reliability OpenBSD can't be beat; I'm still waiting to see if OpenOffice 3 finishes compiling successfully. 

I've been disappointed with Ubuntu 9.04 on my System76 laptop. This is probably not System76's fault in any way. Rather, it seems to be (more than anything) Javascript vulnerabilities in Firefox. For some reason running Firefox for a long time (without NoScript) always results in a system hang and massive (but reparable) filesystem corruption. I thought this was a problem with ext4, but after reinstalling with ext3 the same thing has happened over and over. 

I should add that this is using the standard, updated release of Ubuntu 9.04, not the System76 ship-time image. If the OpenBSD install and configure is successful, System76 might consider shipping with it. Personally, if such a laptop had been available at a comparable price, I would have bought it instead of the pre-installed Ubuntu Pangolin Performance.

---

### Post by gila_monster on 2009-08-28
Never tried a BSD. 

I can confirm that Sabayon does install and run quite nicely on a Pangolin. Minimal issues, most resolvable with diligence and experience.

---

### Post by miniyak on 2009-08-30
I put browser puppy in the other day but i couldn't get the wireless to connect out of the box. With some more tweaking it could work but thats puppy for you. Only so much can come from a 64mb iso. 

-no full resolution 1680x1050 down to 1280x800 i think
-no wireless
-ethernet worked
-still yet to test battery life (not a really fair test without wireless) 

The only reason I would use browser puppy or other puppy derivative is to get better battery life while just browsing the web (since puppy only loads into RAM). If i can get +2 hours with a lighter OS that should prove interesting

---

