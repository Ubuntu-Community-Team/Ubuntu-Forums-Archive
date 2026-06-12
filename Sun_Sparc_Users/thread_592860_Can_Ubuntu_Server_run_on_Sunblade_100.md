---
title: "Can Ubuntu Server run on Sunblade 100"
date: 2007-10-26
forum: Sun Sparc Users
---

### Post by jamajama on 2007-10-26
I am brand new to Bubuntu and just installed the Desktop version on an old Dell Inspiron 5100 and it runs great  Did no run into and issues here.  I have 3 SunBlade 100 machines available to play with and I was wondering if and how Ubuntu 7.1 Server can be installed?

Any help is appriciated in advance!!!

---

### Post by jcastill on 2007-10-26
Yes it can, and instructions to intall it can be found over this forum.

---

### Post by zanderred on 2007-10-26
Hi, yes you can, being new to ubuntu $ sparc have a look at [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) & you should look here first [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
try installing xubuntu - it light?, [http://cdimage.ubuntu.com/xubuntu/ports/daily/current/](http://cdimage.ubuntu.com/xubuntu/ports/daily/current/)
good luke

---

### Post by jamajama on 2007-10-29
Thanks to all ...

Not only am I new to Ubuntu, I have no Sun or UNIX experience either.  So to say I'm a newbee is an understatement.  

I've been able to stop the Solaris load by "Stop +A"  and typing the "boot cdrom" command with the Ubuntu Server 7.10  DVD in the drive (Yes, the current CD is CD\DVD) and now I get a the followving  msg:

Boot device:  /pci@1f,0/ide@d/cdrom@1, 0:f file and argss:
Bad magic number in disk lable 1
can't open disk lable1 package 

cannot open boot device

ok


Any help is appreciated ...

---

### Post by zanderred on 2007-10-29
Hi, you have put a cd image on a dvd disk? bad magic number = bad disk
cd.iso = cd, I personally use cd/rw disks, you say you are new to linux-unix, why not start with something like xubuntu, install - configure get a fell for it, then go for the server!.

---

### Post by drosky on 2007-11-01
> **jamajama said:**
> I am brand new to Bubuntu and just installed the Desktop version on an old Dell Inspiron 5100 and it runs great  Did no run into and issues here.  I have 3 SunBlade 100 machines available to play with and I was wondering if and how Ubuntu 7.1 Server can be installed?

Any help is appriciated in advance!!!

A few tips that might help get you running more quickly:

1) IDE DMA is unstable in Linux on Sun Blades.  To avoid file system corruption, you need to pass the paramter "ide=nodma" to the kernel.  During install, this can be done by typing "install ide=nodma" when the CDROM boots.  Note, the kernel in the newest release (7.10) seems to ignore the ide=nodma parameter (at least on my sun blade 150's), which can lead to file system corruption and random hangs during install.  I would recommend installing the LTS release (6.06.1) instead until this problem is fixed (if it is ever fixed).  After installation, you will want to modify /etc/silo.conf so that the ide=nodma parameter is automatically passed every time the system boots.

2) Since it is intended as a server distro, the CD will install a system with only a text console, there will be no GUI environment (Gnome, KDE, etc.).  If you want a GUI environment, you can add it after install using apt-get.  Type one of the following in the text console:

sudo apt-get install ubuntu-desktop    (this will install a GNOME environment)
sudo apt-get install xubuntu-desktop   (this will install an XFCE environment)
sudo apt-get install kubuntu-desktop   (this will install a KDE envorinment)

Note, this will take a long time - about 250-300MB of files need to be downloaded, unpacked and configured.

3) If you do install a GUI environment and are using the built-in ATI graphics chip, you will need to add the following line to the "Device" section of the /etc/xorg.conf file:

Option          "reference_clock"       "28.636 Mhz"

---

### Post by jamajama on 2007-11-02
Thanks to all for the advice.  I have created a bootable CD and DVD of Ubuntu 7.1 Server and both work just fine on Intel based Dell boxes.  The installations went very smooth.  Since I have the 3 Sun Blade 100's just sitting around I wanted to use them as DNS servers.    The have Solaris 9 installed on them, but no one knows the UserID's or PWs.

My thought was to install Ubuntu, but it seems this may be more difficult on the SB's.  They  have plenty of memory and disk space so it is a shame not to put them to use.  Any ideas?

---

### Post by drosky on 2007-11-02
> **jamajama said:**
> 

My thought was to install Ubuntu, but it seems this may be more difficult on the SB's.  They  have plenty of memory and disk space so it is a shame not to put them to use.  Any ideas?

I agree, I have four SB 150's that I got for pennies on the dollar from a company that was ditching them for Intel hardware.  They aren't that fast, especially the built-in graphics, (the 150's are 650MHz ultrasparcII) and no IDE DMA, but they are low power, run cool, and make good servers for lightly loaded services like DHCP, NIS, print servers, low-volume web or ftp servers, etc.

I wouldn't be afraid to experiment around with them, especially if they are just sitting around and you have time to go through a short learning curve.  Installing Linux on them will require a little more technical intervention than on most Intel hardware, but it's not that bad once you know the tricks, and most of them can be found by searching the forums.  The three things I mentioned were the ones that took me the longest to figure out.  Plus, I would start with LTS (6.06.1) until the ide=nodma problem is fixed in 7.10.

Note that if you are planning to use them as desktop systems (as opposed to servers), there are a number of things that are not available, primarily the proprietary stuff like Flash,  or an up-to-date Java environment, etc.

Of course you could also use Solaris 10, which is very easy to install and very stable from my experience, but if you're not familiar with it, the big learning curve will come *after* installation because, even though it's UNIX, it is structured quite differently than Linux.

---

