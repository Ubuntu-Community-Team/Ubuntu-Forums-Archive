---
title: "Howto: Yukon/Marvell Gigabit network card"
date: 2005-07-09
forum: Tutorials
---

### Post by kleeman on 2005-07-09
No longer needed by most users now. See last few lines below!

BACKGROUND

This network card worked in warty but does not in Hoary and may not in Breezy.
The problem is that it used to use the sk98lin driver provided by the vendor syskonnect but the kernel guys decided to replace it with skge in January 2005. At that stage sk98lin was broken in the new 2.6.10 kernel and the kernel developers said the code was bloated and did not follow their guidelines so they did not fix it and instead wrote skge (Stephen Hemminger wrote it). This driver did not appear in the kernel until 2.6.12 as I understand it. 

SO this card would not work in hoary (grrrr!). This is a real pain since most of Ubuntu installs by the internet.

According to the posts on the kerneltrap website the new driver skge (which is in the new Breezy 2.6.12) only works for the old Yukon gigabit cards AND NOT FOR the new Yukon 2 card. I have confirmed this as I have the latter card. 

SOLUTION

1) Download the latest vendor driver package from here:

[http://www.syskonnect.com/support/driver/](http://www.syskonnect.com/support/driver/)

2) Install the build-essential package; kernel headers for your particular kernel (eg linux-headers-2.6.12-3 and linux-headers-2.6.12-3-686-smp in my case on breezy); the linux source code (linux-source-2.6.12 in my case).

3) Install the source tree:
In my case:
sudo tar jxvf /usr/src/linux-source-2.6.12.tar.bz2
cd /usr/src 
sudo ln -s   linux-source-2.6.12 linux

4) Uncompress the vendor package
cd
tar jxvf install-*_*.tar.bz2  (replace the stars here with the version numbers you have)

5) Install the driver:
cd Driv*

sudo sh install.sh

and follow the options (install driver not generate patch)

For Breezy and the Yukon 2 card there are further problems at this stage. Firstly the Ubuntu devs removed the sk98lin stuff because the skge driver was the replacement. This doesn't work for the Yukon 2 card  ](*,)  ](*,) however. In addition the kernel I am using at present (7/9/05) was compiled with gcc-3.4 but the default compiler is presently set to gcc-4.0- this may be fixed by the time Breezy is released. So here is what I did
CC=gcc-3.4
export CC
sudo cp /boot/config-2.6.12-3-686-smp /usr/src/linux/.config

Edit 
/usr/src/linux/.config and replace the sk98lin line with:
CONFIG_SK98LIN=m                (this restores the old sk98lin stuff in the source tree)

then proceed as above

7/23/05 Re the last 4 lines: The latest breezy kernel 2.6.12-4 does not allow the above hack (the devs are getting even tidier  ](*,)  ](*,)  ](*,)) . If you have a Yukon 2 you now need to generate a patch using the install.sh script and install it in the kernel source tree as per the instructions in the README file. Also follow the instructions in there for doing a make gconfig. You can enable Rx polling (NAPI) if you wish (works for me). Following the kernel reconfiguration do the following as root (see the kernel compile howto and posts below)
cd /usr/src
make-kpkg clean
make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers
dpkg -i kernel-headers-2.6.12-custom_*_i386.deb kernel-image-2.6.12-custom_*_i386.deb

where * is your datestamp (see the debs you have created)

Hopefully this should put a new kernel into your boot menu. This kernel
will have the sk98lin module ready to go which hotplug will find and load.



6) Bring up the new driver:
sudo modprobe sk98lin
sudo ifconfig eth0 up
sudo dhclient eth0

Whew that took a lot of effort!

Final update 9/21/05  (hopefully!). The Ubuntu kernel developer has said that the vendor sk98lin will be placed in the kernel package for Breezy which should solve all the problems listed above and below.

READ THIS!!!!!!!!!!!!!

CONFIRMED 9/27/05. With the 2.6.12-9.18 kernel release the Yukon II is again functional out of the box! Kudos to the developers for listening to us users!

---

### Post by kolya on 2005-07-11
Forgive my ignorance but is this an onboard network card or one you purchased.  I have a DFI nForce 3 Lanparty UT motherboard with Marvell's single port 88E1111 GbE ethernet.  Should I be worried?

---

### Post by kleeman on 2005-07-11
My card is indeed onboard and I googled your card and it looks like sk98lin is the driver for it as well (don't quote me on that however  :smile: ). So you may be in the same situation as me....

---

### Post by kolya on 2005-07-12
Thanks for the heads up.  So you had to do this in order to get your network card to work in Hoary, is this correct?

---

### Post by kleeman on 2005-07-12
Yes I'm afraid.

---

### Post by patwest on 2005-07-12
I have a k8V-X motherboard that has an onboard marvell Gigabit network card and I didn't have to do anything special. I am running 32bit ubuntu Hoary(5.04) and I seem to have the sk98lin driver. My network is 100Mbit.

From lspci:
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Et
hernet 10/100/1000Base-T Adapter (rev 13)


From dmesg:
sk98lin: Asus mainboard with buggy VPD? Correcting data.
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter

uname -a
Linux ubuntu 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

---

### Post by kleeman on 2005-07-13
That's good to hear. According to the kernel dev (Fabbione) the kernel tree driver for hoary (sk98lin) works for some people and not for others. More info in my bugreport here for those who are interested. I read a story on this on kerneltrap which said
sk98lin was broken in 2.6.10....

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6142](https://bugzilla.ubuntu.com/show_bug.cgi?id=6142)

---

### Post by mikkoli on 2005-07-27
I had a similar problem and it went like this

In hoary and with knoppix the card has been working ok but when I installed gentoo base system from hoary and then rebooted to hoary I could not go to net.

After reading kernel documentation and testing allsorts of ideas i went back to gentoo and installed links web browser and came to theese forums and searched for skge. 

 Jihuuu!!!!

I downloaded the vendor driver and now hoary goes to net with no problems.

Thank you very much for your information:))

Just wondering what did the gentoos 2.6.12 kernel driver do.

Ok gotta hit the sack now.

---

### Post by darkjedi8359 on 2005-09-12
Hello, I recently bought an asus board with the yukon gigabit lan... I have been following this howto, but how do I get a copy of the linux source without internet at all with apt-get or synaptic?

---

### Post by kleeman on 2005-09-12
I checked and could not see it on the cdrom. As I said in the howto not having a network in Ubuntu is very unpleasant which makes this bug VERY ](*,)  ANNOYING!

What I did was install warty first because the sk98lin driver there works. I then grabbed all the debs I needed using the network before performing a standard upgrade to hoary. Before you do this make sure that you comment out the line 

auto eth0 (put a # in front of the line)

in

/etc/network/interfaces

 because this tries to automatically bring up the network with the broken sk98lin driver. On my system that causes a hang which I could not get out of.

Once you get your network going you can uncomment the line and you should be good to go after rebooting (or else use sudo ifup eth0)

---

### Post by darkjedi8359 on 2005-09-12
thanks, unless some one has a better solution between now and dloading & burning warty... I am going to try that :)

