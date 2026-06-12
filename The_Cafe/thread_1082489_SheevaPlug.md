---
title: "SheevaPlug"
date: 2009-02-27
forum: The Cafe
---

### Post by m-p{3} on 2009-02-27
Hello, I'm currently not very active among the community, but I was reading an article about the [SheevaPlug](http://www.linuxdevices.com/news/NS9634061300.html).

It seems to be an initiative from Marvell to launch a type of product called [plug computing](http://www.marvell.com/featured/plugcomputing.jsp).

Here are the announced specs of the device

Processor: 1.2Ghz Marvell Sheeva (ARM 9)
Storage: 512MB Flash
RAM: 512MB
1x USB 2.0 Port
1x Mini USB port
1x SDIO port
1x Gigabit Ethernet port
Power Consumption: < 5W

According to Marvell, they are making it as open-source as possible.

I was thinking that it could be interesting to see an Ubuntu-based headless server to run on this device, for example turning an external USB Hard-Drive into an NAS, host a command-line torrent client (ie: rtorrent) and control it through a Web GUI (ie: wTorrent). I think it could make a nice home server for anybody willing to configure it for his/her requirements.

I think I saw a while ago that there was some plan to support the ARM platform in the Ubuntu official distribution (maybe I was daydreaming)?

Oh, and apparently it will be available in March.

Anyway, just wanted to hear about the opinion of other community members!

Thanks,
m-p{3}

---

### Post by zmjjmz on 2009-02-27
I could use this for a lot of things that I probably shouldn't talk about here.
Thanks Sheeva :D

---

### Post by slick666 on 2009-03-01
I currently have some NSLU2s setup that this thing could replace and it would be MUCH more powerful.

---

### Post by m-p{3} on 2009-03-13
Apparently it can be (pre)ordered [here](http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit.aspx) at USD$99 + shipping.

---

### Post by DMcA on 2009-03-13
Ok I want one of these, or at least something very similar; a very low energy computer to leave on all the time for backup and as a media server. For future proofing, HD video decoding would be nice, I guess this box would struggle a bit with that?  

Any one know how development kits like this work? presumably price would go down when these come out but maybe they'd only be available to manufacturers after general release? I'm tempted to order one, anyone know of any similar products out these?

---

### Post by argie on 2009-03-13
> **m-p{3} said:**
> Apparently it can be (pre)ordered [here](http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit.aspx) at USD$99 + shipping.

And I would, if I could. Except their shipping estimates don't work, and it has been two weeks since I sent them an email asking them.

---

### Post by DMcA on 2009-03-13
> **argie said:**
> And I would, if I could. Except their shipping estimates don't work, and it has been two weeks since I sent them an email asking them.

Worked for me. said shipping cost would be $30 something to the UK

---

### Post by Hells_Dark on 2009-03-13
I'll probably buy one too. My only concern is the storage capacity.

---

### Post by argie on 2009-03-13
> **DMcA said:**
> Worked for me. said shipping cost would be $30 something to the UK

Right you are. It works fine for me now too. I was foolishly pressing enter after entering my PIN code instead of hitting Get Estimates.

---

### Post by GeoDesigner on 2009-03-16
I'm really looking forward to using SheevaPlug as a file/print/web server in my office. Ever since I saw info about it on the net I've been very enthusiastic about it, and I think there are really cool things to do with it. I'm trying to gather SP information on this forum here: sheevaplug.ownforum.org . Please share some insights there!

---

### Post by smartboyathome on 2009-03-16
> **Hells_Dark said:**
> I'll probably buy one too. My only concern is the storage capacity.

Get an external hard drive or even flash drive, and use LVM to combine the SeevaPlug's Flash drive with it. I might actually use this instead of what I currently have as a server (as what I currently have isn't working very well, but it is mostly my fault for trying to install a hard drive when I didn't know what I was doing :P).

---

### Post by comprx on 2009-03-17
I wonder How difficult this device would be to setup as a NAS with samba?  I honestly suck at Linux outside of the simple gui of ubuntu and slax so I would need a nice walk through to do it as im certain it would require 100% terminal work to do.

Anyone have one of these? or know how difficult this concept would be? 
setup samba on the plug-computer sheeva with a usb HD share it out to the windows/linux home network.

---

### Post by smartboyathome on 2009-03-17
> **comprx said:**
> I wonder How difficult this device would be to setup as a NAS with samba?  I honestly suck at Linux outside of the simple gui of ubuntu and slax so I would need a nice walk through to do it as im certain it would require 100% terminal work to do.

Anyone have one of these? or know how difficult this concept would be? 
setup samba on the plug-computer sheeva with a usb HD share it out to the windows/linux home network.

Right now, it would actually be pretty difficult since it is only a developer version. You'd need to manually install Linux on the flash drive from another computer using something like Cross Linux From Scratch, along with SSH so you can finish it. Then, it would be easy to install the rest of the stuff on the SheevaPlug.

---

### Post by comprx on 2009-03-17
And that sounds simple enough but i do agree, too difficult for me as I am not good with linux on the technical side.  I have no idea how I would go about installing linux from scratch from another computer.  and given that this would need not gui frontend to run I highly doubt my feeble attempts at the linux terminal would suffice to accomplish all of this.

---

### Post by kaput on 2009-03-18
*Wow. Haven't posted here in a *long* time.*

Actually, from the documentation, it appears to ship with the ARM build of 9.04, so installing Samba, or most any other Ubuntu package (assuming ARM compatibility), should be as easy as 'apt-get install.'

Ubuntu, locked and loaded. I pre-ordered mine as soon as I saw it was shipping with usable software. :D

---

### Post by DMcA on 2009-03-18
Looks like it's out of pre-order and available for purchase already. I'd get one but the cost is just a bit too much (considering I'd have to buy a usb port, a bluetooth dongle and an external hard drive to do everything I want, and import it from the US). Maybe in a year or so (hopefully less) these sort of things will get much cheaper and more available

---

### Post by comprx on 2009-03-18
how would you just run the sudo apt get though? you cannot connect a keyboard to it. is there a way to do it remotely? (im such a newb)

---

### Post by smartboyathome on 2009-03-18
> **comprx said:**
> how would you just run the sudo apt get though? you cannot connect a keyboard to it. is there a way to do it remotely? (im such a newb)

Connect to it through OpenSSH, then run the command. ;)

---

### Post by comprx on 2009-03-20
Is openssh a package that would need to be installed thoug? or does it come on the sheeva plug? ( Sorry I am asking all these stupid questions. linux makes the windows admin in me feel like a kindergartner)

---

### Post by smartboyathome on 2009-03-20
> **comprx said:**
> Is openssh a package that would need to be installed thoug? or does it come on the sheeva plug? ( Sorry I am asking all these stupid questions. linux makes the windows admin in me feel like a kindergartner)

I don't know if it is installed or not. I don't have one yet. ;)

---

### Post by comprx on 2009-03-22
When you get one will you let us know? This would make an amazingly cheap NAS  ($100 for sheeva + ~$100 for 1tb ext drive= 200 awsome samba nas! )

---

### Post by gletob on 2009-03-22
Anyone know if you can put an SD card in the SDIO slot and use it for storage?

---

### Post by egrep on 2009-04-03
Whoot! Mine just arrived via Fedex ground. Initial observations:

o Mounted plug comes off to reveal a laptop type cord receptacle. They include the power cord. No wall wart after all. Pics later.
o Next to the mini usb serial port there is an SD memory card slot, so yes, external memory can be an SD card.
o Kit includes:

1. Documentation Package: This package consists of the documents needed to bring up SheevaPlug development kit platform and SheevaPlug reference design guide.
2. Schematics and Bill of Materials: This package provides the schematics, layout and BOM necessary to design SheevaPlug development kit reference boards.
3. U-Boot: This package consists of the files and source codes needed to build U-Boot, initial bring-up of SheevaPlug development kit reference design as well as upgrading the U-Boot.
4. Linux Support Package: This package provides the files and sources needed to build and configure the Linux kernel 2.6.22.18 with Marvell’s LSP. It also includes a compiled uImage to bring-up SheevaPlug development kit reference design.
5. File System: This package consists of Ubuntu’s jaunty filesystem.
6. Host Software Support Package: This package consists of support software for Windows host and Linux host.
a. Windows Host: This package consists of the mini-USB to USB driver that needs to be installed on the Windows host in order to access the debug console for SheevaPlug development kit.
b. Linux Host: This package consists of the GCC crosscompiler that needs to be installed on the Linux Host. The package also consists of the basic root filesystem that needs to be installed on the Linux host to boot SheevaPlug development kit using NFS.

Should be an interesting weekend...

---

### Post by linuxisevolution on 2009-04-03
My laptop is only 100mhz faster than this thing.:lolflag:

---

### Post by smartboyathome on 2009-04-03
> **egrep said:**
> Whoot! Mine just arrived via Fedex ground. Initial observations:

o Mounted plug comes off to reveal a laptop type cord receptacle. They include the power cord. No wall wart after all. Pics later.
o Next to the mini usb serial port there is an SD memory card slot, so yes, external memory can be an SD card.
o Kit includes:

1. Documentation Package: This package consists of the documents needed to bring up SheevaPlug development kit platform and SheevaPlug reference design guide.
2. Schematics and Bill of Materials: This package provides the schematics, layout and BOM necessary to design SheevaPlug development kit reference boards.
3. U-Boot: This package consists of the files and source codes needed to build U-Boot, initial bring-up of SheevaPlug development kit reference design as well as upgrading the U-Boot.
4. Linux Support Package: This package provides the files and sources needed to build and configure the Linux kernel 2.6.22.18 with Marvell’s LSP. It also includes a compiled uImage to bring-up SheevaPlug development kit reference design.
5. File System: This package consists of Ubuntu’s jaunty filesystem.
6. Host Software Support Package: This package consists of support software for Windows host and Linux host.
a. Windows Host: This package consists of the mini-USB to USB driver that needs to be installed on the Windows host in order to access the debug console for SheevaPlug development kit.
b. Linux Host: This package consists of the GCC crosscompiler that needs to be installed on the Linux Host. The package also consists of the basic root filesystem that needs to be installed on the Linux host to boot SheevaPlug development kit using NFS.

Should be an interesting weekend...

Thanks! This just makes me want to get it that much more. We will see how much money I get today. ;)

---

### Post by lastword on 2009-04-03
Greetings!

I am new to this forum, but not new to linux (I have Ubuntu installed on a couple pc's).

I too have ordered and received the Sheeva Plug. Yesterday I opened the box. Inside the box I found the unit itself, a mini-USB cord, a rj-45 cord, a power cord (in case you want to use that instead of the wall mount) and a CD (version 1.0 software, but I downloaded 1.1). The software details - I believe- were mentioned in a previous post. 

I am not too far into the process and thus have very little to report. Today I learned that I can use windows to connect to the unit. So, I installed the FDT2322D driver from CD as specified on the pdf. 

Next, I am supposed to use HyperTerminal application (windows), with the proper settings (e.g., COM4, 115200 baud rate, 8 data bits, no parity, 1 stop bits and no flow control) to connect to the Sheeva. If nothing happens I may have to reset the SheevaPlug. We will see. That's all I know. 

I will be back seeking advice. 

Regards,
lastword

---

### Post by mips on 2009-04-05
> **egrep said:**
> 
o Mounted plug comes off to reveal a laptop type cord receptacle. They include the power cord. No wall wart after all. Pics later.


This sounds good. So essentially you could take the innards plus + USB-SATA adapter + HD and build it into a new enclosure you can run 24/7 as a NAS, torrent box etc.

Looking forward to the pictures of the innards.

---

### Post by Hells_Dark on 2009-04-05
yep, me too.

---

### Post by briankircho on 2009-04-05
I also received my SheevaPlug in the mail yesterday, and have had some success with ubuntu on it :)

First I tried to use my 8.10 desktop and the mini USB connector to get a serial console to the unit. It seems like the ftdi_sio module should work for this, but I could not get it to detect the unit and create /dev/ttyUSB0 in the standard 8.10 or 9.04 kernels.

At this point I had a windows machine lying around so I used the serial port drivers in SheevaPlug_Host_SWsupportPackageWindowsHost.zip.  This worked and I was able to see what was happening.  I expected to have a empty device and have to NFS boot from my linux machine to flash the root filesystem.  

I was a bit surprised to find ubuntu 9.04 is already flashed onto the 512MB of NAND and will bootup when you plugin the unit so you dont even need the serial console or to flash the unit.  There is an SSH server running and you can use the login from the manual: root/nosoup4u

I attached a USB hard drive, and have installed a bunch of packages (samba, nfs, apache), everything working great and its very fast for its size and (3W) power use so im excited about this so far.

Some info from the unit:
# df -h
Filesystem            Size  Used Avail Use% Mounted on
rootfs                507M  176M  332M  35% /

# uname -a
Linux kirchoff 2.6.22.18 #1 Thu Mar 19 14:46:22 IST 2009 armv5tejl GNU/Linux

# cat /proc/cpuinfo
Processor       : ARM926EJ-S rev 1 (v5l)
BogoMIPS        : 1192.75
Features        : swp half thumb fastmult edsp
CPU implementer : 0x56
CPU architecture: 5TE
CPU variant     : 0x2
CPU part        : 0x131
CPU revision    : 1
Cache type      : write-back
Cache clean     : cp15 c7 ops
Cache lockdown  : format C
Cache format    : Harvard
I size          : 16384
I assoc         : 4
I line length   : 32
I sets          : 128
D size          : 16384
D assoc         : 4
D line length   : 32
D sets          : 128

---

### Post by AlanPorter on 2009-04-05
I am anxiously watching the mailbox, too.  I ordered three of them last weekend.

My plan is to use two of them to run BackupPC with external USB hard drives (1 for me, 1 for a friend).  The third one will be for tinkering.

I am glad to hear that they come with some basic filesystem and sshd already loaded.  That'll make the BackupPC installation a snap: boot, install, configure, forget.

Alan

---

