---
title: "HOWTO: Set your system up for Wake On LAN (WOL)"
date: 2006-08-11
forum: Tutorials
---

### Post by Chris Tucker on 2006-08-11
This is really common, but I haven't seen a ubuntu howto for it, people more or less peice it together from posts and blog entries and the like.

So, here it goes. First off, make sure your system supports WakeOnLAN (WOL), if you know your system well, you already know if it does or doesn't.

--

[SIZE="5"]**Automatic way:**[/SIZE]
This script does everything described in the Manual way, for you, except step 1 and step 4.
**------------------------**

The automatic method is super dialup friendly! thanks to gzip compression the filesize is a mere 1.5kb! almost half the extracted size of 3.4kb! :wink: 


1. If you havent already, go to your BIOS, and turn on WakeOnLAN (it varies, look for it.) If your network card is onboard, your set for step 2, otherwise there is *probably* a cable that should go from your network card to your motherboard, though this is not always the case.


Before continuing, note the interface you want to do this to. Most people know how to do this, if you do not, look at step 2a of the manual method.

2. Download and extract this: You can do it with the GUI and run the extracted program in a terminal by double clicking it, or open a terminal and do the following:

**** Removed dead link ****

3. As the exit of the program notes, now you just need to get/use a wake on lan sending program, like wakeonlan.

4. Sit on your lazy *** and have fun :)

--

[SIZE="5"]**Manual way:**[/SIZE]
**------------------------**
1. If you havent already, go to your BIOS, and turn on WakeOnLAN (it varies, look for it.) If your network card is onboard, your set for step 2, otherwise there is *probably* a cable that should go from your network card to your motherboard, though this is not always the case.

2. Back in ubuntu, kubuntu, xubuntu, w/e, we now need to make a script that will run every time the computer is started, because this command only lasts until the computer is turned on again once.

2a. Find out what network device you want to have the computer wake-able from, usually all, which is just one. If you have more network devices in your system, 9 chances out of 10, you already know what they are called.
**You can NOT wake up a laptop or computer that is only connected via wireless with wake-on-lan, unless the bios has a method for this, this is very rare, and I do not garuntee this howto will work in such cases.**
In your terminal, type:
```
ifconfig
```
You'll get something like: (I have removed my mac address for security)
```
eth0      Link encap:Ethernet  HWaddr 01:23:45:67:89:ab
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe6f:3487/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23164212 (22.0 MiB)  TX bytes:7625016 (7.2 MiB)
          Interrupt:217 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:161182 (157.4 KiB)  TX bytes:161182 (157.4 KiB)

```
So, I want this system to be wake-able from eth0.

2b. Now we create the script.
**Note: you must be an administrator on the system you are doing this to.**
```
sudo -i
```
Enter your password at the prompt.
Change to the startup script directory and start editing a new file:
```
cd /etc/init.d/
pico wakeonlanconfig
```

Paste, or type this into the file, replacing eth0 with your network device, repeat the ethtool line as many times for your devices before the exit line:
```
#!/bin/bash
ethtool -s eth0 wol g
exit
```

Set the permissions of the file:
```
chmod a+x wakeonlanconfig
```

Make the script run on startup:
```
update-rc.d -f wakeonlanconfig defaults
```
You should see something like:
```
 Adding system startup for /etc/init.d/wakeonlanconfig ...
   /etc/rc0.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc1.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc6.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc2.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc3.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc4.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc5.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig

```

Now we finish by running it, and making sure there are no errors.
```
/etc/init.d/wakeonlanconfig
```
This should produce no output and put you right back at the prompt you started at.

3. Use it. you'll need something to send wake-on-lan packets with, "wakeonlan" is in the repos. And you'll need the mac address of the system.

To get your MAC address, on the same system you just enabled WOL on, type:
```
ifconfig | grep HW
```
its the thing that looks like 01:23:45:67:89:ab , write it down.
turn off that system:
```
sudo halt
```

if your using wakeonlan from the repos, and you are on the same network as the computer your tying to wake up, replace 01:23:45:67:89:ab with your mac address and do, from another computer:
```
wakeonlan 01:23:45:67:89:ab
```
**In MOST cases, you CAN SEND wake on lan packets from a wireless connected computer.**
If that doesnt work, its likely the port on the system your trying to wake up isnt the default (9), try 7, or if your BIOS settings or book told you one, use that one.
```
wakeonlan -p 7 01:23:45:67:89:ab
```

If that STILL doesnt work, make sure wakeonlan is enabled in your bios and your hardware supports it.

*Note: It has been said that you need to disable -i from halt, however I have never had to do this, nor do I know how.

4. Sit on your lazy *** and have fun :)

Feel free to post any questions, suggestions, problems and I will tend to them ASAP.

Added notes:
* For this to work, most systems must be shut down properly, ie: with the power button or halt, or any of the ways to shut down. Unclean power-offs (like a power outage or holding the power button for 5s) seem to stop WOL from working untill the system is powered on and shut down properly. Though, there my be a few exceptions. This is a hardware issue with the BIOS. In my opinion, WOL should work regardless of how the system is powered off, but thats not the case. I suggest, if you have frequent power outages, that you have your BIOS set to Power ON after a power failure, most new systems allow this.

---

### Post by hvollebregt on 2006-08-25
Many Thanks Chris, for this clear explanation. It saved me a lot of time.. I am very new to Linux, and already found how that the ethtool wol settings aren't persisted, but I didn't figure out yet how to make my system remember them.

The only problem I now have is: my computer wakes up within a minute after shutting down. *Something* wakes it up (which gives me hope that WOL *is* actually working on my system) but I want it to start up only if *I* send a magic package of course! I did set the wol setting to: g. 

Do you have any idea what could be causing this? In the mean time, I am going to check my bios settings.. 

Cheers
Hans

---

### Post by hvollebregt on 2006-08-25
Yep! It works! The problem was in the BIOS settings. I set the Wake on PCI Card setting to Yes, and disabled the Wake on PCI Master (which was probably causing the computer to start up too soon)