---

### Post by darkjedi8359 on 2005-09-13
installing warty :)

Anyone know if breezy will support this by defualt? I couldn't find anything much about it on the breezy dev board.

Warty wont even load on this pc. lol

---

### Post by kleeman on 2005-09-13
Breezy uses skge which is the new open source driver meant to replace sk98lin. It supports some Yukons and not others. If you want to check whether it works get the Colony 4 livecd for Breezy and try it out.....

---

### Post by Swerver on 2005-09-13
I have a yukon/marvell 1000 onboard on my asus A8V deluxe board, both hoary and breezy pick this up just fine upon install

---

### Post by darkjedi8359 on 2005-09-13
When I fist installed ubuntu I think internet worked, it quit working after I had to install it again.

---

### Post by darkjedi8359 on 2005-09-13
Would it be worth it to just go and buy a PCI network card? Sounds like it may be less of a hassle x_x

---

### Post by saik0 on 2005-09-14
Well i restored the sk98lin driver to the source tree and compiled it and installed it as a kernel package and it's working flawlessly...........but it broke my ipw2200 wireless NIC. Any idea what this means

> ~$ dmesg | grep ipw2200
[4294694.444000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294694.444000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294694.448000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294694.496000] ipw2200: ipw-2.3-boot.fw load failed: Reason -2
[4294694.496000] ipw2200: Unable to load firmware: 0xFFFFFFFE
[4294694.496000] ipw2200: failed to register network device
[4294694.504000] ipw2200: probe of 0000:06:02.0 failed with error -5

---

### Post by kleeman on 2005-09-14
Found this 

Firmware files fail to load even if installed
In some kernel configurations (users have most frequently reported the problem only with 2.6.9), the default timeout value for the hotplug subsystem is too low. You may have this problem if you see the following in your kernel log (via dmesg or /var/log/messages):

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.1
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: ipw-2.2-boot.fw load failed: Reason -2
ipw2200: Unable to load firmware: 0xFFFFFFFE
ipw2200: failed to register network device
ipw2200: probe of 0000:00:0b.0 failed with error -5

To work around this, you can increase the default timeout value:

	echo 100 > /sys/class/firmware/timeout

and then reload the ipw2200 module. If this corrects your problem, you may wish to add the above line to your system startup scripts prior to the point at which the driver module would be loaded.

The other most common reason for getting the above error is that the firmware files are not installed in the correct location. Please see the INSTALL document for information on installing the firmware files. 


Here:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by saik0 on 2005-09-14
Thanks for the info, but I still get the same error. The interface works wondefully in the stock ubuntu kernel, WPA and all. But i broke it with my custom kernel...

---

### Post by TheJester on 2005-09-14
[QUOTE=kleeman]Breezy uses skge which is the new open source driver meant to replace sk98lin. It supports some Yukons and not others. If you want to check whether it works get the Colony 4 livecd for Breezy and try it out.....[/QUOTE]

Is there any possibility for sk98lin to get into breezy? I got an Asus v6800v Notebook here, and skge didn't work for me. Unlike in Ubuntu Hoary (or debian etch, which uses sk98lin), i didn't get any traffic through in Breezy.

linux-*-restricted-modules would be imho a nice place for sk98lin. So theres a fallback for these cards, which will not work in Breezy right now. 

```

root@deepblue:/home/sven # lspci|grep net
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
root@deepblue:/home/sven # uname -a
Linux deepblue 2.6.10-5-386 #1 Thu Sep 8 06:18:41 UTC 2005 i686 GNU/Linux
root@deepblue:/home/sven # lsmod|grep sk
sk98lin               149216  0

```

---

### Post by kleeman on 2005-09-14
I agree completely but it is up to the devs that is why I suggest we make a big fuss by adding to my bugzilla entry and possibly upping the bug severity to major....

If I was betting however I would seriously doubt whether this is going to get into Breezy....Hope I'm wrong!

---

### Post by darkjedi8359 on 2005-09-14
[QUOTE=kleeman]I agree completely but it is up to the devs that is why I suggest we make a big fuss by adding to my bugzilla entry and possibly upping the bug severity to major....

If I was betting however I would seriously doubt whether this is going to get into Breezy....Hope I'm wrong![/QUOTE]
 I am just going to go and buy a network card at bestbuy or something, this one looks like it will be a hassle x_x

---

### Post by mvaniersel on 2005-09-15
I have a new PC with ASUS P5GD2 motherboard, Onboard Marvell Gigabit LAN. During installation of Hoary 5.04 I get a message "no network interface detected". Then I searched and found this howto. 

So what I then tried was to go back to a Warty installation. First I tried the live CD, but networking doesn't work. Then I figure I should try a complete installation of Warty, but again during the installation process I get a "no network interface detected".

Now I'm not sure anymore that going to Warty will fix this problem. Any advice to what I might try next? 


A side issue is that when the "no network interfaces detected" pops up during installation, it says "you may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step." However, when I go back I have no idea how to do that. There doesn't seem to be a way to load a module at all.

---