### Post by Entilzha on 2009-04-06
I'm really excited about this thing. Finally a cheap and energy efficient way for my modest hosting needs. Keep up the testing, and please provide them pics also. If they'd have made a European variant, I'd have bought one myself. Actually, I'll order one the second they provide this option.

On the flip side, this prolly means you guys will have done all the hard work testing/getting stuff running by the time I'll get mine! :)

---

### Post by AlanPorter on 2009-04-06
> **Entilzha said:**
> If they'd have made a European variant, ...

If you un-clip the US-style plug, it reveals a small laptop-style power plug hole.  And the power supply is 110V~240V.  That sounds like it should work just fine in Europe.  You just won't be able to hang it on the wall from the plug (and personally, I don't consider that a limitation).

See the photo here.
[http://www.flickr.com/photos/h_u_p/3358652691/](http://www.flickr.com/photos/h_u_p/3358652691/)

Alan

---

### Post by Hells_Dark on 2009-04-06
but is the power cable «offered» ?

---

### Post by AlanPorter on 2009-04-06
These cords are not offered by Marvell or by GlobalScale Technologies as part of the kit (nor do they offer European, British or Australian wall wart snap-ons).  But that should not be a show stopper.

A quick Google search shows that companies like powerbrixx.com offer these cords for $5 or less.  Look for "2-prong European figure-8 power cord".

You'll also notice that Marvell does not include an SD card with the kit either.  Finding an SD card is left as an exercise for the reader.

Alan

---

### Post by mips on 2009-04-06
> **AlanPorter said:**
> Look for "2-prong European figure-8 power cord".



I have plenty of those, lost of equipment use them.

---

### Post by hessiess on 2009-04-06
> **linuxisevolution said:**
> My laptop is only 100mhz faster than this thing.:lolflag:

Its based on an ARM cpu, which is a completely different arch designed from the ground up to use as little power as possible. The performance of CPU's using a different architectures cannot be compared by clock speed.

---

### Post by egrep on 2009-04-07
> **briankircho said:**
> I also received my SheevaPlug in the mail yesterday, and have had some success with ubuntu on it :)

I was a bit surprised to find ubuntu 9.04 is already flashed onto the 512MB of NAND and will bootup when you plugin the unit so you dont even need the serial console or to flash the unit.  There is an SSH server running and you can use the login from the manual: root/nosoup4u

I attached a USB hard drive, and have installed a bunch of packages (samba, nfs, apache), everything working great and its very fast for its size and (3W) power use so im excited about this so far.


Did the unit come up and grab a dhcp address or did you still have to connect via the usb console?

---

### Post by cneth on 2009-04-07
> **egrep said:**
> Did the unit come up and grab a dhcp address or did you still have to connect via the usb console?

dhclient is running, mine showed up right away.  hostname is 'debian'.

Literally out of the box and on the net in one minute...

---

### Post by lastword on 2009-04-07
What's happened so far with the SheevaPlug? I can tell you what I have done.

I was busy this weekend, so didn't get that far but I did manage to connect to the unit via mini-USB and windows xp hyperterminal with the default username and password for SheevaPlug. I noticed that the system has Perl and Python. I have a lot of scripts (mostly for Perl) and so I was happy to see this.

perl -v gave:
This is Perl, v5.10.0 built for arm-linux-gnueabi-thread-multi

python -V gave:
Python 2.5.4.

Later I connected the unit to my cable modem via RJ-45 and set the cable modem to allow port forwarding to the address of the SheevaPlug. I can now ssh to it from remote locations. 

My next goal is to connect an external USB hard drive. I have a Western Digital My Book Essential Edition 500 GB USB 2.0 External Hard Drive (WDH1U5000N). 

-more later
lastword

---

### Post by egrep on 2009-04-07
> **cneth said:**
> dhclient is running, mine showed up right away.  hostname is 'debian'.

Literally out of the box and on the net in one minute...

Whoot! Yep, logged into my router and saw a new client at .109. Sweet! I really did not want to wait until I built the system from the ground up to play with it. This is soooo cool! ssh connected fine. Thanks for the info cneth!.

Now, if we could only get someone to design in a powerline ethernet interface on one of the unused GigE ports, we could have an internet router that could connect to the entire house. Smart Grid anyone?

---

### Post by mips on 2009-04-07
> **lastword said:**
> I have a couple **500gig flash drives** sitting around.

???

---

### Post by lastword on 2009-04-07
> **mips said:**
> ???

I edited the original post to make it clear what I was going on about.

-lastword

---

### Post by jsevy on 2009-04-07
I got my SheevaPlug yesterday, and was able to log right in using ssh through the Ethernet port once the SheevaPlug had gotten its IP address from my router via DHCP. Very nice! Ran apt-get to install apache2, and had a web server in no time. Next up: get the USB thumb drive and Wifi adapter working.

The one thing I had a bit of difficulty with was logging in through the mini-USB connector using minicom, but I finally got it by modprobing the ftdi_sio serial driver with appropriate usb vendor and product args:

modprobe ftdi_sio vendor=0x9e88 product=0x9e8f

I was then able to use minicom to connect through /dev/ttyUSB1 using 115200 8-N-1 settings (not sure what's on /dev/ttyUSB0...)

Jon

---

### Post by egrep on 2009-04-07
> **jsevy said:**
> IVery nice! Ran apt-get to install apache2, and had a web server in no time. Next up: get the USB thumb drive and Wifi adapter working.

Jon

What apt-get command did you use? I am very green when it comes to ubuntu (being a Slack geek), and I had to create /var/cache/apt/archives/partial and /var/cache/apt/archives. It looks like it got some stuff, but a lot of archives were 404's. bummer.
apt-get install apache2
and
apt-get install apache2-mpm-worker
no luck.

Maybe I will just build Apache2 from source?
-steve

---

### Post by jsevy on 2009-04-07
Steve,
before apt-get would work right for me - I too got lots of irritating 404's - I had to "update":

apt-get update

This somehow syncs the local apt repository contents with those on the server. After that apt-get worked fine.
  \
  Jon

See  [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)  for more details...

---

### Post by pjratl on 2009-04-07
apt-get update not working for me  what am I missing?

root@debian:~# apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by pjratl on 2009-04-07
Ok I just created the directory and now update is running just fine

---

### Post by egrep on 2009-04-08
Doh! I remember the instructions shipped with it. "Version: 1.0 for reference only - Please download newest version 1.1". I wonder what version of the install is flashed at the factory?

Ummm... last line of apt-get:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
hahahahahah.... What a dummy. _grin_

Ok, I will give this my best shot using the installed Ubuntu. I work with RHEL at work, and Slackware at home. I will have to see how easy it is to compile on this monster (in the case of no supported package for your program). I have to admit though, everything I look for these days are pre-built for Ubuntu. Now if I can only get it to mount a thumb drive.

Thanks for the help gents! This looks like it will be fun. What a great router/firewall for home and small business. $59.00 for a Linksys router or $99.00 for the same thing except that it has a web server, DNS server, can do email for a business or home and what ever else you can think of... Nice time to be alive...

I'll post the url for the first site I get running. Sweet, it even has an /etc/hosts.allow access list. Anyone else notice the eth1 interface?

-steve

---

### Post by darethehair on 2009-04-08
As someone interested in eventually getting a Sheevaplug (or two), I was pleased to see this thread develop :)

I have asked some Canadian sales reps for info on Canadian suppliers/retailers, but so far no response :(

Right now there are two things on my mind that would help me feel better about a future purchase:

- The details of anyone successfully using some sort of wireless adapter (USB I guess), which is reasonably-priced and works well with the Sheevaplug

- The details of anyone successfully using 'gphoto2' to do remote capture/download of pics from digital cameras attached to the USB port (I was never able to duplicate my success of gphoto2 on the NSLU2 as I was on my desktop, for reasons unknown)

---

### Post by L0rd_D4rk on 2009-04-08
I just bought one, unfortunately it seems that I will have to wait a month to have it at home :-(

I'm planning on using it as 24h downloading box, NAS and FTP (maybe webserver too). But it would be great to be able to use it as firewall as well. So, I'm really interested in which Wifi cards have been tested and if it's possible to put it in hotspot mode. Maybe an USB Ethernet card would also do the job...

I will use an sdhc card for storage, so the USB port will be free for anything else.

---

### Post by egrep on 2009-04-08
> **darethehair said:**
> As someone interested in eventually getting a Sheevaplug (or two), I was pleased to see this thread develop :)

I have asked some Canadian sales reps for info on Canadian suppliers/retailers, but so far no response :(

I ordered mine from Globalscale Technologies. They are the manufacturer for Marvell on this device. Marvell site: [http://www.marvell.com/featured/plugcomputing.jsp](http://www.marvell.com/featured/plugcomputing.jsp) with the development kit page at:
[http://www.marvell.com/products/embedded_processors/developer/kirkwood/sheevaplug.jsp](http://www.marvell.com/products/embedded_processors/developer/kirkwood/sheevaplug.jsp). The Globalscale order site is a "buy now" link on the Marvell page.

---

### Post by code4fun on 2009-04-08
> **jsevy said:**
> I got my SheevaPlug yesterday, and was able to log right in using ssh through the Ethernet port once the SheevaPlug had gotten its IP address from my router via DHCP. Very nice! Ran apt-get to install apache2, and had a web server in no time. Next up: get the USB thumb drive and Wifi adapter working.

The one thing I had a bit of difficulty with was logging in through the mini-USB connector using minicom, but I finally got it by modprobing the ftdi_sio serial driver with appropriate usb vendor and product args:

modprobe ftdi_sio vendor=0x9e88 product=0x9e8f

I was then able to use minicom to connect through /dev/ttyUSB1 using 115200 8-N-1 settings (not sure what's on /dev/ttyUSB0...)

Jon

Hey Jon. Thanks for the tip! It has been a while since I played with USB serial on linux and couldn't figure out why it didn't create the tty devices. Regarding ttyUSB0, I think that is for the Open OCD interface (debugging). See section 3.6 of the "SheevaPlug Development Kit - Reference Design - Rev1.0.pdf". One can either use a 20 pin JTAG or via Open OCD for on chip debugging. I've used JTAG, but I haven't used OpenOCD. Will definitely have to check it out.

---

### Post by lastword on 2009-04-09
Summary of what has worked on my SheevaPlug:

A)Installed Apache: works great!
B)Installed PHP: seems to work, not tested that much
C)Perl and Python are functioning.

My next goal was to get a flash drive working on the SheevaPlug. 

Steps to mount a flash drive on SheevaPlug:

1)A 2gb flash drive was attached to the USB 2.0 of Sheeva for testing.

2)df -k did not show the USB flash drive:

```
[FONT="Courier New"]Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                  519168    180492    338676  35% /
tmpfs                   257816         0    257816   0% /lib/init/rw
varrun                  257816        44    257772   1% /var/run
varlock                 257816         0    257816   0% /var/lock
udev                    257816        16    257800   1% /dev
tmpfs                   257816         0    257816   0% /dev/shm
tmpfs                   257816     36228    221588  15% /var/cache/apt[/FONT]
```

3)fdisk -l showed:
```
[FONT="Courier New"]Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      1           246      1974240   6  FAT16[/FONT]
```

3)A PUBLIC folder was created under /media/
4)The flash drive was mounted with 'mount /dev/sda1 /media/PUBLIC/'
5)df -k again:

```
[FONT="Courier New"]Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                  519168    180492    338676  35% /
tmpfs                   257816         0    257816   0% /lib/init/rw
varrun                  257816        44    257772   1% /var/run
varlock                 257816         0    257816   0% /var/lock
udev                    257816        16    257800   1% /dev
tmpfs                   257816         0    257816   0% /dev/shm
tmpfs                   257816     36228    221588  15% /var/cache/apt
/dev/sda1              1973952   1299328    674624  66% /media/PUBLIC[/FONT]
```


6)Does flash drive interact with Sheeva? To test, I copied a file to the flash and read it.

[FONT="Courier New"]```
root@debian:/var/www# cp index.back /media/PUBLIC/
root@debian:/var/www# cd /media/PUBLIC/
root@debian:/media/PUBLIC# ls *.back
index.back
root@debian:/media/PUBLIC# more index.back
<html><body><h1>It works!</h1></body></html>
root@debian:/media/PUBLIC# 
```[/FONT]

Comments?
-lastword

---

### Post by egrep on 2009-04-09
That rocks. I thought /dev/sda1 was the built-in flash drive. I will try this as soon as I get home. I also tried with an SD card inserted, but it did not work either. Did not check a df -l. Doh!

---

### Post by jsevy on 2009-04-09
I managed to get a VNC connection working to the Sheeva so I'd have a graphical interface to work with (screenshot attached) through the following steps:

apt-get install vncserver
(installs the vncserver)

apt-get install icewm
(installs the ice window manager - lightweight window manager)

 apt-get install xterm
(installs xterm for use in the ice window manager)

The vnc config file ~/.vnc/xstart should contain as its first 2 lines
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc

Also, for some reason the executable xinitrc wasn't set as executable, so I had to make it so:
chmod a+x /etc/X11/xinit/xinitrc 

Then start the vnc server on the Sheeva:
vncserver :2
(runs the vncserver on display :2)


From my laptop I connected to the Sheeva vncserver:
vncclient 10.0.1.7:2
(attaches to the vncserver on the Sheeva at IP address 10.0.1.7)

which resulted in the desktop shown in the attachment. So finally a GUI on the Sheeva!

However, many of the X apps seem broken - for example, xterm fails to start and give the error (in the .xsession-errors file) "xterm Xt error: Unresolved inheritance operation"
There are some other reports of this problem; may have something to do with issues with the libXt library, but doing apt-get upgrade libXt didn't seem to help...

So still some work to do, but nice to see a GUI...

Jon

---

### Post by egrep on 2009-04-10
> **egrep said:**
> That rocks. I thought /dev/sda1 was the built-in flash drive. I will try this as soon as I get home. I also tried with an SD card inserted, but it did not work either. Did not check a df -l. Doh!

I see my error. The usb stick I was testing with was one that I had done a Slackware install on. Of course it looked like the built in os disk... hehehe. What a dope. Thanks lastword!