BTW I start my Ubuntu box from a Windows XP system using the Magic Packet Sender utility ([http://magicpacket.free.fr/]("http://magicpacket.free.fr/")) that's connected via a wireless network. It works like a charm.

Thanks again,
Hans

---

### Post by Chris Tucker on 2006-08-27
Hm, the wake on pci thing could be what puzzled me about some systems i came across before.... i thought there was a wakeonlan thing going on, because within 1 hour, about 3 computers in a lab where i worked would randomly turn on if you turned them off... puzzled the hell out of me.

thanks, and have fun being lazy ;P

---

### Post by Chris Tucker on 2006-08-27
Automated script now available. Currently only supports 1 interface, more means manual. Version 1.0 of the script should be up within 48 hours that supports multiple interfaces.

enjoy :D

---

### Post by sonny on 2006-08-30
How do I wake on WAN my pc? I've tried wakeonlan within my network, but I can't access it outside my network.

---

### Post by Chris Tucker on 2006-08-30
if you use the command "wakeonlan" without the -p option, then use your router to forward port 9 UDP to the computer on the internal network... not sure how well this works with a router, as when a computer is off, it doesnt have an IP to forward to! after that, you'll need a utility that sends the packets over the internet to an ip.
I havent done any research into this precise aspect of wake on lan, At least one of my systems is on at any given time, and they all have custom SSH ports forwarded. All I have to do when waking from the internet, is find a system thats on, ssh in, and send my packets through that....
if you get it working from the WAN, post what you had to do, so that I can add it to the guide!

---

### Post by Waste on 2006-08-30
Just a quick question as I am not familiar with the uses of WoL.
What it useful for?
Security?
Convenience?

---

### Post by Chris Tucker on 2006-09-01
Its not really useful for security, more convienience.
for instance if you have a computer say, in your basement, that you dont always use, and you turn it off. Before you go there you want it to be on and ready, and your near a computer on the 2nd above ground floor. You can wake it up before you head there.
etc, its more or less useless elsewise, because of bios-specific limitations (such as if the power goes out, most systems wont wake up untill powered on and properly shut down)
But, if you can imagine a need to turn on a computer without touching it, WOL is the solution to that need.

My personal main and only use is remote administration while still living at my parents (this need will be gone in 3 days, as i am moving, so i no longer have a use for WOL) Their PC is in the living room, and i usually do most maintance tasks (updates/installs) from my terminal in my room via VNC and ssh. rather than going to turn on the system and come back, i simply use WOL.

---

### Post by heavyt on 2006-09-01
> **sonny said:**
> How do I wake on WAN my pc? I've tried wakeonlan within my network, but I can't access it outside my network.

This wiki may help [http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL)

---

### Post by Thazzil0 on 2006-09-04
hm...I still have problems with this wol-stuff.

I followed the HOWTO and I did set the wol setting to 'g'.
But it don't wanna work.
By the way, if I shut down WinXP, it WORKS!, just when I worked with Kubuntu before, even if the wol setting is set correctly, I can't wake up the computer.

I tried to do this via ssh from my Asus wl-500g Premium.

Any ideas?

thx!!

Thassilo

---

### Post by incubus on 2006-09-10
Thassilo,

Have you tried the other flags? Do you have proper support for your card in linux?
$ sudo ethtool ethX

In my case I have a realtek card which supports WOL in windows, but not in linux. (Even with the latest r1000 module) I've already contacted realtek. They acknowledged the problem and said they would work on it, but this is the kind of thing that requires a lot of people requesting.

incubus

---

### Post by wheatear on 2006-09-13
Hi,
first off, thanks for helping educate the masses (including myself) about the intricacies of wol...

Here's where I am with trying to get it going:  I have Kubuntu 6.06 Drakey-whatsit on a Dell Optiplex with a 3Com 3c905 NIC.  Last night I successfully executed one remote wake up on my LAN but I did it by turning on the Kubuntu PC and turning it off about two seconds later.  I noted at that point that the LED at the back of the NIC was still lit.  Then I sent a magic packet from my other PC and lo and behold the Kubuntu machine turned on.

Now, the problem is that when I shut down Kubuntu (properly or otherwise), the LED on the NIC goes out and consequently WOL doesn't work.

I tried your script and I tried manually issuing the command

% sudo ethtool -s eth0 wol g

but it gives the following error:
Cannot get current wake-on-lan settings: Operation not supported
not setting wol

So, I know the hardware supports WOL and it is enabled in the BIOS but for some reason, Linux does not shut down to the correct power state and the ethtool does not seem to work with my NIC.

Any help would be greatly appreciated,
Eugene

---

### Post by incubus on 2006-09-18
Hey wheatear,

I got the same problem. In my case, the linux module doesn't support WOL. It works in windows.

What do you get from:
$ sudo ethtool eth0

And what is your network card, by the way?

incubus

---

### Post by wheatear on 2006-09-19
Hi Incubus.

Thanks for the reply.  The command you asked about produces the following for me:
---------------------------------------
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Full
                                100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes
---------------------------------------

As I mentioned earlier, I have a 3Com 3c905 network card.

By the way, have you come across this yet:

[http://www.linuxquestions.org/questions/showthread.php?t=444793]("http://www.linuxquestions.org/questions/showthread.php?t=444793")

The guy there seems to have overcome the same problem by installing some alternative network driver... Haven't looked into that yet myself.

Thanks again,
wheatear

---

### Post by incubus on 2006-09-20
Hi wheatear,

I see good and bad news.

The bad news is that, as you already noticed, your current netcard module (for this specific linux distribution) doesn't support WOL. You can see that you don't have the lines like the other guy has:

> 
....
Supports Wake-on: g
Wake-on: g


Now the good news: from what you said and from the other forum thread, you can compile a module for your network card that does support WOL. That's huge. And it's not so complicated. I would:
$ sudo apt-get install build-essential checkinstall linux-headers-`uname -r`

Then at your gunzipped module directory:
$ ./configure
$ sudo checkinstall -D

Note that this doesn't work for me. I don't have an option except for waiting the Realtek guys to sit down, have mercy, and make the module for linux that supports WOL.

Let us know if you're gonna try to compile it and need help.

best,
incubus

---

### Post by Hviid on 2006-09-26
Hi
I also have problems with the wake on LAN function on my system, I have tried following the guide, but with no luck.

But when I power off just after start(mechanical, using poweroff button) or from windows. I can get it started with magic packages.
I have tried both etherwake and wakeonlan.

ethtool gives me.

Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes
So looks like it supports WOL with magic packeges, could it be the power state my system goes into on Halt. As far as I know it should be soft-off.

Hviid

---

### Post by Hviid on 2006-09-26
I found the answer for my problem.

[http://www.nvnews.net/vbulletin/showthread.php?t=70384](http://www.nvnews.net/vbulletin/showthread.php?t=70384)
Last reply.

;) Hviid

---

### Post by mslonik on 2006-11-04
Thank you Chris for this description. I have one important question: what is a purpose for that script that was added to the description? As far as I know WON (Wake On Lan) mechanism is fully based on hardware and is OS (operating system) independent. If you want to use WON you need just a motherboard with BIOS enabled feature of WON and NIC with WON enabled future. That is all. If you are able to boot up a PC remotely that you are able to load any OS. Did I miss something?

Kind regards,
Maciej

---

### Post by frafu on 2006-11-05
@mslonik

I assumed the same until I had to use it practically. 

Now I think it is like this: 

When wol is enabled and the computer is powered down, not all components of the computer are shutdown: for example I suppose that at least the ethernet port has to remain active in order to process the wol magic packet. 

I suppose that the script configures the computer to keep the ethernet active. 

Moreover, I have discovered the following with my hardware: if I pull the power supply plug from my computer and connect it again, the wol does not work any more. I have to start the computer with the poweron button. Afterwards wol works again. 

frafu

---

### Post by jalonsom on 2006-11-09
This script was not working, and I saw that the LED in my router corresponding to the computer I wanted to wake was going off when I powered off the computer.

So I decided to try to remove -i from halt as suggested, and it worked!!!

This is what I did (I'm running Edgy), I warn you that I am not an expert so I don't know if it's OK to do this:

- Make a backup of the /etc/init.d/halt script
- edit the /etc/init.d/halt script
- Locate the line where the halt command is invoked:
```
halt -d -f -i $poweroff $hddown
```
- Remove the -i

That's it. Hope it works for you!!

---

### Post by mslonik on 2006-11-12
Some general remarks on Wake on Lan. First, after some trials on hardware and careful examining all former answers I found the following procedure useful for testing if hardware compoments are ready (compliant) with this technology.

Hardware components:
1. BIOS / motherboard.
2. NIC (Network Interface Card) or Netword Adapter.

Procedure:
1. In BIOS of your motherboard enable WOL functionality (typically in Power Management Setup branch of BIOS options). Is your motherboard compliant to PCI 2.1 standard?
YES | NO

2. Check if for sure your NIC is WOL compatible. Is your NIC compliant to PCI 2.1 standard?
YES | NO

3. Check if your power supply is ATX compliant:
YES | NO

If answer to this question is NO than sorry, you can not use WOL functionality.

3. If answers to questions 1. and 2. are YES than you don't need WOL cable. If any answer to questions 1. and 2. is NO than you need WOL cable. Connect your NIC with motherboard with special WOL cable. See your hardware manuals if any doubts.

4. Experiment. Set your BIOS function WOL enabled and PC in shutdown state. Check if diode on the switch that your NIC is connected to is lit or flashes.
YES | NO

Remark: If NO than there is a problem. Try to boot up your PC and correctly shut it down. Check again.
Remark: Sometimes NIC vendors add a diode for constant monitoring of LAN activity. If BIOS function of WOL is enabled than also diode on your NIC flashes together with diode on a switch. Check your NIC manual if any doubts about diodes functionality.

5. Experiment. Set your BIOS function WOL enabled and PC in shutdown state. From the other computer on the same LAN send MP (Magic Packet) to your PC. Does it awake your PC?
YES | NO

Remark: It should wake it up. Try to boot up your PC and correctly shut it down. Check again.

6. Experiment. Set your BIOS function WOL enabled and PC in shutdown state. Switch off a power supply for at least 10 seconds. Observe if a LED on a switch lights off. Now switch on a power supply. From the other computer on the same LAN send MP (Magic Packet) to your PC. Does it awake your PC?
YES | NO

Remark: My computer does not. Perhaps some people will find their hardware working on these conditions. Please report on that. In my opinion this is one of the weakest points of the whole WOL idea. If there is power loss in your home than your computer can not be awaken remotely. It should be this way, but it seems that most of the NICs do not fulfil this requirement. This fact is very seldomly reported. All I was able to find was honest report of one vendor here: 
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=SF06-D0035](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=SF06-D0035)
Such a feature as remote wake up after power loss just should work. 

7. Experiment. Set your BIOS function WOL enabled and PC in shutdown state. Wake it up with MP (Magic Packet) send from another PC on your LAN. As soon as it starts to boot and beeps single (end of POST procedures) press power button on a chassis and turn it off again. Now send MP again. Does it wake up your PC?
YES | NO

Remarks. Again, it should wake up your PC. If it doesn't than some problems may occure with your system and "clear shutdown".

Answers to above quiz on my hardware:
1. YES. Motherboard: Abit SA6R. Tweaked BIOS (self made) basing on 7X version.
2. YES. Compaq PCI 10/100 WOL, MPX EN 5038 B. Hard to say what piece of hardware it really is. I used to have 3COM 905C TX-M. Unfortunately this one wasn't working with WOL at all on Linux or even Windows. Strange, but true.
4. YES.
5. YES.
6. NO.
7. YES.

Now, the software part of WOL mechanism:
1. OS (Operating System), especially so called "halt scripts".
2. NIC driver.

Remarks: People in this thread reports that special script is required or at least some tweaks with halt script to enable OS clear shutdown with NIC still powered after shutdown. If your hardware passed the above procedure in similar to my than likely you don't need any special script. Nevertheless I've never tried wake on states different from S5 (ACPI). Perhaps such a script is required for S4 (hybernate state).

Remark: I don't feel comfortable with Linux drivers, so please get me right if I'm wrong but driver for NIC is a standard part of a kernel and there is not much to do, at least with standard kernel that comes with distro. Your NIC should work out of a box.

Remark: The rule of a thumb no. 1. If WON works on Windows, it should so on Linux. If your NIC doesn't work on Linux (or you suppose a problem) take it off your PC and put into another one managed by Windows. Check if it works there. 

Remark: The rule of a thumb no. 2. NIC 100 Mbit cards are very cheap nowadays. Borrow one that works with WON from your friend. Now check if yours works with your friend's hardware. Try to exchange with your friend on the NICs.

I hope that this short summary will be of any help to somebody. Good luck!

mslonik (Maciej)

---

### Post by cenobyte on 2006-11-29
Has anyone had any luck with the broadcom b44 network drivers and wake on lan with Edgy? It doesn't seem b44 supports it as ethtool shows nothing.
I cannot get the bcm4400 drivers to compile either. Wake on Lan works on my machine both in windows and in slackware. Cannot get it working with edgy

---

### Post by zasf on 2006-12-24
mslonik, thanks for your very good reply, but I still need some help

my NIC is a DFE-528TX, wich is said to support WOL and PCI 2.1, see [dlink page]("http://www.dlink.it/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oVIF4kP98f8p8M6tj5jkkBSnryiFE/YQIBtw="), my rather old motherboard is [QDI KuDoz 7]("http://www.qdigrp.com/qdisite/eng/products/Kudoz7.htm"), if I look at the page and manual, I don't see any evidence that the motherboard supports PCI 2.1, moreover it has a WOL connector on it.. wich leads me to think it does only support WOL trough the cable, is that the case in your opinion??? If so, either I change mobo or NIC :(

---

### Post by mslonik on 2006-12-24
Hm... As far as I investigated issue of WOL cable connector, many motherboards producers add it for the purpose of compatibility with old NICs. So even if you have modern motherboard (PCI 2.1 compliant) still you can find WOL cable connector. Nowadays it should be fairly easy to find such a cable in a second hand shops or on ebay. I'm not sure from when PCI 2.1 is a standard. You can try to check if your motherboard was produced after.

I hope that this explanation is of any help. Merry Christmas!

mslonik (Maciej)

---

### Post by moon2js on 2007-01-29
Does anyone know how I can check to see if a computer doesn't have wake-on-lan functionality?

I have two older Gateway brand computers, one bought in 1999 and one bought in 2001. I'm working with the newer 2001 one and I just updated the BIOS and there is no mention of wake-on-lan in the BIOS menu options at startup. There is mention of reboot after power outtage.

Does this mean that this computer cannot wake on lan?

The reason I'm asking is that the older Gateway computer (1999) does have the wake-on-lan in the BIOS menu options and I'm a bit confused.

---

### Post by sincewednesday on 2007-02-01
Missed Hviid's post the first time through... basically, due to a driver bug, nForce4 boards need the MAC address reversed to successfully wake.  So instead of wakeonlan 00:01:02:03:04:05, use wakeonlan 05:04:03:02:01:00.

---

### Post by xlr8or on 2007-03-08
3com 3c905c users may benefit my solution here:
[http://www.ubuntuforums.org/showpost.php?p=2265597&postcount=5](http://www.ubuntuforums.org/showpost.php?p=2265597&postcount=5)
There's how I got it to work for my dapper install.

---

### Post by mslonik on 2007-03-12
Now I run Edgy Eft (Kubuntu 6.10) on my machine. I've checked your way for WOL on 3c905x. It does not work for me.

Kind regards,
Maciej (mslonik)

---

### Post by rklauco on 2007-04-19
> **Hviid said:**
> I found the answer for my problem.

[http://www.nvnews.net/vbulletin/showthread.php?t=70384](http://www.nvnews.net/vbulletin/showthread.php?t=70384)
Last reply.

;) Hviid

Thanks a lot.
You saved my life!
It is working, finaly!
Thanks again to all that submit these great ideas to forum and share them with the rest of the world.

---

### Post by dirk_k on 2007-04-22
thanks Jalonsom! removing the -i from the halt script finally worked for me!

---

### Post by jis on 2007-05-22
mslonik, in [Wikipedia]("http://en.wikipedia.org/wiki/Wake-on-LAN") it is told that "systems supporting the PCI 2.2 standard coupled with a PCI 2.2 compliant network adapter typically do not require a WoL cable as the required standby power is relayed through the PCI bus." So maybe PCI 2.1 is not enough.

---

### Post by jis on 2007-05-22
I wonder, if it is any disadvantage to use the WOL cable, if the system can wake up without? I did not find the setting for wake on LAN in my computer's BIOS setup, but there is setting where you can enable or disable PME wakeup events. Well, there is some information about PME vs. WOL in [Intel's site]("http://www.intel.com/support/network/sb/cs-008459.htm"). Don't they tell that you should enable the WOL setting in BIOS, if you want to use the WOL cable for remote wake up? Anyway, when I have it connected and poweroff by the power button, I've got the light there in the Ethernet card of the computer. I don't have the light, if I don't have the cable there, even if I have enabled the PME Wakeup Events in BIOS. Anyway, sending the magic packet (by wakeonlan) won't wake up the computer. If I shut down by ubuntu, the light goes off, even if '-i' is removed from /etc/init.d/halt. I have not tried other tweaks in ubuntu with this system so far.

Computer specifications:
Compaq Deskpro EP series Pentium III (500MHz); I suppose it is PCI 2.1 compliant.
Ethernet controller: [3Com Corporation 3c905C-TX-M]("http://www.3com.com/products/en_US/detail.jsp?tab=prodspec&sku=3C905C-TX-M&pathtype=purchase") 

lspci output:
```
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:00:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
0000:00:0e.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 06)
0000:00:0f.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
0000:00:10.0 Communication controller: Conexant: Unknown device 10b6 (rev 89)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 82)
```

---

### Post by jis on 2007-05-22
Do you have to use some other method than sendig a magic packet to create a PME wakeup event? Or should I disable PME wakeup events when using the WOL cable and run wakeonlan in another computer? (I still cannot find a "Wake on LAN" settion in BIOS. When I use the cable, I can get the NIC light on after reconnecting the power plug or using the power button twice, but not by 'sudo shutdown -h now'. Magic packets don't work at all with this computer. When the same kind of ethernet controller was in another machine, I could wake it up, if the NIC (i.e. ethernet controller) light was on.

---

### Post by jis on 2007-05-24
How can you  cancel the changes made to your system when following the instructions in the first post?

---

### Post by nuddelmaddin on 2007-06-17
i have a problem with wol. i tried to set it up using "ethtool -s eth0 wol g" and it gives no error back. but when i'm using ethtool eth0 after this, it still shows wake-on: d... wol is activated in bios. acording to ethtool the card supports wol. anyone an idea?

edit: it seems, that the card doesn't work right... other card, works fine.

---

### Post by castor troy on 2007-06-20
I also cannot get WOL to work - ethtool listed below;

        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

Machine is a Dell Optiplex GX260 - bios has WOL set to on - and low power mode disabled. Cannot get any wol program to send a packet - tried about 5. Also tried removing the -i from the halt script.

Any ideas?

---

### Post by rklauco on 2007-06-25
Well, can't help - the config works perfectly for me.
The only problem was with the n-force chipset, where I had to send the MAC address in reverse order, e.g. instead of 00:01:02:03:04:05 I had to send 05:04:03:02:01:00 - some bug in the net card, or so, did not investigate any further.
Let us know if you will be able to fix the problem.

---

### Post by zeigerpuppy on 2007-07-10
is it possible to use this function to turn OFF the computer?
Wake-on-lan is working beautifully but I would like to be able to power down my server remotely too

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
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

---

### Post by rklauco on 2007-07-10
> **zeigerpuppy said:**
> is it possible to use this function to turn OFF the computer?
Wake-on-lan is working beautifully but I would like to be able to power down my server remotely too

Is there some problem to login and run init 0 command? Simple openssh-server will do the trick...
Basicaly, as it is server, I prefer not to shutdown, just use some disk powersaving using hdparm.
And, you still can use powersaving to turn off the whole machine if not used for an hour or so.

---

### Post by Big_Croc7 on 2007-07-20
Also, this can be adapted to work over an always-on internet connection.  This method can also be used to turn on a computer from a WAN or over the internet (perhaps its most useful application).  Assuming you're using a router, the procedure is as follows:

1. Set up WoL within you LAN, as above, and check that this all works.

2. Set up a port forward on your router.  Exactly how you do this depends on the make of router.  Typpically, you would forward port 9 from the external connection to port 9 on your LAN - though which port you use on you LAN actually doesn't matter, since the machine listens on all ports.  Most remote applications allow you to set the port as well.
Since the machine won't have an IP address (as its switched off), you have to forward the port to a broadcast address on you local network.  There are three methods to try for this:

a.  The simplest is to use the limited broadcast address 255.255.255.255; however, most routers won't do this for security reasons.  

b.  Use your local network broadcast address.  This is found from your address and subnet mask - for example, if your IP addresses are like 10.0.0.x and your subnet mask is 255.255.255.0, the broadcast address will be 10.0.0.255; again, some routers won't allow this.

c.  If neither of the above works, try changing the subnet mask to e,g, 255.255.255.128; (this gives you 126 possible IP addresses).  Then your broadcast address will be e.g. 10.0.0.127; this should hopefully work.

3. Then test it!  From a remote machine, you can either use a program such as wakeonlan in the repos or one of a number of websites that sends the magic packet to your specified address.  If your computer turns on, success!

---

### Post by ltcmdata on 2007-07-23
Hi!
I am trying to use WOL using the script provided.my problem is that whenever I enable "wake on pci card" in the BIOS my computer won't shut down, it goes as if I am doing a normal restart.in the BIOS in the power management menu there is also an option "PCI master" which I do not entirely understand, but it doesn't have the same effect.
My hardware:A Realtek RTL8139D NIC on an Elitegroup PM800-M2 motherboard.
Any help will be much appreciated.

---

### Post by markonhismobile on 2007-08-17
First off thank you for the handy little script! I knew what was happening (the wol setting is lost on powerdown) but didn't have the linux knowledge to yet implement a fix! I can also confirm this has worked on my Feisty install!

In regards to waking up PC's over the internet the method I use is going via my router - I have a Linksys WRT54G running DD-WRT, which allows for SSH management and with some tunneling I can access the router setup pages and use the built in WOL function :-)

---

### Post by whistlerny on 2007-09-03
I just registered to say thank you for the post, everything worked perfectly.

The forum registration was painful, FF2, wouldn't let me escape the modal box regarding the PM on initial registration to allow pop ups for one sec, page autorefreshed before I could even move a mouse there and hit allow, after I allowed, it just reloading until I closed the tab and came back. Strange.

---

### Post by olet on 2007-09-04
Hello, thank for HOWTO. There was no problem to set it up. But I still have one weird problem. Maybe it will be CHALLENGE for somebody. I have automatically installed via rhine 2 driver module for my ethernet card. When I want to wake the computer up, it wakes up....but only once!!! After magic packet starts computer, my sytem normally boot up. After that I halt computer back and try one more time WOL but second time it does not work. I experienced that after pulling power cord out from PC(or after upgrade to higher version of system) for a moment, boot up and halt it works....but again only once. Maybe something what cut off power from NIC can help but I don't know how to do it. Or something what "reload" completely card, it's configuration and drivers, but modprobe via_rhine -r and modprobe via_rhine -i does not work. THANK YOU for your advices.

---

### Post by 655 on 2007-09-15
I have a Linksys 10/100 Etherfast NIC and Wake on Lan is enabled in the BIOS.
After manually creating the script per the tutorial, and attempting to test the functionality via: 

sudo /etc/init.d/wakeonlanconfig,

the following is returned:
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

Furthermore,  sudo ethtool eth0 returns:
Settings for eth0:
No data available

From what I had read, I thought this card supported Wake on Lan in both Linux and Windows.  It seems strange to me that no information is being returned via ethtool.

---

### Post by jacek2 on 2007-09-23
I do power ON/OFF my PC from remote locations using browser and this card:

  [https://ool-43537bf6.dyn.optonline.net/Power%20Web%20Button.htm](https://ool-43537bf6.dyn.optonline.net/Power%20Web%20Button.htm)

---

### Post by Choad on 2007-10-11
i just set up deluge web UI which is super cool

was wondering, can i set up WOL so i can wake it from anywhere. was thinking all i'd need to do is forward the correct port on my router. i already have a dynDNS account... this could be something very cool.

---

### Post by njparton on 2007-11-01
Hi, I followed these steps successfully a few weeks ago when I initially set up my ubuntu system. To start with I was using the onboard nic (eth0).

I've just added a PCI-E gigabit card that supports a wider range of wake on lan functions (umb and g) and I need to perform this step again for eth1 (eth0 now disabled).

However, I cannot do this until I undo what I did for eth0, but I can't figure this out. How do I reverse the eth0 additions to the startup scripts? Thanks :)

---

### Post by juanto on 2007-12-10
Hi all,

before all thanks for all the information.

I have an issue... in my case the wol runs but not always. 

If I power off a machine (sudo halt) and then send the magic packet, the machine power on.

But If I power off today that machine and tomorrow morning I send the magic packet, the machine doesn´t power on.

Someone could know why it happens?

Thanks a lot.

Juanto.

---

### Post by njparton on 2007-12-10
It's probably down to the way you shutdown your machine.

Sudo halt for me kills all processes and _doesn't_ allow WOL, but just hitting the power button is OK.

---

### Post by juanto on 2007-12-14
Hi,

the problem is that if I do "sudo halt" and next I send the wakeonlan the machine power on.

But if I send the wakeonlan after serveral hours, the machine cannot power on.

¿?:)

---

### Post by njparton on 2007-12-14
What hardware do you have? Onboard NIC or PCI/PCI-E card?

I have to install the latest Intel drivers for my NIC to enable all functionality (e.g. increasing MTU) even though it is recognised by the kernel. 

Are there updated drivers available for your NIC?

---

### Post by juanto on 2007-12-17
Hi,

my computer is a Dell GX280, it has an onboard NIC.

The issue is that I don´t understan why in some cases wakeonlan runs and in others it doesn´t work.

Case in which always it runs:

    Send the wakeonlan subsequently you have power off the machine.

Case in which always it doesn´t run:

    Send the wakeonlan after several hours.

---

### Post by njparton on 2007-12-17
It sounds like a driver issue to be honest or maybe even an ACPI issue.

Your BIOS (via ACPI) may cut power to your MB a specified time after shutdown, hence you can WOL shortly after shutting down, but not several hours later (I'll admit to clutching at straws with that one!).

A driver issue is more likely. As you're using an onboard NIC, try to determine the driver it's using and then search for help on that specifically.

---

### Post by BatPenguin on 2007-12-17
Hello,

I've gotten this to work perfectly over the LAN but from the internet i'm not having much luck. I did all the steps from an earlier post by Big_Croc7 that suggested changing settings at the router if it doesn't work right away.

I'll list my setup here in the hope that one  you could see a wrong setting somewhere that might be the reason why it's not working. I'd be happy to try anything you can think of, so please, all suggestions are welcome :). 

So: from the LAN, no problem at all. Wakes up nicely to the magic packet. From the internet, doesn't work. So the MAC address and Ubuntu settings, BIOS etc. are fine, it's tested plenty of times from within the LAN. 

The router is a "TelewWell TW-EA510 ADSL Firewall Router". I have my computer connected through cable at 192.168.0.7. All local addresses are 192.168.0.X. 

At the router I have set the following

```
SubNetmask  	255.255.255.128

Virtual server rule: Forward ports 9 and 7 (UDP & TCP) to 192.168.0.127 
```

This doesn't work. Did I get the broadcast address right for a LAN of 192.168.0.X?  I've also tried simply forwarding 9 and 7 to the correct IP address (192.168.0.7) and that doesn't do it either (the internal IP stays the same so I thought it might, but it doesn't).

Any ideas? I'd really like to get this going so I don't mind trying whatever you can think of. Also, please let me know if I left out some important detail about the setup. Since it works from within the LAN, it seems like the problem is the router.

---

### Post by Big_Croc7 on 2007-12-18
Hmm... the settings seem ok... what did you use to send the packet?  A page I've used in the past is [http://www.depicus.com/wake-on-lan/woli.aspx](http://www.depicus.com/wake-on-lan/woli.aspx) , though there are lots of others.  One thing to note, is that using this, you should set the subnet mask on the web page to 255.255.255.255 (with your external IP address - it uses these to decide where on the internet to send the packet to, so the subnet mask you enter here is different from your local network mask).

The settings for your router seem ok, and yes, that's the right broadcast address.  Is that the address that you used for testing within your LAN?

---

### Post by BatPenguin on 2007-12-18
> Big_Croc7;3972585 One thing to note, is that using this, you should set the subnet mask on the web page to 255.255.255.255 (with your external IP address - it uses these to decide where on the internet to send the packet to, so the subnet mask you enter here is different from your local network mask).

Thanks for the quick reply. OK, I've been using the same web page to try this but I wasn't setting the subnet mask to all 255's. So that sounded like a great idea, and I tried that now - but unfortunately still no go.

From within the LAN, I've been using my laptop to send either this:

```

wakeonlan -i 192.168.0.127 00:50:8D:9A:73:5D
```

or simply 

```

wakeonlan  00:50:8D:9A:73:5D
```

Both seem to do it just fine so I don't actually know if naming the broadcast address does much there, seems like it's the default somehow when I try it from within the LAN.

I did notice something though: the web page seems to have dashes instead of colons for the MAC address (like 00-XX-...). I tried both ways but was unsure which one is the correct for that page. Which ones do you use for that page?

I've also been trying to use the laptop to send that same terminal command to the external ip, and it won't wake up.

The router's config page has the following for each rule:

Protocol (BOTH selected for TCP and UDP)
Public start port 7
Public end port 7
Mapped Private IP Address 192.168.0.127
Mapped Private Port 7

The page says "Leave blank or input 0 indicating Virtual Server Service" at the final field, and I've also tried leaving it blank.

I'm starting to think that this router just doesn't handle this broadcast address thing for some weird reason. Could that be the case? I do hope I'm missing something really obvious here...

---

### Post by Big_Croc7 on 2007-12-19
It does sound like something weird is happening with your router; can you check the logs on the router, and see if that tells you anything? It would be useful to know if the router is getting the packet and dropping it, or it's not getting there at all.  You could try forwarding a higher-numbered port, just in case there is something happening with those ports (the magic packet can be on any port at all, it should still work).

As an aside, I think the default for wakeonlan is to send to the IP address 255.255.255.255.

---

### Post by Big_Croc7 on 2007-12-19
I've just had another idea.  You can set the card to wake up the PC from a variety of different packets.  In the howto at the start of this thread, there is a line that says "ethtool -s eth0 wol g"; you could try replacing this with "ethtool -s eth0 wol gumb" - this sets it to wake up on other, different messages.  I'm not sure why this would work in this situation but it might be worth a try in the absence of a better idea (man ethtool for more info on what exactly the difference is).

---

### Post by BatPenguin on 2007-12-19
OK, a quick update: this router really is strange. I just looked at the logs and did all sorts of connections to machines within the LAN from both within and outside (ssh'd into a work computer, used it to launch ftp and ssh's back here to make sure connections come from outside) and the log here really records NOTHING. There's  a system log that says the normal DHCP stuff, and a security log that I'd expect to say things about allowed and blocked connections. But nothing gets written into it. Couldn't find anything  to change logging options either. So that's pretty much useless.

I also gave using a big port number and forwarding that to the broadcast IP a shot. Didn't work.

More strangeness: the router has 4 LAN ports (and WLAN). Pretty basic. However, I switched some cables around to see what that would do, and noticed that 2 of these 4 ports are actually "outside" of the LAN's firewall and settings. So they get assigned an "outside" IP address, not one of the 192.168... but they get their own from the ADSL line. Haven't seen this before.  Anyway, so I of course proceeded to keeping my cable plugged to one of these other ports for a while, wrote down the new IP and shut it down and gave wake-up a try. Worked.  So it clearly is an issue with the router not allowing the packet to go through to the local network.

Unfortunately using one of these other LAN ports is not an option for me as they also block me from my local network which I need access to . But this might be a way to devise some sort of a backup plan with another network card that's plugged into another port and only used for wakeups from outside...but I'm not ready to go find a new card just yet for that, I'll keep trying this for a while longer.

Changing the ethtool settings sounds like a good idea. I read the man page and it does sound good to try all those other multicast etc. messages as well. I'll try that next.

To be continued...:)

---

### Post by BatPenguin on 2007-12-19
I tested the "ethtool -s eth0 wol gumb" method now too.

That won't work, it wakes up too easy. I barely had time to shutdown the machine and it woke up.  I tried with "gm" but that was too sensitve too, didn't even have time to get to the laptop before it was up again. So I guess my network has enough things flying around that I do need to get the magic packet to work, waking up to any network activity will just make it boot too often.

Another network card attached to one of those other LAN ports would of course do the trick. I guess that's what I'll have to do.

---

### Post by Big_Croc7 on 2007-12-19
Hmm, how strange!  At least you've managed to narrow it down.  It sounds like you might have what's called a DMZ enabled on the router, though I'm not sure.  If it remembers IP addresses after powering down then maybe ethtool gu (for unicast packets only) might work without waking it up too often, but I'm at the limit of my experience with it now I'm afraid.  Let us know if you solve it without a second network card :-)

---

### Post by foureight84 on 2007-12-19
another very easy method (for dd-wrt users) is to turn on WOL settings in your BIOS and add the MAC of the computer you want to invoke WOL to the DD-WRT Services panel. Invoking WOL is now as easy as logging into your DD-WRT panel and hitting the right button.

---

### Post by BatPenguin on 2007-12-20
Sounds good, I'll give "ethtool gu" a try still when I get the chance. Might be a few days until I have time to play with this thing next, I'm posting this from work and getting mighty busy with holiday stuff at home.

DMZs I wasn't even thinking about, but actually that might be another way of doing it without another card. Perhaps if I get a DMZ setup that exposes that computer completely it might start receiving the packets fine regardless of whether the router believes them worth relaying or not. I'm not even sure if the router will allow that (a truly exposed internal machine), but I'll look into it. I'm running firestarter to setup firewall rules and denyhosts to slam the door on dictionary attacks to ssh, so should be safe enough, maybe change ssh port to be sure. Anyway, I'll try that one too - thanks again for the tips. I love these forums :)

And oh, foureight84, if I had a DD-WRT capable router I'd be a very happy camper, I'm sure - those things look really nice. I guess part of this whole problem is being too stubborn to give up: I know there's plenty of routers that would let me use wol fine but I'm not about to admit defeat and buy one without a fight, heh. Although I've been keeping an eye out for used Linksys routers that would support DD-WRT, but it looks like whoever has one of those old gems in their possession is not about to give them up easily.

---

### Post by elsaturnino on 2008-01-21
I have a Dimension 9100 and there doesn't seem to be any WOL settings in the BIOS. However, when I do "sudo ethtool eth0" I get the following:

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```

This seems to me to imply that WOL should work. However, it does not. I'm not sure how ethtool works so is it possible that the driver I have supports WOL but the NIC doesn't?

---

### Post by njparton on 2008-01-22
It supports wake on lan "g" so you can do:

```
ethtool -s eth0 wol g
```

you can't however use the other options such as multicast (u) or broadcast (b) wake up. However as seen in the posts above, that would mean your pc waking up every time your router pinged it anyway.

---

### Post by juanto on 2008-01-30
Hi all,

I wrote some time ago... about a problem with wakeonlan (you can find it in this threat).

The wakeonlan that I sent it was to a machine placed in another subnet, my machine is 10.161.14.134 and the another machine is 10.161.16.230. 

If pass the enough time, the ip 10.161.16.230 is deleted in the routing tables of the router, in this case, the magic packet is not sent in broadcast in that subnet.

If I send the magic packet from a machine, ex: 10.161.16.229, the 16.230 wake up without problems.

Regards,

Juanto.

---

### Post by bmccorm2 on 2008-02-11
> Hi all,

I wrote some time ago... about a problem with wakeonlan (you can find it in this threat).


Juanto-

I seem to be having the same problem as you.  My WOL works fine if i try to do it within an hour (or so) of shutting down the computer.  However, if I wait for a longer time, it mysteriously stops working.  However, I think all of my computers are on the same subnet (192.168.1.xxx).  Could please elaborate on what you did to make WOL work all the time?

Thanks,
Bryan

---

### Post by garolou on 2008-02-13
Bryan -

I also have the same problem. Have been at it for 2 days and haven't come close to a solution.

What I learnt is that the system should shut down to a G2 (s5) state (see [[COLOR="Blue"]http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface[/COLOR]]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") to learn about ACPI) however seems to do so for a short amount of time, maybe for about half hour or so. Then totally shuts down.

I have a onboard Realtek RTL8101E 10/100.
I get the following results:


```

$ acpitool -w

   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. P0P2         S4     disabled  
  2. P0P1         S4     disabled  pci:0000:00:1e.0
  3. PS2K         S4     disabled  pnp:00:0d
  4. UAR1         S4     disabled  pnp:00:0e
  5. EUSB         S4     disabled  pci:0000:00:1d.7
  6. MC97         S4     disabled  
  7. HDAC         S4     disabled  pci:0000:00:1b.0
  8. P0P4         S4     disabled  pci:0000:00:1c.0
  9. P0P5         S4     disabled  pci:0000:00:1c.1
  10. P0P6        S4     disabled  
  11. P0P7        S4     disabled  
  12. P0P8        S4     disabled  
  13. P0P9        S4     disabled  
  14. USB0        S4     disabled  pci:0000:00:1d.0
  15. USB1        S4     disabled  pci:0000:00:1d.1
  16. USB2        S4     disabled  pci:0000:00:1d.2
  17. USB3        S4     disabled  pci:0000:00:1d.3

```


```

$ ethtool eth0

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

Now I figure it is either hardware related or there is someway to configure the shutdown process to do what we want.

I haven't found any info yet on how that possibly could be done. Maybe it requires patching the kernel but that is beyond my "relatively recent move to Linux" capabilities. I'm still looking.

Dave

---

### Post by Walter_Crankite on 2008-02-21
> **Waste said:**
> Just a quick question as I am not familiar with the uses of WoL.
What it useful for?
Security?
Convenience?

When your server is in a location you can not access easily, this saves a lot of time. Zhen the server is in the attic for example, you don't need to run upstairs to put the server on. Yo uwake on lan, then you ssh for all the rest and shut him down through command line. It's convenient. 


br,
Walter

---

### Post by boardtc on 2008-02-25
New to the WOL idea, went through all the setup steps described by OP. 
To turn on/off the server from my Windows box I installed [http://magicpacket.free.fr/](http://magicpacket.free.fr/) so I can send a magic packet. The mac address from my server is xx:xx:xx:xx:xx:xx but when I put that into the WOL Magic packet sender it says it must be 12 characters ans shows xx-xx-xx-xx-xx-xx as an example. Changing to use - rather than : does not show a message but does not turn on my server. Any thoughts?

---

### Post by lowebb on 2008-02-26
Has anyone got WOL working frin the Internet with a BT Home Hub router? I'm having difficulty and the 'Big_Croc' method isnt helping. The BT Home Hub is pretty configurable so I'm hoping someone has worked out how to do it

---

### Post by ugach on 2008-03-25
works fine on ecs 741-gxm motherboard with SIS chipset. (Found in fry's $100 pc) and Ubuntu Gutsy 7.10 

BTW I am using etherwake gui on ipcop firewall.


 :KS

Thank you chris AKA Kai

---

### Post by Tu13erhead on 2008-04-08
I'm trying to set this up on an Intel Mac Mini that's running Gutsy.  The script seems to run fine, but when I shut down the Mini it loses link with the router and won't wake up.

Any idea what to do to fix this?

Thanks.

---

### Post by alphacrux on 2008-04-20
Hey guys so I also have been fiddling around with wakeonlan and I've got it to work when I do a regular shutdown (command-line or gui). I have also setup my computer to awaken from a hot key on my keyboard ctrl-f1. The problem is when I try to hibernate I can't get wakeonlan to work anymore. I can however get it to awaken from the keyboard hot-key, but this is because my motherboard has jumpers to keep power flowing to my keyboard after shutdown so I can use it to power up. I believe its the operating system somehow that tells my computer to keep supplying power to my nic after my computer is shutdown. As hibernating aka s4 is so similar to a real shutdown (it just saves the state of my machine to hard drive and then really does shutdown) it seems like waking from a hibernating machine shouldn't be any different. In fact I have seen it work once, but I haven't gotten it to work since. Every time I hibernate before it shuts down it outputs the text "failed to activate device 00:a0" or something like that. Has anyone here had any luck getting wakeonlan to work in s4 hibernation? Can anyone help?

---

### Post by alphacrux on 2008-04-20
Ok so I looked around on the forums and found the solution to my problem. Here is the [[COLOR="Blue"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=501439&highlight=wakeonlan+hibernate"). Basically you have to configure /etc/default/acpi-support so that linux does not do a hard shutdown on hibernate/suspend and unload your network modules.

Another thing, although this wasn't a problem for me, while looking around I found that the states that can be "woken" from are set in the bios. It just so happened that my bios already had the right settings. This might be something else to look at if yall are having problems with WOL in s4.

---

### Post by piusvelte on 2008-04-24
Please forgive me if this has already been tried, but I can't find where it has...

I have a 3com 3c905c ... card whose wol configuration is not reported by ethtool, which seems to quite common. 3com has an alternate driver, has anyone tried it?
[http://support.3com.com/infodeli/tools/nic/linux/readme.txt](http://support.3com.com/infodeli/tools/nic/linux/readme.txt)
[http://support.3com.com/infodeli/tools/nic/linux/3c90x-102.tar.gz](http://support.3com.com/infodeli/tools/nic/linux/3c90x-102.tar.gz)

I'm not comfortable yet building and install drivers, but I'd certainly give it a shot if someone could give me a step by step. The readme lists instructions for rh, but I'm not experienced enough to know whether they would work on ubuntu, or xubuntu gutsy in my case.

By the way, I've so far tried:
touch /etc/modprobe.d/network
echo "options 3c59x global_enable_wol=1" > /etc/modprobe.d/network
bios set for wol
mobo link installed and detected

---

### Post by vashwood on 2008-05-29
I thought I should also post my WOL results here.  WOL works even though I get the following error message.

"ethtool -s eth0 wol g" -> "Cannot get current wake-on-lan settings: Operation not supported not setting wol."

"ethtool eth0" -> "No data available"

"ethtool -i eth0" -> 
"driver: tulip
version: 1.1.15
firmware-version:
bus-info: 0000:02:09.0"

NIC:  Linksys LNE100TX v4 

Even though I said it didnt work, I went ahead and sent a magic packet from another system in my network and my ubuntu server booted right up!! :)

It only works if I 'halt' or 'shutdown' the system though.  Anyone have any ideas how how to make WOL work when I suspend or hibernate the system?

---

### Post by vashwood on 2008-06-02
I'm not sure what happened.  But I was playing around w/ settings and now my system does not wake up if it has been powered down for a long time.  It will wake up if it was just shut down.  But if it was  down for a couple of hours then it won't wake up.  It used to wake up regardless of how long it was down.   Also before I could just wake up my system w/ by just sending the MAC address.  Now I also have to send the IP?  What happened?  I'm not sure if I accidentally changed any settings. :confused:

Anyone have any ideas?

---

### Post by Big_Croc7 on 2008-06-30
I think you've probably set it to wake on a unicast message rather than a magic packet.  One way to test this is to send anything (e.g. a ping) to that machine and see if it wakes up.  This would explain why it doesn't work after a long time, as your router might cache the physical location of the IP address for some time then clear it.  Try experimenting with the umbg switches (e.g. ethtool -s eth0 wol bg) - u = unicast, m= multicast, g = magic packet and b = broadcast address I think, or maybe that's not quite right but you get the idea.

---

### Post by ukripper on 2008-07-01
> **lowebb said:**
> Has anyone got WOL working frin the Internet with a BT Home Hub router? I'm having difficulty and the 'Big_Croc' method isnt helping. The BT Home Hub is pretty configurable so I'm hoping someone has worked out how to do it

This may help port forwarding-
[http://www.smallnetbuilder.com/content/view/29941/53/1/3/](http://www.smallnetbuilder.com/content/view/29941/53/1/3/)

I haven't tried by myself yet, I am currently sshing my server over internet  but WOL I have to still configure. Probably will try UDP port forwarding for that.

---

### Post by Adam Ryczkowski on 2008-09-01
I suggest using etherwake instead of wakeonlan
(sudo apt-get install etherwake)

I experienced problems, when using wakeonlan script on OpenVPN server bridged with local lan with Shorewall enabled. No such problems with etherwake.

---

### Post by modmadmike on 2008-09-01
What if you have 3 Ethernet Cards like me? lol

---

### Post by Kain000 on 2008-09-07
Hey everyone, I have a few questions about WOL 
I've gotten WOL to work within my home network with the comand
wakeonlan 00:00:00:00:00:00 and my server powers up fine, but when at home it's not that much of a convience because I can just walk to the box and press power.    I dont know however how to get this to work outside my network.  
also Im not sure how to use wakeonlaa properly, the -i and -p options dont seem to work for me.  Im not sure how to type them
for example i've tried to wake up the server from outside the network with the command
wakeonlan -i 76.120.108.232 and I get (ip address) is not a hardware address and could not resolve it as an ip address. just the command
wakeonlan -i gives me the menu of commands
do i need to braket the ip address?
i've got my router fowarding port 9 udp to the servers priviate ip, and that is assigned by it's mac address.

---

### Post by keatonvictor on 2008-10-11
Hey

WakeOnLan needs the mac address of the machine you wish to power up so what I do is put the mac address in a text file and run the following

wakeonlan -i YOU_IP_ADDRESS -f mac_address.txt

---

### Post by leifanders on 2008-10-13
Hello,

I want to share my findings of WOL using the 3c905b-tx NIC.

My computer is an old HP Vli8 pIII with an 3c905b-tx NIC with a WOL cable connected to the Mobo

Following two ways worked (first connect the cable to the mobo and enable network wakeup in BIOS):

1. manual way
rmmod 3c59x
modprobe 3c59x enable_wol=1 global_enable_wol=1
shutdown -h now
Then send magic packet (UDP, port 9)

But this way i had to arm the computer manually after each startup

2. Automatic way
Added to /etc/modprobe.d/network
alias eth0 3c59x
options 3c59x enable_wol=1 
options 3c59x global_enable_wol=1

rmmod -f 3c59x
update-initramfs -u

shutdown -h 
Then send magic packet (UDP, port 9)

Note that i used the -f flag on rmmod, it was not possible to unload the 3c59x module otherwise (please use with care)


Both two ways worked fine on my old computer, hope it helps someone else with the 3c905B-Tx card

(don't forget the sudo above, i did not include it to be more clear)

regards,
Anders

---

### Post by Bajo_sk on 2008-10-15
Hi everyone

I have a new mainboard GIGABYTE GA-EP35-DS4 and have problem with WOL. After shutdown I can't wake my pc. Bios is set ok, but led on ethernet port is after shutdown off. On my ASUS P5N-E board ether script with ubuntu hardy works perfec, but with Gigabyte and hardy doesn't work 
I'm using ether-wake.

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
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

any idea?
Thx

---

### Post by quee0849 on 2008-10-28
I have the same problem with a Gigabyte mobo. I have a feeling that it may not support WOL. See this post:

[http://www.tomshardware.com/forum/251189-30-gigabyte-ep35-ds3r-wake-integrated](http://www.tomshardware.com/forum/251189-30-gigabyte-ep35-ds3r-wake-integrated)

---

### Post by Oguz286 on 2008-11-08
It should work with the Gigabyte board. I have a Gigabyte P35-DQ6 board and WOL works just fine (unfortunately I haven't tested it with Ubuntu since I'm only running XP on that pc).

Recently I built a server with a Abit A-S78-H board with a 780G chipset and it has a Marvell 88E8056 PCI-E Gigabit Ethernet Controller. Although I set Wake On Lan in the BIOS and used ethtool to use WOL, it still doesn't work. I also adjusted the halt script to remove the -i option but no luck. The light on my LAN-port doesn't light up when I shutdown the server. Btw, I'm using 8.10 server amd64.

Are there others that have the same problem?

---

### Post by dmizer on 2008-11-12
My gigabit NIC works great with this howto under Hardy.
```
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: eth1
       version: 10
       serial: 00:0a:79:98:a7:1b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.7 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
```

---

### Post by StyggeStig on 2009-01-15
Hello all,

I'm now getting officially frustrated with my motherboard an WOL.

Motherboard ASUS P5K-E

WOL works fine when starting after a WinXP session.

Followed the guides and I'm pretty sure that everything went according to the steps mentioned in this thread.

What differs my NIC from the problematic ones mentioned in this thread is that the led is lit (orange one). Then when I send my packet the otherone that indicates network traffic flashes rapidly. 

So I assume that the problem is not whether or not the NIC is set to receive WOL-messages but that it doesn't do anything with them.

Does anyone know how to mend this, because I'm ):P going MAD soon!!!

---

### Post by NTolerance on 2009-01-15
A couple of posters in this thread asked about wake on LAN from suspend mode.  We need to make it clear that waking from suspend is a completely different ball of wax than waking from a shut-down state.  Check [this thread](http://ubuntuforums.org/showthread.php?t=814939) for more info and a small guide I posted near the bottom.

---

### Post by NTolerance on 2009-01-15
> **StyggeStig said:**
> Hello all,

I'm now getting officially frustrated with my motherboard an WOL.

Motherboard ASUS P5K-E

WOL works fine when starting after a WinXP session.

Followed the guides and I'm pretty sure that everything went according to the steps mentioned in this thread.

What differs my NIC from the problematic ones mentioned in this thread is that the led is lit (orange one). Then when I send my packet the otherone that indicates network traffic flashes rapidly. 

So I assume that the problem is not whether or not the NIC is set to receive WOL-messages but that it doesn't do anything with them.

Does anyone know how to mend this, because I'm ):P going MAD soon!!!

[This](http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex) could be potentially useful for you, in particular the NETDOWN setting.  No gaurantees, but it might be worth a try.

---

### Post by chconnor on 2009-01-23
I started this related thread of problems I'm having... prob. should have just put it here...

[http://ubuntuforums.org/showthread.php?p=6601275&posted=1#post6601275](http://ubuntuforums.org/showthread.php?p=6601275&posted=1#post6601275)

---

### Post by al_v on 2009-04-23
One more way is to remotely wake up PC over Internet with a service "Wake-On-LAN Online"  - [http://www.wakeonlan.me](http://www.wakeonlan.me). 
 
It can be used with any device connected to the Internet and allows simple wake up PC just with a link to the page of the site with necessary MAC and IP address. 
 
Furthermore the wake up can be scheduled for certain time and date and the site will wake up the PC automatically in that time.
 
More info on Wake-On-LAN configuration is available at [http://wakeonlan.me/kb/tech/wakeonlan.php](http://wakeonlan.me/kb/tech/wakeonlan.php)

---

### Post by whitethunder on 2009-04-24
guys, I have two question for you: 

1. Can you turn on a PC which was previously shut down using WOL? I mean if you type:
```
sudo halt
```
and shut down your PC, can you turn it on again by sending the wake-up packet? 

I can only wake mine up when it is suspended. It doesn't not wake up if the PC was shut down using the above command. 

2. Why should WOL need an OS setting any way? If the bios let's the ethernet card to watch for the magic packet, it should be able to turn on the computer when that packet is received regardless of what OS you have, shouldn't it?

---

### Post by dmizer on 2009-04-28
BIOS won't leave the NIC in a WOL listening state unless it's told to. This is why you have to run a script on shutdown.

---

### Post by Grenage on 2009-05-08
As a quick note to those who were having problems with wol not functioning after a few minutes (or few seconds) of the computer being turned off, I believe it's something to do with the router connected to your machine.

A lot of routers seem to have issues dealing with forwarded rules to inactive machines, especially after they have cleared the ARP cache (after all, the machine isn't present).  If you can add a static ARP entry for your computer, it 'should' fix the problem.

---

### Post by gavinhughes86 on 2009-05-17
Wow thanks [Chris Tucker]("http://ubuntuforums.org/member.php?u=49236") it was really bugging me that i couldn't start the Server remotely,

Just a note under my BIOS i didn't have a option for WOL but i did have an option for "modem ring resume" which enabled the WOL support also i turned on the option for the server to boot up automaticaly following a power outage or more specfically to return to previous state

:D

---

### Post by loko_loko on 2009-05-30
This worked for me once after doing the "Manual Way" on my freshly installed 9.04 on my Dell 600m laptop.  Everything seemed to be fine.  Got my laptop to WOL.  After the first shutdown to test WOL out again my laptop bricked.  I can't even get into the bios.  The ethernet light keeps blinking but after pressing the power button, the power light goes on for a few seconds like it's going to boot but then nothing.  Even after holding the power button down for 5 or 10 seconds.  Unfortunately I have to take the laptop out of a newly built DIY picture frame to try and figure out what's going on.  Any suggestions?

---

### Post by dmizer on 2009-05-30
> **loko_loko said:**
> Any suggestions?

Unplug power and disconnect the battery. Leave everything off for a good 15 - 20 seconds or more. Reconnect and attempt to power on.

---

### Post by gavinhughes86 on 2009-05-30
> **loko_loko said:**
> This worked for me once after doing the "Manual Way" on my freshly installed 9.04 on my Dell 600m laptop.  Everything seemed to be fine.  Got my laptop to WOL.  After the first shutdown to test WOL out again my laptop bricked.  I can't even get into the bios.  The ethernet light keeps blinking but after pressing the power button, the power light goes on for a few seconds like it's going to boot but then nothing.  Even after holding the power button down for 5 or 10 seconds.  Unfortunately I have to take the laptop out of a newly built DIY picture frame to try and figure out what's going on.  Any suggestions?

Id say it will have to come out of the frame to troubleshoot ;)

I asume you trying to boot from the ethernet port and not the wifi card correct?

Did you re-check your steps?
  	 	 	 	 	 	  Check for errors


/etc/init.d/wakeonlanconfig 



or whatever you called your config file as per your setup,


Does it WOL?


When you say it doesn't boot just goes through the motions then cuts out do you get anything on screen?  Do you get any errors on the screen at shutdown?


I would do what the previous posts says proper power off & reboot. You could try to undo the changes with a live CD if you have too. 

 
I think their is something wrong in they way your laptop boot/shutdown config settings so i would start their.



[FONT=DejaVu Sans Mono, sans-serif][SIZE=2][/SIZE][/FONT]

---

### Post by lexarrow on 2009-06-18
It doesn't work for me. The green ethernet light is up even if the computer is shut down, but wol doesn't work

---

### Post by roadrunner_23 on 2009-06-19
woo.. hoo....i got the wake on lan working, well... in hibernate and suspend mode...NOT in Shutdown.

For Shutdown..
i followed the usual steps, like check BIOS for setting, remove -i option from halt.., add startup scripts for WOL still could not get WOL to work during Shutdown. I used "shutdown -h now", menu option. none worked.

For Hibernate..
i did not do anything new. just selected Hibernate from menu option and WOL just worked.

I wish, things are like this for Shutdown too.. wish they just worked, rather than tweaking... 

So.. i feel, shutdown still shuts down my network ports too, and does not hear magic packet.

ok.. now that WOL is not an issue anymore for me.. let me get back to tweaking my NVIDIA display driver  and xorg.conf preferences, so that i can get "Extra" setting for my display. ](*,)

---

### Post by klrspz on 2009-06-22
I think the shutdown thing is a problem with something new in 9.04... I just upgraded from 8.04 where everything was working flawlessly. I used the same script in 8.04 that I'm using in 9.04 (which is the same as described in the OP), and upon shutdown it doesn't work... As roadrunner said, hibernate it works fine...

---

### Post by klrspz on 2009-06-22
> **Hviid said:**
> I found the answer for my problem.

[http://www.nvnews.net/vbulletin/showthread.php?t=70384](http://www.nvnews.net/vbulletin/showthread.php?t=70384)
Last reply.

;) Hviid

OK I started re-reading this thread, and came across Hviid's response... Sure enough, it IS a bug since a newer release of 8.04, but it's not Ubuntu's fault... It's a fault of the NFORCE drivers...

To recap, this used to work, and works in Windows just fine. With the newest version of the nForce drivers, there is a bug that writes the MAC addy backwards.

This has been fixed on Feb 2, 2009 as a patch, but has not made it to upstream yet. Cross your fingers!

[http://bugzilla.kernel.org/show_bug.cgi?id=6604](http://bugzilla.kernel.org/show_bug.cgi?id=6604)

So for now I am changing my mac addy's to be backwards for any boxes using forcedeth in the kernel (or as a module, duh!).

---

### Post by ukripper on 2009-07-01
Thanks for this nice Howto. Wakeonlan worked perfectly following manual steps for Jaunty 64bit.

I am using dell vostro's wireless to WOL my ASUS- VD2MX motherboard system running jaunty.

---

### Post by lethalfang on 2009-07-09
Router problem?

```
wakeonlan -i my.ip.address AA:BB:CC:DD:EE:FF
```

works after right after I shut down my computer, but somehow that command does not work via the internet after the PC is off overnight. However, ```
wakeonlan AA:BB:CC:DD:EE:FF
``` via local network works (default to 225.225.225.225:9). 

Anyone has suggestion why does the former only works shortly after shutdown, but the latter always works? And how do I fix that problem?

---

### Post by MaximCarnage on 2009-07-09
> **lethalfang said:**
> Router problem?

```
wakeonlan -i my.ip.address AA:BB:CC:DD:EE:FF
```

works after right after I shut down my computer, but somehow that command does not work via the internet after the PC is off overnight. However, ```
wakeonlan AA:BB:CC:DD:EE:FF
``` via local network works (default to 225.225.225.225:9). 

Anyone has suggestion why does the former only works shortly after shutdown, but the latter always works? And how do I fix that problem?


I have the same problem.
I too would like to know the answer. :)

---

### Post by lethalfang on 2009-07-11
I'm using the Linksys WRT110 Router.
I set subnet mask to 255.255.255.128, so that the broadcast address becomes 192.128.1.127.
I set port 9 forward to 192.168.1.127.

But it still does not work from the internet, but the following code locally works:
```
wakeonlan -i 192.168.1.127 AA:BB:CC:DD:EE:FF
```

So confusing........ :frown:

---

### Post by lethalfang on 2009-07-11
> **BatPenguin said:**
> Thanks for the quick reply. OK, I've been using the same web page to try this but I wasn't setting the subnet mask to all 255's. So that sounded like a great idea, and I tried that now - but unfortunately still no go.

From within the LAN, I've been using my laptop to send either this:

```

wakeonlan -i 192.168.0.127 00:50:8D:9A:73:5D
```

or simply 

```

wakeonlan  00:50:8D:9A:73:5D
```

Both seem to do it just fine so I don't actually know if naming the broadcast address does much there, seems like it's the default somehow when I try it from within the LAN.

I did notice something though: the web page seems to have dashes instead of colons for the MAC address (like 00-XX-...). I tried both ways but was unsure which one is the correct for that page. Which ones do you use for that page?

I've also been trying to use the laptop to send that same terminal command to the external ip, and it won't wake up.

The router's config page has the following for each rule:

Protocol (BOTH selected for TCP and UDP)
Public start port 7
Public end port 7
Mapped Private IP Address 192.168.0.127
Mapped Private Port 7

The page says "Leave blank or input 0 indicating Virtual Server Service" at the final field, and I've also tried leaving it blank.

I'm starting to think that this router just doesn't handle this broadcast address thing for some weird reason. Could that be the case? I do hope I'm missing something really obvious here...

I am having the same issue....... puzzled.
I really wish to get it to work!

---

### Post by dmizer on 2009-07-12
It may simply be that your router is blocking this. And really, that's a good thing. Enabling WOL via the Internet opens a huge security hole because magic packets are sent over the data link or OSI-2 layer which means that anyone on the same LAN as you (the entire Internet if you forward the port to your box) can exploit it.

The only way to do this, and do it safely is to be sure you have a NIC which supports TLS encrypted WOL. Then, you'd have to figure out how to send a TLS encrypted magic packet. Otherwise, you're better off without it.

---

### Post by coolnezz on 2009-09-05
awesome!  this thing works!
thanks! :D

---

### Post by jmiter on 2009-09-10
Perhaps the problem in Jaunty is with the Network Manager.  This was the problem for me in Hardy.

I had WOL working in 8.04, but only after reading a number of posts and suggestions - and finding one that referenced the removal of network-manager (network-manager-kde, knetworkmanager, what ever your variant) would allow wol to work.

Today. I removed the network manager and wol worked fine.  Specifically, I used Synaptic and removed knetworkmanager, network-manager, network-manager-kde, and the one for the plasma desktop was also removed.  At boot time, dhclient runs for my NIC to get my connection.

After my upgrade to 9.04 Jaunty, my WOL no longer worked.  I corrected /etc/init.d/halt to read NETDOWN=no.  WOL still did not work, but the NIC lights were now on (they were off after the upgrade).  After removal of the network managers - it now works.

I also run wakeonlanconfig, as noted in the beginning of this post.  I had it set up this way in 8.04.

Good luck

---

### Post by ngoctu on 2009-09-17
Thank you very much, Chris ! It works well for me with network card onboard.
But Could you help me with motherboard support Wake_On_Lan with PCI network card.

:D

---

### Post by ngoctu on 2009-09-17
Thanks you very much, Chris !

It works well for me with network card onboard.

Could you help me with PCI network card and motherboard support WakeOnLan !

:KS:guitar:

---

### Post by boulderbum on 2009-10-03
> **dmizer said:**
> It may simply be that your router is blocking this. And really, that's a good thing. Enabling WOL via the Internet opens a huge security hole because magic packets are sent over the data link or OSI-2 layer which means that anyone on the same LAN as you (the entire Internet if you forward the port to your box) can exploit it.

The only way to do this, and do it safely is to be sure you have a NIC which supports TLS encrypted WOL. Then, you'd have to figure out how to send a TLS encrypted magic packet. Otherwise, you're better off without it.


Not to disagree with you entirely, as I do see there is some security concern to this.  However, saying it is a huge security hole is a bit of a stretch, don't you think?  I have been looking around the internet and most security sites are saying it is not too big of a deal.  Bad guys turning on your computer would still need another exploit to get into your computer.  If your other option is leaving your computer on all the time this is already an issue.

The hole in the firewall could potentially be a larger problem.  However, that is easily resolved with more intelligent firmware available for some routers.  Tomato or OpenWRT (among others) installed on a LinkSys WRT54GL allow you to use the router to send the wakeup call so you do not need a port-forwarding hole.

Am I way off base?  Has anyone run into major security issues with WoL? Perhaps my google skills are not strong enough to find them...

---

### Post by leduc900 on 2009-10-04
If i sleep my server using "sudo halt" and then do a wol using "wake-on-lan" it goes perfectly. The server wakes-up. 

But if a try the same action when it hibernates (it is a ubuntu 8.04) or goes to sleep. It never wakes-up after sending wake-on-lan "MAC ADDRESS". 

I have the same problem when my server his completely shut-downed. 

What is the difference between "halt" and "hibernates"? And how to have my wake-on-lan working in this second case? 

Thanks in advance for any help. 

Benoit.

---

### Post by leduc900 on 2009-10-05
Sorry. My wake-on-lan works perfectly when my system is halted or completely down. But it still wont work if ubuntu went to sleep or hibernates.

---

### Post by grahams on 2009-10-13
Thanks for this Howto

I have WOL working but only when I've fully shut down via "halt" or shutdown -h etc. I can not WOL after a suspend or hibernate. This seems to be the reverse of most peoples problems with WOL.

Has anyone seen similar issues and know of a fix?

My PC is a CQ5110F, which uses a Nvidia mcp61 chipset.

---

### Post by grahams on 2009-10-21
I just updated to 9.10 and WOL works on suspend, hibernate and halt :-)

---

### Post by ricojonah on 2009-10-29
+1 for this excellent tutorial! The steps for manually configuring it were especially useful for me (prior to trying WOL, I just started becoming familiar with /etc/init.d and updating it using the update-rc.d command).

On a side note, I noticed that my /proc/acpi/wakeup configuration was already set to allow my network card to wake the system (I'm sure this is different from the ethtool configurations, but I assume that the ethtool configs wouldn't work if /proc/acpi/wakeup didn't have my ethernet card, IGBE, set to enabled). 

Thanks again!

---

### Post by Shhnap on 2009-10-30
I completely agree, this was a really nice tutorial and still valid today. I now use it to startup my Acer Aspire 2010 (which is currently acting as my server) from other places.

Probably the most useful part of the tutorial was the ethtool part. That was what I was missing. The man pages show this:

```
wol p|u|m|b|a|g|s|d...
              Sets Wake-on-LAN options.  Not all devices support this.  The argument to this option is a string of characters specifying which options to enable.
              p  Wake on phy activity
              u  Wake on unicast messages
              m  Wake on multicast messages
              b  Wake on broadcast messages
              a  Wake on ARP
              g  Wake on MagicPacket(tm)
              s  Enable SecureOn(tm) password for MagicPacket(tm)
              d  Disable (wake on nothing).  This option clears all previous options.

```

Just incase somebody wants to do a different type of wol request.

---

### Post by MMistro on 2009-11-01
I followed the steps above and I still can't seem to get this to work :( Here's the details:

The machine is a Sun Cobalt LX50.
It has two onboard ethernet ports, (Intel 82557/8/9/0/1 Ethernet Pro 100) both use the e100 driver; I'm currently only using the eth0 interface.
It's running 9.10


Here is the output of ethtool:
```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```in /etc/init.d/halt I have changed this line to "no" from "yes"
```

NETDOWN=no

```which affects this line below
```

        # Make it possible to not shut down network interfaces,
        # needed to use wake-on-lan
        netdown="-i"
        if [ "$NETDOWN" = "no" ]; then
                netdown=""
        fi

        log_action_msg "Will now halt"
        halt -d -f $netdown $poweroff $hddown

```I've also tried removing $netdown all together so it avoids the -i option for sure.

Here is the output of /proc/acpi/wakeup
```

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S4     disabled  no-bus:pci0000:00
PS2K      S1     disabled  pnp:00:06
UAR1      S4     disabled  pnp:00:08
UAR2      S4     disabled  pnp:00:09
USB       S1     disabled  pci:0000:00:0f.2
PCI1      S4     disabled  no-bus:pci0000:01

```I don't see NIC there... could this be it?

```

$lspci
00:00.0 Host bridge: Broadcom CNB20HE Host Bridge (rev 23)
00:00.1 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.2 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.3 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:0c.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 ISA bridge: Broadcom CSB5 South Bridge (rev 92)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 92)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 Host bridge: Broadcom CSB5 LPC bridge
01:07.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
01:07.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)

```When I shut the machine down using "halt", it shuts down, and the Ethernet light stays on.

When I use various WOL tools to send the magic packet to the MAC address (I have verified that it is the correct MAC addy various times), I can see the ethernet LED blink on par with me sending it; I know that the packet is in fact reaching the machine, so this isn't a network infrastructure problem.

I have tested the WOL tools on my other box running 9.10 server and it seems to work, so it's not a problem with the tools either.

Settings in the bios are on as well.

Any Ideas?

EDIT: Ok and to add, if I shut down the machine right when grub is loading, I can WOL the machine. So it's most definitely a configuration issue within Ubuntu rather than the hardware, infrastructure, or WOL tools.

---

### Post by MMistro on 2009-11-01
So I stumbled upon this:
[http://forums.fedoraforum.org/showthread.php?t=63763](http://forums.fedoraforum.org/showthread.php?t=63763)

so I went into the grub boot options and added in "acpi=off" and this seems to be able to "shutdown" and start the box again with WOL.

However, the problem is that the machine doesn't really "shutdown" into the lower power state it used to. The fans and hard drives are still running. It's the same problem the guy in the post was mentioning.

The only way to fully shut it down is via the power button. After pushing the power button to turn it fully off, I can still invoke power on with WOL like it should be.

I'd rather have it go straight into this state when it shuts down though :( On that forum post, no one seems to have figured it out either. The last post seems to be fedora related, but I did try creating a script which unloads the module before shutting down (With normal acpi settings). No luck

Any ideas?

---

### Post by ironstorm on 2009-11-02
> **MMistro said:**
> 
Here is the output of /proc/acpi/wakeup
```

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S4     disabled  no-bus:pci0000:00
PS2K      S1     disabled  pnp:00:06
UAR1      S4     disabled  pnp:00:08
UAR2      S4     disabled  pnp:00:09
USB       S1     disabled  pci:0000:00:0f.2
PCI1      S4     disabled  no-bus:pci0000:01
```I don't see NIC there... could this be it?


I think you might be on to something with this, I have 2 machines, The one which works shows:
```

ged@mythtv:~$ lspci | grep -i eth
**00:12.0** Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
ged@mythtv:~$ cat /proc/acpi/wakeup | grep 12.0
[COLOR="SeaGreen"]ILAN	  S4	 disabled  **pci:0000:00:12.0**[/COLOR]
```
The one that doesn't shows:
```

ged@quadcore:/etc/network/if-up.d$ lspci | grep -i eth
**03:00.0** Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)

ged@quadcore:/etc/network/if-up.d$ cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:0a.0
XVR0	  S5	 disabled  pci:0000:00:0b.0
XVR1	  S5	 disabled  pci:0000:00:0c.0
XVR2	  S5	 disabled  pci:0000:00:0d.0
UAR1	  S5	 disabled  pnp:00:08
USB0	  S3	 disabled  pci:0000:00:04.0
USB2	  S3	 disabled  pci:0000:00:04.1
AZAD	  S5	 disabled  pci:0000:00:09.0
[COLOR="Red"]MMAC	  S5	 disabled  [/COLOR]
```
I think the MMAC should have a sysfs node of "pci:0000:00:03.0" but I can for the life of me figure out how to associate it (the S-state may also be wrong too if it's S4 on the other box).

EDIT: it looks like this is the case with the sky2 driver, according to [http://bugzilla.kernel.org/show_bug.cgi?id=13764#c9](http://bugzilla.kernel.org/show_bug.cgi?id=13764#c9), without an acpi context the kernel can not be set to wake-up.  Perhaps a similar problem exists with your ethernet driver?

---

### Post by MMistro on 2009-11-04
Hm... I also found this:
[http://patchwork.ozlabs.org/patch/30055/](http://patchwork.ozlabs.org/patch/30055/)

I'm going to try a few more things and report back on the findings...

---

### Post by MMistro on 2009-11-05
Hm... seems like I can get it to do what I somewhat want it to do, but it involves putting it into hibernate (I think?)

I was googleling some more and stumbled upon this:
[http://lists.pdxlinux.org/pipermail/plug/2007-May/054264.html](http://lists.pdxlinux.org/pipermail/plug/2007-May/054264.html)

and so I tried
```

# echo mem > /sys/power/state

```

which didn't work, but upon outputting the contents of /sys/power/state, there was only standby and disk.

So I then tried 
```

# echo disk> /sys/power/state

```

and it seems like it successfully shut's down the machine, most likely hibernating it. I don't have the server hooked up to any monitor right now, and I'm too lazy to disconnect it and pull it out for that purpose, and my serial cables haven't arrived yet.... so there's no way for me to verify what exactly is happening.

Either way, the power state is low enough that the system and cpu fans shut off, but high enough that it still wakes up.

I still need to test to see if it wakes up after extended periods of hibernating though.

---

### Post by MMistro on 2009-11-05
[SIZE=3]**Full "Solution"**[/SIZE]

Ok so for reference, here are the full steps I followed to get it "working". Once again, I have an old Sun LX50 with dual Intel Pro 10/100 On-board Ethernet interfaces using the e100 driver.

I managed to get it to "work" by, instead of shutting it down, suspending the system to disk. This may not be what you're looking for, but for me it is an adequate solution as it turns off the system to a lower state then suspend to memory.

Instructions:

Create a script to run at startup which makes sure that ethtool sets wol to g, and also to make sure the appropriate entries in /proc/acpi/wakeup are set to enabled. This can be done by modifying the script mentioned in the start of the tutorial to be like this:

```

$ cat /etc/init.d/wakeonlanconfig

#!/bin/bash
ethtool -s eth0 wol g;
ethtool -s eth1 wol g;

grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI0  > /proc/acpi/wakeup;

grep 'PCI1.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI1  > /proc/acpi/wakeup;

exit;

```I did both pci0/eth0 and 1 to get both my NIC's enabled, even though I'm only using one right now.

So this needs to be included in some file, and be invoked at startup. Refer to the great tutorial on the original post for details. Basically you just throw the script in the /etc/init.d folder, make it executable, and invoke 
```
update-rc.d -f [scriptname] defaults
```to make sure it runs at startup.


Once this is done, try rebooting your machine and running
```

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S4     [COLOR=Red]**enabled **[/COLOR]no-bus:pci0000:00
PS2K      S1     disabled  pnp:00:06
UAR1      S4     disabled  pnp:00:08
UAR2      S4     disabled  pnp:00:09
USB       S1     disabled  pci:0000:00:0f.2
PCI1      S4     [COLOR=Red]**enabled **[/COLOR]no-bus:pci0000:01

```Make sure that they are automatically enabled on startup by the script you just created. This just makes your life easier, and it's one less thing to remember when "shutting down".

Now, the reason I did a suspend to disk is because it seems to be the lowest state where the NIC is set properly to receive wol signals and act on them.

Your computer may (if not will) be different. You can check the supported states by running
```

$ cat /sys/power/state
standby disk

```As you can see, in my case, there is only standby and disk. Standby kept the chassis/cpu fans running. Since it's a 1U rackmounted chassis, I'd rather have the tiny fans off when the computer is supposed to be shut down since it sounds like a vacuum cleaner when running :biggrin: The disk state seems to bring the system down into that level.

Now to suspend the system to the disk, run:
```

# echo disk > /sys/power/state

```You can always throw this into a script called "hibernate" or something and put it in some directory on your classpath to make things easier.

And all that's left to do is to test it!

Again, I havn't tested this for periods longer than 15 minutes. There could still be that issue where the mobo cuts power to the NIC's after a certain period of time. I'm going to leave the machine like that overnight and I'll report on the results in this post in the morning.

Hopefully all this ends up helping someone with an older system like mine ;)

---

### Post by NJC on 2009-11-26
Can I assume my NIC does not support WOL?

> Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 24
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000001 (1)
    Link detected: yes


---

### Post by konsole on 2009-11-27
After following the advice in this thread on Hardy 8.04 LTS, my server could never be woken a few hours after shutdown.

Hardware: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet(rev 03)

My solution was to grab the latest driver from Broadcom's website and compile it as a kernel module.

This upgraded the driver from v3.86 (November 9, 2007) to v3.99k (August 17, 2009)

Now I can wake my media server even if it's been powered off for days. :D

Don't forget to update your initramfs or your new module won't be used. You'll also need to do this each time a kernel package upgrade is performed.```
sudo update-initramfs -u
```

Thanks to all previous contributors.

---

### Post by rsriram22 on 2009-12-24
I believe my LAN chipset supports WOL, but my BIOS does not. (weird!). Here are the details:

1) lspci returns:

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

2) BIOS has following settings:
  PME event wake up - enabled
  acpi suspend type - S1 or S3 (S3 is selected)
  power on by ring - enabled
  resume by alarm- disabled.

Does that mean that i cannot wake up the system from S5 at all.. I thought I d clarify this before I tweak ubuntu..

thanks!

Ubuntu 9.10 x64 on Gigabyte ga g41m es2h

---

### Post by dmizer on 2009-12-25
> **rsriram22 said:**
> I believe my LAN chipset supports WOL, but my BIOS does not. (weird!). Here are the details:

1) lspci returns:

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

2) BIOS has following settings:
  PME event wake up - enabled
  acpi suspend type - S1 or S3 (S3 is selected)
  power on by ring - enabled
  resume by alarm- disabled.

Does that mean that i cannot wake up the system from S5 at all.. I thought I d clarify this before I tweak ubuntu..

thanks!

Ubuntu 9.10 x64 on Gigabyte ga g41m es2h

Probably just means that you have to go into your bios settings and turn on WOL.

---

### Post by rsriram22 on 2009-12-25
> **dmizer said:**
> Probably just means that you have to go into your bios settings and turn on WOL.

How do I enable WOL in BIOS -- I have mentioned all the options under ACPI in my earlier post... 

Somewhere else I read that if the LAN port light blinks after complete shutoff (S5), WOL is enabled.. In my case,no lights blink after S5..

Any clues?

---

### Post by dmizer on 2009-12-26
> **rsriram22 said:**
> How do I enable WOL in BIOS -- I have mentioned all the options under ACPI in my earlier post... 

Somewhere else I read that if the LAN port light blinks after complete shutoff (S5), WOL is enabled.. In my case,no lights blink after S5..

Any clues?

Enabling WOL in the bios has nothing to do with running commands in Ubuntu CLI. You have to enter the BIOS configuration page for your computer during boot, so it will depend on your computer. Usually you have to hit the ESC, F12, or DEL key during post in order to enter the BIOS settings page.

---

### Post by jimmi on 2010-01-21
Hi,

weird problem here, I really can't realize what's going on.

I'm testing the WOL on a Compaq AP550. At the first attempt from the LAN, different subnet, it was perfectly working using the command:
wakeonlan -i IPADDRESS MACADDRESS

Then I tested it from WAN throught my router (FritzBox) and despite the green led of the network card was flashing it was not working.
I then switched off my laptop used to send the WOL and when I tested again after a few hours it was not working either from LAN and WAN.
When I send the packet the green led is always flashing 6 times but nothing else happen.

I switched on the AP550 and, using tcpdump, I saw that it was receiving the "magic packet" both from LAN and WAN with the FFFFFFFFFFFF series and then 8 times the MAC address instead of the 16 times specified by the standard protocol, but I don't really know whether this is important or not.

Anybody has further suggestion on how to trace the problem?

UPDATE: It is now working from the same subnet using the sintax:
wakeonlan MACADDRESS. I suspect that something may be wrong in the FritzBox.

---

### Post by Ordes on 2010-01-22
my basic wol set up by this tutorial works great. but still confused about some things..

sudo halt  >> i assumed this will put my system to sleep, however my system goes into power-off  (using Karmic)

the behaviour of my wol is:
1. sudo halt; or sudo shutdown; or shutdown >> i can wake up my system from a power-off state by using wol

2. however i cannot wake my system from suspend or hibernate.
tried with /etc/acpi/sleep.sh ; pm-suspend ; and suspend (gui)  >> no matter how i suspend it wont wake up through wol

when i am reading through the forums, it seems most people have no problem waking from suspend, but waking from power-off... for me its exactly contraverse... and "halt" does not suspend for me, but power-off??

any ideas

---

### Post by wbaguhn on 2010-02-16
Look at /etc/init.d/halt .

Try setting NETDOWN=no .

---

### Post by AlexanderDGreat on 2010-02-17
I just put all my commands on the next post. Pls. help!

---

### Post by AlexanderDGreat on 2010-02-17
Hi here's my ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:b8:e7:e1  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feb8:e7e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6399281 (6.3 MB)  TX bytes:797273 (797.2 KB)
          Interrupt:19 Base address:0xdead 

eth1      Link encap:Ethernet  HWaddr 00:17:9a:37:20:8b  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28679 (28.6 KB)  TX bytes:28679 (28.6 KB) 
```

I already Enabled Power On LAN in my Bios, but I'm stuck on this step:

```

$ sudo /etc/init.d/wakeonlanconfig
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol 
``` What am I doing wrong? I followed the previous steps by the letter.


Here's my:

```

$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: yes

``` 

Does it mean my NIC isn't supported? I have 2 NIC's but I know eth0 is the integrated one I want to use, the other is a pci card Nic. Thanks.

---

### Post by Ordes on 2010-02-17
at which step of /etc/init.d/wakeonlanconfig are you?

did you already create the file itself?

>> gksu gedit /etc/init.d/wakeonlanconfig

if so, did you allow permissions and update.d-rc?

---

### Post by AlexanderDGreat on 2010-02-17
Yes I already created all files: to make it short I read from top to bottom...
> 
...
Make the script run on startup:

Code:

update-rc.d -f wakeonlanconfig defaults

You should see something like:
Code:

 Adding system startup for /etc/init.d/wakeonlanconfig ...
   /etc/rc0.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc1.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc6.d/K20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc2.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc3.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc4.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig
   /etc/rc5.d/S20wakeonlanconfig -> ../init.d/wakeonlanconfig

Now we finish by running it, and making sure there are no errors.
Code:

/etc/init.d/wakeonlanconfig


The last line above I typed in CLI, but it produced the error 
[B]
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol[/B]

Yes, I allowed permissions and update.d-rc, I was root user. I think my NIC isn't supported?

---

### Post by Ordes on 2010-02-17
did u just upload your eth & ifconfig. i didnt see that before....

yeah, it seems like your eth is not supporting wol. When you turn off your PC are the network lights on the back on your PC still on or off? If you have a eth that support wol, than they will be on, no matter if enable / disable wol.

---

### Post by AlexanderDGreat on 2010-02-17
Oh, I see, yes, I uploaded that before, maybe you didn't notice... Yes when the computer is plugged but turned off, I can see there's a light in the integrated NIC, and I also have the Bios settings that says Enable Power On LAN. But the command produces error.

---

### Post by George18 on 2010-02-18
many many thanks :)

---

### Post by bb93 on 2010-04-20
> **AlexanderDGreat said:**
> 

```

$ sudo /etc/init.d/wakeonlanconfig
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol 
``` 




I have the same problems on computer that i'm work it.

Here's my: 

```
sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

Any kind of suggestion?

[EDIT] i´ve resolved it! I had to change Eth0 for Eth1 on the Script.

---

### Post by Bagleemo on 2010-04-25
A very helpful thread!
Just set this up on my Lucid machine with the instructions in the first post. One thing - I had to install ethtool , as in:
sudo apt-get install ethtool

And then it all worked swimmingly.

---

### Post by kiwi_nigel on 2010-05-21
Thank you so much.

I spent hours reading all the conflicting information....stumbled across your post, followed your steps..and it worked first time !!!

My server is a Dell PE1850 - running Ubuntu Server 10.x ... mounted under the house so not readily accessible to hit the power switch :p

I wake it from a laptop on the LAN by using the etherwake package

Appreciated

Cheers
Nigel

---

### Post by Dleonard0 on 2010-05-22
With 10.04 I think you don't need to go to all that trouble.
Make sure you have the **ethtool** package installed and edit /etc/network/interfaces and add this fragment:
```
auto eth0
iface eth0 inet dhcp
        ethernet-wol g
```

Check by running *ethtool eth0* next time you reboot to see if wol was enabled.

---

### Post by Dleonard0 on 2010-05-23
And further, you may need to enable APCI.
For me, I have a LAN0 device listed in **/proc/acpi/wakeup**
And I enable it with the script below I saved in **/etc/init/acpi-wol.conf**. You may need to change the DEVICE= line to whatever network device you have in **/proc/acpi/wakeup**. (Run **lspci** if you are not sure which device is which).

```
# acpi-wol - enable the LAN device in acpi/wakeup
# This allows the ethernet-wol entry in /etc/network/interfaces to work
description "enable LAN device wakeup"
start on runlevel [2345]
task
script
    DEVICE=LAN0
    if grep -s "^$DEVICE.*disabled" /proc/acpi/wakeup; then
      echo "$DEVICE" > /proc/acpi/wakeup
      grep -s "^$DEVICE.*enabled" /proc/acpi/wakeup
    fi
end script
```

---

### Post by JanHus on 2010-07-08
Hi everyone

im new to ubuntu and the forums. I just got nomachine running and im rather pleased with that. Now wakeonlan is the next step. My hardware supports wake on lan and it is enabled in the bios. I was doing oke untill i stumbled at this problem:

> 
root@serverpc:/etc/init.d# /etc/init.d/wakeonlanconfig
/etc/init.d/wakeonlanconfig: line 1: 1: command not found
/etc/init.d/wakeonlanconfig: line 2: 2: command not found
/etc/init.d/wakeonlanconfig: line 3: 3: command not found
:) Hope you can help me out :popcorn:

---

### Post by tealio on 2010-07-25
I've gotten everything to work, but now when the system wakes it boots into X, then almost immediately freezes. If I need to post logs or anything let me know.

---

### Post by ubit on 2010-08-27
Hi,

i still have problems with wake-on-lan. On Bootup my system shows (dmesg-output):

> 
[ 0.339419] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[ 0.339433] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[ 0.339442] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdff8000-0xfdffbfff]
[ 0.339448] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebe0000-0xfebfffff]
[ 0.339474] pci 0000:02:00.0: supports D1 D2
[ 0.339476] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.339479] pci 0000:02:00.0: PME# disabled


After booting ethtool show (without any action taken by me!) that wake-on-lan is enabled for magic packets on eth0:

> 
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

My problem is: I am unable to find my network adapter in /proc/acpi/wakeup. lspci gives:
> 
lspci -tv
-[0000:00]-+-00.0  Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
           +-01.0-[0000:01]--+-05.0  ATI Technologies Inc RS880 [Radeon HD 4200]
           |                 \-05.1  ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
           +-05.0-[0000:02]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
           +-11.0  ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
           +-12.0  ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
           +-12.1  ATI Technologies Inc SB700 USB OHCI1 Controller
           +-12.2  ATI Technologies Inc SB700/SB800 USB EHCI Controller
           +-13.0  ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
           +-13.1  ATI Technologies Inc SB700 USB OHCI1 Controller
           +-13.2  ATI Technologies Inc SB700/SB800 USB EHCI Controller
           +-14.0  ATI Technologies Inc SBx00 SMBus Controller
           +-14.1  ATI Technologies Inc SB700/SB800 IDE Controller
           +-14.2  ATI Technologies Inc SBx00 Azalia (Intel HDA)
           +-14.3  ATI Technologies Inc SB700/SB800 LPC host controller
           +-14.4-[0000:03]--
           +-14.5  ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
           +-18.0  Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
           +-18.1  Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
           +-18.3  Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
           \-18.4  Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
lspci -vv gives:
> 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 7596
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 26
        Region 0: I/O ports at e800 [size=256]
        Region 2: Memory at fdfff000 (64-bit, prefetchable) [size=4K]
        Region 4: Memory at fdff8000 (64-bit, prefetchable) [size=16K]
        Expansion ROM at febe0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0100c  Data: 4181
        Capabilities: [70] Express (v2) Endpoint, MSI 01
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [ac] MSI-X: Enable- Mask- TabSize=4
                Vector table: BAR=4 offset=00000000
                PBA: BAR=4 offset=00000800
        Capabilities: [cc] Vital Product Data <?>
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-e0-4c-68-00-00-00-03
        Kernel driver in use: r8169
        Kernel modules: r8169

Actually Power Managemant seems to be disabled (like dmesg told...). 
/proc/acpi/wakeup is this:
> 
cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCE2      S4     disabled
PCE3      S4     disabled
PCE4      S4     disabled
PCE5      S4     disabled  pci:0000:00:05.0
PCE6      S4     disabled
PCE7      S4     disabled
PCE9      S4     disabled
PCEA      S4     disabled
PCEB      S4     disabled
PCEC      S4     disabled
SBAZ      S4     disabled  pci:0000:00:14.2
PS2K      S3     disabled  pnp:00:0b
P0PC      S4     disabled  pci:0000:00:14.4
UHC1      S4     disabled  pci:0000:00:12.0
UHC2      S4     disabled  pci:0000:00:12.1
UHC3      S4     disabled  pci:0000:00:12.2
USB4      S4     disabled  pci:0000:00:13.0
UHC5      S4     disabled  pci:0000:00:13.1
UHC6      S4     disabled  pci:0000:00:13.2
UHC7      S4     disabled  pci:0000:00:14.5
PWRB      S3    *enabled

I tried to enable PCE5 as i think that my network-adapter is connected to this pci(express)-device which is a brigde? No result in respect to wake-on-lan :-(
If i enable PS2K in /proc/acpi/wakeup i am able to resume from s3 with the keyboard. No reaction with wol.exe from a windows-system. I tried wol.exe with a different target-machine (an old amd system) and it works there. But not with my new pc.
I am working at this problem for a couple of hours. Google told me that other people have had simular problems but i do not found a working solution. How can i "include" my network in /proc/acpi/wakeup? I think there must be the problem.
Btw: If i switch my system to s3 or s5 the network lights are still on. On the mainboard as well as on a connected switch. That means that ubuntu doesn not shut down the network. Nevertheless the network-adapter does not recognises a wol-magic-packet :-(

Anyone out there with a solution for me? I am one step before ordering an additional network card für the pce-bus and try it this way. But that cannot be the "right" solution for my problem. The Mainboard is a MSI 785GM-E51.

Ciao, Udo

---

### Post by mightyiam on 2010-09-17
Dear ones,

[https://wiki.ubuntu.com/wakeonlan](https://wiki.ubuntu.com/wakeonlan) was written.

Blessings,
Shahar

---

### Post by cosmolee on 2010-09-24
That site responds that no such page exists for that link... :confused:

---

### Post by mightyiam on 2010-09-25
> **cosmolee said:**
> That site responds that no such page exists for that link... :confused:

Dear friends,

I apologize for that.

It has been moved: [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) .

Blessings,
Shahar

---

### Post by jonny_bowes on 2010-10-10
Thanks for the thread!! I had an idea in my head to make my laptop(with a busted screen) into a media center connected to my TV.

Now I can wake my system,use a remote mouse and view the desktop all from my iPhone.

Perfect!!

---

### Post by jonny_bowes on 2010-10-13
OK,now im stuck with two issues.My WOL works great from suspend

I cant WOL from hibernate or complete shutdown.

I cant WOL after a power disruption

Can anyone help?

---

### Post by rklauco on 2010-10-14
> **jonny_bowes said:**
> OK,now im stuck with two issues.My WOL works great from suspend

I cant WOL from hibernate or complete shutdown.

I cant WOL after a power disruption

Can anyone help?

Same here, I'm affraid. Also, if I do suspend and the power runs out, the WoL does not work.

---

### Post by iponeverything on 2010-10-14
> **rklauco said:**
> Same here, I'm affraid. Also, if I do suspend and the power runs out, the WoL does not work.

its normal, once the machine is completely dead the WoL intelligence of your device dies too -- it's in volatile RAM. I don't know if its like this on every machine, but have ran into in every machine I have tested. The solution is to use a UPS so that the box always has power.

It limits WoL usefulness a bit or a least it forces you replace bad UPS batteries..

---

### Post by jonny_bowes on 2010-10-18
I can see why it would happen after a complete shut down and loss of power.In my BIOS the only WOL option is by USB,however by editing the files as indicated in this thread I was able to activate WOL from standby. why can't I do. WOL from hibernate or normal shut down?can I edit any files to enable this?

---

### Post by The Unknown on 2010-11-25
Im not an expert so dont quote me on this :P
i believe that you are able to use wake on lan in standby becuase the os its self is still running, with most processes stopped. So due to the way you have set it up, it can still listen to requests with that 1 per cent of cpu that is running

On the other hand when you shutdown or hibernate the machine turns off completely (for those that are technical, it turns of completely from the OS's point of view)  and the os stops running thus it can not listen for the request. The only way to enable it in this situation is by making the BIOS listen for requests then start the computer.

easy analogy; when the computer is suspended, it is sleeping and you can prod it awake (if set up properly) 

when the computer is shutdown or hibernating, it is dead and is so until the BOIS revives it.

---

### Post by zcruzm on 2011-01-09
Hi, I've been reading this thread and [http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939), among other resources on the net, regarding WOL. I want to wake after shutdown, not hibernation, and so far, I've been unable to make it work. My setup is an old IBM netvista 6578 motherboard with a Realtek 8139C (chipset) network card. I'm running Ubuntu server 9.10 with the latest upgrades available. Manual from the motherboard says it supports WOL and I've enabled it in the BIOS. The network card does not have a connection for a dedicated cable, and the motherboard manual states that it can do WOL through the PCI bus.

The configuration of the system is as follows

```
$ sudo lspci -tv

-[0000:00]-+-00.0  Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub
           +-02.0  Intel Corporation 82815 Chipset Graphics Controller (CGC)
           +-1e.0-[0000:01]--+-08.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
           |                 +-0d.0  Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller
           |                 \-0e.0  Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller
           +-1f.0  Intel Corporation 82801BA ISA Bridge (LPC)
           +-1f.1  Intel Corporation 82801BA IDE U100 Controller
           +-1f.2  Intel Corporation 82801BA/BAM USB Controller #1
           +-1f.3  Intel Corporation 82801BA/BAM SMBus Controller
           \-1f.5  Intel Corporation 82801BA/BAM AC'97 Audio Controller
``````
$ sudo lspci -v

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
        Flags: bus master, fast devsel, latency 0
        Capabilities: [88] Vendor Specific Information <?>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: feb00000-febfffff
        Prefetchable memory behind bridge: 20000000-200fffff
        Kernel modules: shpchp

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Kingmax Technology Inc Device 0203
        Flags: bus master, medium devsel, latency 208, IRQ 16
        I/O ports at 7800 [size=256]
        Memory at febff700 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at ff000000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: 8139too
        Kernel modules: epl, 8139too, 8139cp

(some stuff removed for clarity)


```I've followed the ethtool stuff until I managed to get this after every boot:

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```So far, the "g" here is supposed to enable the WOL. Checked to see if pci devices were enabled to wakeup the machine and got this

```
Device  S-state   Status   Sysfs node
PS2K      S3     disabled  pnp:00:03
UAR1      S5     disabled  pnp:00:05
UAR2      S5     disabled  pnp:00:06
USB0      S3     disabled  pci:0000:00:1f.2
PCI2      S5     disabled  pci:0000:00:1e.0

```I guessed that PCI2 had to be enabled and since I couldn't find the network card, I went into the /sys/devices directories and realized they were all disabled. I then enabled them with

```
$ sudo su
# echo PCI2 > /proc/acpi/wakeup
# echo enabled > /sys/devices/pci0000\:00/0000\:00\:1e.0/power/wakeup 
# echo enabled > /sys/devices/pci0000\:00/0000\:00\:1e.0/0000\:01\:08.0/power/wakeup 
```which gives me

```
# cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
PS2K      S3     disabled  pnp:00:03
UAR1      S5     disabled  pnp:00:05
UAR2      S5     disabled  pnp:00:06
USB0      S3     disabled  pci:0000:00:1f.2
PCI2      S5     enabled   pci:0000:00:1e.0

#cat /sys/devices/pci0000\:00/0000\:00\:1e.0/power/wakeup 
enabled

#cat /sys/devices/pci0000\:00/0000\:00\:1e.0/0000\:01\:08.0/power/wakeup 
enabled

```Up to this point I understand that the motherboard and the network card both support WOL, and by the commands above everything is already running. I've also modified the etc/init.d/halt script adding

```
# Modified on 2011-01-09 to try Wake-on-LAN
# NETDOWN=yes
NETDOWN=no

```But haven't run any update-rc.d or anything similar. (Is it needed?)

With all this going, if I shutdown the server (with sudo shutdown -h now) it goes off and no light is blinking on the network card. I guess this might be the key issue here, but I'm not sure. Are the lights (ACT and LINK) supposed to be blinking all the time or only when they get traffic?

As expected (but not desired) it doesn't wake up when magic packet is sent from other machines in the network (tried from a couple of machines with wakeonlan). Does anybody have an idea of how to troubleshoot this?

Sorry for the long post and thanks in advance,

Alberto

---

### Post by GuiGuy on 2011-04-13
OK, that's a doddle so thanks. Worked a treat.

But seriously, the functionality seems very limited if I need to type wakeonlan bla:bla:bla:... into a shell whenever I need to wake a remote computer. It would be far better if simply by requesting a connection through an application the remote and asleep computer could be woken. 

[Windows 7 does this quite intuitively and easily]("http://technet.microsoft.com/en-us/library/ee617165%28WS.10%29.aspx").

IS similar functionality available in Linux? For example, if the mythserver is asleep and a remote myth frontend wants to access it, can that be done without opening a shell and typing "wakeonlan hardwaredevice"?

The other thing I noticed with linux it seems to very prone to sending a PC to sleep even when it is in the middle of an intensive task such as file copying etc. 



Thanks

---

### Post by sn9ke.eyes on 2011-05-04
> **JanHus said:**
> Hi everyone

im new to ubuntu and the forums. I just got nomachine running and im rather pleased with that. Now wakeonlan is the next step. My hardware supports wake on lan and it is enabled in the bios. I was doing oke untill i stumbled at this problem:

:) Hope you can help me out :popcorn:

This is probably because ethtool is not installed on your system.

sudo apt-get install ethtool

---

### Post by sn9ke.eyes on 2011-05-04
> **GuiGuy said:**
> OK, that's a doddle so thanks. Worked a treat.

But seriously, the functionality seems very limited if I need to type wakeonlan bla:bla:bla:... into a shell whenever I need to wake a remote computer. It would be far better if simply by requesting a connection through an application the remote and asleep computer could be woken. 

[Windows 7 does this quite intuitively and easily]("http://technet.microsoft.com/en-us/library/ee617165%28WS.10%29.aspx").

IS similar functionality available in Linux? For example, if the mythserver is asleep and a remote myth frontend wants to access it, can that be done without opening a shell and typing "wakeonlan hardwaredevice"?

The other thing I noticed with linux it seems to very prone to sending a PC to sleep even when it is in the middle of an intensive task such as file copying etc. 



Thanks

There's gwakeonlan available for install in the ubuntu repositories if you don't want to open a shell and go command line to wake the remote machine.

As far as the other software (mythfrontend), it's probably possible to do that, but you'd need to do a small bit of scripting or configuration to set it up yourself or ask a feature request for the mythtv developers.

I think that most people want their mythbackend running full time so that it can be recording, but if you don't then you could likely customize it.

Another option if you want to leave your mythbackend off for several house because doesn't ever record before say 5pm and you don't get home until 6pm, your BIOS may allow the machine to alarm and wake itself up everyday at say 4:45.

---

### Post by GuiGuy on 2011-05-05
> **sn9ke.eyes said:**
> 
Another option if you want to leave your mythbackend off for several house because doesn't ever record before say 5pm and you don't get home until 6pm, your BIOS may allow the machine to alarm and wake itself up everyday at say 4:45.

The backend is sorted nicely. It suspends 5 minutes if it isn't recording or if a remote user isn't accessing one of the DBTV cards. It wakes up twenty minutes before a scheduled recording. 

Were it falls apart is on the wakeonlan, which is tedious and low on WAF. The other issue is that it will suspend even when users are accessing video or music files from their front ends, the backend will go to suspend. I've tried the scripts that are supposed to prevent this but they haven't worked for me and I don't have the depth of knowledge to write my own. So I usually have to take the backend off suspend when users are watching recordings or listening to music. At this point I am looking at my neighbour's Win Home Server with some envy. But then, it probably isn't as much "fun", right? :D

Let's call it a work in progress....

---

### Post by GuiGuy on 2011-05-05
> **sn9ke.eyes said:**
> 
Another option if you want to leave your mythbackend off for several house because doesn't ever record before say 5pm and you don't get home until 6pm, your BIOS may allow the machine to alarm and wake itself up everyday at say 4:45.

The backend is sorted nicely. It suspends 5 minutes if it isn't recording or if a remote user isn't accessing one of the DBTV cards. It wakes up twenty minutes before a scheduled recording. 

Where it falls apart is on the wakeonlan, which is tedious and [low on WAF]("http://www.pcmediacenter.com.au/forum/topic/1422-wife-approval-factor-waf/"). The other issue is that it will suspend even when users are accessing video or music files from their front ends, the backend will go to suspend. I've tried the scripts that are supposed to prevent this but they haven't worked for me and I don't have the depth of knowledge to write my own. So I usually have to take the backend off suspend when users are watching recordings or listening to music. At this point I am looking at my neighbour's Win Home Server with some envy. But then, it probably isn't as much "fun", right? :D

Let's call it a work in progress....

---

### Post by kot7k on 2011-05-06
> **rsriram22 said:**
> I believe my LAN chipset supports WOL, but my BIOS does not. (weird!). Here are the details:

1) lspci returns:

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

2) BIOS has following settings:
  PME event wake up - enabled
  acpi suspend type - S1 or S3 (S3 is selected)
  power on by ring - enabled
  resume by alarm- disabled.

Does that mean that i cannot wake up the system from S5 at all.. I thought I d clarify this before I tweak ubuntu..

thanks!

Ubuntu 9.10 x64 on Gigabyte ga g41m es2h



> **rsriram22 said:**
> How do I enable WOL in BIOS -- I have mentioned all the options under ACPI in my earlier post... 

Somewhere else I read that if the LAN port light blinks after complete shutoff (S5), WOL is enabled.. In my case,no lights blink after S5..

Any clues?

I just wanted to answer you cause i had the exact same configuration as you and the one that answered you didnt seem to read your post at all. After some time messing up with this i finally made it.
At first i thought the same as you, i had that bios settings and i didnt see any lights on the nic when pc was off but after some thinking i realize something. I read somewhere that the mobo needs to be pci 2.2 to support wol from nic without extra cable, i knew my mobo was, but what happens if the nic wasnt? (my pc is old). And that was exactly the problem, i installed another nic that i had on a newer pc and it worked like a charm.

I hope this could help some others too, before giving up, look at your NIC and try with another (newer one). And check if your mobo is pci 2.2 compliant.

---

### Post by fmouse on 2011-06-27
Chris, as you pointed out, wakeonlan only supports 1 interface: eth0, and although it's been five years since you posted your solution (otherwise spot on), Ubuntu is still distributing a version of wakeonlan with no ability send MagicPackets to interfaces other than eth0.  An equivalent tool, which *does* support multiple interfaces, is ether-wake, available in the etherwake package in the universe sub-dist.

This is important since a common use of wake-on-LAN is to access a desktop or other private box from a gateway server from outside a home or office LAN.  In my particular case, the WAN IF on our gateway/router got knocked out by lightning a couple of years ago, and the remaining on-board IF, eth1, is connected to our in-house LAN, while the WAN is on a PCI NIC card designated as eth2.  In most cases, a gateway server will have multiple interfaces, so it's a toss-up as to which one will be appropriate for sending out wake-on-LAN packets to an internal box.

Otherwise, thanks for your solution, which was very helpful in getting wake-on-LAN running here.

---

### Post by W0153R on 2011-08-20
My squeezeboxserver runs on Ubuntu server 10.04.3, and uses an onboard Via Rhine II, which [_has some problems_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462933"). However I've finally found a way to make it WOL from suspend.
I've made a script to put it in suspend, it works (fast) although it's probably full of crap that either doesn't have to be there, or should be somewhere else.

```
#!/bin/bash
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
echo 1 > /sys/class/net/eth0/device/remove
echo 1 > /sys/class/pci_bus/0000\:00/device/0000\:00\:00.0/rescan
ethtool -s eth0 wol g
grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI0  > /proc/acpi/wakeup;
grep 'LAN0.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo LAN0  > /proc/acpi/wakeup;
echo enabled > /sys/devices/pci0000\:00/power/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:12.0/power/wakeup
echo mem > /sys/power/state
```

EDIT: I think I'm halfway there, WOL only works for the first 10sec...anyone has any bright ideas?

---

### Post by grumio8 on 2011-11-02
I need some help with WOL:
WOL WORKS from S5 if I shutdown thru Windows XP.
WOL WORKS from S4 if I hibernate thru Ubuntu 11.10 Server.
WOL DOES NOT WORK from S5 if i shutdown thru Ubuntu.

My NIC is an integrated Broadcom BCM5752. 
>I have WOL from S5 enabled in bios.
>WOL is enabled in Windows.
>I am running the wakeonlanconfig startup script.
>I have removed the -i option from halt
>The lights on my NIC are on after shutdown and show activity when I send the MagicPacket.
Here is my ethtool output:
```

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: yes

```Here is the output for the file /proc/acpi/wakeup 
note: my NIC is device BLAN
```

Device  S-state   Status   Sysfs node
SLPB      S4    *enabled
P32       S4    *disabled  pci:0000:00:1e.0
UAR1      S4    *disabled  pnp:00:09
PEX0      S4    *disabled  pci:0000:00:1c.0
BLAN      S4    *enabled   pci:0000:02:00.0
PEX1      S4    *disabled
PEX2      S4    *disabled  pci:0000:00:1c.2
PEX3      S4    *disabled  pci:0000:00:1c.3
PEX4      S4    *disabled  pci:0000:00:1c.4
PEX5      S4    *disabled  pci:0000:00:1c.5
UHC1      S3    *disabled  pci:0000:00:1d.0
UHC2      S3    *disabled  pci:0000:00:1d.1
UHC3      S3    *disabled  pci:0000:00:1d.2
UHC4      S3    *disabled  pci:0000:00:1d.3
EHCI      S3    *disabled  pci:0000:00:1d.7
AC9M      S4    *disabled
AZAL      S4    *disabled  pci:0000:00:1b.0

```I suspect that the issue is that S4 is listed instead of S5, I have tried manually changing the file to S5 but that didn't work.
If anyone has some suggestions I'd greatly appreciate it.

---

### Post by iditude on 2011-12-14
Oh boy, I have exactly the same problem as you...

I'm using Ubuntu Oneiric.

>I have WOL from S5 enabled in bios.
>WOL is enabled in Windows.
>I am running the wakeonlanconfig startup script.
>I have removed the -i option from halt
>The lights on my NIC are on after shutdown and show activity when I send the MagicPacket.
Here is my ethtool output:

Different driver though... I use a via VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (driver via-velocity). 

Here is the output of lscpi -tv:

```
-[0000:00]-+-00.0  VIA Technologies, Inc. VX855/VX875 Host Bridge: Host Control
           +-00.1  VIA Technologies, Inc. VX855/VX875 Error Reporting
           +-00.2  VIA Technologies, Inc. VX855/VX875 Host Bus Control
           +-00.3  VIA Technologies, Inc. VX855/VX875 DRAM Bus Control
           +-00.4  VIA Technologies, Inc. VX855/VX875 Power Management Control
           +-00.5  VIA Technologies, Inc. VX855/VX875 APIC and Central Traffic Control
           +-00.6  VIA Technologies, Inc. VX855/VX875 Scratch Registers
           +-00.7  VIA Technologies, Inc. VX855/VX875 North-South Module Interface Control
           +-01.0  VIA Technologies, Inc. VX855/VX875 Chrome 9 HCM Integrated Graphics
           +-0f.0  VIA Technologies, Inc. VX855/VX875 EIDE Controller
           +-10.0  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.1  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.2  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.4  VIA Technologies, Inc. USB 2.0
           +-11.0  VIA Technologies, Inc. VX855/VX875 Bus Control and Power Management
           +-11.7  VIA Technologies, Inc. VX8xx South-North Module Interface Control
           +-13.0-[01]----03.0  VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
           \-14.0  VIA Technologies, Inc. VT8237A/VT8251 HDA Controller
```

And acpitool -w

```
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. USB0	  S4	*disabled  pci:0000:00:10.0
  2. USB1	  S4	*disabled  pci:0000:00:10.1
  3. USB2	  S4	*disabled  pci:0000:00:10.2
  4. EHCI	  S4	*disabled  pci:0000:00:10.4
  5. SBRG	  S5	*enabled   pci:0000:00:11.0
  6. P2PB	  S5	*enabled   pci:0000:00:13.0
```

To get there, I had to modify the rc.local script as follows:

```
/sbin/ethtool -s eth0 wol g
grep 'SBRG.*enabled' < /proc/acpi/wakeup >/dev/null || echo SBRG  > /proc/acpi/wakeup
grep 'P2PB.*enabled' < /proc/acpi/wakeup >/dev/null || echo P2PB  > /proc/acpi/wakeup
echo enabled > /sys/class/net/eth0/device/power/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:13.0/power/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:13.0/0000\:01\:03.0/power/wakeup

```

As you can see, I'm sort of enabling everything I can!

Finally, I've removed network-manager (who is known to create issues) and configuring my interfaces manually through /etc/network/interfaces

```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.253.2
        netmask 255.255.255.0
        broadcast 192.168.253.255
        network 192.168.253.0
        gateway 192.168.253.1
        up /sbin/ethtool -s eth0 wol g
        post-up /sbin/ethtool -s eth0 wol g
        post-down /sbin/ethtool -s eth0 wol g
        pre-down false

```

The command ethtool eth0 outputs the following:

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
	Supports Wake-on: puag
	Wake-on: g
	Current message level: 0x00000002 (2)
			       probe
	Link detected: yes
```

It is to be noted that wol works for Debian Squeeze (kernel 2.6.32). Wol has been broken since Ubuntu 11.04. I have tried Debian testing and Mint without success as well and I fear this may be related to a kernel change...

I'm completely lost, please help!

Thanks a lot guys

---

### Post by mightyiam on 2011-12-14
> I'm completely lost, please help!
If you think that this is a kernel issue, then please file a bug report on the linux package.

Some thoughts:
Perhaps a module not loaded?
Perhaps still some BIOS configuration bad?
Perhaps router or switch is messing with packets?
Perhaps you've messed up the MAC address or using the address of the wrong NIC?

Good luck.

---

### Post by garolou on 2011-12-14
I was unsuccessful getting WOL to work almost 4 years ago, I try again using the additional info provided in this thread, software updates and gained experience...

I can now wake up my home server (10.04.3) after shutting it down via the command: ```
sudo halt -i
``` and awakening it using: ```
wakeonlan 01:23:45:67:89:a0
```

There was no need to modify the halt script or create another script to make the 'g' persistent. A shutdown using ```
shutdown -P now
``` or any variant will not work. Only the 'halt' command _with_ the 'i' switch will.
Awakening will also not work if the ip address is specified (actually it will work for a few minutes only after shutdown).

This may not be sufficient for those who are trying to wake a hibernating computer or that was shut off manually, but in my case this is perfectly acceptable. Hopefully this can help someone else.

---

### Post by iditude on 2011-12-15
Thanks Guys for your help. I've done a bit more digging...

DawnLight thoughts are good, thoughts are great!

Here's my original post for reference...

> **iditude said:**
> Oh boy, I have exactly the same problem as you...

I'm using Ubuntu Oneiric.

>I have WOL from S5 enabled in bios.
>WOL is enabled in Windows.
>I am running the wakeonlanconfig startup script.
>I have removed the -i option from halt
>The lights on my NIC are on after shutdown and show activity when I send the MagicPacket.
Here is my ethtool output:

Different driver though... I use a via VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (driver via-velocity). 

Here is the output of lscpi -tv:

```
-[0000:00]-+-00.0  VIA Technologies, Inc. VX855/VX875 Host Bridge: Host Control
           +-00.1  VIA Technologies, Inc. VX855/VX875 Error Reporting
           +-00.2  VIA Technologies, Inc. VX855/VX875 Host Bus Control
           +-00.3  VIA Technologies, Inc. VX855/VX875 DRAM Bus Control
           +-00.4  VIA Technologies, Inc. VX855/VX875 Power Management Control
           +-00.5  VIA Technologies, Inc. VX855/VX875 APIC and Central Traffic Control
           +-00.6  VIA Technologies, Inc. VX855/VX875 Scratch Registers
           +-00.7  VIA Technologies, Inc. VX855/VX875 North-South Module Interface Control
           +-01.0  VIA Technologies, Inc. VX855/VX875 Chrome 9 HCM Integrated Graphics
           +-0f.0  VIA Technologies, Inc. VX855/VX875 EIDE Controller
           +-10.0  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.1  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.2  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.4  VIA Technologies, Inc. USB 2.0
           +-11.0  VIA Technologies, Inc. VX855/VX875 Bus Control and Power Management
           +-11.7  VIA Technologies, Inc. VX8xx South-North Module Interface Control
           +-13.0-[01]----03.0  VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
           \-14.0  VIA Technologies, Inc. VT8237A/VT8251 HDA Controller
```

And acpitool -w

```
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. USB0	  S4	*disabled  pci:0000:00:10.0
  2. USB1	  S4	*disabled  pci:0000:00:10.1
  3. USB2	  S4	*disabled  pci:0000:00:10.2
  4. EHCI	  S4	*disabled  pci:0000:00:10.4
  5. SBRG	  S5	*enabled   pci:0000:00:11.0
  6. P2PB	  S5	*enabled   pci:0000:00:13.0
```

To get there, I had to modify the rc.local script as follows:

```
/sbin/ethtool -s eth0 wol g
grep 'SBRG.*enabled' < /proc/acpi/wakeup >/dev/null || echo SBRG  > /proc/acpi/wakeup
grep 'P2PB.*enabled' < /proc/acpi/wakeup >/dev/null || echo P2PB  > /proc/acpi/wakeup
echo enabled > /sys/class/net/eth0/device/power/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:13.0/power/wakeup
echo enabled > /sys/devices/pci0000\:00/0000\:00\:13.0/0000\:01\:03.0/power/wakeup

```

As you can see, I'm sort of enabling everything I can!

Finally, I've removed network-manager (who is known to create issues) and configuring my interfaces manually through /etc/network/interfaces

```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.253.2
        netmask 255.255.255.0
        broadcast 192.168.253.255
        network 192.168.253.0
        gateway 192.168.253.1
        up /sbin/ethtool -s eth0 wol g
        post-up /sbin/ethtool -s eth0 wol g
        post-down /sbin/ethtool -s eth0 wol g
        pre-down false

```

The command ethtool eth0 outputs the following:

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
	Supports Wake-on: puag
	Wake-on: g
	Current message level: 0x00000002 (2)
			       probe
	Link detected: yes
```

It is to be noted that wol works for Debian Squeeze (kernel 2.6.32). Wol has been broken since Ubuntu 11.04. I have tried Debian testing and Mint without success as well and I fear this may be related to a kernel change...

I'm completely lost, please help!

Thanks a lot guys

Now I have downloaded Debian Squeeze again and installed it on my system (so same hardware is used: linux machine, computer sending wol, network hardware)

I've successfully managed to setup wol following exactly what's written above. I have to add that debian was still a bit tricky so I modified the /etc/init.d/networking script so it never shuts down my network interface. Here is the modification:

Original:

```
        log_action_begin_msg "Deconfiguring network interfaces"
        if [ "$VERBOSE" != no ]; then
            if ifdown -a --exclude=lo; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        else

```

New version:
```
        log_action_begin_msg "Deconfiguring network interfaces"
        if [ "$VERBOSE" != no ]; then
            if ifdown -a --exclude=lo --exclude=eth0; then
                log_action_end_msg $?
            else
                log_action_end_msg $?
            fi
        else

```

I've played around with Ubuntu 11.10 again but it seems that it keeps doing something to the network interface before shutting down. I've even removed the networking script from /etc/rc0.d/ without success.

Now it seems that this has changed recently. Apparently there are new scripts involved (/etc/init.d/network-interface and /etc/init.d/network-interface-security). No idea what they do...

now to answer your questions 


Perhaps a module not loaded?

-> I checked all loaded modules between the working debian 6 and the non-working ubuntu 11.10, they are the same

Perhaps still some BIOS configuration bad?

-> I checked everything for the sake of it, but given the fact that I can wol with debian, I believe the Bios is setup correctly

Perhaps router or switch is messing with packets?

-> Again using the exact same hardware in both configurations, so I don't think so...

Perhaps you've messed up the MAC address or using the address of the wrong NIC?

-> Checked also, no problem there...

Any ideas or leads greatly appreciated! Thanks a lot guys

---

### Post by bash321 on 2012-02-08
Is there a way to change the port on wake on lan?? cause my isp blocks ports 1-10.

---

### Post by jmiter on 2012-02-08
Sounds like you want to do this over the internet.  See post #113 July 12th, 2009 by dmizer.  Its not a good idea.

An alternative, I do option #1...
1. Have an old laptop running some low ram version of debian (remember - its an old otherwise useless laptop).  Have an ssh port open on my router to the old laptop.  Use some other port beside the default one for added security.  Have a simple script to send a magic packet. SSH to your box, call the script.
2. Some routers will send a WOL on your lan.  Linksys wrt54g older versions for example, flashed with dd-wrt.  Access the router and have it send the magic packet.

---

### Post by bash321 on 2012-02-08
it describes tls encyption? does that mean it needs password authentication?
and also if there is a way to change the wake on lan port how do you do it using ethtool?

---

### Post by Rebelli0us on 2012-02-09
This thread is way too technical.

NIC is Intel Gigabit 82574L using driver e1000e

How to configure WOL for magic packet only?

How to enable Power saving mode?

I've installed ethtool, what next?

Thanks.

---

### Post by gdea73 on 2012-03-18
Thanks for a helpful guide.
I meant to also add that while computers connected with a true "wireless" connection will very rarely work with WOL, if you want a desktop that is too far away to be wired to the router to have WOL, consider using an older router flashed with DD-WRT.

For example, I have several computers connected to a Linksys WRT54G with DD-WRT, configured as a Client Bridge. However, the difference is, the router is always on, and the computers are physically using wired ethernet (and get 100mpbs speeds among themselves). Now this way, you can use the WOL feature of the ethernet adapter, while still having, to some degree, a "wireless" connection.

Obviously that's recommended only for desktops, and if possible multiple ones, as one router can connect up to 5 of them.

---

### Post by desaputra on 2012-05-17
I solved it by disable firewall in my router....

my step :

- first follow this first thread post
- disable firewall in my router
- configure port forwarding in my router
- tried and succeed, then enable back firewall in my router... then all set.

---

### Post by The Linuxist on 2012-07-17
I wrote this article describing my own setup:

[http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/](http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/)

---

### Post by Rebelli0us on 2012-07-18
> **The Linuxist said:**
> I wrote this article describing my own setup:

[http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/](http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/)

Thank you. I wish you'd publish one on how to set up Home Server with a static IP.

---

### Post by frafu on 2012-07-18
> **The Linuxist said:**
> I wrote this article describing my own setup:

[http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/](http://www.linuxist.com.au/index.php/2012/07/saving-power-on-the-home-server/)

Since you are talking about energy savings in your article, I wonder whether you also have a solution to have the server automatically go into hibernation after a determined time of inactivity. (For example, in the case where somebody forgets to turn it off after using it; this would be especially interesting if also children are allowed to connect to the server.)

---

### Post by sefs on 2012-09-07
Just an observation....

Set up here is trying to wake a computer on the same lan as I am.

I installed wakeonlan

and neither 
wakeonlan xx:xx:xx:xx:xx:xx
or
wakeonlan -i xxx.xxx.xxx.255 xx:xx:xx:xx:xx:xx

works... however i discovered etherwake in the repos and that works where wakeonlan seems to fail

sudo etherwake xx:xx:xx:xx:xx:xx.

---

### Post by dez93_2000 on 2013-01-27
Hi guys,
I know this is an old thread but I'd really appreciate if someone with more experience/knowledge could eyeball my problem and suggest any tips if they think of them.

I set up WOL as per the instructions, forwarded port 9 to my machine and WOL worked from the internet using a magic packet sending site which needs IP & MAC addresses only. Yay! (implicit & now explicit: BIOS supports WOL & it's turned on)
Then I tried it a day later and it doesn't work. I've not changed anything.

Info / terminal printouts:
"ethtool eth0" gives:
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
Cannot get link status: Operation not permitted

"sudo ethtool eth0" gives
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: yes

wakeonlanconfig done correctly, defaults set up as per instructions, chmod done as per instructions.
/etc/init.d/wakeonlanconfig produced no output, as desired.

When the machine's powered off, the NIC LEDs are on (green) and intermittently flash (yellow/orange). Sending magic packets makes the orange LED flash more regularly, tested until satisfied by sending loads and loads, compared to the flash regularity of sending none. Therefore I feel reasonably sure the machine's getting the packets.

Any ideas for a step-by-step debugging procedure for me to find out what's not working? I've installed wireshark but either I don't know how to set up a WOL filter, or it should be picking up WOL inputs and isn't.

I looked at the advice here: [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) and added the 'auto eth0' bit in etc/network/interfaces, however it didn't make WOL work, AND it meant I can't surf the net. So I undid that. It also mentioned network-manager may be interfering, but why would I be able to use WOL successfully already if that were the case? I'm reluctant to remove something as important-sounding as network manager in case it loses me other things, as is so often the case when following instructions!

"Remove -i option from halt" - have read about this but not done anything. It worked before by shutting down normally, via menu, so again i'm reluctant to change unless there's a good logical reason.

I've looked into other people having the problem of it working once and not again, but that seems to be related to saving scripts to ensure ethtool is run before each shutdown. Since I'm manually running it while trying to make this work, evidently this isn't a (currently) relevant problem, however. For reference: [http://askubuntu.com/questions/190898/wol-stops-working-after-booting-ubuntu](http://askubuntu.com/questions/190898/wol-stops-working-after-booting-ubuntu)

Thanks in advance
dez

more thoughts: if the community wiki says I should set wakeonlanconfig to run via /etc/network/interfaces, should I do that instead of this thread's instructions?
Also: I'm not 100% sure, but I don't *think* that this line was coming up in "sudo ethtool eth0" when I first started this process:
"Current message level: 0x000000ff (255)
                                               drv probe link timer ifdown ifup rx_err tx_err"

---

### Post by rajhanschinmay on 2013-11-07
In Windows, there is GUI based software called wake on lan.

Is there any such software for Ubuntu.
It will be easier to use it than many other text or command based software.

TY.

---

### Post by adamalm on 2014-04-06
I am having trouble getting wake on lan to work and I can't for the life of me figure out what isn't working.  I'm running xubuntu 12.04 LTS and I know the NIC supports wol because i've used the same computer for it with both windows xp and xubuntu 9.  If i run sudo ethtool eth0 it says:

supports wake-on: pg
wake-on: g

but if i suspend the system, wake on lan wont work for me.

I'm using sudo /usr/sbin/pm-suspend to suspend the system. with pm-utils.

Any thoughts?  They'd be most appreciated.  Thanks

---

