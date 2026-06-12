---
title: "Wireless died on Starling netbok"
date: 2011-07-16
forum: System76 Support
---

### Post by likescookies on 2011-07-16
I'm running a Starling netbook running Ubuntu 11.04. I've been running 11.04 for at least a couple of months. Yesterday, I let the update manager install the latest updates as usual (over wireless). This morning when I turned the machine on, it doesn't seem to recognize the wireless card--the network applet shows no wireless options at all, and FN-F2 has no apparent effect.

Troubleshooting steps taken:
1. Reboot
2. Make sure the little 3G-WiFi button is to WiFi.
3. Plus into a wired connection and reinstall System76 drivers and reboot (I appear to be running 2.6.7).
4. Walk through Ubuntu's troubleshooting guide for wireless. None of the command line commands it had me enter showed any indication that there is even a wireless card installed.
5. Run Update Manager. Says system is up to date.
6. Browse the last few weeks of this forum.

Not sure where to go from here; I'd love it if anyone could throw me a lifeline.

Note that I'm a Linux novice, but I'm learning.

Thanks much.

---

### Post by Bleak888 on 2011-07-17
I've had this issue a couple of times since I upgraded my Pangolin. I have been able to perform cold reboot to get it working. Make sure you fully shutdown your system not just reboot and if the issue is the same, wireless card should be recognized when system is restored.

---

### Post by isantop on 2011-07-18
Let's go ahead and check the wireless network switch one more time, to be sure. Go ahead and restart your system, to start with a fresh plate, then once it's booted up, slide the switch once to the right, release it, then reboot the computer again. Now, the wireless card should be turned on. Did that fix it?

---

### Post by likescookies on 2011-07-18
I never knew that a cold reboot wasn't the same as a reboot from the system menu. Alas, shutting all the way down and rebooting didn't help.

isantop, I also tried the sequence you suggest without success--still no indication of wireless capability in the networking menu at the top, and no flashing wifi light. I'm certainly open to further suggestions.

---

### Post by nealaustin on 2011-07-19
Same problem here, help?


> **likescookies said:**
> I'm running a Starling netbook running Ubuntu 11.04. I've been running 11.04 for at least a couple of months. Yesterday, I let the update manager install the latest updates as usual (over wireless). This morning when I turned the machine on, it doesn't seem to recognize the wireless card--the network applet shows no wireless options at all, and FN-F2 has no apparent effect.

Troubleshooting steps taken:
1. Reboot
2. Make sure the little 3G-WiFi button is to WiFi.
3. Plus into a wired connection and reinstall System76 drivers and reboot (I appear to be running 2.6.7).
4. Walk through Ubuntu's troubleshooting guide for wireless. None of the command line commands it had me enter showed any indication that there is even a wireless card installed.
5. Run Update Manager. Says system is up to date.
6. Browse the last few weeks of this forum.

Not sure where to go from here; I'd love it if anyone could throw me a lifeline.

Note that I'm a Linux novice, but I'm learning.

Thanks much.

---

### Post by thomasaaron on 2011-07-21
OK, let's run a sequence of tests... Quit when you get wireless.

1. Open your System76 driver and click the Install tab and the Install button. When the driver finishes running, reboot the machine. Do you have wireless?

2. Press Fn and F2 simultaneously. Reboot the machine. Wifi?

3. Press the wifi-3g switch *once* to the right. Reboot. Wifi?

4. 2. Press Fn and F2 simultaneously again. Reboot the machine. Wifi?

If you don't have wifi at this point, it's probably a bad wifi card.

---

### Post by nealaustin on 2011-07-21
It strikes me as funny that the wifi card would be broken right after an upgrade. Did this fix your's "likescookies" It didn't mine. I tried Thomas' sequence and then some just to be sure. Can the Wifi card be switched out? If so is there a more stable product that would fit in the Starling. At this point I wish I had spent the extra money and bought a Pangolin.

> **thomasaaron said:**
> OK, let's run a sequence of tests... Quit when you get wireless.

1. Open your System76 driver and click the Install tab and the Install button. When the driver finishes running, reboot the machine. Do you have wireless?

2. Press Fn and F2 simultaneously. Reboot the machine. Wifi?

3. Press the wifi-3g switch *once* to the right. Reboot. Wifi?

4. 2. Press Fn and F2 simultaneously again. Reboot the machine. Wifi?

If you don't have wifi at this point, it's probably a bad wifi card.

---

### Post by likescookies on 2011-07-22
Alas, the sequence had no effect.

I hear what you are saying, Neal, though if the latest update was killing wifi I'd expect more chatter, even if it was limited to the Starling. I suppose one way to test that would be to back up a version, perhaps booting off a flash drive.

Another thing you and I have in common is approximate location. I suppose it is possible the heat wave or killer humidity did the cards in.

In any case, my machine is out of warranty so I have the same question: how hard is it to swap out the card for a new one?

---

### Post by nealaustin on 2011-07-23
Got out my USB boot stick, started all over and the wi-fi came right on. I even ran the update manager and all is well. Haven't loaded the system 76 drivers yet.

---

### Post by likescookies on 2011-07-24
Interesting; that's great news. Just so I'm clear--you put on a fresh install of 11.04 when you booted off the USB key, yes?

---

### Post by nealaustin on 2011-07-24
Yes that's all I did. I had already made the key (just in case). Then I did the upgrade (ON WIRELESS) and everything turned out fine. A bigger problem that I had looming though was a need to access a program from work. This program would not work with Linux on a net-book. The IT department were not cooperative so I needed to get a new computer. I picked up a windows laptop from Best Barf and will eventually make it a dual boot machine. My son offered me $100 for the starling and I sold it. Maybe someday I will be buying another System 76 product. Now that I set this computer up I remembered exactly all of the things I hated about windows.

