---
title: "Networking problems"
date: 2013-08-21
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-08-21
My system was updated to the 3.11.0-3.6 kernel yesterday, and on boot this morning, I had no network. I'm running the following network device:

```
sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 11
       serial: 00:1b:11:b2:63:65
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full ip=192.168.0.104 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:deefc000-deefffff ioport:df00(size=256) memory:deec0000-deedffff
```

Booting into the previous kerenl, networking works as it should. 

There was another kernel update available today, I plan to reboot a little later on today, after I've had a chance to take care of some real life stuff.

---

### Post by ventrical on 2013-08-22
Nothing here yet of that sort.  I do have some machines that just will not  hook back up  after a suspend.. but that is another matter..

---

### Post by grahammechanical on 2013-08-22
Today's update, which required a reboot (newer kernel) did not affect networking here (the only network connection I have is to the router) but it has removed the time & date app indicator. And the options in the Clock tab are greyed out. It might come back with a reboot which I will try later on. I have two keyboard layouts and the app indicator icon to switch keyboard layout has a changed design.  I think it is that 'flat' look. So may be there is something wrong with the icons. May be not been put in the correct location?

Regards.

Edit: I have just changed themes from Ambiance to Radiance and the network and power/cog icons changed colour but the keyboard layout and sound icons did not change from the Ambiance theme colour.

---

### Post by VinDSL on 2013-08-24
> **cariboo907 said:**
> Booting into the previous kernel, networking works as it should...
Haven't installed that kernel (I'm running 3.11-rc6) but...

I've only had two occurrences of my network going away, after a kernel update, in the past two years.

The first one drove me crazy.  In the end, I'm 99% sure that they pulled support for the integrated, southbridge-driven network chipset on my legacy mobo, in the new kernel.  Switching to a nic with a real chipset solved the problem.

Most recently, I lost the network on my Dell D620.  Turned out, I was inadvertently running two network managers -- an OEM Dell manager, and network manager, AKA NM.  Disabling the Dell manager took care of the problem.

Anyway, just tossing a couple of ideas around...  ;)

---

### Post by cariboo on 2013-08-24
I ran into similar problems as you earlier with integrated nics on two different systems using the same motherboard. On the one system, the one I'm using now, I just added a D-Link network card, and all was good until the 3.11-3 kernel. The other system is still running 12.04, and the integrated nic works as it should.

I'll have to create an off-line bug report on this system.

---

### Post by VinDSL on 2013-08-25
What chipset does your NIC have?

I went with a [Netgear PCI NIC]("http://www.amazon.com/Netgear-FA-310TX-100Mbps-Fast-Ethernet/dp/B00000J4L8") with a DEC "Tulip" chipset.  

My thinking was... there are still millions of these Tulip chipsets in [NOCs]("https://en.wikipedia.org/wiki/Network_operations_center") around the globe.  If they do away with Tulip support, the web would come crashing down like a house_of_cards.

Also, have you tried switching to WiCD yet?  Switching over to WiCD is easy. [the following is for n00bs]

[LIST=1]
[*]Download WiCD, in advance.
[*]Remove NM. 
[*]Install WiCD.
[*]Reboot.
[/LIST]

To switch back to NM, just do the opposite.

Might be a good workaround, until somebody comes up with a patch or whatever.

---

### Post by cariboo on 2013-08-25
The bug has to be reported, before it can be fixed, and I just haven't had time yet. The D-Link nic I use, uses the skge driver, which was no problem with the previous kernel version.

I've tried wcid before, and never really had any luck with running it.

I'll just continue booting into 3.11.0-2 until I can get some time to work on the issue.

---

### Post by cariboo on 2013-08-26
I created an off-line bug report, #[lpbug]1216745[/lpbug] and it was marked confirmed by the Brad FIgg bot. :-)

---

### Post by VinDSL on 2013-08-26
> **cariboo907 said:**
> ...it was marked confirmed by the Brad FIgg bot.
Good job, detective!  :D

---

### Post by cariboo on 2013-08-26
I got the standard answer when these types of problems crop up, the bug dude wants me to try the upstream kernel to see if the problem exists there. I've got a day off tomorrow, so I'll have time to give it a try.

---

### Post by VinDSL on 2013-08-26
3.11-rc7 will probably work.

I've had great luck with mainline kernels, as long as I steer clear of the dailys.

---

### Post by cariboo on 2013-08-27
> **VinDSL said:**
> 3.11-rc7 will probably work.

I've had great luck with mainline kernels, as long as I steer clear of the dailys.

Unfortunately running 3.11.0-rc7  networking doesn't work. We have determined the change was made between 3.11.0-rc5 and 3.11.0-rc6, as networking does work when running 3.11.0-rc5, and doesn't with the rc6 kernel.

---

### Post by cariboo on 2013-08-27
This is just an update in the progress of solving the problem, Joseph Salisbury created three kernels where he removed the suspected commits, on the third reverted kernel, my networking is working again.

This has been quite the experience so far, as I installed a total of 6 different kernels today to help point to exactly where the problem is.

---

### Post by VinDSL on 2013-08-28
~Cool.

It restores your faith in the_system, when the process works.

I think it helped when you supplied all the information necessary to satisfy the kernel team's bot, on the first round.

I've had some satisfying experiences on launchpad too.  It's a good *feeling*, eh what? :)

---

### Post by VinDSL on 2013-08-30
> **cariboo907 said:**
> I've tried wcid before, and never really had any luck with running it.[...]
You (and others) might find this interesting and/or helpful, Cariboo...  ;)

I just posted [OVER HERE]("http://peppermintos.net/viewtopic.php?&p=38432") (Peppermint OS Forum)

> I tried installing wicd in Peppermint 4 this morning and it wouldn't start.

After a lot of Googling there seems to be a lot of it about

(not just Peppermint, but **[COLOR="#0000CD"]Ubuntu[/COLOR]**, Mint, Debian, and other distros too) [...]

---

### Post by cariboo on 2013-09-24
To update this thread, kernel 3.12-rc2 seems to have fixed the problem, Joe Salisbury is going to submit an SRU, to update the latest Ubuntu kernel. He created a test kernel, 3.11-8 that I'm using at the moment, and hopefully it should make it into the repositories real soon.

---