### Post by kleeman on 2005-09-15
I have put up my hoary sk98lin drivers here:
[http://www.math.nyu.edu/faculty/kleeman/hardware/](http://www.math.nyu.edu/faculty/kleeman/hardware/)
There is a 386 and a 686-smp variant.

Put them in either

/lib/modules/2.6.10-5-386/kernel/drivers/net/

OR

/lib/modules/2.6.10-5-686-smp/kernel/drivers/net/

and make sure they have the same file permissions as other modules. Let me know if this woks at all.

Also please lodge another entry on my bugzilla report at

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6142](https://bugzilla.ubuntu.com/show_bug.cgi?id=6142)

so the developers know more people are getting annoyed by this...

---

### Post by mvaniersel on 2005-09-15
Thanks kleeman. I copied the 386 module ok using a floppy, but this doesn't solve my problem yet. 

The module seems to get loaded ok, I see it back with lsmod.
With dmesg, I see there is the following error at the end of the log:
```

eth%d: -- ERROR --
   class : internal software error
   Nr: 0x2bd
   Msg: TWSI: transfer does not complete
sk98lin: SkGeInitAssignRamToQueues failed.
```

Does that tell you something? I really don't know much about these things...

---

### Post by kleeman on 2005-09-15
Doesn't look like the module was compatible. What kernel and distro are you using? Try

uname -a

to find out....

---

### Post by kleeman on 2005-09-15
If this does not work with hoary, I strongly suggest downloading the vendor driver as well as all the packages mentioned in the howto and giving them a whirl. If you have a dual boot with Windows XP you can read the files you need off the ntfs (windows) partition.

---

### Post by mvaniersel on 2005-09-16
I will try that, but it'll take some time (sigh). Unfortunately, popping in a different network card is not an option for me right now because in the system we have here the IP address is linked to the MAC address of the network card. In the mean time, here is the output of that command:

Linux Bigcat012 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 Gnu linux

That's what it should be right?

---

### Post by kleeman on 2005-09-16
Looks right. So you will need to compile your own module using the vendor script I'm afraid.

---

### Post by kleeman on 2005-09-18
I found this on the linux-netdev mailing list by Stephen Hemminger the developer for the new sky2 driver that supports the Yukon 2 card. The text in bold appears to explain why this driver is still buggy (see my bugzilla entry):

Here is revised patch against netdev sky2 branch.
It includes whitespace fixes, all the changes from the previous
review as well as some optimizations and timing fixes to
solve some of the hangs.

[B]The stall problem is better but not perfect. It appears that
under stress the chip can't keep up with the bus
and sends a pause frame, then hangs.[/B] This version is for
testing, and hopefully other eyes might see the root
cause of the problem.

I don't want to reinvent the ugly watchdog code in the syskonnect
version of sk98lin.  If you read it you will see, the original
driver writer and the hardware developer obviously didn't
understand each other.

---

### Post by darkjedi8359 on 2005-09-19
is there a way to use this sky2 testing module? I have still not been able to get my card running. I don't put my network under stress. Unless playing some games on cedega is stressful.. :P

[COLOR=Red]* EDIT *[/COLOR]
I just had an idea, I could install linux again on my old pc, and add the source and take the source from it... Would that work?
[COLOR=Red]* EDIT *[/COLOR]
for some reason it seems to be working, again... wierd. Guess I just had to install 5 or 6 more times before it would work? lol

---

### Post by Mr. Electric Wizard on 2005-09-19
I was not able to get mine working either (SMC9452TX).
The chip that this card uses is not the Yukon 2, but the Yukon...
I am going to try the Breezy Colony 4 Live CD.

---

### Post by Mr. Electric Wizard on 2005-09-19
Dammit, the skge driver doesn't work either with the Breezy LiveCD (colony 4)...
I mean the card won't even power on. :| 
So I guess I jumped the gun on Gigabit, huh?

---

### Post by kleeman on 2005-09-19
You haven't tried
sudo modprobe ns83820
by any chance have you?

---

### Post by Mr. Electric Wizard on 2005-09-20
no, is this a breezy driver, or is it in hoary?

---

### Post by kleeman on 2005-09-20
It's in both. The reason I ask is I did a quick google on your nic and some people were using this driver in earlier kernels. Just a wild guess on my part. After you modprobe see what dmesg gives. If nothing then this doesn't work either...

---

### Post by Mr. Electric Wizard on 2005-09-20
do I have to cd into the kernel directory to do the modprobe, or can I just open up a terminal and sudo modprobe xxx?

---

### Post by Mr. Electric Wizard on 2005-09-20
I just did a modprobe ns83820, and nothing happened.
I rebooted, still nothing happened.
The card won't even power up.
I find it highly unlikely that anyone has gotten this card to work with Linux, let alone Ubuntu.
Oh, well maybe I'll return it...

Is there any Gigabit cards that _do_ work well with Linux?

---

### Post by Mr. Electric Wizard on 2005-09-20
I have opened a case with ubuntu bugzilla to see if I can get this dang thing resolved.
Here is what has been said so far:

**Quote Ben Collins**
sk98lin will be reintroduced in the next kernel upload, just to support cards like
the Yukon that skge does not support. The sky2 driver in the current kernel is known to be unstable.

---

### Post by kleeman on 2005-09-20
Yeah just saw that. Looks like all the whining over the past 6 months has paid off at last  :smile:  :smile:  :smile:

---

### Post by kleeman on 2005-09-20
BTW I hope things go OK for you guys in Texas in the next few days with Hurricane Rita.

---

### Post by Mr. Electric Wizard on 2005-09-20
Thanks, I'm going to wait until Wed. night to make a decision on whether to leave or not.
My brother in law lives in San Antonio;  we might be going there...

---

### Post by Mr. Electric Wizard on 2005-09-21
Well, I did as suggested and tried the 9/20 daily build, and it still did not work.
 :|

---

### Post by kleeman on 2005-09-21
As of morning 9/21 the new kernel with the vendor sk98lin has not appeared in breezy yet. If you want to check whether the updated kernel has it in there do this

sudo lsmod | grep sk98

and if this shows nothing try
sudo modprobe sk98lin

and if this complains then its not there.

---

### Post by Mr. Electric Wizard on 2005-09-27
Well I just saw the Thread by Colin that states that the sk98lin driver is missing from the Colony 5 Live CD...
**Please, Please, Please, Please get this driver working before the official launch!**

> Some notable known bugs, which we hope to iron out before release:

* The sk98lin driver is missing; network cards with Yukon chipsets
will not be detected.

---

### Post by kleeman on 2005-09-27
sk98lin is now present and working for me. Happy days are here again etc etc ;-) ;-) ;-) ;-)

---

### Post by Mr. Electric Wizard on 2005-09-27
Present where might I ask?
And BTW, what is the sudo password for a Ubuntu Live CD?

---

### Post by kleeman on 2005-09-27
Latest breezy update with the 2.6.12-9.18 kernel.

---

### Post by 23meg on 2005-09-27
perfectly working here with the latest kernel as well.

---

### Post by Mr. Electric Wizard on 2005-09-27
What did you guys have to do to get it working?
Are you using the LiveCD from 9/27?
If so, what did you have to do?

***Edit***
Are both of you by chance using this card with a 100 MB switch, or are you actually hooked up to a Gigabit Switch?
This card worked fine when I was hooked up to a 100 MB router...

---

### Post by 23meg on 2005-09-27
no, i just installed the latest breezy kernel, 2.6.12-9.18.

---

### Post by Mr. Electric Wizard on 2005-09-27
From Synaptic?

---

### Post by kleeman on 2005-09-27
I also just installed 2.6.12-9.18 (using apt-get update && apt-get dist-upgrade).
Check your installed linux-image for it's version number (using synaptic). I am using a 100Mb router btw.

---

### Post by 23meg on 2005-09-27
right, it's been in the repositories since yesterday.

---

### Post by Mr. Electric Wizard on 2005-09-28
[QUOTE=kleeman]I am using a 100Mb router btw.[/QUOTE]

That's the thing, my card worked fine when connected to a 100Mb router, but as soon as I changed to a Gigabit switch, nothing...
I believe that a "generic" driver will work with this card if it is connected to a straight up 100Mb router/switch, but it requires a specialized driver for it to work with a gigabit connection.
I will do some more troubleshooting as soon as I get home from work.

I am almost wondering if it is a cabling issue?  100Mb uses 2 pairs of wires (4 wires), and gigabit uses all 4 pairs (8 wires).  Hmm, that would explain why my card worked fine when hooked up 100Mb, and will not work at 1,000Mb.

---

### Post by Mr. Electric Wizard on 2005-09-29
YEAH BABY!
It was a cable issue!


Here's the deal.  When you have 100Mb connection using Cat5 cable, you are only using 2 pairs of wires, and the other 2 pairs are not used.  But in gigabit configuration, all 4 pairs are used.  So, when I had this card plugged up to a 100Mb router, it worked fine because all the wires that 100Mb needed to function were there.  But, when I changed the 100Mb Router to a 1,000Mb Switch, one of the wires was not connected.  DOH!
So I plugged the last wire in and VOILA it started working!
:D :D :D 

