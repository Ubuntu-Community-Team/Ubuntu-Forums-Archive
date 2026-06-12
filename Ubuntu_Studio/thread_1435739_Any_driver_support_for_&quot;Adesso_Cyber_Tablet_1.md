---
title: "Any driver support for &quot;Adesso Cyber Tablet 12000&quot; graphics tablet?"
date: 2010-03-21
forum: Ubuntu Studio
---

### Post by Visible Spirit on 2010-03-21
**Hi all,**


I have an [Adesso Cyber Tablet 12000]("http://www.adesso.com/index.php/en/home/tablets/159-cybertablet-12000") graphics tablet and would like to know if there's any Linux drivers and/or software support for this model? I've installed Xournal which somewhat works with my tablet, but the stylus cursor isn't stable nor am I able to calibrate the tablet to the screen area. I've also tried using it in GIMP to no avail with the same result/problem. I'd really like to use this tablet on Linux if it's possible.

If no one has or is working on a solution, is there anyone out there willing to tackle this project?

I'll gladly upload the software/driver CD that came with it if someone wants to work up a stable solution. On the CD is factory support for MS-Windows 2k-XP(Vista?) and Mac OSX OS's, so I would think there's a solution for Linux. Or you can download the .zip file with new drivers from the page linked above for MS-Windows 2k-7 and Mac OSX-(update -- you must now register membership to access Adesso website downloads as of March 2010). My offer to upload driver(s) from disc still stands -- PM me?. I'm not a programmer and haven't a clue how one would go about this. Any takers?

Anyone have any suggestions, ideas, or leads to a solution or a work in progress?

*Any* help would be greatly appreciated.


[B]Thanks,
Visible Spirit[/B]

OS = Ubuntu Studio v8.04 LTS

PS -- I originally posted this question as a response-(#2) to ["*[ubuntu] How is Support for Non-Wacom Tablets*"]("http://ubuntuforums.org/showthread.php?p=8259930#post8259930") in the "Hardware & Laptop" forum.

---

### Post by mikitz on 2010-04-26
I was thinking of buying a cyberpad and using it with ubuntu as well, but doesn't look like it is supported... I heard the tablet will work in ubuntu but only like a mouse after installing the wacom tools package.

---

### Post by Favux on 2010-04-26
Hi Visible Spirit and mikitz,

OK, it's a non-wacom usb tablet with 512 levels of pressure.  Do we know if the tablet is rebranded?  OEM's include Waltop, Aiptek, and WizardPen, and each have their own drivers.  We can look at the output of:
```
grep -i name /proc/bus/input/devices
```
in a terminal as a first try.

---

### Post by Nickel1010 on 2010-07-10
Sorry to bump an old post, but I do believe it is rebranded. There is an Aiptek model that uses the same driver.

---

### Post by Visible Spirit on 2010-09-24
> **Favux said:**
> Hi Visible Spirit and mikitz,

OK, it's a non-wacom usb tablet with 512 levels of pressure.  Do we know if the tablet is rebranded?  OEM's include Waltop, Aiptek, and WizardPen, and each have their own drivers.  We can look at the output of:
```
grep -i name /proc/bus/input/devices
```
in a terminal as a first try.


Hi Favux,


My apologies for not replying sooner regarding your offer to help with this issue. As well as being a busy person, in all honesty, the fact that you replied and offered help slipped my mind as time went on. However, if your still willing to help me with this problem, it will be greatly appreciated.

I ran the command-line you suggested in a terminal session. As Nickel1010 suggests, it seems to be listed as an "Aiptek" as you can see in the terminal report below.
```
XXXXXXXXXX@ubuntu:~$ grep -i name /proc/bus/input/devices
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="PC Speaker"
N: Name="ImPS/2 Generic Wheel Mouse"
**N: Name="Aiptek"**
XXXXXXXXXX@ubuntu:~$ exit
```

At one time I had the chip-set info, but can't remember the  terminal/command-line syntax to retrieve it.

I hope to get a response/reply to resolve this matter and look forward to such.


Regards,
Visible Spirit

---

### Post by Visible Spirit on 2010-09-24
> **Nickel1010 said:**
> Sorry to bump an old post, but I do believe it is rebranded. There is an Aiptek model that uses the same driver.


Hi Nickel1010,


Thanks for your input/help. It would appear your correct if you look at my terminal session output I posted here. Hopefully with help from folks such as yourself I can get this puppy working and enjoy it's benefits as an aspiring amateur graphic artist.


Regards,
Visible Spirit

---

### Post by Favux on 2010-09-24
In Synaptic Package Manager install the xserver-xorg-input-aiptek driver package.

---

### Post by Visible Spirit on 2010-10-04
> **Favux said:**
> In Synaptic Package Manager install the xserver-xorg-input-aiptek driver package.

A quick note to let you know I appreciate your response. I did dwnld and install the " xserver-xorg-input-aiptek driver package " you suggested but haven't had time to play around with things yet. I'll get back here with a report once I find time to investigate things further.

Thanks again for your reply Favux.


Regards,
Visible Spirit

---

### Post by PedalPowered on 2011-01-13
Visible Spirit,

I was thinking of purchasing this tablet for use in Ubuntu, as well. Curious if you found that it worked well.

Thanks,
PedalPowered

---

### Post by Visible Spirit on 2011-01-18
> **PedalPowered said:**
> Visible Spirit,

I was thinking of purchasing this tablet for use in Ubuntu, as well. Curious if you found that it worked well.

Thanks,
PedalPowered


Hi PedalPowered,


My apologies for not replying sooner, but I'm so busy these days I don't have time to get on-line outside business anymore. I haven't even been to any of my old hang-outs and miss some of the folks I used to be in contact with. We'll see who remembers me when things do settle and I eventually get time to enjoy on-line, not to mention do some of my art work again. For now, I've just got more on my plate than I should but haven't much choice in most matters as it all stands.

That said, I haven't had time to actually sit and play with my Adesso tablet either. As noted in my post above, I did install the *xserver-xorg-input-aiptek driver package* some time ago and that didn't seem to work. Nothings changed. I'm still hoping to get this drawing tablet working under Linux if and when I have time. So I'm sorry I can't be of much help. Looks as though we both need some help getting this drawing tablet to function on Ubuntu, so I hope someone sees this and offers some soon.

I do get notices of responses to this thread amongst some others I'm watching and try to get in here asap when I do. Hopefully anyone that does comment will have patience for my reply, or if helping you or someone else, finds a resolution for all and it's clearly posted here for reference so I can use my tablet too!

I don't have the expertise to code and troubleshoot this kind of stuff, so again, I hope someone that does helps all that have this tablet (and others made by Adesso) by finding a solution. At one time I emailed Adesso for a solution and don't remember if I got a reply or not. If I did, I'm sure it was a generic type with no solution. I think it's a great tablet with lots of potential if only someone with the knowhow would help get it working on Linux.

Don't give up! There's got to be someone with an answer out there somewhere.


Regards,
Visible Spirit... ;)

---

