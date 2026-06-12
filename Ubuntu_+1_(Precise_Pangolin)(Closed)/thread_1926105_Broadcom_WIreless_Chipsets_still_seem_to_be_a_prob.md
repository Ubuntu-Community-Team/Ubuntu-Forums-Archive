---
title: "Broadcom WIreless Chipsets still seem to be a problem"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-02-15
I have tried to install OO and PP to a Dell Vostro 1310, which has a Broadcom BCM4312 Wireless Chipset. Wireless wont work after a default install. Jockey failed to fix it with no specific message. 

Searching a little, I found out that this also affects BCM4310, BCM4311, BCM4312, BCM4321, BCM4322and possibly other 6 BCM Broadcom chipsets (inconclusive reports). That effectively creates a problem for many Dell Vostro/Inspiron, Lenovo, Asus, Acer (and some other Laptop brands I could found that use this chipset) owners.

It seems that some fix attempt has already been tried (see /etc/modprobe.d/blacklist.conf and the wl module). But apparently the available wl module doesn't work to all chipsets. 

So what online tutorials report as the working procedure for this chipsets involves an impossible procedure for the average user: Get, compile and load a new wl module from broadcom. The easiest ones use module-assistant, of course.

> 
- Remove ndiswrapper* if installed
- Install module-assistant
- Run module-assistant prepare (gets linux-headers, build-essential, autotools, etc)
- Get kernel module from Broadcom via wget of FTP to /usr/src
- Untar
- Make it clean and make it to /lib/modules/`uname -r`, etc, you now the drill.
- insmod it and depmod -a 
- Blacklist (modprobe.d/bcm-<something.>.conf) bcm43xx, b43, b43legacy and ssb)
- Get other modules to load via /etc/modules (ieee80211, ieee80211_crypt_tkip and, of course, the new wl one).
- Cold rebootAFAIK, Atheros and Broadcom would be the most popular Chipsets in all notebooks, from low to high-end, and Atheros works out of the box. If Broadcom-based PCs will require the procedure above, we can safely say that about 99,99% of these Ubuntu users will be offline.

Sadly every blog post, tutorial and howto I find mention something like the procedure above as the way to use Broadcom. The alternative (ndiswrapper and windows drivers) is just as complex for the average user.

I'm hoping I'm wrong and there's an easier way to make it work? If BCM chipsets are not confirmed to work in an easier way, it would call for a major bug re-triaging and dev hunting before April. The reports about it seem to persist since 2009 (if so, this is a major issue IMO).

Can you guys please report your experience with Broadcom and the chipset version?

**EDIT:** See this -> **[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)**, and the procedures mentioned in the "official" source of info. 

Regards,
Effenberg

---

### Post by fyfe54 on 2012-02-15
I have the BCM4213 in an Inspiron 1545.
I used to run the STA driver, but am currently running the b43 driver that is in kernel 3.3.0-030300rc3 that is available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
 
No issues, so far.

Oneiric 11.10 64 bit
6gig ram

---

### Post by prusswan on 2012-02-15
age old problem since the time of 10.04, 4312 should work with both b43 and STA drivers depending on whether you like it as a eth1 or a wlan. At least one of the drivers can be manually installed from disc without the internet. Another similar problem on such laptops would be r8168 nic that defaults to r8169 driver (and usually not working), this requires an internet connection to download the r8168 driver source and hence is more problematic.

---

### Post by cariboo on 2012-02-15
My Compaq Mini-1100 netbook uses the broadcom 4312 chipset, and it actually works better with the latest kernel. It now connects to my access point seemingly before the desktop is finished loading, even when coming out of sleep mode. I've had intermittent problems with the module not being built when a new kernel is installed, but this time it was built the way it should be.

**Edit**: I forgot to mention, I use the wl driver.

---

### Post by nm_geo on 2012-02-15
I run the B43 driver and firmware-b43-installer on all versions.

Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)


I have found it to be good from Lucid to Testing Precise. At one time I got the wl (STA) driver working in Maverick but it broke for me.  This issue had me helping lots in the wireless Forum.

Chili555 and I wrote a wiki up on this I will post later.

---

### Post by xajeiw9I on 2012-02-15
I have a machine with Broadcom 4313, and I had to blacklist the default driver (brcmsmac) and install the WL drivers. It was not working ok, it was disconnecting and showing low signal with every connection I tried. Now it is working fine. I don't understand why the default driver is a faulty one. This is also a very popular chipset in 2010/2011 machines.

---