```

egrep@greenmachine:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                  519168    167060    352108  33% /
...
/dev/sda1              1730264     35380   1606988   3% /media/cruiser

```

-steve (greenmachine.igroklinux.com)

---

### Post by lastword on 2009-04-10
Egrep, 

It is good that it worked. Now you have more flash to use. I am curious if you can boot from an external drive instead of the built-in one? 

Anyway, I think I will try Jon's method for VNC. 

Isn't this plug computer fun? I may order a couple more. hmm.

-lw

---

### Post by jsevy on 2009-04-10
There's already a bug report about xterm (and other x apps) not launching on ARM Jaunty platforms at [https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/343574/]("https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/343574/") - hopefully some resolution in the near future...

Jon

---

### Post by dcherryholmes on 2009-04-10
I got mine a few days ago.  The main use I intend to put it to is as an always-up server to run rtorrent and pytvshows from, so I can leave the big horkin media PC in suspend when I'm not actually watching TV.  For the moment I'm using a 4GB SDHC card for storage, but I'll eventually attach an external USB HD.

A few things I've noticed while playing with it so far:

1) no kernel support for nfs-kernel-server.  I intend to work around this by using sshfs on the media machine.  We'll see how that goes

2) Can't make tzdata persist across reboots. Actually, the time zone stays set, but the time is still off.  I'm aiming for extreme uptime with this little guy, so setting it by hand with ntpdate isn't the worst thing in the world.

3) The default file permissions make setting up cron jobs a mess, and I suspect they will not persist across reboots, either.

It seems most issues stem from mounting several filesystems as tmpfs to keep them in RAM.  I'm reluctant to physically mount them with only the internal storage space, as I assume it was done for good reason.

---

### Post by jsevy on 2009-04-10
I managed to get a terminal package installed for use with VNC since xterm won't launch (see above) and xvt seems not to want to display text (though it does launch and execute commands - just invisibly, inconveniently). I installed lxterminal, which works but pulls in lots of other libs; also, I had to run apt-get update again first because there were some lib dependency libraries that gave apt-get install problems:
apt-get update
apt-get install lxterminal
This finally gave a usable terminal on the VNC remote desktop (after restarting the vnc server). Slowly but surely...

Jon

---

### Post by djpandemonium on 2009-04-10
To everyone that got theirs already: when did you order?  I placed an order on March 4th, and no sign of it yet.  I just called them.  The lady apologized, referring to unforeseen demand.  She said she'd have them ship mine Monday.

What's the performance like via VNC?  You should be able to get better graphical performance by connecting to the xwindows server on the plug from an xwindows client on your local machine.  There would be less processing overhead involved in that than VNC.

Does anyone have an SDIO wifi card to try in the thing?  Something like this could be useful if there are drivers:
[http://tinyurl.com/dbcw2j](http://tinyurl.com/dbcw2j)

---

### Post by cbxbiker61 on 2009-04-10
I just ran a read/write test on my SheevaPlug to an 2Gig OCZ 150X SD card.  The bad news is that it's not very fast writing (~700K/sec).  The good news is that it's acceptably fast for reading (~9.6M/sec).  The actual numbers might be a little slower due to caching.

root@debian:/tmp# cat TestXferWrite.sh
#! /bin/bash

((meg = 1024*1024))
dd if=/dev/zero of=/mnt/sdcard/test.out bs=1024 count=$meg
sync

root@debian:/tmp# cat TestXferWrite.sh
#! /bin/bash

((meg = 1024*1024))
dd if=/dev/zero of=/mnt/sdcard/test.out bs=1024 count=$meg
sync
root@debian:/tmp# cat TestXferRead.sh
#! /bin/bash

((meg = 1024*1024))
dd if=/mnt/sdcard/test.out of=/dev/null bs=1024 count=$meg
sync

root@debian:/tmp# ./TestXferWrite.sh
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 1486.38 s, 722 kB/s
root@debian:/tmp# ./TestXferRead.sh
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 111.928 s, 9.6 MB/s

---

### Post by cbxbiker61 on 2009-04-10
Following up my test of read/write performance on SD here's the same test(more flexible scripts) using 16 Gig Patriot XPorter XT USB sticks.  Here the read/write performance is VERY good (~22M/sec write, ~32M/sec read).

cat TestXferWrite.sh                                               
#! /bin/bash                                                                                  

if [[ $# != 1 ]]; then
        echo "usage: $0 testdirectory"
        exit 1
fi
testdirectory=$1
((meg = 1024*1024))
dd if=/dev/zero of=$testdirectory/test.out bs=1024 count=$meg
sync

cat TestXferRead.sh
#! /bin/bash

if [[ $# != 1 ]]; then
        echo "usage: $0 testdirectory"
        exit 1
fi
testdirectory=$1
((meg = 1024*1024))
dd if=$testdirectory/test.out of=/dev/null bs=1024 count=$meg
sync

root@debian:/tmp# ./TestXferWrite.sh /mnt/usbstick
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 48.3956 s, 22.2 MB/s

root@debian:/tmp# ./TestXferRead.sh /mnt/usbstick
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 33.577 s, 32.0 MB/s

---

### Post by egrep on 2009-04-10
I will be trying wireless tonight so I will let all know. Now that I think about it, wired connection would have been a ton easier to set up. Gotta be able to route through it to give it that extra selling point.

Found a "ports" page for Debian's port to the ARM processor. They have mailing lists that might be useful to ask questions to. Might save a bit 'o trial and error. Maybe everyone hear knows the site already :-)

[http://www.debian.org/ports/arm/](http://www.debian.org/ports/arm/)
Debian GNU/Linux on ARM
...
# orion5x: we support Marvell's new Orion platform and we have specific support for a number of devices, including the QNAP Turbo Station (TS-109, TS-209, TS-409) and HP mv2120.

---

### Post by egrep on 2009-04-10
Here are some notes on things I edited/changed to secure the server as much as I know how to and get it ready to put on the net. Use what makes sense and let me know of any glaring errors.

o uncomment #  %sudo group in visudo to enable group sudo
o change (NOPASSWD) to (ALL) in visudo so that sudo requires password - security
o add users to the sudo group in /etc/group
o edit /etc/network/insterfaces to make IP static
auto eth0
iface eth0 inet static
address 75.146.60.202
netmask 255.255.255.248
gateway 75.146.60.206

o set root password
o in /etc/sshd_config edit PermitRootLogin - security
#PermitRootLogin yes
PermitRootLogin no

o edit /etc/hosts.deny and block sshd - security
All:All

o edit /etc/hosts.allow and add friendly ip addys to the sshd daemon
sshd:75.146.60.201, etc

o edit /etc/hosts
75.146.60.202 greenmachine.igroklinux.com greenmachine

o add the tcp_timeout_time = 60 to the end of /etc/rc.local - keep ssh alive over the internet (change this to 60 if idle connections timeout after 5 minutes or so)
echo 60 > /proc/sys/net/ipv4/tcp_keepalive_time

o edit /etc/resolv.conf to change/add nameservers
domain pirk.net
search pirk.net
#nameserver 127.0.0.1
nameserver 75.146.60.201
nameserver 68.183.140.225
nameserver 66.218.33.210

o set the date
date MMDDhhmm[CCYY][.ss]
o set the timezone
vi /etc/timezone - does not work as others have pointed out.

---

### Post by jsevy on 2009-04-10
Bit of a PIA, but the standard X apps (xterm, etc.) now work - but to do this I had to build the libXt library from source and replace the existing one. Hopefully this will be fixed in the standard Ubuntu package feed, but until then this works:

modify /etc/apt/sources.list to include the source repositories: add the line
deb-src [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty main restricted universe multiverse

update apt so it knows about the source stuff:
apt-get update

get basic build tools and headers
apt-get install build-essential

get headers for other X library stuff that libXt references
apt-get install xorg-dev

get source for libXt; this will be downloaded to the current directory
apt-get source libxt

untar the libXt source
tar xvfz libxt_1.0.5.orig.tar.gz

cd into the libxt_1.0.5 directory, configure, and build
cd libxt_1.0.5
./configure
make

copy the newly build library to the system location - but first save the old one in case something goes wrong
mv /usr/lib/libXt.so.6.0.0 /usr/lib/libXt.so.6.0.0.bak
cp src/.libs/libXt.so.6.0.0  /usr/lib/libXt.so.6.0.0 
(In place of the "cp" line you could just do   
make install
but I wanted to have control over exactly what went where...)

The X apps now start correctly using the new libXt library (don't even have to restart the VNC server, though that doesn't hurt). Hope the standard libXt gets fixed soon in the Ubuntu package repository!

Jon

---

### Post by jsevy on 2009-04-11
Oh, as a last step for the libXt fix, you should make sure the links in /usr/lib point to the new libXt library:
cd /usr/lib
rm libXt.so
rm libXt.so.6
ln -s /usr/libXt.so.6.0.0 libXt.so.6
ln -s /usr/libXt.so.6.0.0 libXt.so
Interestingly, when I did the moving and copy of the old and new libs, one of the links was still pointing to the old lib and that caused some of the X apps to still fail while others worked.

Jon

---

### Post by Irregular Joe on 2009-04-11
Thanks for the pointers, folks!  Great stuff!

I am having trouble with my /etc/resolv.conf getting reset at each boot. The parameters are getting saved incorrectly, setting my nameserver to 127.0.0.1 instead of the values my other Ubuntu (hardy) installations get from my router.  I can change it manually, and they take until the next boot.

Thanks in advance.  Ideas are welcome.

---

### Post by jdonth on 2009-04-11
The SheevaPlug is my first foray into embedded computing and I have a question.

When I make a change to the Ubuntu filesystem and then reboot, the changes "survive" a power off/reboot.

If the file system is being loaded from a .jffs2 image, how are the changes saved? Is an updated .jffs2 image saved?

Any education on this would be appreciated.

---

### Post by Irregular Joe on 2009-04-11
> **jdonth said:**
> 
When I make a change to the Ubuntu filesystem and then reboot, the changes "survive" a power off/reboot.

If the file system is being loaded from a .jffs2 image, how are the changes saved? Is an updated .jffs2 image saved?


The internal storage is on embedded flash memory, much like an embedded version of the card from your digital camera.  JFFS mounts that as a Unix filesystem.  Any changes you make will be saved on the flash memory, via JFFS.  Think of it is a 512M disk drive, since that is exactly how it behaves.

Let us know if you need additional details.

---

### Post by jdonth on 2009-04-11
> **Irregular Joe said:**
> The internal storage is on embedded flash memory, much like an embedded version of the card from your digital camera.  JFFS mounts that as a Unix filesystem.  Any changes you make will be saved on the flash memory, via JFFS.  Think of it is a 512M disk drive, since that is exactly how it behaves.

Let us know if you need additional details.

Thank you.

To be sure I understand you...
If I update the filesystem with the latest updates and add a package or two via apt-get, I could then reboot into u-boot and copy the (revised) jffs2 image from the NAND flash and copy the image in other SheevaPlug devices rather than having to manually update every SheevaPlug box. Is that correct?

---

### Post by Irregular Joe on 2009-04-11
> **jdonth said:**
> Thank you.

To be sure I understand you...
If I update the filesystem with the latest updates and add a package or two via apt-get, I could then reboot into u-boot and copy the (revised) jffs2 image from the NAND flash and copy the image in other SheevaPlug devices rather than having to manually update every SheevaPlug box. Is that correct?

That is correct.

However, from some of the comments here (including my own) there seem to be some files that get overwritten.  I've also created the archive directory for apt-get several times now.  Not sure why these are the only files that are causing me problems, as I have created additional userids, installed and configured other software, and these continue to work without issue.

---

### Post by pmalmsten on 2009-04-11
> **Irregular Joe said:**
> That is correct.

However, from some of the comments here (including my own) there seem to be some files that get overwritten.  I've also created the archive directory for apt-get several times now.  Not sure why these are the only files that are causing me problems, as I have created additional userids, installed and configured other software, and these continue to work without issue.


A quick look at the output of df -l might point you in the right direction:

```
paul@debian:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                  519168    248284    270884  48% /
tmpfs                   257816         0    257816   0% /lib/init/rw
varrun                  257816        44    257772   1% /var/run
varlock                 257816         0    257816   0% /var/lock
udev                    257816         4    257812   1% /dev
tmpfs                   257816         0    257816   0% /dev/shm
tmpfs                   257816     33484    224332  13% /var/cache/apt
```

I also thought it was odd that the /archives/partial path needed to be recreated after each restart. After taking a look at the above output, it looks like /var/cache/apt is mounted on tmpfs, which is most likely a RAM filesystem. That would explain why it is blown away after every shutdown.

Perhaps a ```
mkdir -p /var/cache/apt/archives/partial 
``` placed in /etc/rc.local to run at boot would cover up the annoyance.

~Paul Malmsten

---

### Post by tmessick on 2009-04-12
> **Irregular Joe said:**
> Thanks for the pointers, folks!  Great stuff!

I am having trouble with my /etc/resolv.conf getting reset at each boot. The parameters are getting saved incorrectly, setting my nameserver to 127.0.0.1 instead of the values my other Ubuntu (hardy) installations get from my router.  I can change it manually, and they take until the next boot.

Thanks in advance.  Ideas are welcome.


Edit file /etc/dhcp3/dhclient.conf and comment out this line

supersede domain-name-servers 127.0.0.1;

This will allow your DHCP server to provide name server info.

A better solution is apt-get update and then apt-get upgrade
--
tom

---

### Post by dieseloreo on 2009-04-12
recieved mine last week, and i have been working on moving the file system to the SD card, and crashed the box :)

2 hints on returning the box to factory.

As long as you havent deleted /dev/mtd0 which holds u-boot.

use instuctions and a second linux box and to boot from nfs.

use nandwrite to rewrite mtd1 and mtd2 and your golden :)

Im researching setting mmcblk0p1 as the boot device :)

---

### Post by Irregular Joe on 2009-04-12
Kudos to Paul and Tom!  Those were the answers I was needing.  The directory being in RAM makes sense now, and it's been answered so we know that most stuff won't disappear.  That mkdir line is already in the /etc/rc.local, but after the two 'insmod' lines that fail... moved things around a bit:
[INDENT]...
# By default this script does nothing.
mkdir -p /var/cache/apt/archives/partial
# Don't know what this is...
#/root/discoverd
cd /
#Get the date
/usr/sbin/ntpdate-debian
#Comment these out since I already set the date
#./demo.sh
#date 012618002009
#hwclock -w
# These used to fail...
insmod /boot/fat.ko
insmod /boot/vfat.ko[/INDENT]


In my haste, I did the 'apt-get update' but forgot 'apt-get upgrade' to apply the fixes.  There's a new dhcp3 package that makes one change beyond Tom's edits, so that should work automatically after the update.

Also, I noticed that the tzdata package has been updated, and the 'dpkg-reconfigure tzdata' now holds the settings after a reboot.  Another set of problems solved (gotta love the open source community for fixing these for us).

For the ntpdate issue, it was still not connecting to a server (unless I listed the ntp servers on the command line).  Editing the /etc/ntp.conf file (new or empty in the default install) should make it look something like this:

[INDENT]# NTP configuration file

#driftfile sets the name of a file to be created and used for
#          statistics to gain accuracy
driftfile /var/lib/ntp/ntp.drift

#server sets the name of the NTP server to contact.
#       using a few entries helps improve accuracy
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org
[/INDENT]

Still had the error, but read that 'ntpdate-debian' command should be used instead.  This works great.  I added it to an hourly cron to keep things in sync.

This solves most, if not all, of the issues I've seen here so far.  Group effort is great!

-- Joe

---

### Post by axMan5389 on 2009-04-12
> **dieseloreo said:**
> recieved mine last week, and i have been working on moving the file system to the SD card, and crashed the box :)

2 hints on returning the box to factory.

As long as you havent deleted /dev/mtd0 which holds u-boot.

use instuctions and a second linux box and to boot from nfs.

use nandwrite to rewrite mtd1 and mtd2 and your golden :)

Im researching setting mmcblk0p1 as the boot device :)


