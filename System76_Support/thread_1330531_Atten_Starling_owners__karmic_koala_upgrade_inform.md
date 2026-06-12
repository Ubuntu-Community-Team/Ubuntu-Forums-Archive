---
title: "Atten: Starling owners | karmic koala upgrade information"
date: 2009-11-18
forum: System76 Support
---

### Post by thomasaaron on 2009-11-18
**SOLVED WITH TODAYS 2.4.4 RELEASE OF THE SYTSEM76 DRIVER**

**If you're still running 9.04...**

First, DO A COMPLETE BACKUP OF YOUR IMPORTANT INFORMATION BEFORE UPGRADING. The upgrade to 9.10 has been a rough one all around, and you should be prepared in case the upgrade fails.

Second, run all 9.04 system updates and reboot.

Third, upgrade to 9.10 using the instructions here...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

**If you are already running 9.10...**

First, go to System > Update Manger and run ALL system updates BEFORE running the 2.4.4 version of the System76 driver.

Then go to System > System76 Driver and click the Install Drivers tab and the Install button.

Reboot, and wireless will be fixed.

**If you've done a fresh install of Ubuntu 9.10...**

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.

--------------------------------------------------------------------------------

**Earlier Content...**

If you own a Starling Netbook and you are currently running 9.04, please stay there for now. An upgrade to **9.10 will break your wireless**, and we do not have the fix in place yet.

If you've already upgraded to 9.10, we've released the 2.4.0 verion of the System76 Driver, which provides short-range wireless capabilities for the Starling until we are finished working on the full-scale fix. We are working hard on the fix, and will deliver it as soon as possible via a System76 Driver update.

**Please subscribe to this thread to be updated on further developments.**

**If you are still running 9.04** and are having wireless difficulties, please read this...

> Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

