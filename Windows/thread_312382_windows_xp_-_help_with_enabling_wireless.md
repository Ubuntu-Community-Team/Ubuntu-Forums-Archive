---
title: "windows xp - help with enabling wireless"
date: 2006-12-04
forum: Windows
---

### Post by megamania on 2006-12-04
At work (bank) I just received a flashy new Dell Latitude 620 laptop. 

Obviously (and unfortunately) it runs Windows XP Pro, so I need your help. Since I can take the laptop at home, I'd be interested in connecting it wirelessly to my router to access the internet.

The problem is that in the Network Connections window there's no "wireless" option - there's only a "Local Area Connection" icon for wired connection. I believe it's been disabled by our IT managers, but since I can log in as administrator I'd like to know where to look in order to enable it.

I know this has to be a trivial task, but any help would be appreciated anyway because I've been windows-free long enough to be afraid of messing things up...

---

### Post by d3v1ant_0n3 on 2006-12-04
Isn't there a 'wireless settings' option in control panel or something? It's been a while since I needed to set it up. If the laptop has LAN and Wifi, it might have been disabled in BIOS as well, or not have the drivers installed- check in device manager to see if it shows up and is enabled maybe? Oh hell I can't troubleshoot windows anymore:p

---

### Post by Marquis_de_Carabas on 2006-12-04
I recently spent a couple of hours trying to get a friend's wireless access working, before realising that I had to press something like fn+F9 to turn the wireless card on. Something which wasn't well documented at all. Until I'd done this Windows didn't see the wireless card at all. If your problem is more serious than this then I have no idea :)

---

### Post by megamania on 2006-12-04
> **d3v1ant_0n3 said:**
> If the laptop has LAN and Wifi, it might have been disabled in BIOS as well, 
good guess!

It's disabled in the BIOS, and the bios is password-protected. I can't ask my IT manager for the bios password - any way to reset it without opening the computer?

---

### Post by Chinkostu on 2006-12-04
the only way to reset it is a CMOS clear via a jumper (on desktops at least, but i would think that laptops would still have the Cr2032 battery). but that involves opening the system :(

---

### Post by KiwiNZ on 2006-12-04
> **megamania said:**
> good guess!
 
It's disabled in the BIOS, and the bios is password-protected. I can't ask my IT manager for the bios password - any way to reset it without opening the computer?
 
I would advise caution. Your Management have disabled it for reason. 
And circumventing company security policy is a dangerous and silly thing to do.
 
I am an IT Manager, I would fire immediately anyone who did what you are proposing.

---

### Post by megamania on 2006-12-05
> **KiwiNZ said:**
> I would advise caution. Your Management have disabled it for reason. 
And circumventing company security policy is a dangerous and silly thing to do.
 
I am an IT Manager, I would fire immediately anyone who did what you are proposing.
I see your point, and I think you're right.

They disabled the wireless because they're afraid of viruses. I can't see the direct link wireless=virus (it's the same thing as wired connection, obviously), but I'll just cope with it.

As I wrote in my previous message, I have administrator rights even if officially I'm not an IT manager . I thought I would enable the wireless if it was a matter of software tweaking, and then got carried away with the bios-hacking thing.

Thanks for making me think about it.  :-)

---

### Post by hkq35 on 2006-12-07
You still may be able to use a device such as a USB-wireless device.

---

### Post by meng on 2006-12-07
I'm no expert, but if your wireless interface is enabled, and say you're using the laptop in a cafe, it seems to me that it may be possible for someone else to gain access to your files. I'm not saying it would be easy to do this, but possible. Perhaps that's the rationale for the IT folks being extra-cautious. Then again, perhaps they're complete bastards.

---

### Post by megamania on 2006-12-07
> **meng said:**
> Perhaps that's the rationale for the IT folks being extra-cautious. Then again, perhaps they're complete bastards.
They're not bastards, they just have to manage a lot of machines in an environment where most people think that Word is an operating system and call "modem" the computer itself (to them, the monitor is "the computer") :-)

They just try to avoid problems as much as possible, and I can't blame them for that.

I'll probably try a usb-wireless one of these days anyway...

---

### Post by Circus-Killer on 2006-12-07
yeah, i agree with previous posters. trying to go against company policies is a no-no. this is exactly why i run XP at work, because my  work tells me to. i leave all my personal stuff for my personal machines at home.

if there is a firm rule against something, i will avoid trying to do it. my job is more important than fiddling around. the fiddling can wait till i get home from work.

i also agree with posters that said your company is doing the right thing. due to the nature of large companies, companies need to be strict on the use computers and access. its not that they dont trust you, its that they dont trust anybody, not even your boss. these type of precautions are not only taken by banks, but by companies in all industries. just take it from their perspective, they're just trying to protect their assets as best they can.

---

### Post by megamania on 2006-12-07
> **Circus-Killer said:**
> if there is a firm rule against something, i will avoid trying to do it. my job is more important than fiddling around. the fiddling can wait till i get home from work.

The point is that the notebook is also for my personal use. I *am allowed* to take it home, watch movies, write emails, store music on it, and so on.
I also have an UMTS card to surf the net from anywhere for free. I wanted to have wireless connection *at home* to prevent the bank from wasting money using the umts connection when I have a broadband connection.

Anyway, I'll not hack the bios to enable the wireless card.

---

### Post by scc4fun on 2006-12-08
> **megamania said:**
> The point is that the notebook is also for my personal use. I *am allowed* to take it home, watch movies, write emails, store music on it, and so on.
I also have an UMTS card to surf the net from anywhere for free. I wanted to have wireless connection *at home* to prevent the bank from wasting money using the umts connection when I have a broadband connection.

Anyway, I'll not hack the bios to enable the wireless card.
If they're smart your umts connection is paid for as unlimited* service. I can understand that your broadband connection would be preferable while at home. Perhaps you could submit a request to your boss/it manager to enable to the wireless card if you will sign your life away saying you'll use all security precautions (eg: using ZoneAlarm/Check Point Integrity Flex--corporate version of ZoneAlarm--with Trusted zone set only to corporate network addresses and not popular Wi-Fi addresses like 192.168.*.* and 172.whatever).

---

