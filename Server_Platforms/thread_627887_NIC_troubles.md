---
title: "NIC troubles"
date: 2007-11-30
forum: Server Platforms
---

### Post by vsiege on 2007-11-30
Im installing U Server and I got to the part where it wants to look for a network - and it cannot detect DHCP.  What do I do?

All my other boxes (mac and windows) are running fine on my router. The lights on the back of the soon-to-be linux box does not indicate a network connection (little lights next to RJ-45 socket) and the one on my router. I took down the netowork and put it back up and still nothing.

I thought that maybe it would not work b/c its installling linux and maybe the driver to run the NIC card neeeds to be installed - so I looked on my MOBO disk for Linux drivers and found a NIC driver and heres what i found...sounds like i need to have it installed after linux is in.  any ideas?
[INDENT]<Linux device driver for Realtek Ethernet controllers>

  This is the Linux device driver released for RealTek Ethernet controllers, which are listed as following.
	1. RTL8169S/SB/SC (Gigabit Ethernet with PCI interface)
	2. RTL8168B (Gigabit Ethernet with PCI-Express interface)
	3. RTL8101E (Fast Ethernet with PCI-Express interface)

<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

  Unpack the tarball :
	tar vzxf r1000_vX.YZ.tgz

  Change to the directory:
	cd r1000_vX.YZ

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a
<Force Link Status>
1. Force the link status when insert the driver.
	If the user is in the path ~/r1000, the link status can be forced to one of the 5 modes as following command.

	#insmod ./src/r1000.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

	,where
		SPEED_MODE	= 1000	for 1000Mbps
				= 100	for 100Mbps
				= 10	for 10Mbps
		DUPLEX_MODE	= 0	for half-duplex
				= 1	for full-duplex
		NWAY_OPTION	= 0	for auto-negotiation off
				= 1	for auto-negotiation on
	For example:
	#insmod ./src/r1000.ko speed=100 duplex=0 autoneg=0
	will force PHY to operate in 100Mpbs Half-duplex.

2. Force the link status by using ethtool.
	a. Insert the driver first.
	b. Make sure that ethtool exists in /sbin.
	c. Force the link status as the following command.

	#ethtool -s eth? speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

	,where
		SPEED_MODE	= 1000	for 1000Mbps
				= 100	for 100Mbps
				= 10	for 10Mbps
		DUPLEX_MODE	= half	for half-duplex
				= full	for full-duplex
		NWAY_OPTION	= off	for auto-negotiation off
				= on	for auto-negotiation on
[/INDENT]

---

### Post by DDuong on 2007-11-30
Hello,

Hrmm, does your server have 2 NIC ports?  If so, try connecting the other port and try to let it detect again.

Now at this point when you have it all installed.  

Type the following in the command line:

> 
 lspci


See if it lists your NIC there.

---

### Post by vsiege on 2007-11-30
got it to work... not sure but it works

btw i put that command in and def. saw my NIC card on the list - does that mean it has a driver for everything on the list? how do i scroll up to see the top of the list (dont laugh - ok now laugh)

---

### Post by DDuong on 2007-12-01
That's wonderful news that it works :)

Don't worry I won't laugh, I'm here to help :)

There are a couple of ways to do it.

1.  Hold "shift" and press the "Page up" key.

2. type:

> 
 lspci | less


> 
btw i put that command in and def. saw my NIC card on the list - does that mean it has a driver for everything on the list?


Basically yes, the kernel reconizes those devices and installed the correct drivers/modules for them.

---

### Post by vsiege on 2007-12-01
thanx.... that helps

So im at the point where the server software is installed and i installed xubuntu desktop. I logged in with the account i created during the OS install... do I have this right...

each user you create has only one place they can store files - in their home folder - which is located on the "File System" hdd?

My setup:
2 500 gig HDDs
**first drive:**
[INDENT]use as: ext 3 journeling file system
mount point: /
mount options: defaults
label: none
reserved blocks: 5 %
typical usage: standard
bootable flag: none[/INDENT]
i imagine this is the drive that appears as *File System* on my desktop
**second drive:**
[INDENT]use as: ext 3 journeling file system
mount point: /media/best
mount options: defaults
label: none
reserved blocks: 5 %
typical usage: standard
bootable flag: none[/INDENT]
i imagine this is the drive that appears as *500G Volume* on my desktop
what I want to be able to do is have each user of a certain group be able to put thier files in a sub folder of thier "home" folder and on the *500G Volume*. how do i achieve this?

---

### Post by DDuong on 2007-12-01
No problem :)

Since I am currently at work and don't have the desktop in front of me, you go to Applications -> System -> User and Groups (?).  Here, you can add users and assign where their home directory is (I think).

---