### Post by ronacc on 2012-02-15
broadcom wireless has been a problem for as long as I can remember .

---

### Post by effenberg0x0 on 2012-02-15
@fyfe54  (BCM4213 - B43 / wl (broadcom-sta))
@prusswan  (BCM4312 - B43 / wl (broadcom-sta))
@Cariboo907 (BCM4312 - wl (broadcom-sta))
@nm_geo (BCM4312 - B43 and firmware-b43-installer))

But did you you guys had properly working (out-of-the-box) WiFi after a fresh install of PP? Or you used previous knowledge or tutorials to get it to work? 

My concern is that, according to my tests on a small number of equipments (6 so far) and limited set of BCMs (3), I had no WiFi after installing PP. And Jockey couldn't do a thing about it. Fixing it is obviously doable for us, but it would require knowledge that can't be expected from average users. Look at this mess: [http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers](http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

IMO, that would call for immediate action. It's much more important than the type of blur used in the dash.

Regards,
Effenberg

---

### Post by cariboo on 2012-02-15
In my case jockey recommended the STA driver for my wireless device the first time I install Maverick on the Compaq, and I've been using it ever since. I have a PCI 4318, I had to do some experimenting to get the firmware to load, because jockey recommended the firmaware-b43legacy-installer, which didn't work, I tried the other 2 b43 firmaware installers, and found the firmware-b43-installer was the one I needed.

---

### Post by prusswan on 2012-02-15
> **effenberg0x0 said:**
> @fyfe54  (BCM4213 - B43 / wl (broadcom-sta))
@prusswan  (BCM4312 - B43 / wl (broadcom-sta))
@Cariboo907 (BCM4312 - wl (broadcom-sta))
@nm_geo (BCM4312 - B43 and firmware-b43-installer))

But did you you guys had properly working (out-of-the-box) WiFi after a fresh install of PP? Or you used previous knowledge or tutorials to get it to work? 

My concern is that, according to my tests on a small number of equipments (6 so far) and limited set of BCMs (3), I had no WiFi after installing PP. And Jockey couldn't do a thing about it. Fixing it is obviously doable for us, but it would require knowledge that can't be expected from average users. Look at this mess: [http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers](http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

IMO, that would call for immediate action. It's much more important than the type of blur used in the dash.

Regards,
Effenberg

nope and yes to your question, as otherwise I would not have mentioned the possibility for a manual install. Considering a whole plethora of similar issues that plague Ubuntu and remaining unaddressed over several releases, I have little faith that they can be effectively fixed without workarounds anytime soon, as the fanfare surrounding Unity and other gimmickry continues..


below is stock network gear on a Vostro 1320 (when everything is working):
```

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Dell Device 02bb
	Flags: bus master, fast devsel, latency 0, IRQ 47
	I/O ports at 3000 [size=256]
	Memory at f6004000 (64-bit, prefetchable) [size=4K]
	Memory at f6000000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at f6020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8168
	Kernel modules: r8168

0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

```

Edit: It seems that one of the updates replaced the b43 driver with ssb, which seems to be working just as well. This was not what I saw when I initially upgraded from fresh 10.04.3 to Alpha 2

---

### Post by nm_geo on 2012-02-15
> **effenberg0x0 said:**
> @fyfe54  (BCM4213 - B43 / wl (broadcom-sta))
@prusswan  (BCM4312 - B43 / wl (broadcom-sta))
@Cariboo907 (BCM4312 - wl (broadcom-sta))
@nm_geo (BCM4312 - B43 and firmware-b43-installer))

But did you you guys had properly working (out-of-the-box) WiFi after a fresh install of PP? Or you used previous knowledge or tutorials to get it to work? <snip>


Effenberg

Nope I never had a working out of the box wifi and the additional driver rarely worked with my Dell D620 laptop which I really like. I did buy another Intel wireless card and tried it for awhile but the BCM card is really faster on mine and very stable once I get it installed.

Now, I have saved the B43 firmware in a folder that I move to /lib/firmware as soon as I do an install of a Ubuntu version.  I even have a multiboot rescue flash drive that I place mint 9 on persistent and used that folder instead of a Synaptic download of firmware-b43-installer.

I have helped numerous users get their Broadcom Cards going, and yes I learned a lot from my own experiences.  Early in Lucid 10.04 the B43 driver was offered as a driver but I believe in Maverick it was not..  You know I still get private messages when someone says thanks I read one of your messages and it worked for me.  Kinda cool..