For optimal wireless performance until the 9.10 fix is completed, you can re-install Ubuntu Netbook Remix 9.04. Instructions are here...
[http://knowledge76.com/index.php/Restoring_Your_Netbook#Directions](http://knowledge76.com/index.php/Restoring_Your_Netbook#Directions)

---

### Post by thomasaaron on 2009-11-18
For further information, please subscribe to...
[http://ubuntuforums.org/showthread.php?t=1330531](http://ubuntuforums.org/showthread.php?t=1330531)

---

### Post by thomasaaron on 2009-11-18
We currently have a technician deployed to the Ubuntu Developers Summit to try and get a permanent fix in place. I'll post back here with his progress as I hear more.

---

### Post by rubbsdecvik on 2009-11-21
Not trying to be inpatient but is there any news?

---

### Post by jbraswell on 2009-11-27
Er, should those of us who jumped the gun just go ahead and downgrade?  Any chance we'll get the update within the next week?

---

### Post by thomasaaron on 2009-11-27
It's not going to be in the next week.

We are looking at a few different options for solving this. We know we can do it by rolling a new kernel that includes the API necessary for compiling the old driver. This would be a one-version solution (i.e. it would work for Karmic, and then when the next version of Ubuntu comes along, we'd try to have the fix rolled permanently into the kernel).

Or, we can keep working with Realtek to get them to re-code the driver to conform with Linux's new API. That one's a bit tougher, but we're trying to leverage a little pressure on Realtek by having Intel go to them for us. Realtek hasn't been responsive thus far.

Or we can continue to try to modify the driver code ourselves, which is tough.

The first option is the easiest, but not a long-term solution. The second option is ideal, but takes a lot of communications work and some good-will.

The third option is doable, but since we aren't C programmers, it is pretty tough.

At any rate, our deadline for getting this done has basically moved out about another three weeks.

---

### Post by Carl Hamlin on 2009-11-27
> **thomasaaron said:**
> The third option is doable, but since we aren't C programmers, it is pretty tough.

You know, a lot of us who use System76 hardware *are* C programmers. I imagine some of us represent an untapped resource which could be leveraged towards fixing this problem, if you guys are up to it.

---

### Post by jsimmond on 2009-11-28
I messed up and upgraded before checking the forums, so I also broke my wireless. My temp (and ugly) fix was to use ndiswrapper to install the current Windows driver for the Starling wireless card. My wireless is usable again :D When the new driver comes out, I'll get rid of ndiswrapper.

The only problem I haven't fixed is that I don't have wireless after coming out of a suspend.

---

### Post by ligaa9mm on 2009-11-28
> **jsimmond said:**
> My temp (and ugly) fix was to use ndiswrapper to install the current Windows driver for the Starling wireless card.

Hey jsimmond, can you post the steps you went through in that process to get it working again? The card, as best I can tell, is this...

Model: RTL8187B
Latest XP driver version: 1158.0113.2009

I installed ndiswrapper and followed the instructions as best I could to install using the .inf file. I'm not sure if it did anything, but I haven't noticed a difference...

---

### Post by jsimmond on 2009-11-29
> **ligaa9mm said:**
> Hey jsimmond, can you post the steps you went through in that process to get it working again? The card, as best I can tell, is this...

I'll try to post my steps tonight. It's been a couple of weeks since I installed the driver, so I don't remember the individual steps of the top of my head.

---

### Post by jsimmond on 2009-11-30
My situation: I had spotty wireless right after the upgrade to Karmic. So, I decided to "fix" it. After various attempts, I tried to go back to the previous driver, but this completely screwed things up. The OS recognized the wireless card, but I couldn't do anything with it. After reading a bit, I decided to try installing the windows driver for the card, using ndiswrapper.

Result: wireless is back to pre-update levels. The only problem is that I don't have wireless when I bring the laptop out of suspension/hibernation. I have to reboot to get the wireless working after I suspend (so I'm switching it off now instead of suspending).

Ok, you've been warned. If you still want to go ahead, here is what I did:

1. Figure out what chipset your wireless card has.

```
jsimmond@ito:~$ lsusb
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
...
jsimmond@ito:~$ 
```My Starling has a USB wireless card, so I used lsusb. If you don't find anything with lsusb, see if you have any luck finding it using ```
lspci -v | less
```.

If your card is also a RTL8187B, continue.

2. Install ndiswrapper

```
jsimmond@ito:~$ sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```3. Download the windows driver for the RTL8187B

[html]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=143&DownTypeID=3&GetDown=false&Downloads=true[/html]Watch out: the drivers for 2 other wireless cards are on the same download page. Scroll down to the RTL8187B section. I got the Win2K/WinXP/Vista driver (version # 1158, filename: 8187B_WindowsDriver_5_6.1158.0113.2009.zip

4. Extract the driver zip file to some directory.

```
jsimmond@ito:~$ unzip 8187B_WindowsDriver_5_6.1158.0113.2009.zip
```Driver location (the .inf file):
```
jsimmond@ito:~/temp/(090310)RTL8187B_WindowsDriver_5_6.1158.0113.2009_ISS_1.01.0087/RTL8187B/WinXP2K$ ls -l
total 368K
-rw-r--r-- 1 jsimmond jsimmond 8.4K 2009-01-16 12:23 net8187b.cat
-rw-r--r-- 1 jsimmond jsimmond  15K 2009-01-13 17:56 net8187b.inf
-rw-r--r-- 1 jsimmond jsimmond 333K 2009-01-13 17:56 rtl8187B.sys
```5. Fire-up the ndiswrapper GUI

```
jsimmond@ito:~$ sudo ndisgtk 
```6. Click on the "Install New Driver" button. You should get an open file dialog, pick the .inf file from step 4. I don't remember exactly what happened at this point, I think I clicked ok on a couple of screens. I don't have any new driver to install to check :)

I've attached a screenshot of what ndisgtk should look like if the install was successful.

7. After you exit ndisgtk (and reboot for good measure), check if the new driver is available under ndiswrapper:

```
jsimmond@ito:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)
jsimmond@ito:~$ 
```For the curious, here are the contents of my /etc/modprobe.d/ndiswrapper file:
```
jsimmond@ito:~$ cat /etc/modprobe.d/ndiswrapper
alias usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip* ndiswrapper
```8. After rebooting, my network-manager had a "Wireless" subsection again. Now I could see my router and connect to it. Around this time, I also switched to WPA, since my old router died and the new one's WEP authentication doesn't work.

I hope this guide is detailed enough to help.

---

### Post by thomasaaron on 2009-11-30
Thank you. I'm passing this on to R&D for their consideration.

---

### Post by thomasaaron on 2009-11-30
Unless they change their minds and go with the wrapper option, it looks like we are moving forward with the custom kernel.

---

### Post by ligaa9mm on 2009-11-30
Thanks for the instructions, jsimmond. I followed them to the letter, but unfortunately, my wireless still does not work. My network has only MAC filtering on it but is otherwise unsecured, so I know it's not a WEP/WPA issue. I guess I'll just have to wait. :(

thomasaaron, thanks for the update. Any ETA yet on the kernel? And just out of curiosity, do you know what exactly it is with the old wireless code that is incompatible with karmic?

---

### Post by thomasaaron on 2009-12-01
**[SIZE="5"]Starling Update:[/SIZE]**

We've decided that the best route is going to be a custom kernel for the Starling for the remainder of 9.10. 

Our techs have already made significant progress in that direction. Not sure about the ETA yet or how they will send the fix down to you, but we'll make it happen -- and make it as painless as humanly possible.

I'll follow up the moment I get more information.

Best,
Tom

---

### Post by rluethy on 2009-12-05
> **thomasaaron said:**
> **[SIZE="5"]Starling Update:[/SIZE]**

We've decided that the best route is going to be a custom kernel for the Starling for the remainder of 9.10. 

Our techs have already made significant progress in that direction. Not sure about the ETA yet or how they will send the fix down to you, but we'll make it happen -- and make it as painless as humanly possible.

I'll follow up the moment I get more information.

Best,
Tom
Does that mean, if I install the custom kernel I will not be able to upgrade the kernel in the future?

---

### Post by hoodwink on 2009-12-06
Thanks for the workaround. ndiswrapper did the trick for me. Replying via wireless. Too bad thad Ubuntu didn't do a little more testing before releasing KK.

---

### Post by thomasaaron on 2009-12-07
> Does that mean, if I install the custom kernel I will not be able to upgrade the kernel in the future?

I'm not sure. Possibly.

But we're also working to get the wireless driver added to the *next* version. That will  cure the problem permanently.

---

### Post by HotShotDJ on 2009-12-08
Thomasaaron:

If you are going to be using a custom kernel for Starling, why not kill two birds with one stone?  By compiling it with "CONFIG_ACPI_AC=m" and "CONFIG_ACPI_BATTERY=m" you can improve power management as well.  Although this doesn't correct the problem with some computers calculating percentage to fully discharged/charged, it DOES improve the following:

AC detection by NVidia graphics (at least with the G105M)
Better (more agressive) power-saving when on battery power (I'm not sure what subsystem is responsible for this -- perhaps "laptop mode?")

Attached are my config changes.  Of course, my CPU dependent settings are probably not appropriate for general distribution.

---

### Post by ligaa9mm on 2009-12-16
Just throwing my bit in - I reinstalled 9.10 and then followed jsimmond's tutorial before doing any other updates or anything... and it works! Thanks again, jsimmond!

---

### Post by qiMakur on 2009-12-20
Someone should alter the page at [http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade) so that it reflects the current upgrade-not-recommended status.  

This morning I decided to finally perform the upgrade and followed the instructions on that page and only when I ran into problems did I discover this discussion and the recommendation that the upgrade NOT be performed.  Would that I'd had that information about 4 hours ago.  :(

---

### Post by rubbsdecvik on 2009-12-23
> **qiMakur said:**
> Someone should alter the page at [http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade) so that it reflects the current upgrade-not-recommended status.  

This morning I decided to finally perform the upgrade and followed the instructions on that page and only when I ran into problems did I discover this discussion and the recommendation that the upgrade NOT be performed.  Would that I'd had that information about 4 hours ago.  :(

I've made a quick edit to the Wiki page explaining that Starling users should NOT upgrade. I (or anyone) can change it once the upgrade is supported.

~Pat

---

### Post by black_ice=cream on 2009-12-25
hey System76, I have Ubuntu Netbook Remix9.04 on my starling netbook and my wireless wasn't working so I followed the instructions above for 9.04 if your wireless wasn't working, and my wireless **still** isn't working! I'm on a wired connection right now. Thanks for the help guys.

---

### Post by ShowMeGrrl on 2009-12-26
Did you follow these steps?


Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

If you did these things and still don't have wireless, I don't know what the answer is.

---

### Post by Uber_ubuntu on 2009-12-30
I bought a new Starling a while back and have the same wireless problem after upgrading.  

I tried all the suggestions posted in this thread to no avail.  I love the Starling, but this has been a terribly disappointing experience!

---

### Post by docwhb on 2009-12-31
On being bored, I did a fresh install of Karmic on my starling. No wireless, of course. But a wired connection, download of 2.4 System 76 drivers and installation followed by a twitch of the wifi button and presto I had perfectly acceptable (for me) wireless. I see only about 1/2 of the unhidden wireless setups in my neighbourhood that I could see formerly, the furthest being some 100 yards from me. That is good enough for my purposes and the interface is SO much nicer,

Hunter

---

### Post by ShowMeGrrl on 2009-12-31
> **thomasaaron said:**
> It's not going to be in the next week.

We are looking at a few different options for solving this. We know we can do it by rolling a new kernel that includes the API necessary for compiling the old driver. This would be a one-version solution (i.e. it would work for Karmic, and then when the next version of Ubuntu comes along, we'd try to have the fix rolled permanently into the kernel).

Or, we can keep working with Realtek to get them to re-code the driver to conform with Linux's new API. That one's a bit tougher, but we're trying to leverage a little pressure on Realtek by having Intel go to them for us. Realtek hasn't been responsive thus far.

Or we can continue to try to modify the driver code ourselves, which is tough.

The first option is the easiest, but not a long-term solution. The second option is ideal, but takes a lot of communications work and some good-will.

The third option is doable, but since we aren't C programmers, it is pretty tough.

At any rate, our deadline for getting this done has basically moved out about another three weeks.
Hi Thomas - Any ETA on the wireless fix for the Starling? Four weeks ago, you estimated it would be about three weeks.

---

### Post by thomasaaron on 2009-12-31
I've emailed the guy who is working on it, but he's out until the 4th.

---

### Post by noknyc on 2010-01-04
> **ShowMeGrrl said:**
> Hi Thomas - Any ETA on the wireless fix for the Starling? Four weeks ago, you estimated it would be about three weeks.


I am also curious.  Not trying to heap added pressure on you guys...  I'm sure it's a sticky problem, and I am impressed by your dedication to support your products through a untested/half-baked upgrade cycle.

But, yeah...  just curious on the ETA of the fix.

---

### Post by rubbsdecvik on 2010-01-06
> **noknyc said:**
> I am also curious.  Not trying to heap added pressure on you guys...  I'm sure it's a sticky problem, and I am impressed by your dedication to support your products through a untested/half-baked upgrade cycle.

But, yeah...  just curious on the ETA of the fix.

I too am just curious. I updated the knowledgebase to reflect the fact that starling users should not upgrade. I'd like to know ASAP so I can change it to refect the latest developments.

---

### Post by fredricbohm on 2010-01-06
[SIZE=4]This is getting to be a rather long process, tedious even!  So far, System76 doesn't seem to have put a lot of thought or time into this driver problem. And I know this comment reflects my very real frustration at having this nifty little Starling netbook that has to be tethered to an Ethernet cable in order to function. On several occasions since October, Starling users have been told that it will only take a couple of more weeks for System76 to fix the problem; along the way, we have been presented with "fixes" (more like guesses) that do not work and fixes that, after they have been presented, we are almost immediately warned NOT to install them. We have received suggestions that we wait until April--or is it May--for the successor to Karmic. (a convenient delaying tactic as I see it). In all, not an impressive performance. My guess is that System76's $1,800 super-hot new laptop with Ubuntu installed has trumped any concern the organization has for those of us who bought the much less expensive Starlings.[/SIZE]

---

### Post by thomasaaron on 2010-01-06
> This is getting to be a rather long process, tedious even! 
Agreed.

> So far, System76 doesn't seem to have put a lot of thought or time into this driver problem.
Not the case at all. We're actually racking our brains on it. It's a very tough one.

 > And I know this comment reflects my very real frustration at having this nifty little Starling netbook that has to be tethered to an Ethernet cable in order to function. 
You may want to consider re-installing UNR 9.04 for now. Then your wireless will work great.

```
On several occasions since October, Starling users have been told that it will only take a couple of more weeks for System76 to fix the problem; along the way, we have been presented with "fixes" (more like guesses) that do not work and fixes that, after they have been presented, we are almost immediately warned NOT to install them. 
```
Yes, it is taking longer than anticipated. But the only fix we've presented (in 9.04) works great. I'm not sure what you're talking about on the rest of them... and the warnings. If you're talking about the nswrapper solution, that one is from the community, not from System76.

> We have received suggestions that we wait until April--or is it May--for the successor to Karmic. (a convenient delaying tactic as I see it). 
We've never suggest that at all. We have mentioned that we hope the next version of Ubuntu will integrated the fix into the main stream. But we're certainly not *waiting* on that.

> In all, not an impressive performance. My guess is that System76's $1,800 super-hot new laptop with Ubuntu installed has trumped any concern the organization has for those of us who bought the much less expensive Starlings.
No, we're quite concerned about it.

I'm sorry it's taking so long.

---

### Post by ShowMeGrrl on 2010-01-06
> **fredricbohm said:**
> [SIZE=4]This is getting to be a rather long process, tedious even!  So far, System76 doesn't seem to have put a lot of thought or time into this driver problem. And I know this comment reflects my very real frustration at having this nifty little Starling netbook that has to be tethered to an Ethernet cable in order to function. On several occasions since October, Starling users have been told that it will only take a couple of more weeks for System76 to fix the problem; along the way, we have been presented with "fixes" (more like guesses) that do not work and fixes that, after they have been presented, we are almost immediately warned NOT to install them. We have received suggestions that we wait until April--or is it May--for the successor to Karmic. (a convenient delaying tactic as I see it). In all, not an impressive performance. My guess is that System76's $1,800 super-hot new laptop with Ubuntu installed has trumped any concern the organization has for those of us who bought the much less expensive Starlings.[/SIZE]
This attributes the worst of motives to System76. I greatly doubt these suspicions are justified. Of course, we always want above all to have System76 be upfront and honest with its customers about problems. In my experience of seven months as a customer, they appear to be. And that is their reputation. Nonetheless, it would be helpful to hear from Thomas about exactly what the situation is re: the Karmic fix for the Starling.

---

### Post by ShowMeGrrl on 2010-01-06
> **ShowMeGrrl said:**
> This attributes the worst of motives to System76. I greatly doubt these suspicions are justified. Of course, we always want above all to have System76 be upfront and honest with its customers about problems. In my experience of seven months as a customer, they appear to be. And that is their reputation. Nonetheless, it would be helpful to hear from Thomas about exactly what the situation is re: the Karmic fix for the Starling.
Oops. I see that Thomas already responded! But Thomas's response does raise a few questions with me.

Is it unknown or uncertain whether a fix will be "integrated into the main stream" in 10.04? If so, why is it unknown or uncertain?

I worry about the fact that System76 is having such difficulty coming up with a fix. Makes me wonder whether a fix will be forthcoming in time to make it into 10.04

If a fix is not integrated into the mainstream, does this essentially mean that Starling owners are stuck at 9.04 for perpetuity?

---

### Post by thomasaaron on 2010-01-06
The precise problem is this:

In 9.10 Ubuntu removed the libraries that allowed the wireless driver to compile against the kernel.

Those libraries conflict with the current 9.10 libraries, and so they can't be re-introduced.

It is theoretically possible to compile a custom kernel that contains the older libraries, and then compile the driver. However, this is proving much harder in practice than it is in theory.

We've tried to get a new driver from realtek, but that has not succeeded.

We've tried to re-write the driver so that it will compile against the newer libraries. We've managed to get it to compile, but the driver doesn't work once compiled (yet). 

We're still working on the custom kernel angle.

---

### Post by thomasaaron on 2010-01-06
> Is it unknown or uncertain whether a fix will be "integrated into the main stream" in 10.04? If so, why is it unknown or uncertain?


Simply because, while we communicate with Ubuntu on this issue, we have no way of controlling what *actually* happens on their end.

> I worry about the fact that System76 is having such difficulty coming up with a fix. Makes me wonder whether a fix will be forthcoming in time to make it into 10.04

Honestly, R&D feels that this is totally fixable. There is just more involved in it than meets the eye. It's time-intensive.

> If a fix is not integrated into the mainstream, does this essentially mean that Starling owners are stuck at 9.04 for perpetuity?
I don't think so. It just means that either 1) we find a way to fix it and integrate that fix into the System76 Driver, or 2) we start building a custom kernel for the Starling.

Just a note to all of those following this forum: Please understand that this issue has sort of left the "tech support" arena and entered back into the R&D arena. As such, I'm not actively working on the solution. Instead, I'm relaying back and forth between you and our R&D guys.

---

### Post by val67 on 2010-01-06
Thomas,

If the R&D feels this is" totally fixable" what estimates can we get from them? 

thanks,

Val.


> **thomasaaron said:**
> Simply because, while we communicate with Ubuntu on this issue, we have no way of controlling what *actually* happens on their end.



Honestly, R&D feels that this is totally fixable. There is just more involved in it than meets the eye. It's time-intensive.


I don't think so. It just means that either 1) we find a way to fix it and integrate that fix into the System76 Driver, or 2) we start building a custom kernel for the Starling.

Just a note to all of those following this forum: Please understand that this issue has sort of left the "tech support" arena and entered back into the R&D arena. As such, I'm not actively working on the solution. Instead, I'm relaying back and forth between you and our R&D guys.

---

### Post by thomasaaron on 2010-01-07
I'll let you know the moment I know.

---

### Post by Uber_ubuntu on 2010-01-07
"You may want to consider re-installing UNR 9.04 for now. Then your wireless will work great."

Thomas, I'm not entirely new to Linux, and I generally know my way around the command line, etc.  However, I tried the 9.04 reinstallation twice and my wireless still does not work correctly.  It completely defeats the purpose for which I purchased the Starling; having to tether a netbook to an Ethernet cable.  

I'm not trying to cast asperions or anything, but I must reiterate both my former post and the opinions of others here who feel a bit dogged by this situation.  

I'm sorry you have to shoulder the brunt of the System76 criticism here, but it was a bit of a slap receiving email regarding the new, darling System76 laptop when I purchased a Starling in August that has been severely hamstrung for months.

I'm curious:  Is System76 willing to offer a special deal to their Starling customers to keep good relations?

---

### Post by thomasaaron on 2010-01-07
**[SIZE="5"]UPDATE!!!![/SIZE]**

I just got a phone call from the R&D tech in charge of the Starling wireless issue. He said they have the Starling's wireless fixed under 9.10.

They still have to do final testing and get it integrated into the System76 Driver. But that should only a day or two, barring the unforseen. Right now it is testing out well with good range, though.

I'll let you know if anything changes, and I'll update this forum with the official go-ahead as soon as the new System76 Driver is ready.

---

### Post by ShowMeGrrl on 2010-01-07
That is great news, Thomas! Congratulations System76! I am sure you will be happy to have this resolved, as will Starling owners!

> **thomasaaron said:**
> **[SIZE="5"]UPDATE!!!![/SIZE]**

I just got a phone call from the R&D tech in charge of the Starling wireless issue. He said they have the Starling's wireless fixed under 9.10.

They still have to do final testing and get it integrated into the System76 Driver. But that should only a day or two, barring the unforseen. Right now it is testing out well with good range, though.

I'll let you know if anything changes, and I'll update this forum with the official go-ahead as soon as the new System76 Driver is ready.

---

### Post by eagle-eye on 2010-01-07
I have been following this thread with interest.

I am not a Starling owner but my laptop has a Realtek 8187b wireless chip.

My laptop would not work at full speed with Ubuntu 9.04 until I discovered Thomas's driver on another Linux forum. I am hoping that I will now be able to get 9.10 working properly following Thomas's latest announcement.:D

---

### Post by thomasaaron on 2010-01-07
Just tested the new driver. Got a solid 120 feet out of it (that's as long as the hall is). Seems like it might even be slightly faster than 9.04.

The new System76 Driver probably will be released tomorrow.

---

### Post by pemadorje on 2010-01-07
I've been following this thread closely since I ordered a Starling a week or so ago and this really is great news! It sounds like this was really a challenge considering since there were some factors beyond System 76's control. 

Out of curiosity, what was the final resolution? I assume that you didn’t go the custom kernel route and were able to modify the Realtek driver to conform with the new API in 9.10? Also, will this be a long term solution (with Lucid not too far off now) ?

Thanks again for keeping us all informed during this process.

---

### Post by noknyc on 2010-01-07
> **thomasaaron said:**
> Just tested the new driver. Got a solid 120 feet out of it (that's as long as the hall is). Seems like it might even be slightly faster than 9.04.

The new System76 Driver probably will be released tomorrow.

Great news!  I can't wait to get my grubby little paws on the new driver.

---

### Post by nealaustin on 2010-01-07
Ordered my Starling yesterday. I hope that it comes out Karmic with the new driver. (Superstitious). Otherwise I'll get some more practice on upgrading. Either way the one thing system 76 doesn't offer is instant gratification. Woohoo!

---

### Post by rubbsdecvik on 2010-01-10
Do we know if it's been officially released yet?

---

### Post by jml on 2010-01-10
rubbsdecvic, I am pretty sure that Tom will post an announcement on this forum once it is officially released.  Patience young grasshopper. ;-)

Joe

---

### Post by val67 on 2010-01-10
> **jml said:**
> rubbsdecvic, I am pretty sure that Tom will post an announcement on this forum once it is officially released.  Patience young grasshopper. ;-)

Joe

Joe,

At least partially the impatience is generated by Tom himself, when stating thing like "The new System76 Driver probably will be released tomorrow" or the other one about taking some "3 weeks" (back in November), and the examples can go on and on, and S76 never meeting those deadlines.

It's like he's trying to wave candies in kids' face, and we are not kids anymore.:D

val.

---

### Post by gamerchick02 on 2010-01-10
Maybe it's silly of me to suggest, but I wonder if the System76 developers could release the new drivers in an "Alpha PPA" which the users can then download and test.

Not only would this help System76 with development, it would allow the users who want to help improve the drivers.

I've been (unfortunately) just as impatient as the other Starling users.  At least I have some wireless functionality; I bought a USB dongle to help with times when the internal card is not working or not reaching the network.

Just something to think about.

Amy

---

### Post by jml on 2010-01-10
val, I really was not trying to be critical.  I agree with you that Tom's estimates are at best "optimistic."  Since I am lucky enough to have another computer as my primary device, I am happy to wait.  In fact, I will probably wait until other members of this forum get and try the update before I will commit to 9.10.  The longer it takes, the more waiting until 10.04 arrives begins to make sense.

Amy, you raise a good point. the folks at System 76 would be well served if they would consider your idea.  In addition to the small development staff at System 76 testing the driver, they could benefit from a number of customers who would like to help in the process.

And while I am on a wireless rant,  ;-)  I know that Tom has often stated that netbooks tend to have poorer wireless performance  when compared to a full size laptop.  But that does not explain why my smaller ASUS 900HA actually has better wireless performance than my larger Starling, even when I run the same distro on both.

Joe

---

### Post by gamerchick02 on 2010-01-10
jml:

Thanks.  I was thinking of a way for the System76 devs to actually increase their testing pool. I know I'd be willing to help; that's the whole idea behind Linux, right?  :)

I agree with you about the wireless rant, but could the eeePC have a better range because of their card?  I know different cards have different ranges and some are better than others.  For instance, in my old laptop, I had a Broadcomm card *shudder* as the internal card.  I was barely able to get a signal on the other side of the house (from the router) but when I installed a PCMCIA card, I was able to get wireless access points from all over the neighborhood (well, maybe not, but the surrounding houses, at least!).  The difference was very measurable.

I'm afraid I'm hijacking the thread, so I'll stop now.  ;)

Amy

---

### Post by ShowMeGrrl on 2010-01-11
> And while I am on a wireless rant,   I know that Tom has often stated that netbooks tend to have poorer wireless performance when compared to a full size laptop. But that does not explain why my smaller ASUS 900HA actually has better wireless performance than my larger Starling, even when I run the same distro on both.

Hmmmm. Good question jml. I'm interested in the answer to this, too.

---

### Post by thomasaaron on 2010-01-11
Guys, I try to give you the best information that I have when it gets funneled down to me. It doesn't always turn out to be correct, but it is indicative of the state of the issue, as best we can tell, when I give you the information. 

I do what I can. Sorry if that fuels frustration. I'm sure it would fuel frustration if I just refused to answer or never gave my best estimates (which you guys are constantly asking for). From my chair, it's one massive catch 22, and it's as frustrating to me as it is to you. I'm human, guys.

Regarding, my comparison of notebook wireless to netbook wireless, there are two things you should know...

1. The "antenna size" argument is based on my own observations when I open notebooks and netbooks to have a look. It's also based on other observations. For instance, if you have a desktop system with a wireless card installed, it will have an external antenna on the back of the machine. If you remove that antenna, your signal strength will drop dramatically, as well may your connection speed. Put the antenna back on, and you again have a strong signal and a fast connection.

2. There are **several factors** involved in the strength of wireless reception: antenna area; the wireless card being used (they are not all created equal); the driver being used to power the card (is it a windows driver designed specifically for the hardware? is it a linux driver that is created without the assistance and blessing of the hardware vendors?); and I'm sure there are other factors as well.

When talking about stuff like this, it's important to make apples-to-apples comparisons if you want to *understand* the issue. Just saying that your 3-year old Toshiba laptop gets better reception than your new netbook, or that a 9-inch notebook gets better reception than a 10-inch, isn't really an apples-to-apples comparison on an electronics level.


**[SIZE="5"]THAT SAID, AN UPDATE AND SOME EXTRA GOOD NEWS[/SIZE]**

The driver was finished late Friday, but not in time to release it before the weekend. But it will be out in a few hours.

NOT ONLY THAT, we have made a nice improvement in the driver. From now on, it will automatically re-compile the wireless driver after a kernel update, so kernel updates should no longer hose the wireless driver.

---

### Post by thomasaaron on 2010-01-11
OK, guys. It's all yours.

[B]SOLVED WITH TODAYS 2.4.4 RELEASE OF THE SYTSEM76 DRIVER
[/B]
[B]If you're still running 9.04...
[/B]
First, DO A COMPLETE BACKUP OF YOUR IMPORTANT INFORMATION BEFORE UPGRADING. The upgrade to 9.10 has been a rough one all around, and you should be prepared in case the upgrade fails.

Second, run all 9.04 system updates and reboot.

Third, upgrade to 9.10 using the instructions here...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

[B]If you are already running 9.10...
[/B]
First, go to System > Update Manger and run ALL system updates BEFORE running the 2.4.4 version of the System76 driver.

Then go to System > System76 Driver and click the Install Drivers tab and the Install button.

Reboot, and wireless will be fixed.

**If you've done a fresh install of Ubuntu 9.10...**

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.

---

### Post by Wildbill1 on 2010-01-11
> **thomasaaron said:**
> OK, guys. It's all yours.

[B]SOLVED WITH TODAYS 2.4.4 RELEASE OF THE SYTSEM76 DRIVER
[/B]
[B]If you're still running 9.04...
[/B]
First, DO A COMPLETE BACKUP OF YOUR IMPORTANT INFORMATION BEFORE UPGRADING. The upgrade to 9.10 has been a rough one all around, and you should be prepared in case the upgrade fails.

Second, run all 9.04 system updates and reboot.

Third, upgrade to 9.10 using the instructions here...
[http://www.knowledge76.com/index.php...ystem76_Driver](http://www.knowledge76.com/index.php...ystem76_Driver)

[B]If you are already running 9.10...
[/B]
First, go to System > Update Manger and run ALL system updates BEFORE running the 2.4.4 version of the System76 driver.

Then go to System > System76 Driver and click the Install Drivers tab and the Install button.

Reboot, and wireless will be fixed.

**If you've done a fresh install of Ubuntu 9.10...**

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.
Currently running upgrade following instructions for already running 9.10.  Completed system updates.  System 76 driver has been running for the last half-hour.  Is this expected or ???

---

### Post by thomasaaron on 2010-01-11
> **Wildbill1 said:**
> Currently running upgrade following instructions for already running 9.10.  Completed system updates.  System 76 driver has been running for the last half-hour.  Is this expected or ???

No, it shouldn't run more than a few minutes. Did you initially upgrade from 9.04, or did you do a fresh install of 9.10. If you upgraded...

> Stop the driver. Make sure you have a wired Internet connection. Go to a terminal and run...

sudo apt-get install grub-pc

Then reboot the machine and try running the driver again.

---

### Post by Wildbill1 on 2010-01-11
> **thomasaaron said:**
> No, it shouldn't run more than a few minutes. Did you initially upgrade from 9.04, or did you do a fresh install of 9.10. If you upgraded...
Thanks.  System up and wireless working.  Hope future upgrades will be less painful for you.

---

### Post by thomasaaron on 2010-01-11
Excellent.

> **Wildbill1 said:**
> Thanks.  System up and wireless working.  Hope future upgrades will be less painful for you.

That makes two of us!

---

### Post by nealaustin on 2010-01-11
Say Thomas, My order for a starling has been in manufacturing since Thursday, I was wondering which version I am going to get. I may be 55 but I still feel like a 7 year old a week away from Christmas. BTW you guys at sys76 rock. 


Neal

---

### Post by johnkhobson on 2010-01-11
> **thomasaaron said:**
> OK, guys. It's all yours.

[B]SOLVED WITH TODAYS 2.4.4 RELEASE OF THE SYTSEM76 DRIVER
[/B]
[B]If you're still running 9.04...
[/B]
First, DO A COMPLETE BACKUP OF YOUR IMPORTANT INFORMATION BEFORE UPGRADING. The upgrade to 9.10 has been a rough one all around, and you should be prepared in case the upgrade fails.

Second, run all 9.04 system updates and reboot.

Third, upgrade to 9.10 using the instructions here...
[http://www.knowledge76.com/index.php...ystem76_Driver](http://www.knowledge76.com/index.php...ystem76_Driver)

[B]If you are already running 9.10...
[/B]
First, go to System > Update Manger and run ALL system updates BEFORE running the 2.4.4 version of the System76 driver.

Then go to System > System76 Driver and click the Install Drivers tab and the Install button.

Reboot, and wireless will be fixed.

**If you've done a fresh install of Ubuntu 9.10...**

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.


I have a starling running 9.10 since the wireless debacle, all updates done. If I download 2.4.4 where do I put it, so to speak.

---

### Post by thomasaaron on 2010-01-11
> Say Thomas, My order for a starling has been in manufacturing since Thursday, I was wondering which version I am going to get. I may be 55 but I still feel like a 7 year old a week away from Christmas. BTW you guys at sys76 rock.

They should start putting 9.10 on them starting in the next few days. Yours will be cutting it close. If you want them to hold it for 9.10, though, email sales...at...system76...dot...etc...

---

### Post by thomasaaron on 2010-01-11
> I have a starling running 9.10 since the wireless debacle, all updates done. If I download 2.4.4 where do I put it, so to speak.

When you download it, it will go to your Downloads folder. Navigate to that folder and double-click the driver's .deb file to install it.

Once it's installed, go to Admin > System76 Driver > Restore > Restore.

Then reboot.

NOTE: Make sure you run all 9.10 updates before running the driver.

---

### Post by johnkhobson on 2010-01-11
> **thomasaaron said:**
> When you download it, it will go to your Downloads folder. Navigate to that folder and double-click the driver's .deb file to install it.

Once it's installed, go to Admin > System76 Driver > Restore > Restore.

Then reboot.

NOTE: Make sure you run all 9.10 updates before running the driver.


yeah, baby!  got it going...i finally saw the install package button in the upper right corner of the .deb window... Also it appears that even if all updates have been done, you need to run update manager one more time *after* installing the deb file--otherwise, the 76driver install just goes on and on... you might emphasize this if true.

---

### Post by thomasaaron on 2010-01-11
Hmm... I've not seen that happen here in the shop.

---

### Post by jml on 2010-01-11
Tom, I was wondering.  I am currently running 9.04 on a base Starling.  Do you have a sense of the relative performance of a Starling running 9.04 with all updates compared to a base Starling running 9.10 with all updates and the new driver.  I ask because, I am trying to decide if it is worth upgrading to 9.10 when 10.04 is so close to being released.  Can one safely upgrade to 10.04 from 9.04 or will I have to do an interim upgrade to 9.10 anyway.

Oh, by the way, congratulations and thanks to all at System 76 who made this fix possible.  Despite our comments, questions and whining, you guys really do rock.

Joe

p.s.  Sorry about the "optimistic" comment.  That was a bit harsh and uncalled for.  I can identify with your frustration of being caught between a rock and a hard place working on this forum.  You really do a great job and it's appreciated.   OK, I'm going to stop now or I may break out into a chorus of cum by ya.  jml

---

### Post by sonoftherighthand on 2010-01-11
Hey Tom, thanks for all your work.

I'm having trouble with my update.  I previously installed Karmic and used the ndiswrapper solution posted earlier on this thread.  When this update came out, I uninstalled the ndiswrapper driver using "sudo ndiswrapper -r", then proceeded with the instructions posted for the update.

Everything seemed to go find, but I can't get the wireless adapter to show up in the Network Manager Applet.  When I open System -> Administration -> System76 Driver, it show as being version 2.4.4 and when I go to System -> Administration -> Hardware Drivers, it shows the driver as being activated but not in use.

I've restarted the computer and tried to reinstall the driver; I've tried to restore from the System76 Driver app; and I've tried to flip the little network toggle switch on the front and restart.  All were without success.

I'm at a dead end.  If anyone can help, please do.

Thanks

Ben

---

### Post by jml on 2010-01-11
When I click on the link that Tom supplies:

[http://www.knowledge76.com/index.php...ystem76_Driver](http://www.knowledge76.com/index.php...ystem76_Driver)

I get a 404 error.  URL not found.  Is there a typo in the link, or have we maxed out the server's bandwidth?

Joe

---

### Post by jdb on 2010-01-11
> **jml said:**
> When I click on the link that Tom supplies:

[http://www.knowledge76.com/index.php...ystem76_Driver](http://www.knowledge76.com/index.php...ystem76_Driver)

I get a 404 error.  URL not found.  Is there a typo in the link, or have we maxed out the server's bandwidth?

Joe

It kind of looks like there should be some more text where the ellipse is.

I'm pretty sure ystem76 should be system76 & there's probably a lot more than just the s missing.

Edit:

This might be it

[http://www.knowledge76.com/index.php/System76_Driver]("http://www.knowledge76.com/index.php/System76_Driver")

jdb

---

### Post by dcharlton on 2010-01-11
Help!  I fell into the 9.10 trap, then saw the new fix, so I tried to get it...
 
Like WildBill1, I got the system updates, then the System76 driver update got stuck...
 
So as instructed, I ran "sudo apt-get install grub-pc".  This gave a few prompts, I accepted defaults, completed, and rebooted.
 
BUT, now I can't even get a wired connection!  I'm dead in the water!
 
When I reboot, I get "wicd needs access to your computer's network cards."  I enter the password, but get no connection, although I'm on a good ethernet.  And of course, the wireless is still nowhere to be found.
 
Maybe I did something dumb.  I'm pretty green with linux, and this starling is only 2 weeks old. I didn't think I could break stuff faster than my 8yr old.  ;-)

---

### Post by WarLokk on 2010-01-12
Well thank you to the System76 folks for working hard to get the update to us.  I applied the update tonight and everything is working like a charm.

---

### Post by bvandev on 2010-01-12
I've successfully completed my upgrade.  Here's what I did:
1.  Backed up.
2.  Ran the Update Manager.  (Noticed the System76 Driver as one of the packages to be upgraded.  How cool.)
3.  Pressed the long forbidden button to upgrade to Ubuntu 9.10.
4.  2.5 hours later, Karmic was installed.  I accepted the defaults.
5.  No wireless, as expected.  Added the System76 repository back to the Software Sources.  (System -> Software Sources, Other Software tab.  A little tricky.  One of the items listed as "Disabled on upgrade to Karmic" was in fact the System76 repository.  There were three of these.  I chose each and clicked on "edit" to see what it was.  I renamed it System76 in the Comments field so I can find it again later.
6.  For kicks, tried running the System76 Driver without a cable.  No dice, it checks for an internet connection.
7.  Plugged in and ran the System76 Driver.  It ran for a few minutes, no lights, no communication.  Having read an earlier post describing the same experience, I killed it.  (Did I simply not wait long enough?)  
8.  Popped open a terminal window and installed grub-pc using the standard defaults.  (sudo apt-get install grub-pc) (Grub stands for GRand Unified Bootloader.)
9.  At this point I wondered how to reboot the machine.  Ubuntu Remix has a new look.  In Jaunty, it contained three columns and a panel across the top.  The left column held high-level categories that expanded into the middle.  The right held the user's top-level directories that expanded into the middle.  It also held at the bottom the log-out icon.  The new version has merged the right column into the left, with the middle (now right two-thirds) holding the software launchers.  Now to the point; the log-out icon is gone.  I ran through the various software categories, but could not find it.  

The panel at the top comes tightly packed, disallowing new items to be added.  Remembering a tip from a different forum, I unlocked the date applet (right-click and un-check "Lock to panel"), clicked "move" and moved it to the left.  This left a space.  I right-clicked and added the "Log Out" applet.  One bummer from this move, I can't get the date back to the right corner where I want it.  There is probably a way I haven't found yet.

10.  Now able to Restart the machine at will (what power!), I did so.
11.  Back up with the System76 repository active, I ran the System76 Driver from my wired connection.  Lights blinked, always a good sign, and after a minute or two, it said it was done and that I should reboot.  
12.  I did so and saw the friendly orange light shine
13.  My brief test confirms the wireless to be more robust than before, well worth the painful, though relatively short (in the long run) wait.

Sorry for the long post, just thought it might be helpful for those about to embark to have a little more detail.

And, last but not least, thank you to System76 for resolving this issue.  The incident illustrates the risk we take by running linux on our boxes and the great benefit we derive from choosing a hardware vendor who will resolve the problems for us.

---

### Post by thomasaaron on 2010-01-12
Nice post. Thanks.

> My brief test confirms the wireless to be more robust than before, well worth the painful, though relatively short (in the long run) wait.

We've noticed that in the shop too. It seems a little faster too, maybe. Don't really have a way to benchmark it, though.

---

### Post by thomasaaron on 2010-01-12
OK, I've fixed that link. Should have been...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

**[SIZE="4"]Let's move support for upgrade issues to email. I'm having a hard time tracking them all on this post now.[/SIZE]**

So, drop me a line at support...at...system76...dot...com and I'll be able to answer much more efficiently.

---

### Post by Eyore15 on 2010-01-12
> **thomasaaron said:**
> **SOLVED WITH TODAYS 2.4.4 RELEASE OF THE SYTSEM76 DRIVER**

**If you're still running 9.04...**

First, DO A COMPLETE BACKUP OF YOUR IMPORTANT INFORMATION BEFORE UPGRADING. The upgrade to 9.10 has been a rough one all around, and you should be prepared in case the upgrade fails.

Second, run all 9.04 system updates and reboot.

Third, upgrade to 9.10 using the instructions here...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

**If you are already running 9.10...**

First, go to System > Update Manger and run ALL system updates BEFORE running the 2.4.4 version of the System76 driver.

Then go to System > System76 Driver and click the Install Drivers tab and the Install button.

Reboot, and wireless will be fixed.

**If you've done a fresh install of Ubuntu 9.10...**

First, run all System updates before running the System76 Driver.

Second, download and install the 2.4.4 version of the driver from...
[http://planet76.com/repositories](http://planet76.com/repositories)
...It will be the second link from the bottom.

Third, go the the System76 Driver and click the Restore tab and the Restore button. Then reboot your computer.

--------------------------------------------------------------------------------

**Earlier Content...**

If you own a Starling Netbook and you are currently running 9.04, please stay there for now. An upgrade to **9.10 will break your wireless**, and we do not have the fix in place yet.

If you've already upgraded to 9.10, we've released the 2.4.0 verion of the System76 Driver, which provides short-range wireless capabilities for the Starling until we are finished working on the full-scale fix. We are working hard on the fix, and will deliver it as soon as possible via a System76 Driver update.

**Please subscribe to this thread to be updated on further developments.**

**If you are still running 9.04** and are having wireless difficulties, please read this...



For optimal wireless performance until the 9.10 fix is completed, you can re-install Ubuntu Netbook Remix 9.04. Instructions are here...
[http://knowledge76.com/index.php/Restoring_Your_Netbook#Directions](http://knowledge76.com/index.php/Restoring_Your_Netbook#Directions)

Among the issues with 9.10, the most important was the wireless of course.  But there were other problems -- like just about everybody it seems had audio issues.  Are these resolved in this "fix" too?

---

### Post by rubbsdecvik on 2010-01-13
> > **thomasaaron said:**
> OK, I've fixed that link. Should have been...
[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)


Thank you for fixing up the wiki pages for Karmic. I'm sorry I dropped the ball. It's been a busy week for me personally. I'll start the upgrade tonight!

Thank you for all your support and patience while us users pestered you for updates ;)

Thank you to the System76 staff and to you personally for caring about us. 

~Pat

Not a problem. I appreciate any and all help I get.

---

### Post by thepurist on 2010-01-13
upgrade procedure ( install grub-pc) worked for me last night and my wireless worked perfectly at home last night. 

but here at work i can barely ping the gateway with 93% packet loss. when i try to connect to the only unsecure wifi around here, the entire system crashes ( black screen/frozen mouse ). the crash happened twice identically. the wireless driver is not production ready :(

let me know what i can do to help. i can send copies of logs at tonight where internet works ;)

---

### Post by thomasaaron on 2010-01-13
> **thepurist said:**
> upgrade procedure ( install grub-pc) worked for me last night and my wireless worked perfectly at home last night. 

but here at work i can barely ping the gateway with 93% packet loss. when i try to connect to the only unsecure wifi around here, the entire system crashes ( black screen/frozen mouse ). the crash happened twice identically. the wireless driver is not production ready :(

let me know what i can do to help. i can send copies of logs at tonight where internet works ;)

Your System76 Driver has a feature for creating logs. It would be best to capture them immediately after failing to connect to the AP at work. Or, at least make careful note of the time the connection attempt fails so that it will be easy to locate the event in the logs.

---

### Post by thepurist on 2010-01-13
thanks will do. 

also, i inquired with IT as to what model router we have:

apple time capsule 1 terabyte

---

### Post by thomasaaron on 2010-01-13
We've seen a number of issues with apple routers. There are also a bunch of them in the forums. Here's one...
[http://ubuntuforums.org/showthread.php?t=955814](http://ubuntuforums.org/showthread.php?t=955814)

If the computer doesn't freeze up with other access points, this may be worth investigating.

Some time ago I helped a customer that also had an Airport.  I think there is a setting on the Airports admin page specifically for Apple computers and another page for other computers.  You may want to have the IT guys check this.

If there's anybody else out there with an apple router that can render assistance with the admin screens, it would be appreciated.

---

### Post by jml on 2010-01-13
Just thought I would relate a relative success story.  Trying to upgrade my Starling borked the system.  I then downloaded 9.10 UNR and installed it to a "thumb drive".  That install went without a hitch.  I then installed the System 76 driver and the Medibuntu repositories. I now have a system that is fully functional.  My wireless has better range than it did with 9.04.  I am typing this from my den via the Starling's wireless connection.  Something I could not do before the upgrade and the new driver.  Many thanks to Tom and his colleagues at System 76! 

Joe

---

### Post by thepurist on 2010-01-14
thomasaaron - where do i send the logs?

jml - can your starling connect to apple wireless routers?

---

### Post by thomasaaron on 2010-01-14
You can send logs to me directly at support...at...system76...dot...com.
Another question just came to me: That apple router, what wireless protocol is it using? a,b,g,n? The Starling is only capable of b and g.

---

### Post by jml on 2010-01-14
Sorry, thepurist, I do not have access to an Apple router.  

Tom makes a good point.  It is quite possible that the router is set exclusively on 802.11n to maximize performance.  If it is set to connect with .g hardware, the maximum speed is limited to the slowest connection on the network.

Joe

---

### Post by jsimmond on 2010-01-16
> **sonoftherighthand said:**
> Hey Tom, thanks for all your work.

I'm having trouble with my update.  I previously installed Karmic and used the ndiswrapper solution posted earlier on this thread.  When this update came out, I uninstalled the ndiswrapper driver using "sudo ndiswrapper -r", then proceeded with the instructions posted for the update.

Everything seemed to go find, but I can't get the wireless adapter to show up in the Network Manager Applet.  When I open System -> Administration -> System76 Driver, it show as being version 2.4.4 and when I go to System -> Administration -> Hardware Drivers, it shows the driver as being activated but not in use.

I've restarted the computer and tried to reinstall the driver; I've tried to restore from the System76 Driver app; and I've tried to flip the little network toggle switch on the front and restart.  All were without success.

I'm at a dead end.  If anyone can help, please do.

Thanks

Ben

Hi Ben, did you check if the rtl8187 driver is still blacklisted? 
Look in the files in the /etc/modprobe.d directory. I had to manually remove rtl8187 from one of these blacklists, and I also deleted a file called ndiswrapper from this directory. After that I rebooted and my wireless was back (no more ndiswrapper)

---

### Post by nealaustin on 2010-01-16
Got my starling new,added all of my stuff and as a last task I updated in the update manager. This morning the wireless didn't work. So Ithought it was time for the upgrade to karmic. Did everything according to the instructions but instead of 3 rd party software it said other software. I downloaded the sys76 2.4.4 and the install is now running about 1/2 hour should it take that long? Tat silly toggle switch on the front. Should it be left or right?

---

### Post by black_ice=cream on 2010-01-16
No. This is the EXACT same thing that happened 2 me and this is how I fixed it:

1st - run this command in terminal and accept all defaults 
    
sudo apt-get install grub-pc



2nd reboot

3rd re-run driver

4th reboot

5th run any updates in update manager

then hopefily it will work

---

### Post by thepurist on 2010-01-17
nealaustin,  you can do what black_ice=cream says, but when you do get it working, your  wifi will only work with CERTAIN wireless routers. for instance the starling will not work with an apple wireless router using WPA2 encryption. it's not my apple router so i can't try an alternate router configuration, but according to what i've read in the forums, there's something about apple's encryption that isn't compatible with the system76 build of the rtl8187 wireless driver so perhaps it works without encryption. having said that, a netbook should work with ANY wireless router and ANY type of encryption else it's not a very useful netbook.

i'm now wondering if compiling my own kernel/modules will remedy this problem but that kind of goes against my entire idea for buying a system76 netbook- i thought i'd save all that linux hacking time by buying from a company that supports linux. i'm thankful that so many devices work such as the webcam, the audio, and the power management but the two most important things that i need are just not there "out of the box", namely a reliable wifi driver and a reliable driver for at&t's usbconnect 881. same is true for both ubuntu 9.4 and 9.10.

does anyone know what would happen if i put the "normal" karmic 9.10 on my starling instead of the remix netbook edition? will i have a better chance at connecting to an apple router?

i edited out some whiny comments here- long story short, i do feel a bit foolish for not having read the forums before purchasing the starling.

---

### Post by thomasaaron on 2010-01-18
Hey, guys. Where are we on this one?

---

### Post by thomasaaron on 2010-02-08
jsimmonds, are you still wrapping the windows driver? If so, that's completely unnecessary now.

It would be better to completely ditch that one and run the 2.4.4 or greater version of the System76 Driver.

---

### Post by jsimmond on 2010-02-09
> **thomasaaron said:**
> jsimmonds, are you still wrapping the windows driver? If so, that's completely unnecessary now.

It would be better to completely ditch that one and run the 2.4.4 or greater version of the System76 Driver.

Yup, I got rid of the windows driver about 3 weeks ago. I have 100% connection with the new driver (I used to get 75% with the old one from the same spot).

---

### Post by kfries6 on 2010-02-18
My WiFi only partially works.

Unencrypted Networks... Check
WEP w/low encryption... Check

Everything else... No Go

Here is a /var/log/messages capture of me trying to connect to a 
Linksys WRT54G

-------------------------------------------------------------------------
Feb 18 11:55:16 system76-netbook kernel: [  466.615352] rtl8187B: ISLeave(): Turn on RF.
Feb 18 11:55:16 system76-netbook kernel: [  466.616710] rtl8187B: Now Radio ON!
Feb 18 11:55:17 system76-netbook kernel: [  466.993814] Linking with CCTNewTechnologies, channel:6
Feb 18 11:55:17 system76-netbook kernel: [  467.128518] Associated successfully
Feb 18 11:55:17 system76-netbook kernel: [  467.128537] Using G rates
Feb 18 11:55:18 system76-netbook kernel: [  468.140775] alg name:TKIP
Feb 18 11:55:18 system76-netbook kernel: [  468.145032] alg name:TKIP
Feb 18 11:55:22 system76-netbook kernel: [  472.154802] Linking with CCTNewTechnologies, channel:6
Feb 18 11:55:22 system76-netbook kernel: [  472.219828] Linking with CCTNewTechnologies, channel:6
Feb 18 11:55:22 system76-netbook kernel: [  472.266172] Associated successfully
Feb 18 11:55:22 system76-netbook kernel: [  472.266185] Using G rates
Feb 18 11:55:22 system76-netbook kernel: [  472.309149] alg name:TKIP
Feb 18 11:55:22 system76-netbook kernel: [  472.317795] alg name:TKIP
Feb 18 11:56:03 system76-netbook kernel: [  513.251719] Linking with CCTNewTechnologies, channel:6
Feb 18 11:56:08 system76-netbook kernel: [  518.528122] rtl8187B: IPSEnter(): Turn off RF.
Feb 18 11:56:08 system76-netbook kernel: [  518.529174] rtl8187B: Now Radio OFF!
-------------------------------------------------------------------------

It does this on my WRT54G at home, also with TKIP (but I tried changing to AES with the same results), and a Comcast supplied wireless router (unsure of the encryption method, but it is WPA.

Something ain't quite right on this.

Please Help, without wireless, this netbook is far less useful!

Kevin Fries

---

### Post by thomasaaron on 2010-02-18
Sounds like you used the ndiswrapper method mentioned earlier. I think that method might not support wpa. 

If you get rid of the wrapper, though, and run the 2.5.5 vesion of the System76 driver, it will support wpa. That's what we use for testing here in the office.

---

### Post by kfries6 on 2010-02-18
Nope, I pick this up from you guys last week :-)

kfries@system76-netbook:~$ dpkg -l | grep system76
ii  system76-driver                            2.4.5                                      Universal driver for System76 computers.
kfries@system76-netbook:~$ 

I even tried to manually update the driver to the newest version on planet76... this was at 2.4.4, tried upgrading to 2.4.5, still no go.  If you want, I can stop it back buy for you to take a look in person.

Kevin

---

### Post by thomasaaron on 2010-02-18
That's cool, Kevin.

If you want to stop by, we'll test it on our shop AP. If you want a clean image for any reason, make sure you're all backed up.

---

### Post by jbraswell on 2010-03-02
Sorry, this may be a bit of hijack, but I just upgraded, and it appears that the wireless is fine, but I'm having some serious gnome issues or something.  The mousepad doesn't work at all, and using the keyboard to navigate the GUI menu is *super* slow, as in, it takes about 5 seconds to move my icon highlight.

If I open a terminal, though, it's very responsive. Applications, also, seem to be running normally, it just takes me about 5 minutes to navigate to one.  

Anyone have any similar difficulties or ideas?

Thanks

---

### Post by thomasaaron on 2010-03-02
I've not seen exactly THOSE symptoms, but I've seen some that are pretty close.  Try this...

> This is a new bug we've recently encountered. There is a package called winbind that, as far as we can tell, is breaking HAL (the hardware abstraction layer), which provides an interface to your keyboard and mouse.

Here is the fix...

1. Establish a wired (Ethernet) Internet connection.

2. Boot into recovery mode.
Right after the System76 Splash Page, you will see the word "Grub" in the upper left corner of your LCD. The moment you see it, quickly press "Shift." This should get you to a list of available kernels. Choose the first kernel that has "Recovery Mode" in its title. You will then be prompted to select a particular recovery mode functionality. Select Netroot (or "boot into a root prompt with networking").

3. Once you're in recovery mode, run the following commands. (In some instances, the letters typed are not echoed to the screen, but they are being entered.)

dpkg --configure -a
apt-get remove winbind
apt-get install winbind
apt-get --reinstall install hal
apt-get update
apt-get dist-upgrade
reboot -h now

---

### Post by jbraswell on 2010-03-02
Er, afraid not. All the instructions seemed to work OK, but it's the same situation when I reboot. 

Two incidental things, though:

One, when I chose the kernel, all my options were prepended with 9.04 instead of 9.10.

Two, I don't get a System76 splash screen at startup, nor have I ever since I first purchased it. I just get a message about not being able to hot add a device or something.  I still got to the boot menu with Esc, though.

---

### Post by jbraswell on 2010-03-02
Also, I just tried uninstalling winbind completely and not reinstalling it.  No luck.

---

### Post by thomasaaron on 2010-03-03
OK, for starters it sounds like your upgrade didn't upgrade to the latest version of grub (which is why the 'Esc' key still works to get to a kernel menu). In 9.10, it should be the shift key.

So, establish a wired Internet connection again, boot into recovery mode and then into netroot (or recovery mode with networking) and run...

apt-get install grub-pc

Then reboot.

---

### Post by jbraswell on 2010-03-03
OK, tried that, but now I get "GRUB loading, please wait...Error 15"

*sigh*

I suppose I need to boot live from USB to fix this now?

---

### Post by jbraswell on 2010-03-03
Nevermind. I'm just going to reinstall...too much of a pain in the ***.

---

### Post by Scoats on 2010-03-18
I was having trouble reinstalling 9.04, then I realized it was installing it to the SD card, creating 2 versions of Ubuntu on the Starling. Once I pulled the SD out, the install finally worked fine. I finally have wireless networking again.

---

### Post by mrchuc on 2010-04-11
> **jml said:**
> Just thought I would relate a relative success story.  Trying to upgrade my Starling borked the system.  I then downloaded 9.10 UNR and installed it to a "thumb drive".  That install went without a hitch.  I then installed the System 76 driver and the Medibuntu repositories. I now have a system that is fully functional.  My wireless has better range than it did with 9.04.  I am typing this from my den via the Starling's wireless connection.  Something I could not do before the upgrade and the new driver.  Many thanks to Tom and his colleagues at System 76! 

Joe

Sorry to come so late to the party. :)

I had the same thing happen when I tried to upgrade some weeks ago. I waited until I thought all the issues were solved, but my system is apparently hosed and I didn't have time to work on it. I just put my old Mac back in service for this semester and limped along. 

I am getting ready to try what you suggest--reinstall from a thumb drive. Any other details or warnings you can supply? I am not very knowledgeable on Linux issues yet. (But I LOVE my Starling and want it back!!!) :)

Thanks!

Chuc

---

### Post by thomasaaron on 2010-04-12
Yes, follow the instructions here...

[http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)

---