---

### Post by ParsonT on 2011-07-26
Here's some of that chatter. I have the same problem with a Starling 1, after applying the same updates. I've tried all the Fn F2 and wifi button reboots, reinstalled the System 76 driver, etc to no avail. The system doesn't seem to know that a wireless card is present. 

I'd like to be able to repair without having to re-install 11.04. Help would be appreciated.

---

### Post by likescookies on 2011-07-27
A fresh install of 11.04 cleared the problem--wireless is functioning again. Yay!

---

### Post by thunderbolt16 on 2011-07-30
I'm also having this issue with my star1's wireless driver and the latest Ubuntu update.

Trying the sequence of steps for troubleshooting provided no relief. I don't have the time right now to reinstall, but I'll let anyone know if I discover a better solution.

---

### Post by ParsonT on 2011-08-01
I resorted to a fresh install of 11.04, and the radio came back. It is still working after applying all the updates.

Time-consuming and annoying. Oh well.

---

### Post by isantop on 2011-08-01
> **thunderbolt16 said:**
> I'm also having this issue with my star1's wireless driver and the latest Ubuntu update.

Trying the sequence of steps for troubleshooting provided no relief. I don't have the time right now to reinstall, but I'll let anyone know if I discover a better solution.

Can you try running from a LiveUSB drive? That will tell me a lot about what works and what doesn't.

---

### Post by vantage1313 on 2011-08-02
Hi all,

I had the same issue. Looks like the module for the wireless card is no longer loading on boot.

I loaded the module manually
vantage1313@system76-netbook:~$ sudo modprobe rtl8187

Played with Fn F2 a bit until I got a light
vantage1313@system76-netbook:~$ dmesg | grep rtl8187 
[ 6906.249592] rtl8187: Customer ID is 0x00
[ 6906.257148] Registered led device: rtl8187-phy0::radio
[ 6906.257971] Registered led device: rtl8187-phy0::tx
[ 6906.258902] Registered led device: rtl8187-phy0::rx
[ 6906.259706] rtl8187: wireless switch is off
[ 6906.261664] usbcore: registered new interface driver rtl8187
[ 7056.992879] rtl8187: wireless radio switch turned on
[ 7062.000863] rtl8187: wireless radio switch turned off
[ 7216.992789] rtl8187: wireless radio switch turned on

Wifi started working at this point.

Added rtl8187 to /etc/modules , rebooted and the wifi came up fine.

Hope this helps.

---

### Post by wilhelmj on 2011-08-02
Hi,

I applied the update to my Starling yesterday and today I noticed I am having the same problem, no wireless.

---

### Post by isantop on 2011-08-03
have you tried running from a LiveUSB?

---

### Post by bstudent on 2011-08-04
Hi,

I am thinking about buying a Starling within the next few days, but this thread has got me worried. I'm completely new to linux, so I would be quite lost trying to fix this. And I'm really not going to have time to figure out how to fix something major on day one. So my question is...

Will system76 install the most recent updates to ubuntu 11.04 before shipping? And if so, will they check everything out to make sure that it is all working before shipping? (In particular, this problem) It seems like there's a good chance that this issue is going to happen, so I would much rather it be checked and/or solved on my netbook before it gets shipped. Finally, if updating and checking is not part of the company's normal routine, can I make a special request that this be done for my order?

Hopefully this message doesn't sound too critical. This seems like a nice company, and I'm really excited about the Starling and about switching to linux. I just want my netbook to work when I get it.


Thanks,
wdb
Potential Customer

---

### Post by nealaustin on 2011-08-04
> **bstudent said:**
> Hi,

I am thinking about buying a Starling within the next few days, but this thread has got me worried. I'm completely new to linux, so I would be quite lost trying to fix this. And I'm really not going to have time to figure out how to fix something major on day one. So my question is...

Will system76 install the most recent updates to ubuntu 11.04 before shipping? And if so, will they check everything out to make sure that it is all working before shipping? (In particular, this problem) It seems like there's a good chance that this issue is going to happen, so I would much rather it be checked and/or solved on my netbook before it gets shipped. Finally, if updating and checking is not part of the company's normal routine, can I make a special request that this be done for my order?

Hopefully this message doesn't sound too critical. This seems like a nice company, and I'm really excited about the Starling and about switching to linux. I just want my netbook to work when I get it.


Thanks,
wdb
Potential Customer

As I previously said in this thread. I would have bought a more powerful computer. The atom processor just didn't cut it for me. But I would definitely go with System 76. GREAT COMPANY! They really are helpful and this forum is great too!:KS

---

### Post by bstudent on 2011-08-05
> **bstudent said:**
> Hi,

I am thinking about buying a Starling within the next few days, but this thread has got me worried. I'm completely new to linux, so I would be quite lost trying to fix this. And I'm really not going to have time to figure out how to fix something major on day one. So my question is...

Will system76 install the most recent updates to ubuntu 11.04 before shipping? And if so, will they check everything out to make sure that it is all working before shipping? (In particular, this problem) It seems like there's a good chance that this issue is going to happen, so I would much rather it be checked and/or solved on my netbook before it gets shipped. Finally, if updating and checking is not part of the company's normal routine, can I make a special request that this be done for my order?

Hopefully this message doesn't sound too critical. This seems like a nice company, and I'm really excited about the Starling and about switching to linux. I just want my netbook to work when I get it.


Thanks,
wdb
Potential Customer


Thanks for the response neal. I've heard and read a lot of good things about this company. I'm planning to place my order today if I can get my question answered.

---

### Post by isantop on 2011-08-05
The system will ship up to date as of the time of manufacture. There may be a few more updates once the system arrives, though.

---

### Post by bstudent on 2011-08-05
Sounds good. Order placed!

---

