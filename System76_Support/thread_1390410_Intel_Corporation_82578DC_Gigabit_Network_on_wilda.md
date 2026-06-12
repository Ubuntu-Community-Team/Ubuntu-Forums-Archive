---
title: "Intel Corporation 82578DC Gigabit Network on wildabeast performance machine"
date: 2010-01-25
forum: System76 Support
---

### Post by ejwettstein on 2010-01-25
I just got my new Wildabeast (wilb1) from System76 this week. I started by transferring stuff from my old PC that has a gigabit card going through a gigaibit switch. It was painfully slow.

The old PC and router are running at 1000m, but the new Wildabeast isn't. I only get one light on the ethernet connection on the back and the switch only shows 100mb.

I've switched cables and ports on the switch with no change in the computer's card.

lspci reports -- 
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)


mii-tool on eth0 reports ---

SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD flow-control, link ok


What else should a be looking at?

Thanks,
Eric

---

### Post by thomasaaron on 2010-01-25
I responded to your email on this one.

---

### Post by ejwettstein on 2010-01-26
Wildabeest Performance (wilb1)
64bit Karmic Koala

uname -a
Linux boxer-04 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

mii-tool eth0
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD flow-control, link ok

lspci | grep Eth 
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)



sudo dmesg | grep "Link is"
[253621.891654] e1000e: eth0 NIC Link is Up 10 Mbps Full Duplex, Flow Control: RX


ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

ethtool -i eth0
driver: e1000e
version: 1.0.2-k2
firmware-version: 0.12-5
bus-info: 0000:00:19.0


============
ethtool -s eth0 speed 100 duplex full autoneg off
brings it up to 100 Mbps

ethtool -s eth0 speed 1000 duplex full autoneg off
takes my card off line

===============

I can get it up from 10 to 100, but it won't go higher.

Eric

---

### Post by thomasaaron on 2010-01-27
Eric,

I'll stop communicating via email on this one and just work with you here on the forums. I have to monitor both, so that will keep me from having to duplicate responses.

We have a gigabit switch on the way for testing. It will be here this afternoon or tomorrow morning.

---

### Post by negage on 2010-01-28
I have exactly the same problem with my new intel DP55WB motherboard. In windows 7 works fine, but with Ubuntu 9.10 the network is detected with the link speed at 10M, and I can make it go to 100M but I lose the network if I force it to 1000M.
I have made a script that I have placed in /etc/init.d to force the connection to 100M after I reboot or it will come up at 10M again.

#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
AUTONEGOTI="off"
SPEED="100 duplex full"
case "$1" in
start)
echo -n "Setting eth0 speed 100 duplex full...";
$ETHTOOL -s $DEV  speed $SPEED autoneg $AUTONEGOTI;
echo " done.";;
stop)
;;
esac
exit 0

---

### Post by ejwettstein on 2010-01-29
The script will certainly help. Good thing I don't have to reboot often, but it was always a rude awakening to be back at 10!

Thank you.

---

### Post by thomasaaron on 2010-01-29
OK, we've verified that the issue exists under 32-bit Ubuntu as well. Testing with a gigabit switch is underway.

---

### Post by thomasaaron on 2010-02-04
Thanks for your patience, gentlemen. This one is fixed.

We're not yet sure how we're going to distribute the fix, and the current fix will break with kernel updates.

I'm doing some testing now to see if the fix is implemented under Lucid Lynx.

Please contact me via email for the fix (support...at...system76...dot...com).

Eric, I've already got your email and am sending the fix to you now.

---

### Post by dwhecht on 2010-02-08
I'm also experiencing this problem (mythbuntu 9.10) on my new Intel DP55SB motherboard.  Upon boot, it starts at 10Mbps connection, and I can force it to 100 Mbps, using ethtool.  However, even at 100 Mbps, I don't see speeds at all like my laptop that is also up at 100 Mbps.

I found "Intel Wired Ethernet" linux drivers on the e1000 sourceforge project.  I updated my IGB but I see no difference.
[http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

My NAS to laptop can transfer 80 MBs in less than 10 seconds, but my NAS to this new Intel DP55SB takes 4-5 minutes.  By my assessment, all the important variables are the same.  

Both fstab's mount the NAS with the same parameters too.  
192.168.0.101:/data /media/NAS nfs rw,nolock 0 0

Below is the eth0 information from my DP55SB
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:f7:ab:9b  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fef7:ab9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:454811 errors:171638 dropped:0 overruns:0 frame:171638
          TX packets:437924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:658151676 (658.1 MB)  TX bytes:42976365 (42.9 MB)
          Memory:f3900000-f3920000


ethtool eth0
Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

---

### Post by thomasaaron on 2010-02-09
dwhecht, we don't sell that mobo, so I'm not exactly sure if our fix will work for you. But if you want to send me an email at support...at...system76...dot...com, I'll send you our fix. No guarantees or warranties implied.

---

### Post by igguk on 2010-02-09
hello,

I have exactly the same problem with my new configuration : Intel DH55TC
The LAN chipset is the same : 82578D.

> igguk@cixi:~# lspci | grep Eth
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)