Whenever I run a live USB I add the firmware and get wireless going and rarely use the ethernet cable.  Just install the firmware from my Lucid partition.

Let me see.  

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

That is one of the Wiki pages we wrote ... Wow I am still the last editor. We have some if not the best wireless peeps in the Wireless Forums here Chili555 and I bought and tested lots of USB wireless dongles just to help others.

Check back later I am doing some mini.iso installs of the non-pae kernel.

---

### Post by nm_geo on 2012-02-15
> **prusswan said:**
> n
<snip>
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
[/code]Edit: It seems that one of the updates replaced the b43 driver with ssb, which seems to be working just as well. This was not what I saw when I initially upgraded from fresh 10.04.3 to Alpha 2

I am not at all trying to argue with you but the ssb module is used by the b43 driver and I bet you have the firmware-b43-lowpower installer to find the correct firmware. There are times and drivers both wireless and ethernet when the ssb module must be used and the wl (STA) driver automatically blacklisted the ssb module.  We called that "The Perfect Storm"..because many users tried the wl (STA) driver first and lost their ethernet as well as no wireless.   Bad deal for new users.

---

### Post by prusswan on 2012-02-15
> **nm_geo said:**
> I am not at all trying to argue with you but the ssb module is used by the b43 driver and I bet you have the firmware-b43-lowpower installer to find the correct firmware. There are times and drivers both wireless and ethernet when the ssb module must be used and the wl (STA) driver automatically blacklisted the ssb module.  We called that "The Perfect Storm"..because many users tried the wl (STA) driver first and lost their ethernet as well as no wireless.   Bad deal for new users.

I admit the current situation on 12.04 is a little lost on me as it looks like some of the driver support has changed since the time of 10.04. In those days to use the b43 driver it just means to install b43-fwcutter. Ssb was not known as a solution for me then.

Right now I have firmware-b43-installer, firmware-b43-lphhy-installer,b43-fwcutter (only this is installed), firmware-b43legacy-installer

---

### Post by nm_geo on 2012-02-15
> **prusswan said:**
> I admit the current situation on 12.04 is a little lost on me as it looks like some of the driver support has changed since the time of 10.04. In those days to use the b43 driver it just means to install b43-fwcutter. Ssb was not known as a solution for me then.

Right now I have firmware-b43-installer, firmware-b43-lphhy-installer,b43-fwcutter (only this is installed), firmware-b43legacy-installer

NP I was just trying to point out that ssb is needed for b43 drivers. In terminal do a 

```
lsmod
```I think you will see that the b43 is dependent on ssb.

This one installs your firmware<>  firmware-b43-lphhy-installer
Notice the LP-PHY in you message above.  Low Power firmware module

---

### Post by Gregory Lee on 2012-02-16
> **effenberg0x0 said:**
> 
Can you guys please report your experience with Broadcom and the chipset version?

I don't think I can help, but I do think I have a Broadcom driver that works.  When I first installed 12.04, I was using wireless, and it seemed to work okay.  However, now I'm using wired ethernet, since I got impatient with the slowness of wireless and strung a 50ft ethernet cable.  I see that I have a driver module loaded called "brcmsmac", which I guess is the driver for Broadcom wireless.

---

### Post by effenberg0x0 on 2012-02-16
Thanks for the feedback guys. It looks like it is possible to make most (all?) BCMs work reasonably well, as long as the (advanced) user has the capability to identify his hardware properly, make his driver choice based on this id plus already existing online info and perform additional necessary steps that differ for every possible choice.

When searching Google for "Ubuntu Jockey", the 5th result relates to  BCM. As you browse through the results, create some temporal filters, it  becomes evident that Nvidia issues have decreased over time and BCM  issues have remained the same or increased.

So, if it all is mapped and documented properly, and its logical enough that a user can successfully script/flowchart it, I wonder why it has not been fixed yet? Would you blame it on Jockey exclusively? What is the real problem?

Have a look at this. It's what Jockey does for this hardware.
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/precise/jockey/precise/view/head:/data/handlers/broadcom_wl.py](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/precise/jockey/precise/view/head:/data/handlers/broadcom_wl.py)

You don't have to understand Python to see the conditions it checks and what it does. Does it seem correct to you? For me it looks like a partial solution, which does not fit the much more complex reality of current tutorials on this hardware. Patching this file to be a little more complete can greatly improve PP rate of success for this hardware.

Regards,
Effenberg

---

### Post by prusswan on 2012-02-16
maybe they have hundreds of network cards to deal with, and this so happens to be only one of many? Or the workaround has been so effective as to deter enough pple from baying for blood