Kleeman and everyone else that has helped, thanks for all your help, seriously!
:razz: 

I will post this in the other Yukon thread also!

Thanks again!

---

### Post by SGershon on 2005-10-01
Grunf!

My Marvell/Yukon on my Toshiba Satellite M40 displayed as: "Network Device not Found".

After reading this thread, I installed Breezy 5.10 on top of my Hoary 5.04.
Problem is: the Network Device is still unrecognized!

I even tried to install the driver, but it said my gcc version is not the same as the one used to compile the kernel.

What do you recommend? :confused:

---

### Post by TeKKi on 2005-10-05
same problem on Toshiba M40-142

---

### Post by kleeman on 2005-10-05
If you use the vendor package make sure you are root and issue
export CC=gcc-3.4 

in the terminal before you launch the installer for the driver.

---

### Post by Reiver_Fluffi on 2005-10-20
Hey guys, total noob to Ubuntu (although used Mandriva for about 4 months, so maybe you can class me as a total noob?)

Anyway, I am having serious problems with My Marvell Yukon Gigabit adapter, can anyone here digest the following (information I though would be useful after reading a few other threads on this subject).

ifconfig
```

craig@ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0F:EA:EB:C8:FB
          inet6 addr: fe80::20f:eaff:feeb:c8fb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19

```

ifup
```

ifup: interface eth1 already configured

```

subsequently this is what I get when I bring eth1 down:
```

craig@ubuntu:~$ sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 7766
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0f:ea:eb:c8:fb
Sending on   LPF/eth1/00:0f:ea:eb:c8:fb
Sending on   Socket/fallback

```