igguk@cixi:~# uname -a
Linux cixi 2.6.31-19-server #56-Ubuntu SMP Thu Jan 28 03:40:48 UTC 2010 x86_64 GNU/Linux

igguk@cixi:~# dmesg | grep "Link is"
[    6.349357] e1000e: eth0 NIC Link is Up 10 Mbps Full Duplex, Flow Control: RX

igguk@cixi:~# ethtool -s eth0 speed 100 duplex full autoneg off

igguk@cixi:~# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes
My system starts at 10M, I  force 100M with ethtool, if I force 1000M, LAN card died (no more LEDs).
Moreover, the  transfers are very slow, I have an average of 2.4MB/s on a 3GB file,  my network is GB and jai on another small server averaged 55MB/s.

My Ubuntu is a Ubuntu Server 9.10 and my installation is fresh this afternoon.

Have you a fix for me ?
 
Best regards.

Igguk.
( igguk...at...php4mac...dot...com)

---

### Post by dwhecht on 2010-02-09
Thanks Tom for the drivers.  I ran the update, per your instructions, but still experienced the same problem.  My network connection drops when I change speed to 1000Mbps.  I tried a reboot too, with the additional rmmod and modprobes ran again after reboot.

Currently my router is only capable of 100Mpbs, so I'm not sure if maybe this is normal activity when you don't have 1000Mpbs router to talk to on the other end?

That could just be normal operation, and I could be dealing with a different issue currently where my 100Mpbs throughput is very poor, as mentioned by the above poster too.

---

### Post by dwhecht on 2010-02-09
Additional system information.

uname -a
Linux dw-htpc 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

lspci | grep Eth
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)

mii-tool eth0
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: 100 Mbit, full duplex, link ok

sudo dmesg | grep "Link is"
[    7.227768] e1000e: eth0 NIC Link is Up 10 Mbps Full Duplex, Flow Control: None
[   58.163391] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 1073.155316] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None

---

### Post by dwhecht on 2010-02-09
Additional info:

I do receive this message each time I try to make install the e1000e driver.

cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode

The message displays at the bottom of the complete output but all other activity related to make install appears to happen without issue.  I tried sudo -s and still received the above message.

---

### Post by thomasaaron on 2010-02-10
I would think that driver should work for you, but as I said, we just don't have your particular mobo to test with. The name of that particular archive...

e1000e.7.gz

...is a bit perplexing. Please run...

ls /var/cache/man/cat7

...and see if you have a bunch of e100e gz archives. For example...

e1000e.6.gz
e1000e.5.gz
etc...

If you do, try deleting them all with...

sudo rm /var/cache/man/cat7/e100e.*.gz

...and then try running make install again.

---

### Post by dwhecht on 2010-02-10
ls /var/cache/man/cat7/ turns up no files.  Is the make install trying to write the e1000e.7.gz file to this location or update an existing file?

Do you think this "catman mode" message is even relevant to the problem?  I tried restarting my network services, after making, install, rmmod and modprobe, via /etc/init.d/networking restart but that didn't make any difference either.

---

### Post by dwhecht on 2010-02-10
Is the e1000e driver version 1.1.2 you sent the standard driver you can get on sourceforge or from Intel directly?  Did you do any modification to it?

---

### Post by dwhecht on 2010-02-10
sudo ethtool -i eth0
driver: e1000e
version: 1.1.2-NAPI
firmware-version: 0.12-5
bus-info: 0000:00:19.0

---

### Post by thomasaaron on 2010-02-11
> Is the e1000e driver version 1.1.2 you sent the standard driver you can get on sourceforge or from Intel directly? Did you do any modification to it?

Straight from Intel. No modifications.

---

### Post by gdecoster on 2010-03-14
Hello,

I have the exact same problem. My system starts at 10M instead of 1000M. I'm running Ubuntu 9.10 64-bit Desktop edition on a system with an Intel DP55WB motherboard (with integrated Gigabit NIC). The router I'm connecting to is Gigabit capable.

I managed to update the e1000e driver. The new driver works perfectly fine except that it reverts back to the old version after a reboot.
To get it back to work with the new driver I have to run sudo rmmod e1000e & sudo modprobe e1000e.

Is there a way to make the new driver “stick” after a reboot ?