I'm in similar situation, but not golden yet. :(
After 3 days of fighting, I can flash uImage and the jffs2 filesys.  Plug will boot - once.  The 2nd time cold boot, with no changes to anything, it complains of Bad Data CRC for the uncompressed kernel image (uImage) and boot fails.

I'm not quite sure what the problem is.  At first I thought it was a bad block in /dev/mtd2 - so I resized that partition, and got it to boot - once.

Now I suspect there is something weird with flash_eraseall, or possibly with nandwrite.  Or maybe my approach.  ???

I've read a million google results, deep into the bowels of EABI, U-Boot, and MTD.  Most of that stuff is way beyond my skill level.

Currently going to attempt to hexdump from the partitions, to try and see if the badblock info is correct, or if it is being written or changed after flash_eraseall and nandwrite.  I can't see any reason why the CRC would be bad, but I admit to being embedded system n00b.

Any suggestions, url's or faq's would be appreciated.

---

### Post by jdkullmann on 2009-04-12
I've had mine for a few days and it's up and running, I can ssh in and apache works. Amazing.

I'd like to try reinstalling the/an OS on it but I'm a little afraid of bricking it.  From reading the docs I _think_ I can access JTAG over the mini-USB socket, but, I don't have a windows machine (just linux and OS X) nor can I understand what I need in additional hardware to do this.

I recently retired after 20+ years at Apple developing the OS X kernel so I don't need kernel help :) , just pointers on hardware for JTAG for this thing and pointers on s/w on the remote linux machine.

This thing has real potential.

Also, I have a Kill-A-Watt and as soon as I can find it I'm going to measure the actual power this things uses. It has to be tiny.

---

### Post by mips on 2009-04-12
> **jdkullmann said:**
> 
Also, I have a Kill-A-Watt and as soon as I can find it I'm going to measure the actual power this things uses. It has to be tiny.

At full load it's probably no more than 2W. The version of the chip clocked at 2GHz only consumes 2W.

---

### Post by egrep on 2009-04-12
> **pmalmsten said:**
> 
I also thought it was odd that the /archives/partial path needed to be recreated after each restart. After taking a look at the above output, it looks like /var/cache/apt is mounted on tmpfs, which is most likely a RAM filesystem. That would explain why it is blown away after every shutdown.

Perhaps a ```
mkdir -p /var/cache/apt/archives/partial 
``` placed in /etc/rc.local to run at boot would cover up the annoyance.

~Paul Malmsten

Once I sat down, looked there then and added this to rc.local, I realized this is the perfect thing to do. This is all temp data used to hold code while you are updating. Just like Solaris, /tmp et al get deleted on reboot to clean up the temp filesystems. They just did not think about re-creating the paths. Cleans up in case you forget and saves on flash disk space.

---

