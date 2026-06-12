---
title: "Firefox 33 slow?"
date: 2014-10-15
forum: The Cafe
---

### Post by sammiev on 2014-10-15
Well I used Forefox for many years now and the latest is not the greatest. My computer slowed to a new low today. :( Time to move on I guess.

Solved with FF43

---

### Post by ajgreeny on 2014-10-15
Are you using 14.10 as is suggested by your user info in my forum's left hand pane?

FF 33 is working fine on my machines, old and new, 32 and 64 bit, so there must be something about your OS or machine or FF profile thaty is slowing things down.

---

### Post by pfeiffep on 2014-10-15
I keep both Chromium and Firefox installed on my PC; normally I use Chromium but your post prompted me to use FF. I noted version was 33 and didn't notice any difference in speed.

---

### Post by sammiev on 2014-10-15
> **ajgreeny said:**
> Are you using 14.10 as is suggested by your user info in my forum's left hand pane?

FF 33 is working fine on my machines, old and new, 32 and 64 bit, so there must be something about your OS or machine or FF profile thaty is slowing things down.

Yes I'm using 14.10 and after the update today when I move up or down scrolling with the mouse it's rather very jerky. Never had that with FF32.

Using a fully Intel system with 8gib ram and a i5 with a SSD. Boot times are less than 15 seconds with gnome and less than 10 seconds with kde.

---

### Post by sammiev on 2014-10-15
> **pfeiffep said:**
> I keep both Chromium and Firefox installed on my PC; normally I use Chromium but your post prompted me to use FF. I noted version was 33 and didn't notice any difference in speed.

I'm not noticing any difference or slow downs with Google Chrome beta.

---

### Post by Erik1984 on 2014-10-15
Have you tried a clean Firefox profile?

---

### Post by frank75 on 2014-10-15
I just got the Firefox 33 update today in  Ubuntu MATE' and it still seems to run as well as it always did. Don't really see much difference to tell you the truth.

---

### Post by d-cosner on 2014-10-15
Same here in Ubuntu 14.04 x64.

---

### Post by sammiev on 2014-10-15
Tried a new profile and even a new install of FF after deleting the full folder of FF. It's is much slower with the page movements using the mouse but as quick as it was when I slide the bar up and down with the mouse.

---

### Post by bashiergui on 2014-10-17
> **sammiev said:**
> Tried a new profile and even a new install of FF after deleting the full folder of FF. It's is much slower with the page movements using the mouse but as quick as it was when I slide the bar up and down with the mouse.
What addons have you installed?

---

### Post by sammiev on 2014-10-17
I do have a few addons but the very first thing I did was disable all addons when I discovered the lag.

---

### Post by speedwell68 on 2014-10-17
I have FF 33, TBH I only use it for SkyGo, but I have just tried it and it seems as quick as Chrome 38.  I used to be a FF purist, but dropped it in favour of Chrome when Adobe ended support for Flash on Linux.

---

### Post by buzzingrobot on 2014-10-17
> **sammiev said:**
> Yes I'm using 14.10 and after the update today when I move up or down scrolling with the mouse it's rather very jerky. Never had that with FF32.
.

"Jerky" is a bit vague, but try disabling smooth scrolling and see what happens.  I've seen various impacts of that, from good to bad, on different distros but the same Firefox version on the same hardware.

Otherwise, I wouldn't know Firefox had upgraded unless I'd looked. No discernible changes here.

---

### Post by craig10x on 2014-10-17
I have always found firefox to scroll kind of "jerky" and yet scrolling in Chrome (which is what i primarily use) is very smooth...don't know why that is, but that has been my observation...

---

### Post by sammiev on 2014-10-17
> **craig10x said:**
> I have always found firefox to scroll kind of "jerky" and yet scrolling in Chrome (which is what i primarily use) is very smooth...don't know why that is, but that has been my observation...

+1

---

### Post by Mike_Walsh on 2014-10-18
> **speedwell68 said:**
> I have FF 33, TBH I only use it for SkyGo, but I have just tried it and it seems as quick as Chrome 38.  I used to be a FF purist, but dropped it in favour of Chrome when Adobe ended support for Flash on Linux.

Same here. TBH, I only use it for the Ant Video downloader.....it's not available for Chrome, but for everything else I too use Chrome. I tried Firefox again on reading this thread, and can't say as I've noticed any difference at all.

The only thing I always do with FF when I install it, is to go into 'about:config' & change browser:newtaburl to about:blank. I can't stand all those annoying reminders of sites I've just recently visited!

Regards,

Mike.

---

### Post by sammiev on 2014-10-18
> **Mike_Walsh said:**
> Same here. TBH, I only use it for the Ant Video downloader.....it's not available for Chrome, but for everything else I too use Chrome. I tried Firefox again on reading this thread, and can't say as I've noticed any difference at all.

The only thing I always do with FF when I install it, is to go into 'about:config' & change browser:newtaburl to about:blank. I can't stand all those annoying reminders of sites I've just recently visited!

Regards,

Mike.

Try FF33 on this site and try to scroll up... It's very slow when there is attachments and not so on other browsers.

---

### Post by ajgreeny on 2014-10-18
I don't use Chrome, but I do use Chromium sometimes and I don't find that is better at scrolling than FF, but then as I said in post #2, FF 33 works fine here for me on Xubuntu 64bit.

I wonder if this is related to graphics card in some way.  What is your hardware?

---

### Post by sammiev on 2014-10-18
> **ajgreeny said:**
> I don't use Chrome, but I do use Chromium sometimes and I don't find that is better at scrolling than FF, but then as I said in post #2, FF 33 works fine here for me on Xubuntu 64bit.

I wonder if this is related to graphics card in some way.  What is your hardware?

```
sam@sam-L650G:~$  lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Model name:            Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
Stepping:              5
CPU MHz:               1199.000
CPU max MHz:           2667.0000
CPU min MHz:           1199.0000
BogoMIPS:              5333.50
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3
sam@sam-L650G:~$ sudo lshw -short
[sudo] password for sam: 
H/W path        Device      Class          Description
======================================================
                            system         Satellite L650 (Calpella)
/0                          bus            Portable PC
/0/0                        memory         1MiB BIOS
/0/18                       memory         8GiB System Memory
/0/18/0                     memory         4GiB SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
/0/18/1                     memory         4GiB SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
/0/24                       processor      Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz
/0/24/25                    memory         3MiB L3 cache
/0/24/27                    memory         256KiB L2 cache
/0/24/28                    memory         32KiB L1 cache
/0/26                       memory         32KiB L1 cache
/0/100                      bridge         Core Processor DRAM Controller
/0/100/2                    display        Core Processor Integrated Graphics Controller
/0/100/16                   communication  5 Series/3400 Series Chipset HECI Controller
/0/100/1a                   bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                   multimedia     5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                   bridge         5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c/0     eth0        network        AR8152 v1.1 Fast Ethernet
/0/100/1c.1                 bridge         5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0   wlan0       network        RTL8191SEvB Wireless LAN Controller
/0/100/1c.4                 bridge         5 Series/3400 Series Chipset PCI Express Root Port 5
/0/100/1d                   bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                   bridge         82801 Mobile PCI Bridge
/0/100/1f                   bridge         Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2                 storage        5 Series/3400 Series Chipset 4 port SATA AHCI Controller
/0/100/1f.3                 bus            5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                 generic        5 Series/3400 Series Chipset Thermal Subsystem
/0/101                      bridge         Core Processor QuickPath Architecture Generic Non-core Registers
/0/102                      bridge         Core Processor QuickPath Architecture System Address Decoder
/0/103                      bridge         Core Processor QPI Link 0
/0/104                      bridge         1st Generation Core Processor QPI Physical 0
/0/105                      bridge         1st Generation Core Processor Reserved
/0/106                      bridge         1st Generation Core Processor Reserved
/0/1            scsi1       storage        
/0/1/0.0.0      /dev/sda    disk           120GB KINGSTON SV300S3
/0/1/0.0.0/1    /dev/sda1   volume         50GiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2   volume         61GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume         3892MiB Linux swap / Solaris partition
/0/1/0.0.0/2/6  /dev/sda6   volume         50GiB Linux filesystem partition
/0/2            scsi5       storage        
/0/2/0.0.0      /dev/cdrom  disk           CDDVDW TS-L633C
/1                          power          OEM_Define5

```

---

### Post by kurt18947 on 2014-10-19
Using Ubuntu-Gnome 14.04.  I've seen that jerky scroll in the somewhat distant past. What worked for me was disabling smooth scrolling. Ironic, huh?

---

### Post by linuxyogi on 2014-10-19
I am using 34.0a2 (2014-10-13). I downloaded it from their site so I am on Aurora update channel.

No speed difference. 

Addons : NoScript, Ghostery, Bluhell, NetVideoHunter, BetterPrivacy, DownloadThemAll.

---

### Post by Mike_Walsh on 2014-10-19
Just to update;

Tried Firefox again this morning. Sammiev, you are INDEED right about the scrolling with the mouse. It appears to be erratic on my install; sometimes jerky, sometimes smooth. When I posted my previous reply, it was behaving itself.....but I can now see what you mean!

It DOES, however, run and load at its normal speed.....so my issue appears to be simply the scrolling. :confused:

Curious.

Regards,

Mike.

---

### Post by sammiev on 2014-10-19
> **Mike_Walsh said:**
> Just to update;

Tried Firefox again this morning. Sammiev, you are INDEED right about the scrolling with the mouse. It appears to be erratic on my install; sometimes jerky, sometimes smooth. When I posted my previous reply, it was behaving itself.....but I can now see what you mean!

It DOES, however, run and load at its normal speed.....so my issue appears to be simply the scrolling. :confused:

Curious.

Regards,

Mike.

Scrolling is the problem, the more graphics, the worst it is.

---

### Post by kurt18947 on 2014-10-20
> **ajgreeny said:**
> I don't use Chrome, but I do use Chromium sometimes and I don't find that is better at scrolling than FF, but then as I said in post #2, FF 33 works fine here for me on Xubuntu 64bit.

I wonder if this is related to graphics card in some way.  What is your hardware?

I'm curious about graphics hardware as well. I have an AMD board and Nvidia G210 graphics.  The open video driver doesn't like that combination at all, performance and stability are substandard to be kind. Nvidia's driver works great.  I wonder if there's something about Firefox' graphics engine that goes crossways with Sammiev's hardware.

---

### Post by linuxyogi on 2014-10-21
When I tried using Unity for the first time everything seemed fine but video playback was choppy so  I installed the (#apt-get install lubuntu-desktop) the lubuntu DE and tested video performance.  The playback was smooth.   Just install lubuntu-desktop and test FF's performance. If FF runs well under lubuntu then Unity  is too much for your GPU.

---

### Post by Kale_Freemon on 2014-10-21
> **linuxyogi said:**
> When I tried using Unity for the first time everything seemed fine but video playback was choppy so  I installed the (#apt-get install lubuntu-desktop) the lubuntu DE and tested video performance.  The playback was smooth.   Just install lubuntu-desktop and test FF's performance. If FF runs well under lubuntu then Unity  is too much for your GPU.

Before having him do that, wouldn't be a good idea if we asked what kind of GPU he has? I mean, I'm running Unity smoothly on an integrated Intel GPU from 2008.

Granted, it could be the GPU, but it may also just be a bug in either Unity or the driver for his GPU. Also, gotta keep in mind that he is 14.10, which is still an RC.

---

### Post by sammiev on 2014-10-21
I posted all my info already and it only happens with FF33. I will try testing and older version to see how much difference I notice. All other browsers are smooth as glass.

---

### Post by Kale_Freemon on 2014-10-21
> **sammiev said:**
> I posted all my info already and it only happens with FF33. I will try testing and older version to see how much difference I notice. All other browsers are smooth as glass.

I'm still willing to bet bug. Excuse me if I seem a bit newbish when it comes to trying to read the output you posted earlier. But, I'm assuming when you said it was a fully Intel system, you meant that you are also using an integrated GPU.

Regardless of that, your system should be able to handle it fine. My old Macbook runs it flawlessly, as does my old Gateway. All Intel. So, this seems odd. Again, though, it's an RC.

How well did disabling smooth scrolling work? Has it been consistent or did it start acting up again?

---

### Post by vasa1 on 2014-10-21
> **sammiev said:**
> ... It's is much slower with the page movements using the mouse but as quick as it was when I slide the bar up and down with the mouse.
What about when you use the page up and page down keys?

---

### Post by sammiev on 2014-10-21
> **Kale_Freemon said:**
> I'm still willing to bet bug. Excuse me if I seem a bit newbish when it comes to trying to read the output you posted earlier. But, I'm assuming when you said it was a fully Intel system, you meant that you are also using an integrated GPU.

Regardless of that, your system should be able to handle it fine. My old Macbook runs it flawlessly, as does my old Gateway. All Intel. So, this seems odd. Again, though, it's an RC.

How well did disabling smooth scrolling work? Has it been consistent or did it start acting up again?

Made it worse than it was.

---

### Post by sammiev on 2014-10-21
> **vasa1 said:**
> What about when you use the page up and page down keys?

Works perfect.

---

### Post by vasa1 on 2014-10-21
> **sammiev said:**
> Works perfect.
So that plus the fact that using the scrollbar also is perfect narrows down matters to something mousy as opposed to CPU/GPU/RAM, etc.

I've been keeping "Use autoscrolling", "Use smooth scrolling", and "Use hardware acceleration when available" unticked for as long as I remember but you could look at what comes up when you type **scroll** in about:config. I have too much invested in Firefox to dump it :)

---

### Post by tjeremiah on 2014-10-23
Ive been using more and more chromium. It sucks to say because I use to be a huge firefox fanboy. I still like it because I feel its the best browser for extensions that work properly but with a page with a ton of images, for years no matter the cpu im on the browser is just so slow and sluggish. Chromium just seems lighter and faster. Maybe my firefox profile is bloated (ive been using it for years, afraid to change it) but I wish Firefox was better than chromium in terms of performance. A bit off topic but I cant seem to get Amazon prime to work under chromium but only in FF.

---

### Post by /ADM on 2014-10-24
> **tjeremiah said:**
> Ive been using more and more chromium. It sucks to say because I use to be a huge firefox fanboy. I still like it because I feel its the best browser for extensions that work properly but with a page with a ton of images, for years no matter the cpu im on the browser is just so slow and sluggish. Chromium just seems lighter and faster. Maybe my firefox profile is bloated (ive been using it for years, afraid to change it) but I wish Firefox was better than chromium in terms of performance. A bit off topic but I cant seem to get Amazon prime to work under chromium but only in FF.

+1

Firefox has somehow become so bloated.  I don't see how a browser can use at times more resources than a game, but it shouldn't.

---

### Post by sammiev on 2014-11-27
FF34 is out and I had to look to see if I was using the same computer. Problem solved!

---

### Post by vasa1 on 2014-11-27
> **sammiev said:**
> FF34 is out and I had to look to see if I was using the same computer. Problem solved!

That's great but I think the official release date is Dec 2. This page still has 33.1.1: [https://www.mozilla.org/en-US/firefox/channel/#firefox](https://www.mozilla.org/en-US/firefox/channel/#firefox)

---

### Post by Tar_Ni on 2014-11-27
Yep, on Ubuntu we are still at Firefox 33.0 for the driver fixes of 33.1.1 doesn't concern Linux. Firefox 34 stable has been postponed to the 1st or 2nd of December: it was previously scheduled for November 25th.

sammiev must be on the beta channel or else he has the 33.0 stable built.

---

### Post by sammiev on 2014-11-27
FF34 came in on 15.04 today on the updates and I'm using it on VMware. My main  OS 14.10 using FF33 is a turtle and it's not on a VM.

---

### Post by vasa1 on 2014-11-27
> **sammiev said:**
> FF34 came in on 15.04 today on the updates ...
@sammiev, can you please check if it's the beta version? The link I provided normally shows the new version of Firefox before the Software Center does.

---

### Post by sammiev on 2014-11-27
> **vasa1 said:**
> @sammiev, can you please check if it's the beta version? The link I provided normally shows the new version of Firefox before the Software Center does.

Attached

---

### Post by monkeybrain20122 on 2014-11-29
FF33 is slow and it freezes randomly but only on 14.10, on 14.04 it is fast and never freezes. Both run on the same machine (different partitions) so I think it is a 14.10 issue. I posted a thread long ago.[http://ubuntuforums.org/showthread.php?t=2250936&p=13160821#post13160821](http://ubuntuforums.org/showthread.php?t=2250936&p=13160821#post13160821)

---

### Post by adam_smith3 on 2014-11-29
I have noticed that that version of Firefox is pretty slow especially with video settings. When I was video chatting with my girlfriend and her friends it would repeatedly stop connection right when we got to some of the good parts of the conversation. It's pretty annoying when it boots u out right before. They really need to catch up with safari and google chrome in speed.

---

### Post by monkeybrain20122 on 2014-11-29
> **adam_smith3 said:**
> I have noticed that that version of Firefox is pretty slow especially with video settings. 

As I said I have these problems only in Ubuntu 14.10. Which version of Ubuntu do you use?

---

### Post by Linuxratty on 2014-11-30
It's not slow for me,but it has had other strange glitches now and again.

---

### Post by gregor10 on 2014-12-17
Same here, Chromium is very fast, FF slow and sluggish. Manjaro-Linux is running on my other computer, with Firefox as fast as Chromium! 

No solutions?

---

### Post by monkeybrain20122 on 2014-12-17
It has been upgraded to FF34. It seems better as I have not encountered any freeze yet, though I have not logged into Ubuntu 14.10 very much so I haven't done any thorough testing. As I said FF 33 and 34 are both very fast on Ubuntu 14.04 on the same machine (my 'real' work OS, 14.10 is just for testing)

---

### Post by sammiev on 2014-12-17
FF34 fixed all my issues. This thread should be closed.

---

### Post by lisati on 2014-12-17
> **sammiev said:**
> FF34 fixed all my issues. This thread should be closed.

You can mark the thread "solved" by using the "Thread tools" drop-down menu.

---

### Post by sammiev on 2014-12-17
> **lisati said:**
> You can mark the thread "solved" by using the "Thread tools" drop-down menu.

It was moved to the cafe. It can not be marked as solved using Thread Tools.

---

### Post by lisati on 2014-12-17
> **sammiev said:**
> It was moved to the cafe. It can not be marked as solved using Thread Tools.
Good call. I've closed it for you.

---