---

### Post by effenberg0x0 on 2012-02-16
> **prusswan said:**
> maybe they have hundreds of network cards to deal with, and this so happens to be only one of many? Or the workaround has been so effective as to deter enough pple from baying for blood

I'm not sure. I'm just getting into the issue and I don't have enough knowledge on it yet. But it seems like the BCM chipset is used in so many network cards, it is absolutely mandatory to have it working right and out-of-the-box. BCMs respond for a significant portion of posts in many support forums, bug reports, tutorials, etc. 

This is a good indicator: [https://friendly.ubuntu.com/?desktops=&laptops=on&stars=1&release=4&popularity=any&term=&order=overall_rating&order_direction=asc](https://friendly.ubuntu.com/?desktops=&laptops=on&stars=1&release=4&popularity=any&term=&order=overall_rating&order_direction=asc)
See that mostly all wireless chipsets are Broadcom, Atheros or Intel. And that if you classify results from worst to best, you get a lof of broadcom-based hardware in the list.

There's good documentation on the whole (or a good part of) Broadcom story here: [http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers](http://linuxwireless.org/en/users/Drivers/b43#Comparison_of_recent_drivers)

I believe small fixes to Jockey Broadcom handler could largely improve user experiences with this hardware. It all is documented in hundreds of tutorials all over the net - all it takes is to transform their underlying logic into code for this handler. I believe the developer simply had not enough useful bug reports and active supporters / hardware testers to make this handler as good and complete as it can be. 

I'll be checking on it soon.

Thanks,
Effenberg

---

### Post by Inisfad on 2012-02-26
I know this post is a week old, but ran across it while googling for assistance on just this issue.  I will say, as an 'unadvanced' user, that the Broadcom issue is horrible and confusing.  The internet is filled with contradicting instructions on how to get the wifi to work, newbies end up installing and uninstalling a myriad of 'fixes', one must be vigilant in ensuring that the fix you are attempting to follow is not outdated, and the entire issue is mindboggling.  I have currently spent the past 3 days attempting to get Broadcom to work with Lucid, and just this morning received a post on this very forum advising that I should update the distro, as now Broadcom works 'out of the box', which is what I am currently in the process of doing.  I am saddened to read in this post, however, that this may not be the case.  There needs to be one definitive place where newbies, attempting to get this working, can get their info. Even the info regarding which driver to use for which card, is confusing.  Many forum responses are well meaning, but conjecture, and those attempting to do this end up as confused at the end as they were in the beginning.  I cannot believe that it is always this difficult to get this card to work.

---

### Post by effenberg0x0 on 2012-02-26
> **Inisfad said:**
> I know this post is a week old, but ran across it while googling for assistance on just this issue.  I will say, as an 'unadvanced' user, that the Broadcom issue is horrible and confusing.  The internet is filled with contradicting instructions on how to get the wifi to work, newbies end up installing and uninstalling a myriad of 'fixes', one must be vigilant in ensuring that the fix you are attempting to follow is not outdated, and the entire issue is mindboggling.  I have currently spent the past 3 days attempting to get Broadcom to work with Lucid, and just this morning received a post on this very forum advising that I should update the distro, as now Broadcom works 'out of the box', which is what I am currently in the process of doing.  I am saddened to read in this post, however, that this may not be the case.  There needs to be one definitive place where newbies, attempting to get this working, can get their info. Even the info regarding which driver to use for which card, is confusing.  Many forum responses are well meaning, but conjecture, and those attempting to do this end up as confused at the end as they were in the beginning.  I cannot believe that it is always this difficult to get this card to work.

The most complete effort I found regarding the many alternatives for Broadcom and its pitfalls is this one: [http://linuxwireless.org/en/users/Drivers/b43#What_about_broadcom-wl.2Fsta.3F](http://linuxwireless.org/en/users/Drivers/b43#What_about_broadcom-wl.2Fsta.3F)

Many people do get it working out-of-the-box in Oneiric and in PP. But, as I pointed out somewhere in this threads, if you have a look at Jockey Broadcom handler code, you'll see that it is a much less complete solution than whats outlined in the working tutorials for this hardware. IMO, this handler code has to be improved to perform the steps defined in such tutorials.

Regards,
Effenberg

---

### Post by ronacc on 2012-02-26
probably the easiest way to deal with your broadcom problem is to get a cheap wireless dongle with anything other than a chipset made by broadcom and in the future resolve NEVER to buy another laptop with ANY broadcom content .

---