### Post by Blazer0x on 2009-04-12
If anyone is interested, I posted pictures on my blog when I first received my unit: [http://www.the-ownage.com/?p=830](http://www.the-ownage.com/?p=830)

I am currently having issues with mine, and GlobalScale has thusfar ignored my support request emails.

My issues started when I noticed that upon bootup, the boot partition was reporting lots of bad blocks, both seen on the console at boot-time and can also see in "dmesg". Now I know that bad blocks on NAND flash are not unheard of, and that in fact over time more and more blocks go bad and they are automatically marked bad, but I think its not right to have 20 bad blocks right out of the box. Seeing all the errors is annoying.

So, I had the dumb idea of using the "nandtest" binary on the partition in hopes that it would somehow clear the bad blocks or remap them elsewhere. Well it turns out it is a destructive test, so my root partition was erased. 

No problem, I think, just use nandwrite and write the image back onto it....nope! Somehow my root partition is slightly too small for the image to fit!

So now I am stuck on booting it via NFS until I can figure out how to resize mtd paritions. Personally, due to the fact that I have been able to get zero dev work done due to dealing with this, and all the bad blocks, I would prefer an exchange for a new unit, but so far GlobalScale has not acknowledged any of the support questions I submitted, and it has been well over a week.

---

### Post by djpandemonium on 2009-04-13
Call their "Contact Us" number on their site.  I did, hit 0, and was connected with a helpful lady who could handle order processing and the like.  I'm sure she wouldn't be the one to talk to for tech support, but she could forward your call to the right person, or perhaps set you up with a replacement.

---

### Post by cbxbiker61 on 2009-04-13
You might want to move some of this discussion over to a forum dedicated to the SheevaPlug.  Rather than having one long jumbled discussion the topics would be a little easier to follow.  Besides the forums on plugcomputer don't seem to be seeded very well on the search engines and it's a site which you may have overlooked.

[http://www.plugcomputer.org/plugforum/]("http://www.plugcomputer.org/plugforum/")

---

### Post by jdonth on 2009-04-13
I'm getting ready to buy an SD card for my SheevaPlug and must confess I don't know what kind of card to buy.

Like the three bears fairy tale, I tried a Compact Flash drive from my digital camera and it was too big. I tried the SD card from my MP3 player and it was too small. I need one that is "just right".

Any help? (Physical size, speed, recommendations, etc.)
~Joe Donth

---

### Post by jdonth on 2009-04-13
I *think* I have the correct SD card but I can not get the system to see it.

Any help on mounting the SD card?
~Joe Donth

---

### Post by mprince on 2009-04-13
> **jdonth said:**
> I *think* I have the correct SD card but I can not get the system to see it.

Any help on mounting the SD card?
~Joe Donth


See here:

[http://openplug.org/plugforum/index.php?topic=22.0](http://openplug.org/plugforum/index.php?topic=22.0)

---

### Post by jdonth on 2009-04-13
> **mprince said:**
> See here:

[http://openplug.org/plugforum/index.php?topic=22.0](http://openplug.org/plugforum/index.php?topic=22.0)

Thanks! Exactly what I needed.

---

### Post by mkohanim on 2009-04-14
Hi all,

I am looking for Sheeva/Ubuntu gurus to help us at Universal Devices, Inc. ([http://www.universal-devices.com](http://www.universal-devices.com)). If you are interested, please send me your résumé.

With kind regards,
Michel Kohanim

---

### Post by dcherryholmes on 2009-04-14
Has anyone had any luck with removing the wall power adapter so that the cord can be used?  In the Reference Design doc included in the documentation package it says:

"To remove the A/C plug, the suggested method is to hold the SheevaPlug with both hands, with the A/C plug facing
you and away from you. Use both your thumbs to press the plastic just below the prongs and push down and away."

However, I've put about as much pressure on the thing as I feel safe doing, and it still won't come out.

---

### Post by dcherryholmes on 2009-04-14
Another question:  has anybody figured out the correct packages to install in order to have the sheeva run as an NFS server?  ntfs-3g installs, but when I try to modify /etc/exports and run /etc/init.d/nfs-kernel-server restart, I get the following output:

FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
 * Not starting NFS kernel daemon: no support in current kernel.

It seems odd to me that, given the nature of the device, it would not be set up to serve files over NFS.  I could try samba next, but I'd rather use NFS.  Last resort would be to install sshfs on the client side, but I haven't tried that yet, either.

---

### Post by jojo1224 on 2009-04-14
Has anyone open'd there SheevaPlug DevKit up? I would like to see what it looks like inside.

---

### Post by AlanPorter on 2009-04-14
> **jojo1224 said:**
> Has anyone open'd there SheevaPlug DevKit up? I would like to see what it looks like inside.

No... I left mine in the box.  It *is* a nice box.

Alan

---

### Post by AlanPorter on 2009-04-14
Inside photos...

[http://www.linuxdevices.com/news/NS2356496718.html](http://www.linuxdevices.com/news/NS2356496718.html)
[http://www.flickr.com/photos/h_u_p/3358652703/](http://www.flickr.com/photos/h_u_p/3358652703/)
[http://www.cyrius.com/debian/kirkwood/sheevaplug/gallery.html](http://www.cyrius.com/debian/kirkwood/sheevaplug/gallery.html)

Alan

---

### Post by dcherryholmes on 2009-04-14
To sort of follow up on my last two posts:

I did get the power plug cover off.  Took a lot of pulling, but it eventually got there.

I did not solve my nfs-kernel-server problem, but I noted that the sheeva comes with samba pre-installed, so I just used that.  After supplying boxee with my username and password, it added the samba share as a source.  Incidentally, video ripped to 720p is playing nicely on boxee over the network storage attached to the sheeva.

---

### Post by bfmorgan on 2009-04-14
I got the plug removed with much force. First, using both thumbs, press down near the end the the arrow (in between the plug flanges). This should at least move the plug about 1mm. Then, using a flat head screw driver, start wedging the plug until it comes loose. It will travel about 1 cm away from the body of the sheevaplug before the AC plug clears.

Hope this helps,

---

### Post by lyzby on 2009-04-14
I'd like to install Lua 5.1.4 on the plug.  "apt-get install lua" asks me to choose between two versions--lua40 and lua50 (specifically, 5.0.3-3).  I want the latest--lua 5.1.4.  I know I can in theory build it, but Lua 5.1.4 is available on other arm machines, e.g., the NSLU2.   How do the apt-get repositories get built and what is the process for getting something into the repository cycle?

SOLVED: apt-get install lua5.1

I found this here: [http://packages.ubuntu.com/source/intrepid/interpreters/](http://packages.ubuntu.com/source/intrepid/interpreters/)

---

### Post by lyzby on 2009-04-14
I've seen references to the SheevaPlug FAQ.  Where is that located?

---

### Post by jdonth on 2009-04-15
> **jdkullmann said:**
> 
I'd like to try reinstalling the/an OS on it but I'm a little afraid of bricking it.  From reading the docs I _think_ I can access JTAG over the mini-USB socket, but, I don't have a windows machine (just linux and OS X) nor can I understand what I need in additional hardware to do this...

I, too, would like to reinstall the original jffs2 image but am not sure how to do this and don't want to make a brick.

Can it be done from Windows via TeraTerm?

Anyone have instructions? The Marvell docs are confusing for me.
~Joe Donth

---

### Post by jdonth on 2009-04-15
I just visited the Marvell web site and the "File System" (*[http://www.marvell.com/files/products/embedded_processors/developer/kirkwood/SheevaPlug_FileSystem.zip](http://www.marvell.com/files/products/embedded_processors/developer/kirkwood/SheevaPlug_FileSystem.zip)*) file is now listed at 538K.

The previous version I downloaded was 133M. Anyone know what's happening?

Also there is a new file "USB Recovery". It does not contain any documentation - any idea what it is?

Finally, have any of the other files changed? I can't tell by the file names.

Thanks,
~Joe Donth

---

### Post by lyzby on 2009-04-15
I have an external hard drive set up on the Sheevaplug, mounted as /media/D.  How do I set that up so that an apt-get download goes to that drive instead of to the internal flash?

---

### Post by lyzby on 2009-04-15
The uvc video drivers for web cams are reported to be included in Ubuntu, but appear not to be available on the Sheevaplug.  I have not been able to find anything in the repositories which seems appropriate.  How does one load the modules which will recognize web cams.  lsusb shows: 

Bus 001 Device 003: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks

"ls /dev/video*" shows nothing, as does "dmesg | grep video".

---

### Post by leef on 2009-04-15
> **lyzby said:**
> I have an external hard drive set up on the Sheevaplug, mounted as /media/D.  How do I set that up so that an apt-get download goes to that drive instead of to the internal flash?

mount it at "/var/cache/apt/archives" instead? I'm really looking forward to getting one of these to bad about the 4 week delay.

---

### Post by smartboyathome on 2009-04-15
> **lyzby said:**
> The uvc video drivers for web cams are reported to be included in Ubuntu, but appear not to be available on the Sheevaplug.  I have not been able to find anything in the repositories which seems appropriate.  How does one load the modules which will recognize web cams.  lsusb shows: 

Bus 001 Device 003: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks

"ls /dev/video*" shows nothing, as does "dmesg | grep video".

Sounds like you need to recompile the kernel to include those modules. It will be harder since you have to set up a cross compiler in order to compile it on your x86(_64) computer, but it can be done.

---

### Post by caveman978 on 2009-04-15
Has anyone successfully installed mysql?
My issue seems to be with the password set by Ubuntu's default install.  Also I have tried every method to clear the root password.

I posted all the steps I've done in the openplug forum:
[http://openplug.org/plugforum/index.php?topic=70.0](http://openplug.org/plugforum/index.php?topic=70.0)

---

### Post by lyzby on 2009-04-15
The forum here has threaded discussions--perhaps it's time to leave this useful single thread.

[http://openplug.org/plugforum/index.php](http://openplug.org/plugforum/index.php)

The openplug wiki starts here

[http://www.openplug.org/plugwiki/index.php/Main_Page](http://www.openplug.org/plugwiki/index.php/Main_Page)

The wiki FAQ is here

[http://www.openplug.org/plugwiki/index.php/Frequently_Asked_Questions](http://www.openplug.org/plugwiki/index.php/Frequently_Asked_Questions)

---

### Post by sergvp on 2009-04-17
I am new to this forum, and new to linux. I'm working with  SSH and trying get lighttpd.
 apt-get install lighttpd
 apt-get install php5-cgi

 I can't start to edit /etc/lighttpd/lighttpd.conf. 

root@debian:~# cd /etc/lighttpd
-bash: cd: /etc/lighttpd: No such file or directory

Where is it?
The server looks like work. The FireFox showed  "It works!"page

---

### Post by puppetboy on 2009-04-18
Those of you interested in the SheevaPlug may want to contribute to this Forum:
[http://sheevaplug.ownforum.org](http://sheevaplug.ownforum.org)

---

### Post by k3io on 2009-04-22
> **lastword said:**
>  ... I did manage to connect to the unit via mini-USB and windows xp hyperterminal with the default username and password for SheevaPlug. ... 

Maybe I'm blind, but I cannot find the defaults in any of their documentation. Can someone help me?

Thanks, Tom

---

### Post by jdonth on 2009-04-22
> **k3io said:**
> Maybe I'm blind, but I cannot find the defaults in any of their documentation. Can someone help me?

Thanks, Tom

Tom,

Your request is a bit vague. What help do you need? What defaults are you looking for? A few more details and I'm sure this group can help.
~Joe

---

### Post by djpandemonium on 2009-04-22
If it's the default login/password that you're looking for, then it's root/nosoup4u.

It's actually buried in the middle of the documentation for "Writing Jaunty Filesystem on the NAND flash."

---

### Post by DocTauri on 2009-04-25
> **dcherryholmes said:**
> modify /etc/exports and run /etc/init.d/nfs-kernel-server restart, I get the following output:

FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
 * Not starting NFS kernel daemon: no support in current kernel.

Anyone ever figure this out?  I just got my plug, which apparently is coming w/debian now, but I have the same problem.

Thanks,
Doc

---

### Post by pushbx on 2009-04-28
The fatal error you're talking about is because the sheeva doesn't have the modules.dep created in the filesystem.  To fix that do a 

depmod -ae

But I don't think that alone will fix your problem.  I don't think the nfs modules are compiled into the kernel.  So you may have to compile it yourself.  I have a guide to recompiling kernels here:

[http://www.computingplugs.com/index.php/Building_a_custom_kernel](http://www.computingplugs.com/index.php/Building_a_custom_kernel)

I also have performance and power usage data if you're interested

[http://www.computingplugs.com/index.php/SheevaPlug_Performance](http://www.computingplugs.com/index.php/SheevaPlug_Performance)

---

### Post by whosmatt on 2009-04-29
Anybody have an update on current delivery wait times?  I ordered mine 11 days ago and just wondering if I might be pleasantly surprised to get it before the stated 4 weeks is over.

thanks

matt

---

### Post by smbtol on 2009-04-29
I saw that there is also Pogoplug, a branded version of the SheevaPlug. I am not sure how much they changed the software. But the hardware should be the same:
[http://www.pogoplug.com/](http://www.pogoplug.com/)
Did anybody buy the Pogoplug?

Pogoplug looks like it is backordered too. :(

---

### Post by DocTauri on 2009-04-29
Thanks for the info pushbx!  I'll check it out.

Doc

---

### Post by hojnikb on 2009-05-01
> **smbtol said:**
> I saw that there is also Pogoplug, a branded version of the SheevaPlug. I am not sure how much they changed the software. But the hardware should be the same:
[http://www.pogoplug.com/](http://www.pogoplug.com/)
Did anybody buy the Pogoplug?

Pogoplug looks like it is backordered too. :(
are there any other branded versions except pogoplug?
Couse i think i'll buy one of theese.It  just have  to come to europe,soo shipping won't be soo expensive and long.

---

### Post by tschaboo on 2009-05-01
> **hojnikb said:**
> are there any other branded versions except pogoplug?
Couse i think i'll buy one of theese.I just the come to europe,soo shipping won't be soo expensive and long.

Since the pogoplug is an end-user product I guess that it's missing the debug board. But you really do want that. So i'd order the developer kit.

---

### Post by hojnikb on 2009-05-01
> **tschaboo said:**
> Since the pogoplug is an end-user product I guess that it's missing the debug board. But you really do want that. So i'd order the developer kit.
I'll see.If it doesn't have a debug board it's useless then (at least for me).

---

### Post by hojnikb on 2009-05-01
I read somewhere:is it true that the ARM processor doesn't have a hardware flouting point? In which apps is that a big disadvantade?

---

### Post by hojnikb on 2009-05-01
..and one more question:What's is the preformace in bittorrent applications? can it handle for example 10/10mbit of bittorrent traffic or is the cpu too slow ?

---

### Post by tschaboo on 2009-05-01
> **hojnikb said:**
> I read somewhere:is it true that the ARM processor doesn't have a hardware flouting point? In which apps is that a big disadvantade?

I think that there are ARM-processors with HW-FP but it's true that the Sheeva doesn't have one. For most server applications this shouldn't matter much. Of course it doesn't make sense to run stuff like seti@home.

> **hojnikb said:**
> ..and one more question:What's is the preformace in bittorrent applications? can it handle for example 10/10mbit of bittorrent traffic or is the cpu too slow ?

I don't have one yet, but based on the reports of others i'd say it should work fine if you use lightweight clients like rtorrent or transmission. You might want to look at those benchmarks: [http://www.computingplugs.com/index.php/SheevaPlug_Performance](http://www.computingplugs.com/index.php/SheevaPlug_Performance)

---

### Post by jdkullmann on 2009-05-01
> **tschaboo said:**
> Since the pogoplug is an end-user product I guess that it's missing the debug board. But you really do want that. So i'd order the developer kit.

I bought and received the development kit but there was no separate debug board. Is that board inside the box? Is that the thing that can drive JTAG out the mini-usb or one of the other connectors?

---

### Post by tschaboo on 2009-05-01
> **jdkullmann said:**
> I bought and received the development kit but there was no separate debug board. Is that board inside the box? Is that the thing that can drive JTAG out the mini-usb or one of the other connectors?

Yes, the board is inside the SheevaPlug and providing the Mini-USB and the SD-Card-Slot. The Mini-USB provides a serial console and JTAG.

---

### Post by jdkullmann on 2009-05-02
> **tschaboo said:**
> Yes, the board is inside the SheevaPlug and providing the Mini-USB and the SD-Card-Slot. The Mini-USB provides a serial console and JTAG.

That's what I thought. However, no matter what I do I cannot get any serial output to work between it and my OS X iMac. I have all the serial settings right.  Beyond connecting them together and restarting the plug is there some other magic I have to do to get serial working? thanks.

---

### Post by tschaboo on 2009-05-03
> **jdkullmann said:**
> That's what I thought. However, no matter what I do I cannot get any serial output to work between it and my OS X iMac. I have all the serial settings right.  Beyond connecting them together and restarting the plug is there some other magic I have to do to get serial working? thanks.

Try that: [http://openplug.org/plugforum/index.php?topic=34.0](http://openplug.org/plugforum/index.php?topic=34.0)

---

### Post by jdkullmann on 2009-05-03
> **tschaboo said:**
> Try that: [http://openplug.org/plugforum/index.php?topic=34.0](http://openplug.org/plugforum/index.php?topic=34.0)

I discovered that thread earlier today and it does in fact work - I now have serial to my Mac. Thanks.

---

### Post by wzzrd on 2009-05-11
Has anyone that actually owns a Sheevaplug ever tried to run something like the Firefly media server on it? That would be its main purpose for me.

Is it powerful enough to do that?

---

### Post by pushbx on 2009-05-11
for those interested, I was able to compile mythtv-0.21 on the sheeva plug.  Instructions and the patch file you'll need are here:

[http://computingplugs.com/index.php/Compiling_Mythtv-0.21_on_the_Sheeva_Plug](http://computingplugs.com/index.php/Compiling_Mythtv-0.21_on_the_Sheeva_Plug)

---

### Post by Kareeser on 2009-05-25
Hm.

Y'know what's scary about this is that this plug, for a measly $100 + shipping, is more powerful and has more memory than my current server, which probably draws 5x more power.

I want!

---

### Post by whosmatt on 2009-05-25
> **Kareeser said:**
> Hm.

Y'know what's scary about this is that this plug, for a measly $100 + shipping, is more powerful and has more memory than my current server, which probably draws 5x more power.

I want!

good luck getting one. i ordered mine 5 weeks ago and still don't have it.

---

### Post by MedianMajik on 2009-05-26
I'm interested in one as a *very* remote backup server/r-torrent/web hosting w/ a 750gb Hard drive on a 100mb connection.  Would the 100mb connection and USB 2.0 still be sufficient for my needs?

At the mimimum I'm looking for a roll-your-own Dropbox for file and document synching that would also receive larger backups from 4-8gb SSD's once a day.  The device would also seed as many torrents as possible via a webui and host OpenGoo office suite as an alternative to Google Docs.

---

### Post by Kareeser on 2009-05-26
> **whosmatt said:**
> good luck getting one. i ordered mine 5 weeks ago and still don't have it.

I'm sure it'll come... I doubt it's a scam, unless everybody who posted in this thread is in on it :)

Call them back?

This would make a very nice christmas present for myself...

---

### Post by ebp on 2009-06-04
Any word on when the european version will come?

---

### Post by tschaboo on 2009-06-04
> **ebp said:**
> Any word on when the european version will come?

There probably won't be a european version of the development kit. That's no problem though since you can remove the US-connector and attach a standard 2-pole power cable. The power supply tolerates 230V.

---

### Post by ebp on 2009-06-04
> **tschaboo said:**
> There probably won't be a european version of the development kit. That's no problem though since you can remove the US-connector and attach a standard 2-pole power cable. The power supply tolerates 230V.

Ok have heard of that but wasn't shure it was true. Do you know if they will sell the same version in europe? It just makes it easier if it brakes within the warrenty period.

---

### Post by tschaboo on 2009-06-04
> **ebp said:**
> Ok have heard of that but wasn't shure it was true.
I will get mine next week, then i'll know for sure. ;)

> **ebp said:**
>  Do you know if they will sell the same version in europe? It just makes it easier if it brakes within the warrenty period.
Doesn't look like that's going to happen. Marvell chose GlobalScale for production and distribution of the dev-kit and they are only sending from the US. I didn't hear of any plans to find a european distributor but i'm not the best-informed person either.

---

### Post by AlanPorter on 2009-06-04
Again, you can use the SheevaPlug in Europe.  You just can't hang it directly from the wall outlet, because it's missing the little hook-on AC adaptor to make it fit properly into a European electrical outlet.

If you pop off the built-in US plug and then use a standard "figure 8" power cord, it will work fine on 220-240V.  These power cords are used everywhere, and should be available for a couple of dollars/euros anywhere.

I live in the US, and I use a "figure 8" power cord (there is one included in the kit) because I want to lay the plug down on a table instead of letting it dangle from the wall.

If what I am saying does not make sense, send me a private message and I'll send you some pictures.

Don't let a $1 power cable stop you from ordering a SheevaPlug.

Alan Porter

---

### Post by ebp on 2009-06-04
> **AlanPorter said:**
> Again, you can use the SheevaPlug in Europe.  You just can't hang it directly from the wall outlet, because it's missing the little hook-on AC adaptor to make it fit properly into a European electrical outlet.

If you pop off the built-in US plug and then use a standard "figure 8" power cord, it will work fine on 220-240V.  These power cords are used everywhere, and should be available for a couple of dollars/euros anywhere.

I live in the US, and I use a "figure 8" power cord (there is one included in the kit) because I want to lay the plug down on a table instead of letting it dangle from the wall.

If what I am saying does not make sense, send me a private message and I'll send you some pictures.

Don't let a $1 power cable stop you from ordering a SheevaPlug.

Alan Porter

It's not the part with the powercable that's holding me off. It's about the warrenty i would like it to be as smooth as possible if it breaks.

---

### Post by AlanPorter on 2009-06-04
Well, remember that it *is* a development kit... not a fully supported consumer product.

Alan

---

### Post by ebp on 2009-06-04
> **AlanPorter said:**
> Well, remember that it *is* a development kit... not a fully supported consumer product.

Alan


Point taken, maybe i should stop whining and just buy one :P

---

### Post by tschaboo on 2009-06-05
> **ebp said:**
> It's not the part with the powercable that's holding me off. It's about the warrenty i would like it to be as smooth as possible if it breaks.

The warranty-card in my box (which i got today, :D) talks about a "30 day warranty since purchase". So that warranty is useless anyway. Also, the US-power-contacts are constructed to be taken off, you can put it back on later.

---

### Post by whosmatt on 2009-06-07
> **whosmatt said:**
> good luck getting one. i ordered mine 5 weeks ago and still don't have it.

It's here... in it via ssh, so far had to manually create /var/cache/apt/archives and subdirs to get apt working, now updating a ton of packages...  FYI i intend to use mine as a file server with a drobo connected

---

### Post by whosmatt on 2009-06-07
Please delete me, moderator.  Thanks.

---

### Post by Kareeser on 2009-06-07
> **MedianMajik said:**
> I'm interested in one as a *very* remote backup server/r-torrent/web hosting w/ a 750gb Hard drive on a 100mb connection.  Would the 100mb connection and USB 2.0 still be sufficient for my needs?

Seeing as residential internet connections don't exceed 16 Mbits (uploads are capped at 800 **k**bits here...), I think you're fine :)

I thought the Sheevaplug was Gigabit...

---

### Post by ebp on 2009-06-23
Now i've finally ordered one, but it could be a long wait :)

---

### Post by bobnielsen on 2009-06-24
> **ebp said:**
> Now i've finally ordered one, but it could be a long wait :)

I received mine last week, 31 days after ordering.  I had it up and running a server by the next day (of course I was researching it pretty heavily while waiting for the FedEx truck). :D

---

### Post by Hells_Dark on 2009-06-24
Hey european version is out :)

I still need to find 100 euros&#8230;

---

### Post by Phreaker on 2009-06-24
Where can someone buy it from Europe?

---

### Post by Hells_Dark on 2009-06-24
> **Phreaker said:**
> Where can someone buy it from Europe?

[http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit-us.aspx](http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit-us.aspx)

Here for instance.

---

### Post by Phreaker on 2009-06-24
Thanks :]

---

### Post by ebp on 2009-06-25
> **Hells_Dark said:**
> [http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit-us.aspx](http://www.globalscaletechnologies.com/p-22-sheevaplug-dev-kit-us.aspx)

Here for instance.

Isn't it just the same version, just with an european slot?

---

### Post by ebp on 2009-06-25
> **bobnielsen said:**
> I received mine last week, 31 days after ordering.  I had it up and running a server by the next day (of course I was researching it pretty heavily while waiting for the FedEx truck). :D

What are you using your's for? I'm going to use mine as a file server, torrent box, print server and ssh tunnel.

---

### Post by andyathome on 2009-06-25
I currently have a NAS - LS Pro. 

I'm thinking of replacing it with something a bit faster as I use it to download from usenet at the minute - it has no prob maxing out my line (using nzbget I can get ~1.6 MB/second) however decompressing large RAR sets - 6 / 7 gigs takes forever. Would the sheevaplug be significantly quicker?

The LS Pro utilises an ARM926EJ-Sid(wb) (ARMv5TEJ) (ARM9@400mhz) with 128 mb of ram - now i assume the Sheeva @ 1.2ghz is as fast per cycle as the ARM9 so i should see (in raw processing power) a 3x increase + the advantage of extra memory?

Will the fact it has to use USB inflict severely on the speed of decompressing large files?

Thanks, and sorry for the dumb questions. I'm not really all that familiar with ARM processors.

---

### Post by tschaboo on 2009-06-25
> **ebp said:**
> Isn't it just the same version, just with an european slot?

Yes, everything else is identical.

---

### Post by ebp on 2009-06-25
> **tschaboo said:**
> Yes, everything else is identical.

good, i was starting to worry

---

### Post by bobnielsen on 2009-06-25
I suspect it probably is.  I also suspect that the included line cord has the appropriate connector, as well (the fitted plug is easily removed, revealing a figure-8 type connector as used on many devices).

---

### Post by bobnielsen on 2009-06-25
> **ebp said:**
> What are you using your's for? I'm going to use mine as a file server, torrent box, print server and ssh tunnel.

Right now I am running the perl-based "DX Spider" node program  (ham radio means for listing frequencies where stations are operating).  I ran this on a PC (Ubuntu 8.04 LTS server) prior to getting the Sheevaplug.  I'm sure there is plenty of capability to do more, once I get a bit more familiar with it.  I compiled a 2.6.30 kernel today but haven't yet gotten up the courage to install it. :)

---

### Post by jcottier on 2009-07-10
Does this still ship with ubuntu? or is it now Debian?

---

### Post by bncplix on 2009-07-23
4 months later....it has arrived

paid for express shipping, and had a $25 extra duty fee at the door

do i have to install the images from the cd? or is it ready to go out of the box? I have a few things on it, i am just not sure if the thing on the cd is more up to date?

---

### Post by bobnielsen on 2009-07-23
> **bncplix said:**
> 4 months later....it has arrived

paid for express shipping, and had a $25 extra duty fee at the door

do i have to install the images from the cd? or is it ready to go out of the box? I have a few things on it, i am just not sure if the thing on the cd is more up to date?

It should be ready to go.  Check out [http://plugcomputer.org/plugwiki/index.php/New_Plugger_How_To](http://plugcomputer.org/plugwiki/index.php/New_Plugger_How_To)

---

### Post by srynonick on 2009-07-27
hello,

i'm wondering how i can install a new operating system on the sheevaplug? thanks!

---

### Post by AlanPorter on 2009-07-27
> **srynonick said:**
> i'm wondering how i can install a new operating system on the sheevaplug? thanks!

Just like with any Linux system, you need four things: (1) a filesystem with all the right stuff on it (2) a kernel with appropriate drivers (3) an initial RAM disk with enough drivers to get the root filesystem loaded (4) a bootloader to load the kernel and the initial RAM disk and to start the kernel running.

This means that you'll need to feel pretty comfortable in an embedded Linux environment.

(1) Something like debootstrap will get the filesystem set up with your packages.  (2) The Marvel folks included the kernel source for you.  (3) If the kernel is configured to have all of the drivers it needs to access the root filesystem COMPILED IN (and not modules), then the initial RAM disk is not needed.  (4) And Marvel includes a bootloader for you.

So that covers all four bases.  You have all you need... well, you'll also need to provide lots and lots of patience.

In short, if you have not done this before, then don't count on it being a quick-n-easy process.  And don't expect to slap Fedora or SuSE on there using the install disks.  It's WAY more involved than that.

All of your compilation will be done for an ARM target, which most likely means you'll be cross-compiling from an Intel host.

It can be done.  But just know what you're getting into before you start.

I have some notes here on how I built an embedded Linux system for an appliance company that I used to work for.  But I had the advantage of removable media (compact flash) for my bootloader and root filesystem.  And this was not cross compiled.  But you can get the idea.

[http://www.trilug.org/~porter/meetings/2008-09-11_Porter_InternetAppliance.pdf](http://www.trilug.org/~porter/meetings/2008-09-11_Porter_InternetAppliance.pdf)

My bottom-line advice... use the Ubuntu distro that comes on it.

Alan

---

### Post by ebp on 2009-08-06
> **pushbx said:**
> The fatal error you're talking about is because the sheeva doesn't have the modules.dep created in the filesystem.  To fix that do a 

depmod -ae

But I don't think that alone will fix your problem.  I don't think the nfs modules are compiled into the kernel.  So you may have to compile it yourself.  I have a guide to recompiling kernels here:

[http://www.computingplugs.com/index.php/Building_a_custom_kernel](http://www.computingplugs.com/index.php/Building_a_custom_kernel)

I also have performance and power usage data if you're interested

[http://www.computingplugs.com/index.php/SheevaPlug_Performance](http://www.computingplugs.com/index.php/SheevaPlug_Performance)


I have the same problem is it needed to compile the kernel yourself?

---

### Post by Plug PC on 2009-08-08
> **Phreaker said:**
> Where can someone buy it from Europe?
 
I spoke to the people at Globalscale Technologies, they told me that they are in talks to setup a UK distribution site. They said there was a company interested in adding value to their product and should be available in the next few weeks. Which for me is good news because we are looking at using a few of these at each of our sites - File, Print and AV, (looking at other apps as well), and at the prices they are at we can afford to have spares sitting on the shelf.

---

### Post by ebp on 2009-08-09
> **ebp said:**
> I have the same problem is it needed to compile the kernel yourself?

I used the alpha-6 installer and now it works:)

---

### Post by rajubunt on 2009-08-16
> **briankircho said:**
> I also received my SheevaPlug in the mail yesterday, and have had some success with ubuntu on it :)

First I tried to use my 8.10 desktop and the mini USB connector to get a serial console to the unit. It seems like the ftdi_sio module should work for this, but I could not get it to detect the unit and create /dev/ttyUSB0 in the standard 8.10 or 9.04 kernels.

At this point I had a windows machine lying around so I used the serial port drivers in SheevaPlug_Host_SWsupportPackageWindowsHost.zip.  This worked and I was able to see what was happening.  I expected to have a empty device and have to NFS boot from my linux machine to flash the root filesystem.  

I was a bit surprised to find ubuntu 9.04 is already flashed onto the 512MB of NAND and will bootup when you plugin the unit so you dont even need the serial console or to flash the unit.  There is an SSH server running and you can use the login from the manual: root/nosoup4u

I attached a USB hard drive, and have installed a bunch of packages (samba, nfs, apache), everything working great and its very fast for its size and (3W) power use so im excited about this so far.

Some info from the unit:
# df -h
Filesystem            Size  Used Avail Use% Mounted on
rootfs                507M  176M  332M  35% /

# uname -a
Linux kirchoff 2.6.22.18 #1 Thu Mar 19 14:46:22 IST 2009 armv5tejl GNU/Linux

# cat /proc/cpuinfo
Processor       : ARM926EJ-S rev 1 (v5l)
BogoMIPS        : 1192.75
Features        : swp half thumb fastmult edsp
CPU implementer : 0x56
CPU architecture: 5TE
CPU variant     : 0x2
CPU part        : 0x131
CPU revision    : 1
Cache type      : write-back
Cache clean     : cp15 c7 ops
Cache lockdown  : format C
Cache format    : Harvard
I size          : 16384
I assoc         : 4
I line length   : 32
I sets          : 128
D size          : 16384
D assoc         : 4
D line length   : 32
D sets          : 128


---

New to Ubuntu forums. So please go easy...

I am interested in Sheeva plug. But when I go there to purchase at Marvell it says to buy it from its patners.

Did you buy it from [www.globalscaletechnologies.com](www.globalscaletechnologies.com) or some other partner. I am looking for a sheeva plug with ubuntu installed in it so that I can go start running fast...

---

### Post by sbhattacharjee on 2009-08-28
Doesn't seem like I am getting to see /dev/ttyUSB* anything. 

lsusb shows me its connected
shivab@shivab-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 014: ID 9e88:9e8f  --> this is Sheeva-plug
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

usbview also gets its
SheevaPlug JTAGKey FT2232D B
Manufacturer: FTDI
Serial Number: FTSBOO5I
Speed: 12Mb/s (full)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 9e88
Product Id: 9e8f
Revision Number:  5.00

shivab@shivab-desktop:~$ sudo modprobe ftdi_sio vendor=0x9e88 product=0x9e8f
[sudo] password for shivab: 
shivab@shivab-desktop:~$ ls -l /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

from /var/log/syslog I get the following
Aug 28 01:32:33 shivab-desktop kernel: [ 5806.588032] usb 5-2: new full speed USB device using uhci_hcd and address 15
Aug 28 01:32:33 shivab-desktop kernel: [ 5806.797013] usb 5-2: configuration #1 chosen from 1 choice

---

### Post by sbhattacharjee on 2009-08-28
Is this in any way issues b/c of HAL?

---

### Post by bobnielsen on 2009-08-28
> **rajubunt said:**
> ---

New to Ubuntu forums. So please go easy...

I am interested in Sheeva plug. But when I go there to purchase at Marvell it says to buy it from its patners.

Did you buy it from [www.globalscaletechnologies.com](www.globalscaletechnologies.com) or some other partner. I am looking for a sheeva plug with ubuntu installed in it so that I can go start running fast...

I bought mine from there (it was the only partner at the time).  It came with Ubuntu 9.04 installed.  There is some good info on getting started on the [Plug Wiki](http://plugcomputer.org/plugwiki/index.php/Main_Page).

---

### Post by sbhattacharjee on 2009-08-31
> **sbhattacharjee said:**
> Doesn't seem like I am getting to see /dev/ttyUSB* anything. 

lsusb shows me its connected
shivab@shivab-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 014: ID 9e88:9e8f  --> this is Sheeva-plug
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

usbview also gets its
SheevaPlug JTAGKey FT2232D B
Manufacturer: FTDI
Serial Number: FTSBOO5I
Speed: 12Mb/s (full)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 9e88
Product Id: 9e8f
Revision Number:  5.00

shivab@shivab-desktop:~$ sudo modprobe ftdi_sio vendor=0x9e88 product=0x9e8f
[sudo] password for shivab: 
shivab@shivab-desktop:~$ ls -l /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

from /var/log/syslog I get the following
Aug 28 01:32:33 shivab-desktop kernel: [ 5806.588032] usb 5-2: new full speed USB device using uhci_hcd and address 15
Aug 28 01:32:33 shivab-desktop kernel: [ 5806.797013] usb 5-2: configuration #1 chosen from 1 choice

Anyone!? I am not sure where to start debugging. Is it some setup issues with how auto usb stuff is working or something else?

---

### Post by rigsby on 2009-09-08
> **sbhattacharjee said:**
> Anyone!? I am not sure where to start debugging. Is it some setup issues with how auto usb stuff is working or something else?

You're nearly there.
Once you've done ```
sudo modprobe ftdi_sio vendor=0x9e88 product=0x9e8f
```

dmesg should show you something like:

usb 2-1: Detected FT2232C
[265988.082245] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
[265988.082292] ftdi_sio 2-1:1.1: FTDI USB Serial Device converter detected
[265988.082313] usb 2-1: Detected FT2232C
[265988.082343] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB1

Unplug, or plug in the USB cable and you'll see connection or disconnection messages.

---

### Post by wafic01 on 2009-10-06
Hello 
if someone could tell me what are the differences between the sheevaplug Development kit , and PogoPlug , both have  the same architecture but the second comes in already configured for file sharing with a little space for development ? is that all ? 
Thank you in Advance

---

### Post by Crath on 2009-10-12
Sorry this is a bit late, but is there any simple tutorial somewhere to install ubuntu on one of these sheevaplgs? Maybe a self-installing image that I can put on a usb drive and boot it into the plug, so that it installs itself? I'm so lost, thanks!

---

### Post by tschaboo on 2009-10-12
> **Crath said:**
> Sorry this is a bit late, but is there any simple tutorial somewhere to install ubuntu on one of these sheevaplgs? Maybe a self-installing image that I can put on a usb drive and boot it into the plug, so that it installs itself? I'm so lost, thanks!

This should get you started: [http://plugcomputer.org/plugwiki/index.php/SheevaPlug_Installer](http://plugcomputer.org/plugwiki/index.php/SheevaPlug_Installer)

---

### Post by PrinceRiley on 2009-10-26
New User here,

First SheevaPlug almost seven months ago, now up to Rev 3. Haven't heard much going on here. Is it time to bring ourselves together and start figuring out a Ubuntu branch for this device?

Prince

---

### Post by tschaboo on 2009-10-28
> **PrinceRiley said:**
> First SheevaPlug almost seven months ago, now up to Rev 3. Haven't heard much going on here. Is it time to bring ourselves together and start figuring out a Ubuntu branch for this device?

You are just in the wrong forum. Ubuntu is the default operating system for the plug, the arm-port runs out of the box. There even is an installer for the plug, which installs the kernel, u-boot and ubuntu on the internal flash. See the link in my previous post.

---

### Post by Plug PC on 2009-10-28
WOW! Got mine today from [www.newit.co.uk]("http://www.newit.co.uk")  and i only ordered it yesterday!

One of my friends in Germay recomended them, he ordered one and sid it got to him in two days, so i thought beats Globalsales delivery times give them a try.
What a cool little box it comes in, i'm going to be playing with the plug for a while will re post when i have some more news [IMG]http://forums.hexus.net/images/smilies/smile.gif[/IMG]

---

### Post by G|N| on 2009-10-28
Is it possible to buy a sheevaplug with an european power adaptor instead of the uk version from [www.newit.co.uk?](www.newit.co.uk?)

---

### Post by Plug PC on 2009-10-28
> **G|N| said:**
> Is it possible to buy a sheevaplug with an european power adaptor instead of the uk version from [www.newit.co.uk?]("http://www.newit.co.uk?")

Thats what my friend got from them, the EU conector on the unit, even the UK version they ship has the EU slider for the unit.

---

### Post by raemac on 2009-11-13
Has anyone had any success with NPTL functions, makecontext(), swapcontext() in the [_ubuntu-9.05_]("http://plugcomputer.org/index.php/us/resources/downloads?func=select&id=2") from plugcomputer.org?
 
It appears the functions are marked __evoke_link_warning_ in /usr/lib/libc.a and produce linker complaints:
 
warning: makecontext is not implemented and will always fail
warning: swapcontext is not implemented and will always fail
 
Are these known bugs or have these functions been intentionally stripped from libc? Any suggestions for how to obtain a libc with these functions enabled?
 
 
I'm trying to port [_plan9port_]("http://swtch.com/plan9port/") and it needs thread support.
 
tags: arm nptl threads plan9

---

### Post by dennis55 on 2009-11-15
Sheevaplug box contents include a european 2 prong plug from NewIt in the uk.
being very much a"greenhorn" to Linux i have it sitting here not doing very much.
i eventually would like to configure it to run SqueezeBoxserver, which my Qnap 109 is struggling with.....;)

dennis

  






> **G|N| said:**
> Is it possible to buy a sheevaplug with an european power adaptor instead of the uk version from [www.newit.co.uk?]("http://www.newit.co.uk?")

---

### Post by TheTank on 2009-11-30
+1 proud owner of a SheevaPlug

---

### Post by rec9140 on 2009-11-30
Do the Ubuntu versions that are out for these devices include the kernel support for USB audio devices? Or do they need kernel recompiles to get USB audio support?

Specifically to use for line level input to programs such as DarkIce and/or Ices 2.0?

---

### Post by WorldTripping on 2010-01-04
+1 new Sheevaplug user here.

Ordered it from newit.co.uk and it was here within 24 (ish) hours.

15 minutes later I had it unpacked and I could ssh into it.

After a bit of tinkering I now have it mounted to a 1.5 TB hard drive and I can sshfs into it from any wifi hotspot in the world.

(Had to set up port-forwarding on the router and set the /etc/exports permissions.)

I've gone from knowing nothing about these devices to being able to connect via serial, flash the NAND, set up servers; all in about two days.

Next - setting and securing Apache !

{loving the tinkering}

---

### Post by GeneralZod on 2010-01-16
I guess I can add myself to the list, here :) I only use my desktop computer as mass storage and for a few other lightweight functions (svn server, etc), and there's no point having it switched on 24/7, making noise and sucking up power, so I picked up a Sheevaplug from NewIT here in the UK (via one of their ebay auctions).

It arrived the next day, and after a few false starts, I got Debian installed on my [SD card](http://www.play.com/Electronics/Electronics/4-/10537723/PNY-16GB-Optima-High-Speed-SD-HC-Card-Endorsed-By-National-Geographic/Product.html) and got it working with my [USB wifi dongle](http://www.amazon.co.uk/s/ref=nb_ss_w_h_/202-3982289-4794261?url=search-alias%3Daps&field-keywords=167g&Go.x=0&Go.y=0&Go=Go).  I've left it torrenting overnight as a soak test, and it seems absolutely fine, so far (**Edit:** - hmmm - looks like if I lose the connection, I can't re-associate without rebooting :/).  I'm very pleased with it :)

Edit:

Oh, and the cheap MCE infrared remote/ receiver I picked up on ebay Just Worked with it, too, which bodes well for when I get my Pandora.  So far, my tiny and cheap Webcam didn't work, but I'll try that again later.

---

### Post by TheTank on 2010-01-16
> **GeneralZod said:**
> So far, my tiny and cheap Webcam didn't work, but I'll try that again later.
Just wanted to note that I do have a friend that uses a cheap webcam with the sheeva + using motion detection software (iirc it is actually called motion or so).
So it might just be the webcam.

---

### Post by markp1989 on 2010-01-16
I really want one of these, but i cant think of a reason  to buy one :(

i have a machine set up as a torrentslave/fileserver / htpc already

if i had saw this before i built the server/htpc, i would of got this to use as the server side ,moving the hard drives etc away from the tv, and set up a media pc with a cf card as the root drive, so i could have the media pc completly silent (now its quiet, but if i listen i can hear it) 

any specific uses that you can think of that might convince me to want one? :) 


i was thinking a usb audio adapter, and a remote, as a small mpd based jukebox 

if it had a hdmi port, i would love to put this behind my dads tv, put geexbox on it, and mount the nfs shares form my pc for him to watch.

pairing this with a set of x10 home automation hardware plus multiple webcams for home security would also rock :) 

simple uses like setting it up as a poxy server at for you to access when you out using unencrypted wireless networks.


i wish they had made it just abit bigger so you could fit a 2.5inch harddrive/ssd inside it

---

### Post by TheTank on 2010-01-17
> **markp1989 said:**
> 
i wish they had made it just abit bigger so you could fit a 2.5inch harddrive/ssd inside it
On a IT site I frequent (it's in German) they had a news snippet that the next version (3) WILL have a HDD and WLAN.
It was shown at the CES2010.

Though I presume it would also cost more.

---

### Post by rigsby on 2010-01-30
> **markp1989 said:**
> 
if it had a hdmi port, i would love to put this behind my dads tv, put geexbox on it, and mount the nfs shares form my pc for him to watch.



Like the "GuruPlug Display"?

[http://www.globalscaletechnologies.com/c-4-guruplugs.aspx](http://www.globalscaletechnologies.com/c-4-guruplugs.aspx)

---

### Post by markp1989 on 2010-01-30
> **rigsby said:**
> Like the "GuruPlug Display"?

[http://www.globalscaletechnologies.com/c-4-guruplugs.aspx](http://www.globalscaletechnologies.com/c-4-guruplugs.aspx)

yer, thats awsome :) the one with the hdmi out, so i dont have to convert everything to dvd for him to watch, i know what his xmas/bday present mite be this year (funds permiting ovbiously) 

@TheTank : Thats awsome, sheevaplug with built in hard drive would rock :) iu mite have to buy one if the release it

---

### Post by BACHAB on 2010-02-21
Hi, I've just received my sheevaplug from eeuu, and the cd and usb cable are missing. It would be great if someone could tell me the CD contents so I'll know what to download.
Thanks!

---

### Post by rigsby on 2010-02-21
> **BACHAB said:**
> Hi, I've just received my sheevaplug from eeuu, and the cd and usb cable are missing. It would be great if someone could tell me the CD contents so I'll know what to download.
Thanks!

Nothing essential, unless you are a Windows user, in which case there are Windows drivers on the CD.

Most of it can be found here:

[http://www.plugcomputer.org/index.php/resources/downloads](http://www.plugcomputer.org/index.php/resources/downloads)

Oh, I suppose the other "essential" piece of information is the root password ("nosoup4u"). You should look through the Readme [http://www.plugcomputer.org/index.php/us/resources/downloads?func=select&id=10](http://www.plugcomputer.org/index.php/us/resources/downloads?func=select&id=10) and the plugcomputer forum has lots of useful info.

[http://plugcomputer.org/plugforum/index.php](http://plugcomputer.org/plugforum/index.php)

---

### Post by RandomJoe on 2010-02-21
I believe the CD contents are available on the Marvell website, but I never used anything off of mine.  Everything on there is fairly out of date.

More useful is to go to the Plug Computing wiki and forums:
[http://www.openplug.org/plugwiki/index.php/Main_Page](http://www.openplug.org/plugwiki/index.php/Main_Page)
[http://plugcomputer.org/plugforum/index.php](http://plugcomputer.org/plugforum/index.php)

There is a page on the Wiki "New Plugger Howto" that can help you get started.

Edit:
Heh...  I somehow missed the post above...  Duplicated info! :p

---

### Post by IrishWristwatch on 2010-02-23
I've been thinking about ordering a Sheevaplug to replace the aging, power-hungry computer I'm currently using as a server.  How does Ubuntu on ARM work with apt-get?  I noticed the packages on packages.ubuntu.com are only built for i386 and amd64, so how would someone install something like CUPS (for house printer), OpenSSH-server, or proftpd onto a ARM-based device?

---

### Post by rigsby on 2010-02-23
> **IrishWristwatch said:**
> I've been thinking about ordering a Sheevaplug to replace the aging, power-hungry computer I'm currently using as a server.  How does Ubuntu on ARM work with apt-get?  I noticed the packages on packages.ubuntu.com are only built for i386 and amd64, so how would someone install something like CUPS (for house printer), OpenSSH-server, or proftpd onto a ARM-based device?

There is a repository for Jaunty Jackalope, but not for Karmic Koala - support for the ARM processor having been discontinued. Debian continues to support the processor through their repositories.

Here's a list of the packages available from the Ubuntu repository:

[http://www.newit.co.uk/documents/package_list_2009-09-27.txt](http://www.newit.co.uk/documents/package_list_2009-09-27.txt)

---

### Post by IrishWristwatch on 2010-02-23
> **rigsby said:**
> There is a repository for Jaunty Jackalope, but not for Karmic Koala - support for the ARM processor having been discontinued. Debian continues to support the processor through their repositories.

Here's a list of the packages available from the Ubuntu repository:

[http://www.newit.co.uk/documents/package_list_2009-09-27.txt](http://www.newit.co.uk/documents/package_list_2009-09-27.txt)

At this point I'm thinking about running Debian on it.  They seem to have their ARM software better maintained.

---

### Post by thebigob on 2010-02-26
Anyone managed to get a c# compiler to work?

followed the guide here:
[http://plugcomputer.org/plugwiki/index.php/Running_.Net_and_ASP.Net_applications](http://plugcomputer.org/plugwiki/index.php/Running_.Net_and_ASP.Net_applications)

I just get a segmentation fault and an exit code of 139.

Any pointers much appreciated.

Cheers

---

### Post by zenkinz on 2010-03-01
does anybody knows sheevaplug has a software plugin equivalent, that can plug my qnap nas to the cloud?
 
I don't need another device, since I've already qnap, even if the device can connect to my qnap filesystems (which I doubt it does), since I think my qnap is doing something similar, just the lack of plugging into the public cloud so that I can access my media files that resides in my qnap hdd.
 
anybody?

---

### Post by Maisondouf on 2010-04-20
I seen Marvell is going to sell a new Plug with an Armada 300 processor at 2GHz and an integrated 1,8'' HDD.

All spec are Here : [http://www.linuxfordevices.com/c/a/News/Marvell-Plug-Computer-30-and-Armada-300-and-610/](http://www.linuxfordevices.com/c/a/News/Marvell-Plug-Computer-30-and-Armada-300-and-610/)

Is it possible to install Ubuntu in it ?

edit: i've found a seller here : [http://www.ionicsplug.com/cirrus.html](http://www.ionicsplug.com/cirrus.html)

---

### Post by Maheriano on 2010-04-21
Anyone know if there's a way to output video through one of the USB ports to a little 7 inch touchscreen?

---

### Post by Gemnoc on 2010-05-05
> **rigsby said:**
> Oh, I suppose the other "essential" piece of information is the root password ("nosoup4u"). 

Really? "nosoup4u"? LOL! Those guys are [Seinfeld]("http://en.wikipedia.org/wiki/No_soup_for_you") fans I see. :mrgreen:

I'm very tempted by the SheevaPlug or one of the other variants. :)

---

### Post by kazzaerexys on 2010-05-06
I am seriously looking at one of these devices to replace on OpenSolaris file server I am running now.  The thing I would need to figure out is how easily I could port my ZFS pool from OpenSolaris to zfs-fuse under Ubuntu or Debian.

Could anybody provide some pointers for how I can get this done?

Thanks!

---

### Post by doragasu on 2010-05-21
I have recently bought a GuruPlug Server+ (enhanced ShevaPlug), and it comes with Debian preinstalled. I would like to replace Debian with Ubuntu, but I don't know if GuruPlug works with SheevaPlug Ubuntu. Also I can't find clear documentation about the procedure needed to replace the OS included in my GuruPlug unit...

Anybody with a GuruPlug than can shed some light on this?

---

### Post by TheTank on 2010-05-22
> **doragasu said:**
> I have recently bought a GuruPlug Server+ (enhanced ShevaPlug), and it comes with Debian preinstalled. I would like to replace Debian with Ubuntu, but I don't know if GuruPlug works with SheevaPlug Ubuntu. Also I can't find clear documentation about the procedure needed to replace the OS included in my GuruPlug unit...

Anybody with a GuruPlug than can shed some light on this?
Have you tried asking the people at plugcomputer.org?

A quick search gave me this: [clicky]("http://www.plugcomputer.org/index.php/us/component/search/guruplug?ordering=&searchphrase=all")

---

### Post by doragasu on 2010-05-28
Thanks for help.

I had already seen that files at plugcomputer. I found Debian rootfs and kernel, some utils and a script to install a new OS. I had a quick look to the script, and it looks like it's only for 32 bit systems (I'm using a 64-bit Ubuntu distro). If I get some time to analyze the script, maybe I can figure out how to get it working. It looks like you need to set up a TFTP server and do some more things...

---

### Post by pe7er on 2010-06-14
I was able to set up my SheevaPlug as WebCam server with this info: [http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server)
I had to install webcam-server software using
```
apt-get install webcam-server
```
and create a small script that's available at the hacktivision.com site:
```
/etc/init.d/webcam-server
```


> **lyzby said:**
> The uvc video drivers for web cams are reported to be included in Ubuntu, but appear not to be available on the Sheevaplug.  I have not been able to find anything in the repositories which seems appropriate.  How does one load the modules which will recognize web cams.  lsusb shows: 

Bus 001 Device 003: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks

"ls /dev/video*" shows nothing, as does "dmesg | grep video".

---

### Post by skoorbevad on 2010-07-13
> **kazzaerexys said:**
> I am seriously looking at one of these devices to replace on OpenSolaris file server I am running now.  The thing I would need to figure out is how easily I could port my ZFS pool from OpenSolaris to zfs-fuse under Ubuntu or Debian.

Could anybody provide some pointers for how I can get this done?

Thanks!

'zfs export' and 'zfs import' are your friends.

However, don't expect to pull this off. First, ZFS in credibly memory hungry, and proper implementations all but require a 64-bit architecture and a few gigabytes of RAM.

You can get by with ZFS on 32-bit, but it's an exercise in tuning it greatly, and it's not completely solid.

Given the SheevaPlug is an ARM9 (32-bit) with 512MB of RAM, ZFS is basically out the window. If not using OpenSolaris, though, I'd generally say that FreeBSD is the only other robust platform for a proper ZFS implementation until it can run under Linux without FUSE.

---

### Post by handy on 2011-01-01
When I found out about the ARM based GuruPlug Server Plus, touted as the next step in the evolution of the SheevaPlug, I thought this could be what I've been waiting for to make a great low power consumption firewall/router. As the GuruPlug Server Plus, has 2x Gb NIC's on-board. 

Unfortunately it seems that it is made to a very poor design. So I'll have to keep waiting until someone does it right:

[http://1wt.eu/articles/guruplug-slow-heater/](http://1wt.eu/articles/guruplug-slow-heater/)

---

### Post by mips on 2011-01-01
> **handy said:**
> When I found out about the ARM based GuruPlug Server Plus, touted as the next step in the evolution of the SheevaPlug, I thought this could be what I've been waiting for to make a great low power consumption firewall/router. As the GuruPlug Server Plus, has 2x Gb NIC's on-board. 

Unfortunately it seems that it is made to a very poor design. So I'll have to keep waiting until someone does it right:

[http://1wt.eu/articles/guruplug-slow-heater/](http://1wt.eu/articles/guruplug-slow-heater/)

handy, go to the Marvell (makers of Sheevaplug) website and have a look at their ARM development boards, it's kinda hard to find the stuff though as their site has changed, I can't even find the Kirkwood series development boards anymore. They have low power ARM boards that do LAN, SATAII, USB, VGA all in different configurations. I will have a look for links and post them here.

They have the, ARMADA XP, ARMADA 300, Discovery Innovation Series & Kirkwood Series embedded processors.

EDIT: I can't find anything on their site right now so will have to email them next week.

I did however find something related, [http://www.directinsight.co.uk/products/karo/marvell-tk71-88F6281.html](http://www.directinsight.co.uk/products/karo/marvell-tk71-88F6281.html) but the price is just stupid compared to what I saw from Marvell when I could still find something.

---

### Post by handy on 2011-01-01
Thanks for that mips.

I've been looking at Marvell & other sites, it is too hard to find anything useful. So I've given up.

I don't require a change of hardware for my IPCop system, (not that IPCop supports ARM yet) but I'd like to keep gently applying pressure on the IPCop forum so that someone will make an ARM ready port.

These silent low power usage & space efficient solutions are perfect for the job, provided they have 2x NIC's built in (none of this USB shite).

---

### Post by mips on 2011-01-02
I wish more companies would make ARM motherboards. mini-ITX would be nice but even ATX would be fine. A board with 2x GbLAN, 2-4 SATAII, 4xUSB, 1x CF, 1x Wireless & VGA would have some killer potential but for a firewall you would not need all that but the chipset already supports it anyway.

---

### Post by gorillinux on 2011-02-22
Anyone else heard of this? [http://www.pwnieexpress.com ]("http://www.pwnieexpress.com/")

---

### Post by pe7er on 2011-02-23
> **gorillinux said:**
> Anyone else heard of this? [http://www.pwnieexpress.com ]("http://www.pwnieexpress.com/")

No, thanks for that link!.
It looks like a regular SheevaPlug, preinstalled / preconfigured with all kind of hacking & security tools. 

Only the price of the regular version (that has does not seem to have extra hardware) is 2.2 times higher than a regular SheevaPlug.
The more expensive versions seem to have extra hardware (wifi / 3G).

When I searched for more information about the PWN Plug, I found this other interesting page:
"List of Portable Hardware Devices for Penetration Testing!" [http://www.pentestit.com/tag/pwn-plug/](http://www.pentestit.com/tag/pwn-plug/)

---

### Post by TheTank on 2011-02-23
Besides the corny name: [http://www.freedomboxfoundation.org/](http://www.freedomboxfoundation.org/)

---

### Post by NickFankhauser on 2011-04-08
I just got a SheevaPlug with ubuntu installed on it. But I have a problem I can not solve: Running "apt-get update" hangs at "[Connecting to ports.ubuntu.com (91.189.88.36)]", and then timeouts. 
But "ping ubuntu.com" works, so the connection to the inet is there. 
It has "deb [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty main restricted universe multiverse" in /etc/apt/sources.list. 
Strangely, "ping ports.ubuntu.com" does not work, but I can connect to [http://ports.ubuntu.com](http://ports.ubuntu.com) from my laptop. 
What could be the problem?

---

### Post by mips on 2011-04-08
Try using a different repository.

Make sure your IP settings are 100% including DNS & Gateway.

---

### Post by matthewbpt on 2011-04-08
> **NickFankhauser said:**
> I just got a SheevaPlug with ubuntu installed on it. But I have a problem I can not solve: Running "apt-get update" hangs at "[Connecting to ports.ubuntu.com (91.189.88.36)]", and then timeouts. 
But "ping ubuntu.com" works, so the connection to the inet is there. 
It has "deb [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty main restricted universe multiverse" in /etc/apt/sources.list. 
Strangely, "ping ports.ubuntu.com" does not work, but I can connect to [http://ports.ubuntu.com](http://ports.ubuntu.com) from my laptop. 
What could be the problem?

Jaunty is no longer supported so the repositories are closed. Support ended 2010-10-23. You should install a newer version, install 10.04 LTS for the longest support.

---

### Post by pe7er on 2011-04-08
> **matthewbpt said:**
> Jaunty is no longer supported so the repositories are closed. Support ended 2010-10-23. You should install a newer version, install 10.04 LTS for the longest support.
Thanks for that info!
My SheevaPlug is running Jaunty Jackalope (Ubuntu 9.04)....

Is it easy to upgrade from remote? 
I have it at another location but I can reach it using ssh.

I found [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) 
Can I use that "Network Upgrade for Ubuntu Servers (Recommended)" instruction for upgrading Ubuntu at the SheevaPlug? 
I thought that I had read something that it has a special version or special boot for its ARM processor?

---

### Post by Maisondouf on 2011-04-30
@pe7er

No, you can't upgrade at the moment up to 9.04

The reason is in the achitecture (arm) which is not maintened 

If you want newer kernels, you have to have a look on debian installation [http://www.cyrius.com/debian/kirkwood/sheevaplug/install.html](http://www.cyrius.com/debian/kirkwood/sheevaplug/install.html) or on [http://sheeva.with-linux.com/sheeva/](http://sheeva.with-linux.com/sheeva/)

---

### Post by pe7er on 2011-04-30
> **Maisondouf said:**
> If you want newer kernels, you have to have a look on debian installation [http://www.cyrius.com/debian/kirkwood/sheevaplug/install.html](http://www.cyrius.com/debian/kirkwood/sheevaplug/install.html) or on [http://sheeva.with-linux.com/sheeva/](http://sheeva.with-linux.com/sheeva/)
Great, thanks for your reply!

---

### Post by hermie66 on 2011-12-20
hi
i'm running my sheevaplug with
root@ubuntu:/usr/local/albertz-shairport-83c1b71# uname -a
Linux ubuntu 2.6.30.2 #11 PREEMPT Wed Jul 22 19:53:31 MDT 2009 armv5tel GNU/Linux

now i try to install shairport and this needs some package which i cant install.

The following extra packages will be installed:
  libcrypt-openssl-bignum-perl libsocket6-perl
The following NEW packages will be installed:
  avahi-utils libao-dev libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libio-socket-inet6-perl libsocket6-perl
0 upgraded, 6 newly installed, 0 to remove and 43 not upgraded.
Need to get 168kB of archives.
After this operation, 1057kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  avahi-utils libao-dev libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libsocket6-perl libio-socket-inet6-perl
Install these packages without verification [y/N]? y
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main avahi-utils 0.6.23-4ubuntu4
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libao-dev 0.8.8-4ubuntu1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libcrypt-openssl-bignum-perl 0.04-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libcrypt-openssl-rsa-perl 0.25-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libsocket6-perl 0.20-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libio-socket-inet6-perl 2.54-1
  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/a/avahi/avahi-utils_0.6.23-4ubuntu4_armel.deb](http://ports.ubuntu.com/pool/main/a/avahi/avahi-utils_0.6.23-4ubuntu4_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/liba/libao/libao-dev_0.8.8-4ubuntu1_armel.deb](http://ports.ubuntu.com/pool/main/liba/libao/libao-dev_0.8.8-4ubuntu1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-bignum-perl/libcrypt-openssl-bignum-perl_0.04-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-bignum-perl/libcrypt-openssl-bignum-perl_0.04-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-rsa-perl/libcrypt-openssl-rsa-perl_0.25-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-rsa-perl/libcrypt-openssl-rsa-perl_0.25-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libs/libsocket6-perl/libsocket6-perl_0.20-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libs/libsocket6-perl/libsocket6-perl_0.20-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.54-1_all.deb](http://ports.ubuntu.com/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.54-1_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Can somebody tell me if these packages are available for ubuntua and arm9?
Where?

thank you 
René

---

### Post by snowpine on 2011-12-20
> **hermie66 said:**
> hi
i'm running my sheevaplug with
root@ubuntu:/usr/local/albertz-shairport-83c1b71# uname -a
Linux ubuntu 2.6.30.2 #11 PREEMPT Wed Jul 22 19:53:31 MDT 2009 armv5tel GNU/Linux

now i try to install shairport and this needs some package which i cant install.

The following extra packages will be installed:
  libcrypt-openssl-bignum-perl libsocket6-perl
The following NEW packages will be installed:
  avahi-utils libao-dev libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libio-socket-inet6-perl libsocket6-perl
0 upgraded, 6 newly installed, 0 to remove and 43 not upgraded.
Need to get 168kB of archives.
After this operation, 1057kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  avahi-utils libao-dev libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libsocket6-perl libio-socket-inet6-perl
Install these packages without verification [y/N]? y
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main avahi-utils 0.6.23-4ubuntu4
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libao-dev 0.8.8-4ubuntu1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libcrypt-openssl-bignum-perl 0.04-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libcrypt-openssl-rsa-perl 0.25-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libsocket6-perl 0.20-1build1
  404 Not Found
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) jaunty/main libio-socket-inet6-perl 2.54-1
  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/a/avahi/avahi-utils_0.6.23-4ubuntu4_armel.deb](http://ports.ubuntu.com/pool/main/a/avahi/avahi-utils_0.6.23-4ubuntu4_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/liba/libao/libao-dev_0.8.8-4ubuntu1_armel.deb](http://ports.ubuntu.com/pool/main/liba/libao/libao-dev_0.8.8-4ubuntu1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-bignum-perl/libcrypt-openssl-bignum-perl_0.04-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-bignum-perl/libcrypt-openssl-bignum-perl_0.04-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-rsa-perl/libcrypt-openssl-rsa-perl_0.25-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libc/libcrypt-openssl-rsa-perl/libcrypt-openssl-rsa-perl_0.25-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libs/libsocket6-perl/libsocket6-perl_0.20-1build1_armel.deb](http://ports.ubuntu.com/pool/main/libs/libsocket6-perl/libsocket6-perl_0.20-1build1_armel.deb)  404 Not Found
Failed to fetch [http://ports.ubuntu.com/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.54-1_all.deb](http://ports.ubuntu.com/pool/main/libi/libio-socket-inet6-perl/libio-socket-inet6-perl_2.54-1_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Can somebody tell me if these packages are available for ubuntua and arm9?
Where?

thank you 
René

Hi René, Ubuntu 9.04 "Jaunty" has reached its end-of-life and is no longer supported. You need to switch to 10.04 or newer if you want support.

---

### Post by hermie66 on 2011-12-21
thank you
can i do this like described in here?
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Is the seevaplug hardware supported in the newer ubuntu version?

---

### Post by snowpine on 2011-12-21
> **hermie66 said:**
> thank you
can i do this like described in here?
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Is the seevaplug hardware supported in the newer ubuntu version?

I don't know the answer, because it looks like you're running a special Ubuntu version for the ARM processor.

Post #218 has some good suggestions/links.

---

### Post by adrianrosian on 2012-01-19
The only solution seems to be to switch to debian

---