dmesg
```

craig@ubuntu:~$ dmesg
 size: 64 pages
[4294671.584000] VFS: Disk quotas dquot_6.5.1
[4294671.584000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.584000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.584000] devfs: boot_options: 0x0
[4294671.584000] Initializing Cryptographic API
[4294671.584000] isapnp: Scanning for PnP cards...
[4294671.938000] isapnp: No Plug & Play device found
[4294671.952000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.954000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.954000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.954000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.954000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.954000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.956000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.956000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.956000] io scheduler noop registered
[4294671.956000] io scheduler anticipatory registered
[4294671.956000] io scheduler deadline registered
[4294671.956000] io scheduler cfq registered
[4294671.956000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.957000] EISA: Probing bus 0 at eisa.0
[4294671.957000] Cannot allocate resource for EISA slot 1
[4294671.957000] Cannot allocate resource for EISA slot 2
[4294671.957000] EISA: Detected 0 cards.
[4294671.957000] NET: Registered protocol family 2
[4294671.966000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294671.966000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294671.967000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.967000] TCP: Hash tables configured (established 262144 bind 65536)
[4294671.967000] NET: Registered protocol family 8
[4294671.967000] NET: Registered protocol family 20
[4294671.967000] ACPI wakeup devices:
[4294671.967000] HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[4294671.967000] ACPI: (supports S0 S1 S4 S5)
[4294671.967000] Freeing unused kernel memory: 224k freed
[4294671.980000] vga16fb: initializing
[4294671.980000] vga16fb: mapped to 0xc00a0000
[4294672.144000] Console: switching to colour frame buffer device 80x30
[4294672.144000] fb0: VGA16 VGA frame buffer device
[4294672.156000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.293000] Capability LSM initialized
[4294673.302000] NET: Registered protocol family 1
[4294673.314000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.314000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.314000] ACPI: bus type ide registered
[4294673.316000] SCSI subsystem initialized
[4294673.316000] libata version 1.11 loaded.
[4294673.317000] sata_nv version 0.6
[4294673.317000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[4294673.317000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 22 (level, high) -> IRQ 22
[4294673.317000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[4294673.317000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xDC00 irq 22
[4294673.318000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xDC08 irq 22
[4294673.519000] ata1: no device found (phy stat 00000000)
[4294673.519000] scsi0 : sata_nv
[4294673.720000] ata2: no device found (phy stat 00000000)
[4294673.720000] scsi1 : sata_nv
[4294673.733000] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[4294673.733000] NFORCE3-250: chipset revision 162
[4294673.733000] NFORCE3-250: not 100% native mode: will probe irqs later
[4294673.733000] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[4294673.733000] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[4294673.733000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294673.733000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294673.733000] Probing IDE interface ide0...
[4294673.997000] hda: Maxtor 6Y080L0, ATA DISK drive
[4294674.252000] hdb: Maxtor 6Y080L0, ATA DISK drive
[4294674.303000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.303000] Probing IDE interface ide1...
[4294674.975000] hdc: SONY CD-RW CRX230E, ATAPI CD/DVD-ROM drive
[4294675.689000] hdd: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[4294675.740000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.740000] Probing IDE interface ide2...
[4294676.253000] Probing IDE interface ide3...
[4294676.765000] Probing IDE interface ide4...
[4294677.277000] Probing IDE interface ide5...
[4294677.792000] hda: max request size: 128KiB
[4294677.806000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[4294677.806000] hda: cache flushes supported
[4294677.806000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
[4294677.840000] hdb: max request size: 128KiB
[4294677.840000] hdb: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[4294677.840000] hdb: cache flushes supported
[4294677.840000]  /dev/ide/host0/bus0/target1/lun0: p1 p3 < p5 p6 >
[4294677.872000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294677.872000] Uniform CD-ROM driver Revision: 3.20
[4294677.875000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294678.205000] Attempting manual resume
[4294678.212000] swsusp: Suspend partition has wrong signature?
[4294678.236000] usbcore: registered new driver usbfs
[4294678.236000] usbcore: registered new driver hub
[4294678.237000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294678.237000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[4294678.237000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 21
[4294678.237000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294678.237000] ohci_hcd 0000:00:02.0: nVidia Corporation CK8S USB Controller
[4294678.237000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294678.237000] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfc003000
[4294678.290000] hub 1-0:1.0: USB hub found
[4294678.290000] hub 1-0:1.0: 4 ports detected
[4294678.293000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[4294678.293000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 20
[4294678.293000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[4294678.293000] ohci_hcd 0000:00:02.1: nVidia Corporation CK8S USB Controller (#2)
[4294678.293000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[4294678.293000] ohci_hcd 0000:00:02.1: irq 20, io mem 0xfc004000
[4294678.346000] hub 2-0:1.0: USB hub found
[4294678.346000] hub 2-0:1.0: 4 ports detected
[4294678.361000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[4294678.361000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 22
[4294678.361000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[4294678.361000] ehci_hcd 0000:00:02.2: nVidia Corporation nForce3 EHCI USB 2.0 Controller
[4294678.361000] ehci_hcd 0000:00:02.2: debug port 1
[4294678.361000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[4294678.361000] ehci_hcd 0000:00:02.2: irq 22, io mem 0xfc005000
[4294678.361000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[4294678.361000] ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.362000] hub 3-0:1.0: USB hub found
[4294678.362000] hub 3-0:1.0: 8 ports detected
[4294678.389000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[4294678.390000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[4294678.390000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APCH] -> GSI 21 (level, high) -> IRQ 21
[4294678.390000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294678.902000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:05.0
[4294678.968000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[4294678.968000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[4294678.968000] skge addr 0xfb000000 irq 19 chip Yukon-Lite rev 9
[4294678.968000] skge eth1: addr 00:0f:ea:eb:c8:fb
[4294681.451000] ACPI: CPU0 (power states: C1[C1])
[4294681.694000] Attempting manual resume
[4294681.695000] swsusp: Suspend partition has wrong signature?
[4294681.707000] kjournald starting.  Commit interval 5 seconds
[4294681.707000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.696000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.735000] Adding 979924k swap on /dev/hda5.  Priority:-1 extents:1
[4294685.960000] EXT3 FS on hda3, internal journal
[4294691.564000] parport: PnPBIOS parport detected.
[4294691.564000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294691.648000] lp0: using parport0 (interrupt-driven).
[4294691.671000] mice: PS/2 mouse device common for all mice
[4294691.709000] ieee1394: Initialized config rom entry `ip1394'
[4294691.716000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294691.951000] logips2pp: Detected unknown logitech mouse model 62
[4294692.005000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294692.400000] ts: Compaq touchscreen protocol output
[4294694.984000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294695.861000] cdrom: open failed.
[4294695.863000] cdrom: open failed.
[4294696.837000] kjournald starting.  Commit interval 5 seconds
[4294696.837000] EXT3 FS on hda6, internal journal
[4294696.837000] EXT3-fs: mounted filesystem with ordered data mode.
[4294696.843000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294696.901000] NTFS volume version 3.1.
[4294696.955000] kjournald starting.  Commit interval 5 seconds
[4294696.955000] EXT3 FS on hdb1, internal journal
[4294696.955000] EXT3-fs: mounted filesystem with ordered data mode.
[4294697.011000] kjournald starting.  Commit interval 5 seconds
[4294697.012000] EXT3 FS on hdb6, internal journal
[4294697.012000] EXT3-fs: mounted filesystem with ordered data mode.
[4294698.346000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.353000] agpgart: Detected AGP bridge 0
[4294698.353000] agpgart: Setting up Nforce3 AGP.
[4294698.371000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294698.504000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[4294698.516000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[4294698.808000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[4294698.808000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 20
[4294698.809000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294699.119000] intel8x0_measure_ac97_clock: measured 49681 usecs
[4294699.119000] intel8x0: clocking to 46758
[4294699.723000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294699.734000] shpchp: shpc_init : shpc_cap_offset == 0
[4294699.734000] shpchp: shpc_init : shpc_cap_offset == 0
[4294699.734000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294700.024000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294700.025000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[4294700.025000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[4294700.079000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fb008000-fb0087ff]  Max Packet=[4096]
[4294701.339000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea5600e663aa]
[4294701.487000] Real Time Clock Driver v1.12
[4294701.573000] input: PC Speaker
[4294701.670000] Floppy drive(s): fd0 is 1.44M
[4294701.684000] FDC 0 is a post-1991 82077
[4294702.507000] skge eth1: enabling interface
[4294702.518000] NET: Registered protocol family 17
[4294768.068000] ACPI: Power Button (FF) [PWRF]
[4294768.068000] ACPI: Power Button (CM) [PWRB]
[4294768.150000] ibm_acpi: ec object not found
[4294776.354000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294776.354000] apm: overridden by ACPI.
[4294776.900000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294776.907000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[4294777.286000] Bluetooth: Core ver 2.7
[4294777.286000] NET: Registered protocol family 31
[4294777.286000] Bluetooth: HCI device and connection manager initialized
[4294777.286000] Bluetooth: HCI socket layer initialized
[4294777.470000] Bluetooth: L2CAP ver 2.7
[4294777.470000] Bluetooth: L2CAP socket layer initialized
[4294777.480000] Bluetooth: RFCOMM ver 1.5
[4294777.480000] Bluetooth: RFCOMM socket layer initialized
[4294777.480000] Bluetooth: RFCOMM TTY layer initialized
[4294784.701000] NET: Registered protocol family 10
[4294784.702000] Disabled Privacy Extensions on device c02eb280(lo)
[4294784.702000] IPv6 over IPv4 tunneling driver
[4294794.769000] eth1: no IPv6 routers present
[4294944.092000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294944.092000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294944.193000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294944.193000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294944.618000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294944.618000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.060000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.060000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.171000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294945.171000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.250000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.250000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.334000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294945.334000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.415000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.415000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.485000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294945.485000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.574000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.574000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.633000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294945.633000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.726000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.726000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.780000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294945.780000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294945.911000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294945.911000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294946.808000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294946.808000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294946.896000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294946.896000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294948.475000] skge eth1: disabling interface

```

When I try to bring eth1 up again:
```

craig@ubuntu:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0f:ea:eb:c8:fb
Sending on   LPF/eth1/00:0f:ea:eb:c8:fb
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

From my Mandriva set up I have been able to extract the following from /proc/net/sk98lin/eth1
```

Detailed statistic for device eth1
=======================================

Board statistics

Card name                      Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
Vendor/Device ID               11ab/4320
Card type (Bit)                32
Active Port                    A
Preferred Port                 A
Interrupt Moderation           disabled
Bus type                       PCI
Bus speed (MHz)                33
Bus width (Bit)                32
Driver version                 8.23.1.3 (01)
Driver release date            Jun-20-2005
Hardware revision              v1.3

Receive statistics

Received bytes                 5177751
Received packets               30389
Receive errors                 0
Receive dropped                0
Received multicast             0

Transmit statistics

Transmitted bytes              335303
Transmitted packets            2793
Transmit errors                0
Transmit dropped               0
Transmit collisions            0

```

On the motherboard the adapter lights up, visible on a clear RJ45 (or whatever) and a light flases on the cable modem to indicate that it's receiving a signal from the computer.  Unfortunately on Breezy these indicators are as dead as a dodo!

Like I say, i'm fairly noobish, so if anyone can help it would be much appreciated.  The only other thing I can add is that I know my ISP uses DHCP, and that is how my modem is connected.  

Cheers

---

### Post by kleeman on 2005-10-20
From your dmesg listing it appears that your card is being handled by the skge
module. The people who were having problems in this thread needed the sk98lin module to get things working (this is the proprietary driver while skge is the open source driver for the Yukon I cards). To confirm my hypothesis try

lsmod | grep skge

and

lsmod | grep sk98lin

If the first gives output while the second does not then what I said above is true.
Assuming this is right you could try using the sk98lin driver instead. Try this:
sudo ifdown eth1
sudo rmmod skge
sudo modprobe sk98lin
sudo ifup eth1

One final question: What is eth0? i.e. do you have another network card as well?

---

### Post by Reiver_Fluffi on 2005-10-21
kleeman

Thanks for the quick response.

eth0 is a ICS1883 LAN PHY using a nVidia controller (My mobo uses the nforce3 chipset).  Both eth0 and eth1 are onboard.Up until now I haven't been able to get a connection through this device on Mandriva or Windows, but then again that's something I maybe should revisit, althouhg I hear that the nVidia controller is not without its fair share of problems, might be worth another try though.  Like I say I know bits and bobs, but very little about network cards!

I will try removing skge when I get home.

Cheers for your help so far....

---

### Post by Reiver_Fluffi on 2005-10-21
Now this is strange, as I have just got home from work and booted into ubuntu, I am online and didn't need to do anything.........must have done something last night, I don't know, going to try a fresh install and try to solve the problem again (I ldon't normally like to break things, but then again I need to understand how certain things work!!)

Cheers for the help, I may be back to this thread sometime soon!

---

### Post by Desintegr on 2005-10-22
Some bug report :
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14519](http://bugzilla.ubuntu.com/show_bug.cgi?id=14519)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17852](http://bugzilla.ubuntu.com/show_bug.cgi?id=17852)

This problem seems to occur with Marvell LAN Chip revision 13

---

### Post by Reiver_Fluffi on 2005-10-22
It appears I was a little bit too hasty with my last reply.  I have since ascertained that the skge driver does not activate the connection, nor does sk98lin when I remove skge and intsall sk98lin as per kleemans comments above.  The reason why I got online when I made that post was because my partner was using windows that day.  I have discovered that windows does not kill the connection to the network like linux does, it keeps is active.  As Ubuntu did not have to activate the connection, there was no problem, but when it does have to activate the connection, that's when problems arise!!

Desintegr, I take it by rev 13 you are referring to v1.3??

Cheers

---

### Post by Desintegr on 2005-10-22
I get this on my Gentoo (2.6.13 Kernel) :
0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Gigabit Ethernet Controller (rev 13)

I think &#171; rev 13 &#187; is referring v1.3.
Try a &#171; sudo lspci &#187;, and I think you will get a &#171; rev 13 &#187; too.

You can post a comment on this bug : [http://bugzilla.ubuntu.com/show_bug.cgi?id=14519](http://bugzilla.ubuntu.com/show_bug.cgi?id=14519)
And then, the kernel team could fix the module in a future kernel update.

Currently, you can try to make an new updated kernel package (2.6.13), and it should work.

---

### Post by kleeman on 2005-10-23
[QUOTE=Reiver_Fluffi]It appears I was a little bit too hasty with my last reply.  I have since ascertained that the skge driver does not activate the connection, nor does sk98lin when I remove skge and intsall sk98lin as per kleemans comments above.  The reason why I got online when I made that post was because my partner was using windows that day.  I have discovered that windows does not kill the connection to the network like linux does, it keeps is active.  As Ubuntu did not have to activate the connection, there was no problem, but when it does have to activate the connection, that's when problems arise!!

Desintegr, I take it by rev 13 you are referring to v1.3??

Cheers[/QUOTE]

I am surprised that sk98lin did not work since this is the proprietary driver. You could try out my howto at the start of this thread. Download the latest version this might help. There was a new version posted a month or two ago.

---

### Post by Reiver_Fluffi on 2005-10-24
So was I, but I think that part of the problem is that I can see no evidence of the sk98lin directory within /etc/net/, which should be there if sk98lin is installed properly and has recognised the card.  i will try the syskonnect driver later and let you know how I get on (been playing Diablo II far too much this weekend....)

Cheers

---

### Post by Reiver_Fluffi on 2005-10-24
For me, the problem is solved, well kinda.

It came to my attention that the reason I couldn't get eth0 (nvidia controller) to work was because my cable modem is a bit pernickety about mac addresses, basically I had to reset the modem in order for it to play nice with a new connection.  I should have known this when I transferred from the realtek card I had to the onboard Marvell Yukon, as that's what I had to do in that case.  Unfortunately I didn't think of that at the time.  For me this is an easy fix for now, I might download the source and create a new module, I can at least do that now!

Cheers for all your help!

---

### Post by Zahir5776 on 2005-10-30
reate tmp dir (/tmp/Sk98IKKEnQEhbaKfBZhlfQQOJ)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.12-9-386)                                  [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (3.4.5) (Kernel:3.4.5 != gcc:4.0.2)         [ failed ]
There is a version mismatch between the compiler that was used
to build the current running kernel and the compiler which you
intend to compile the kernel module with. In most of the cases,
this is no problem, but there are cases in which this compiler-
mismatch leads to unexpected system crashes

If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH system
variable:
    Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]



Please help me to solve above problem, I tried several options as mentioned in this thread but did'nt work. Thanks in advance.

---

### Post by Desintegr on 2005-10-30
You must install &#171; gcc-3.4 &#187; package.

Currently, you are using gcc 4 and it's unable to compile kernel modules.

---

### Post by Zahir5776 on 2005-10-30
Is it anywhere I can download it. I tried commands that are mentioned in the beginning of this thread, but it did not work.

---

### Post by kleeman on 2005-10-30
You need to install gcc-3.4 which will be difficult if you have no network up. If you do then

sudo apt-get install gcc-3.4
then as root execute

export CC=gcc-3.4

sh install.sh

If you have to download it from Windows or whatever go here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/)
and grab:

 gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
 gcc-3.4_3.4.4-6ubuntu8_i386.deb

---

### Post by Zahir5776 on 2005-10-30
reate tmp dir (/tmp/Sk98ImVjWpJpZYmBSWqnogEMk)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.12-9-386)                                  [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (3.4.5) (use gcc-3.4)                       [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]
C

GCC problem solved now I need to install kernel header, how to do it, My system is uptodate asper update manager, where to get kernel header? and how to install it? I am really pleased to see support among UBUNTO community thank you I really apprciate the help. I have to install Realtek sound drivers and it having the same kernel header problem. Thanks

---

### Post by kleeman on 2005-10-30
There are two linux-headers packages in the repository you need to install. The first will have the kernel number appended to it (2.6.12-9 or something). The second will have the architecture of your cpu appended to that (-686-smp or -386) chose the one corresponding to the kernel you have installed.

---

### Post by Zahir5776 on 2005-10-30
ali@sympatico:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

ali@sympatico:~$ cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

Please see how can I get necessary compilors to compile my drivers. thanks.

---

### Post by kleeman on 2005-10-30
Post your output from 

uname -a

and I'll tell you.

Also you want to comment out the backports lines in your /etc/apt/sources.list
Use a # at the start of the line.

---

### Post by Zahir5776 on 2005-10-30
this is the output:

ali@sympatico:~$ uname -a
Linux sympatico 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

---

### Post by kleeman on 2005-10-31
OK so you need
sudo apt-get install linux-headers-2.6.12-9 linux-headers-2.6.12-9-386

---

### Post by Zahir5776 on 2005-10-31
ali@sympatico:~$ sudo apt-get install linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-9 is already the newest version.
linux-headers-2.6.12-9-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
====================================================

getting same error when installing the driver.

Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]
======================================================

ali@sympatico:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Temporary failure resolving 'antesis.freecontrib.org'
Fetched 50.9kB in 33s (1538B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Temporary failure resolving 'antesis.freecontrib.org'
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


still having the same problem. dont know what to do.

---

### Post by kleeman on 2005-10-31
Try the following:
sudo apt-get install linux-source-2.6.12

sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

and then rerun the driver script

---

### Post by MiddleBrooker on 2005-11-09
Hi to all,
I'm writing this message because initially I've follow the insctruction in this thread for install the sk98lin module into my AMD64 system, after that due to the same problem [STRANGE NETWORK HANG-UP] I've upgraded to the 2.6.14 kernel.

Now the module works fine unlike the 2.6.12 version but I've always the saem problem: [STRANGE NETWORK HANG-UP] .

Sometime, every one minute during normal Internet browsing via Firefox, the network seems to hang-up and firefox is unable to ope web pages or load completely images.

Just now I'm running an apt-get update and in the meantime I'm surfing Internet so: Firefox page hang without open anything and apt-get update process blocked to 23%!!!

Please can anyone explane to me if this problem is normal or I can do someting?


Thanks for all the help!!

Kind Regards,
MB

---

### Post by kleeman on 2005-11-09
You need to be a bit more specific about your problem.

Did the network work with a standard breezy kernel?
With the 2.6.14 kernel did you run the vendor script described above or did you rely on the standard kernel module?

When I tried the standard kernel module (sky2) I got network hanging somewhat like you describe.

Also what is the output of:

lspci 

and the last 100 lines of dmesg

---

### Post by MiddleBrooker on 2005-11-09
[QUOTE=kleeman]You need to be a bit more specific about your problem.

Did the network work with a standard breezy kernel?
With the 2.6.14 kernel did you run the vendor script described above or did you rely on the standard kernel module?

When I tried the standard kernel module (sky2) I got network hanging somewhat like you describe.

Also what is the output of:

lspci 

and the last 100 lines of dmesg[/QUOTE]


Sorry, you're right!

I'm using the buitin module for the Yukon/Marvell Gigabit that is already present into the 2.6.14 that I've downloaded from kernel.org and that I've patched with this ck3 patch [http://ck.kolivas.org/patches/2.6/2.6.14/]("http://ck.kolivas.org/patches/2.6/2.6.14/")

now my dmesg is this 
```

eth0: network connection up using port A
    speed:           100
    autonegotiation: yes
    duplex mode:     full
    flowctrl:        symmetric
    irq moderation:  disabled
    scatter-gather:  enabled
CLASS: Unregistering class device. ID = 'vcs1'
class_hotplug - name = vcs1
device class 'vcs1': release.
CLASS: Unregistering class device. ID = 'vcsa1'
class_hotplug - name = vcsa1
device class 'vcsa1': release.
CLASS: registering class device: ID = 'vcs1'
class_hotplug - name = vcs1
CLASS: registering class device: ID = 'vcsa1'
class_hotplug - name = vcsa1
CLASS: Unregistering class device. ID = 'vcs1'
class_hotplug - name = vcs1
device class 'vcs1': release.
CLASS: Unregistering class device. ID = 'vcsa1'
class_hotplug - name = vcsa1
device class 'vcsa1': release.
CLASS: registering class device: ID = 'vcs1'
class_hotplug - name = vcs1
CLASS: registering class device: ID = 'vcsa1'
class_hotplug - name = vcsa1
CLASS: Unregistering class device. ID = 'vcs1'
class_hotplug - name = vcs1
device class 'vcs1': release.
CLASS: Unregistering class device. ID = 'vcsa1'
class_hotplug - name = vcsa1
device class 'vcsa1': release.
CLASS: registering class device: ID = 'vcs1'
class_hotplug - name = vcs1
CLASS: registering class device: ID = 'vcsa1'
class_hotplug - name = vcsa1
CLASS: Unregistering class device. ID = 'vcs1'
class_hotplug - name = vcs1
device class 'vcs1': release.
CLASS: Unregistering class device. ID = 'vcsa1'
class_hotplug - name = vcsa1
device class 'vcsa1': release.
CLASS: registering class device: ID = 'vcs1'
class_hotplug - name = vcs1
CLASS: registering class device: ID = 'vcsa1'
class_hotplug - name = vcsa1
ACPI: CPU0 (power states: C1[C1])
ACPI: Fan [FAN] (on)
ACPI: Thermal Zone [THRM] (40 C)
CLASS: registering class device: ID = 'vcs2'
class_hotplug - name = vcs2
CLASS: registering class device: ID = 'vcsa2'
class_hotplug - name = vcsa2
CLASS: registering class device: ID = 'vcs3'
class_hotplug - name = vcs3
CLASS: registering class device: ID = 'vcsa3'
class_hotplug - name = vcsa3
CLASS: registering class device: ID = 'vcs4'
class_hotplug - name = vcs4
CLASS: registering class device: ID = 'vcsa4'
class_hotplug - name = vcsa4
CLASS: registering class device: ID = 'vcs5'
class_hotplug - name = vcs5
CLASS: registering class device: ID = 'vcsa5'
class_hotplug - name = vcsa5
CLASS: registering class device: ID = 'vcs6'
class_hotplug - name = vcs6
CLASS: registering class device: ID = 'vcsa6'
class_hotplug - name = vcsa6
CLASS: registering class device: ID = 'vcs7'
class_hotplug - name = vcs7
CLASS: registering class device: ID = 'vcsa7'
class_hotplug - name = vcsa7
CLASS: Unregistering class device. ID = 'vcs6'
class_hotplug - name = vcs6
device class 'vcs6': release.
CLASS: Unregistering class device. ID = 'vcsa6'
class_hotplug - name = vcsa6
device class 'vcsa6': release.
CLASS: Unregistering class device. ID = 'vcs5'
class_hotplug - name = vcs5
device class 'vcs5': release.
CLASS: Unregistering class device. ID = 'vcsa5'
class_hotplug - name = vcsa5
device class 'vcsa5': release.
CLASS: Unregistering class device. ID = 'vcs4'
class_hotplug - name = vcs4
device class 'vcs4': release.
CLASS: Unregistering class device. ID = 'vcsa4'
class_hotplug - name = vcsa4
device class 'vcsa4': release.
CLASS: Unregistering class device. ID = 'vcs3'
class_hotplug - name = vcs3
device class 'vcs3': release.
CLASS: Unregistering class device. ID = 'vcsa3'
class_hotplug - name = vcsa3
device class 'vcsa3': release.
CLASS: Unregistering class device. ID = 'vcs2'
class_hotplug - name = vcs2
device class 'vcs2': release.
CLASS: Unregistering class device. ID = 'vcsa2'
class_hotplug - name = vcsa2
device class 'vcsa2': release.
CLASS: Unregistering class device. ID = 'vcs7'
class_hotplug - name = vcs7
device class 'vcs7': release.
CLASS: Unregistering class device. ID = 'vcsa7'
class_hotplug - name = vcsa7
device class 'vcsa7': release.
CLASS: registering class device: ID = 'vcs7'
class_hotplug - name = vcs7
CLASS: registering class device: ID = 'vcsa7'
class_hotplug - name = vcsa7
[fglrx] Kernel AGP support doesn't provide agplock functionality.
[fglrx] AGP detected, AgpState   = 0x1f00400b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 85831680
[fglrx] max   LFB = 85831680
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
Bluetooth: L2CAP ver 2.7
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM ver 1.5
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
eth0: no IPv6 routers present
CLASS: registering class device: ID = 'vcs2'
class_hotplug - name = vcs2
CLASS: registering class device: ID = 'vcs3'
class_hotplug - name = vcs3
CLASS: registering class device: ID = 'vcsa2'
class_hotplug - name = vcsa2
CLASS: registering class device: ID = 'vcs4'
class_hotplug - name = vcs4
CLASS: registering class device: ID = 'vcsa3'
class_hotplug - name = vcsa3
CLASS: registering class device: ID = 'vcs5'
class_hotplug - name = vcs5
CLASS: registering class device: ID = 'vcsa4'
class_hotplug - name = vcsa4
CLASS: registering class device: ID = 'vcs6'
class_hotplug - name = vcs6
CLASS: registering class device: ID = 'vcsa5'
class_hotplug - name = vcsa5
CLASS: registering class device: ID = 'vcsa6'
class_hotplug - name = vcsa6
bus usb: add driver tiglusb
usbcore: registered new driver tiglusb
/root/Desktop/tiglusb-1.07/tiglusb.c: TI-GRAPH LINK USB (aka SilverLink) driver, version 1.07
usb 2-2.2: USB disconnect, address 4
bus usb: remove device 2-2.2:1.0
PM: Removing info for usb:2-2.2:1.0
CLASS: Unregistering class device. ID = 'usbdev2.4'
class_hotplug - name = usbdev2.4
device class 'usbdev2.4': release.
DEV: Unregistering device. ID = '2-2.2'
bus usb: remove device 2-2.2
PM: Removing info for usb:2-2.2

```

lspci

```

0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
0000:02:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:02:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:02:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:08.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)

```


I'm using the sk98lin modules present into the 2.6.14 that I've statically compiled, not as modules but anyway in both method [M or Y] the problem is always the same.

I've saw this from the dmesg

eth0: network connection up using port A
    speed:           100
    autonegotiation: yes
    duplex mode:     full
    flowctrl:        symmetric
    irq moderation:  disabled
    scatter-gather:  enabled

Maybe I nedd some advanced settings?

Thank you very much for the fast reply and for all the help.
Kind Regards,

MB

---

### Post by kleeman on 2005-11-09
From my reading of the linux network fora the sky2 module (meant for Yukon II nic) is still buggy. skge (meant for Yukon I) is better. You can find out which is being used in 2.6.14 by using

lsmod | grep sk 

(You may see other modules but you should see either sky2 skge or sk98lin)

The standard breezy kernel (2.6.12-9) uses a vendor patched sk98lin and that is what works well for most people here. Is that what you were using? The above command will tell you. If skge was being loaded instead then remove it with
sudo rmmod skge

and bring up sk98lin instead with

sudo modprobe sk98lin

then bring up the interface with

sudo ifup eth0 

I am assuming eth0 is your network interface here. If you have more than one nic it might be eth1 or whatever.

---

### Post by TitoPuente on 2005-11-17
Thanks for the howto. In conjunction with the installation file of the vendor, it worked great for me. I previously had eratic problems with my onboard network chip (Marvell 88E8001) and a Breezy install but now it is solved. I am running a server setup: light and fast!
;-)

---

### Post by scantrell on 2005-12-12
I am unable to connect  to the net with Breezy-64 88E8001 Marvell Ethernet card built in to my Asus K8V deluxe motherboard.  Can I solve this by installing a new ethernet card?  If so, do you have any recs?

---

### Post by kleeman on 2005-12-13
[QUOTE=scantrell]I am unable to connect  to the net with Breezy-64 88E8001 Marvell Ethernet card built in to my Asus K8V deluxe motherboard.  Can I solve this by installing a new ethernet card?  If so, do you have any recs?[/QUOTE]
This is the same card as the previous poster however it sounds like you are using the 64 bit version of the OS. Did the vendor driver install fail?

---

### Post by Sn4ke on 2006-01-19
HI! i'm new in the forum, and i'm italian so sorry if my english is not good :p 

I preput: I DON'T HAVE INTERNET IN my BREEZY so I CAN'T MAKE "apt-get install kernel-source"

I have a toshiba m40-282 with a marvell yukon

[4294697.998000] eth0: Marvell Yukon 88E8036 Fast Ethernet Controller

i have also kernel 2.6.12-9-386 without sources and gcc 4.0 (instead of 3.4)


How can i install a good driver of my ethernet card?? I'm getting crazy ](*,) ](*,) 
If i make the command modprobe sk98lin and eth0 up it seems to work fine, but when i make pppoeconf it doesn't find any concentrator for the connection.

I don't have a lan but a ADSL connection with ethernet modem.

Thank you for help! :( 

pleeeaaseee! :(

---

### Post by Sn4ke on 2006-01-29
[QUOTE=Sn4ke]HI! i'm new in the forum, and i'm italian so sorry if my english is not good :p 

I preput: I DON'T HAVE INTERNET IN my BREEZY so I CAN'T MAKE "apt-get install kernel-source"

I have a toshiba m40-282 with a marvell yukon

[4294697.998000] eth0: Marvell Yukon 88E8036 Fast Ethernet Controller

i have also kernel 2.6.12-9-386 without sources and gcc 4.0 (instead of 3.4)


How can i install a good driver of my ethernet card?? I'm getting crazy ](*,) ](*,) 
If i make the command modprobe sk98lin and eth0 up it seems to work fine, but when i make pppoeconf it doesn't find any concentrator for the connection.

I don't have a lan but a ADSL connection with ethernet modem.

Thank you for help! :( 

pleeeaaseee! :([/QUOTE]

Thank you very very mutch for help....i erased ubuntu from my notebook! :mad: 

I installed fedora core 4 and network driver without problems !!!

i have a suggestion to you: you should also have a web repository with .deb packages or include the kernel source on ubuntu cds, so that a poor man that doesn't have an internet connection working in the installed distro and wants to download a package (like kernel-source) or install something that needs that source can download this with another computer or another OS,and not become crazy or decides to install another distro!

(I don't say anything about gcc wrong verion!!!! #-o )

best regards.

Sn4ke

P.S: hoping that Dapper 6.04 will be better

---

### Post by Sn4ke on 2006-01-30
Sorry for my vent...but i tried a simple method to make my internet connection works fine first with live edition of breezy, then reinstalling it...and it works without need to install any external driver:

booting with **acpi=noirq** and pppoeconf configured my connection in a few seconds!

Now i'm here with my new Ubuntu!:-D 

Next step is to install my Ati X700.
Bye

---

### Post by foresto on 2011-10-23
In case anyone is still struggling with this, I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