For the record, here's how I updated the network driver:
1.Download latest e1000e driver from [http://sourceforge.net/projects/e1000/files/](http://sourceforge.net/projects/e1000/files/) (in e1000e stable folder)
2.cd /home/<userID>/Downloads	(default folder for FireFox downloads)
3.tar zxf e1000e-1.1.2.tar.gz
4.cd e1000e-1.1.2/src
5.sudo make install
6.sudo rmmod e1000e
7.sudo modprobe e1000e

Output of  ethtool -i eth0 after the driver update (and before a reboot)
driver: e1000e

version: 1.1.2-NAPI

firmware-version: 0.12-5

bus-info: 0000:00:19.0

---

### Post by thomasaaron on 2010-03-15
> I managed to update the e1000e driver. The new driver works perfectly fine except that it reverts back to the old version after a reboot.
To get it back to work with the new driver I have to run sudo rmmod e1000e & sudo modprobe e1000e.

You can create a start-up script for auto-loading those module insertions. I would do it like this...

Open a terminal (Applications > Accessories > Terminal), and then open a text editor by running this command...
sudo gedit /etc/init.d/99-module-insertions.sh

Then make the script look like this...

#!/bin/bash
modprobe -r e1000e
modprobe e1000e

Then click "Save" and close the text editor. Then run these commands from the terminal...

sudo chmod a+x /etc/init.d/99-module-insertion.sh
sudo update-rc.d /etc/init.d/99-module-insertion.sh defaults

Then reboot your computer for the change to take effect.

---

### Post by gdecoster on 2010-03-15
Thanks. This works great. I'm getting 1000 Mb/s at startup now.

Note for other folks who want to implement this startup script:
The script name does not need to be prefixed with /etc/init.d in the final update-rc.d command. Just enter:
 sudo update-rc.d 99-module-insertion.sh defaults

---

### Post by jllb on 2010-03-17
The fixed also worked for me. I am using Ubuntu 9.10 (64 bit). 
Thank you very much!

Antonio

---

### Post by jacao on 2010-04-11
Hi, this hint works fine but it's just a workaround nor the solution of the problem. Does anybody know how to manage this problem without additional script? How to keep the proper module after reboot? I'm having this problem on Debian 5 with the kernel 2.6.26-2-amd64. 

Regards, Jacek

---

### Post by thomasaaron on 2010-04-12
The script is the only way I know of. However, the issue is fixed in 10.04.

---

### Post by JHeenan on 2010-04-20
I'm using ubuntu server 9.10 64 bit with a "Intel Corporation 82578DM Gigabit Network Connection (rev 06)", and found I had to change the script to this:

[FONT=Courier New]ifdown eth0
modprobe -r e1000e
modprobe e1000e
ifup eth0
[/FONT]

(without the ifdown & ifup eth0 was never configured up)

I also changed the update-rc.d command to:

update-rc.d 99-module-insertion.sh defaults 10

(ie. adding 10 on the end) but I'm not sure that was significant.

---

### Post by Daniel77 on 2010-04-28
I also have an Intel 82578DC network card and running ubuntu 9.10, but it's just running at 10Mbit or it can be forced to run at 100mbit. But at 1Gbit I lose the connection. So I guess I have the same problem. I have followed this thread bu I'm still stuck on the problem:

cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode

I have tried the sudo -s in a new terminal window and there are no files in the cat7 dir.

How did you guys solve this?

---

### Post by thomasaaron on 2010-04-28
Send an email to support...at...system76...dot...com, and I'll follow up with instructions.

This issue is fixed in 10.04, so you might want to just upgrade in a few days.

---

### Post by @sushi on 2010-06-17
Please ignore this

---

### Post by mdeneen on 2010-06-28
> **jacao said:**
> Hi, this hint works fine but it's just a workaround nor the solution of the problem. Does anybody know how to manage this problem without additional script? How to keep the proper module after reboot? I'm having this problem on Debian 5 with the kernel 2.6.26-2-amd64. 

Regards, Jacek

After updating the module, do the following:

```

sudo update-initramfs -u

```

This will copy the new driver into the file used to create the boot ram disk.  The e1000e driver will be there until you change your kernel, and you don't have to monkey around with scripts at boot time.

---

### Post by ar_hnazari on 2010-11-02
Dear All

I searched alot about the problem, there are some RULES that may seem ISSUES to us.

First of all, IEEE has PROHIBITED forcing connections to 1Gbps at all and the ONLY was that you can reach 1G (and above now) is autoneg, so please stop yelling at your NIC using ethtool, because the driver doesn't let you.
you may wrestle your driver's source and try to find the code ad remove it ..... but then what looks at you angrily will be the bios of your NIC, in case you are a SUPERHERO and can revise your bios ... then the other side will not reply (eg switch or router) because autoneg starts from 10/half and then NICs start to talk about higher speeds untill they get to 1G or above if capable.

So it's better to kindly investigate other environmental matters:

1- A Cat5e unshielded cable can give you 1G only up to 70 meters in a low noise environment
2- A Cat5e Shielded cable makes is 105 meters
3- A Cat6 cable is the most wanted option for this connectivity
4- Make sure the other party supports 1G speed, most home devices such as internet routers only support 100 because in no way a home user wants to pay x4 price on the eth ports of his router
5- Update to latest driver provided by your device vendor, mostly OS provided drivers don't exactly know the abilities or changed on the hardware
6- Check the other side's port config if it's manageable, some switches or routers come with 100M/Full configured by default (don't know why, I has this issue with some 3COM and NetGear stuff)
7- Use the modprobe solution above if everything is ok
8- Be patient, by LAW, FORCING TO G speed is PROHIBITED :)

Wish you a happy 1G connection

---

