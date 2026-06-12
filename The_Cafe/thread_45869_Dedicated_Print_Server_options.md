---
title: "Dedicated Print Server options"
date: 2005-07-02
forum: The Cafe
---

### Post by manicka on 2005-07-02
I have an old Pentium 233 MMX machine with 64mb of ram that I want to set up as a dedicated Print Server to Linux, Windows and OS X machines. Can anyone recommend a good solution? Linux preferred

---

### Post by manicka on 2005-07-02
bump

---

### Post by manicka on 2005-07-02
bump

---

### Post by skirkpatrick on 2005-07-02
I'd recommend installing Ubuntu but selecting the server option during install as it doesn't install all the GUI stuff to slow that machine down further.  Check out my reply to another thread ([http://www.ubuntuforums.org/showthread.php?t=45945](http://www.ubuntuforums.org/showthread.php?t=45945)) about setting up print sharing with Win98 and WinXP machines.

---

### Post by gil-galad on 2005-07-02
Any linux distro will work fine.  Period.

---

### Post by skirkpatrick on 2005-07-02
Well, that's true.  My file/print server is still running RedHat 8.  I just figured that if gil-galad had already setup a machine with Ubuntu that it might be easier :)

---

### Post by manicka on 2005-07-03
Thanks for the thougths. I'm going to have a go at FREESCO and just use the print server part. All on one little floppy. Quite impressive

**FREESCO, a router for networks with static routing.**

FREESCO was developed in the open source tradition as an alternative to routing products offered by Cisco, 3-Com, Accend, Nortel etc. All of these companies offer products that are well made, but they are also proprietary and expensive. Between the cost of the equipment and support, you'll spend a great deal and only address one or two of your networking needs .. Additionally, by being closed source (proprietary), many of these products restrict the user from modifying the source software to better suit their needs and easily fix problems that arise.

As many of us who work in the IS industry know, Management is always looking for ways to make work more efficient and decrease expenses. At the same time though, the IS department is usually restricted by budgetary constraints that prevent it from implementing products that would do just that, cut costs and make people's work easier and more cost effective.

That is where an open source product like FREESCO can make all the difference. It is open source (non-proprietary), easy to use and best of all, free.

FREESCO is based on the Linux operating system and incorporates many of the features of a full operating system into software that fits on a single 1.44 meg floppy diskette. With FREESCO, you can make:

    * a simple bridge with up to 10 Ethernet segments
    * a router with up to 10 Ethernet segments
    * a dialup line router
    * a leased line router
    * an Ethernet router
    * a dial-in server with up to 10 modems (with multiport modems).
    * a time server
    * a dhcp server
    * a http server
    * a ftp server
    * a dns server
    * a ssh server
   ** * a print server (requires TCP/IP printing client software)**

FREESCO also incorporates firewalling and NAT which are resident within the Linux kernel to help protect you and your network. All of these features can be used in conjunction with each other or individually.

How does FREESCO do all this? By using only what you need from the Linux operating system and by utilizing the best in "small" *nix programs such as:

    * thttp ([http://www.acme.com/](http://www.acme.com/))
    * lpr daemon (by Steve Flynn)
    * Pure-FTPd ([http://www.pureftpd.org/](http://www.pureftpd.org/))
    * Dropbear (by Matt Johnston)
    * and many standard small linux programs

Unlike many commercial products, set-up of FREESCO is very simple. FREESCO contains a configuration utility that makes set-up and maintenance of the system easy and fast. Providing you have the basic information needed to operate the system, i.e., IP address, gateway address, how you want to use the system(s) etc., setup can be completed in less that 10 minutes. Once the configuration is complete, all it takes is a simple reboot and connection to your network to begin using FREESCO and enjoying what it allows you to do. FREESCO even provides a web control interface so that you can administer the system from any web browser anywhere, anytime. How is that for convenient?

Support for FREESCO is supplied through our web board. There you can ask any question pertaining to set-up and use, or view postings that have already been placed by other FREESCO users. When posting a question, you will usually get a response within 24 hours from either the Maintainer or another FREESCO user. And best of all, you don't have to pay for the support, that's the beauty of the open source community and FREESCO.

We hope you enjoy using FREESCO! Visit us here frequently for new versions and updates to ensure that you get the best performance from your system.

Some technical info:

    * Minimum instal requires a 386sx 16 with 8mb of ram. 16+mb of ram is recommended for enabling servers;
    * Modes of operation. ethernet, dialup, leased, bridge, RAS, Printer server. Some of these modes can run at the same time as well as switching between dialup and ethernt modes;
    * 2.0.39 Linux kernel;
    * Support for up to ten networks cards;
    * Support for up to five printers;
    * Support for up to ten modems, although only four regular modems. Support includes Unix 4 or 8 port modems;
    * FREESCO v.0.3.x can run entirely from ram. This requires at least 20+MB;
    * FREESCO v0.3.x can run up to 16MB of packages with ramdisks enabled on a floppy install;
    * Ident, DHCP, DNS, Print, SSH, FTP, HTTP servers;
    * RAS (Remote Access Server) for dialin and nullmodem connections;
    * PPPoE, and PPtP clients;
    * Dynamic DNS, Zonedit and DHS support;
    * Limited support for SCSI hard drives;
    * FREESCO v0.3.x can be installed on any FAT 16/32 IDE drive on the primary or secondary controller and the primary or secondary drive;
    * can also be installed on an EXT2 partition with the addon ext2 package availible from FREESCOsoft ;
    * The v0.3.2+ kernel has a 16k masq table and the icmp leak patch as well as mppe for PPtP users;
    * ISA PnP is now included into the floppy in v0.3.2. So network cards and PnP modems can be configured.

---

### Post by manicka on 2005-07-04
Ended up with the solution offered at this link [http://www.pigtail.net/LRP/printsrv/](http://www.pigtail.net/LRP/printsrv/) . 

All fits on one floppy drive and works like a charm. Happily printing now from Ubuntu, OS X, XP and 98 machines.

Now that's penguin power    :grin:

---

### Post by skirkpatrick on 2005-07-04
I bookmarked that page for future use.  The server in my house started life as a 266MHz '686.  It had a spare hard drive that I started storing my music and other stuff on.  As I've upgraded either my computers or friends, I've slowly upgraded the server with the left overs.  Reduce, reuse, recycle  \\:D/

---

