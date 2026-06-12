---
title: "HP ProLiant DL380 G4... If your familiar with this machine please help."
date: 2011-12-27
forum: Server Platforms
---

### Post by Marcus Aurelius on 2011-12-27
Hello,


  I have a few questions about this server.

It has two CPU's 3.20 ghz / 800 mhz / 1MB L2
5120 MB RAM
6 hard disks on HP Smart Array 6i controller (36.4 GB Ultra320 SCSI HD each)
RAID set to RAID 5 (5 discs) with one spare (6th disk)
USB, 2 Ethernet ports, 1 ILO port, 1 SCSI port


My questions:

1.)  Does this server come default with built in wireless access?  If  not, what do you recommend for wireless?  It has PCI-X and PCI-E slots.

2.)  If the processors are "Intel Xeon" CPU's.....then why is it  possible to install (as I did with the live cd) this Ubuntu 11.04  version .... ubuntu-11.04-desktop-amd64.iso.....  Why would amd64 dvd  work with Intel processors?

3.)  I would LIKE to install "Debian-6.0.3-amd64-DVD.iso"  When I try  and load it it freezes on the detecting network hardware screen.  On the  HP site there is no smart start cd/dvd for Debian.  It is not supported  but I have read people have done this.  Any experiences with Debian on  this machine, and what do you suggest as the best OS to use on this  machine keeping security as a priority? 

Thank you.

---

### Post by headvampyre@hotmail.co.uk on 2011-12-27
Okay, firstly, I'm no exactly familiar with this machine, but what your asking is pretty much applicable to any server out there :)

Firstly - No, it doesn't come with wireless. Wireless isn't stable enough and generally not fast enough to run a server off. Have a look at HP or Realtek's site, most of their wireless devices should be supported under Ubuntu (Not the Server edition, you'll need the Desktop version for that)

Secondly - AMD64 is just a 64-bit extension to the x86 architecture which Intel licensed use of off AMD before they developed Intel64 (IA-64 I think). The distribution's are still called amd64 as it's AMD's technology.

Thirdly - Debian may not support your network cards, or you may have a dodgy NIC. Do both NIC's work under another OS?

And for security - Any OS can be compromised, it's down to how the machine is configured. If you have any experience with Linux - Uninstall AppArmor but ensure you install SELinux to stop application's obtaining access to parts of the filesystem that they shouldn't. Also, use a CHROOT jail for every server application to run, so say that Apache get's compromised, then Bind9 won't be affected by it. Use a firewall if you can (I know that with certain software, such as Samba4 this can be difficult), and keep your system up to date.

Hope this answer's some of your questions :)

---

### Post by rubylaser on 2011-12-27
I don't have a DL380G4 but we have a bunch of other HP Servers DL360's, and higher end DL580's.  All of the previous responses are correct other than the third.  Your server should have dual Broadcom NIC's.

Starting with kernel 2.6.24, support for the Broadcom Netxtreme II (bnx2) was removed from Debian. Here are some [older directions]("http://ftzdomino.blogspot.com/2009/06/debianbroadcom-driver-fix.html") to update the Squeeze iso if you'd like to add the drivers.  You will need to replace mkisofs with genisoimage as that is the replacement for mkisofs in Squeeze.  Or, just install Ubuntu Server, and it will work without any extra hoop jumping necessary.

Also, I've always had to do some tweaking to the block parameters to squeeze decent performance out of our Smart Array 6i controllers so I hope yours works better than mine have in the past.  Debian or Ubuntu will both be great for this box.

---

