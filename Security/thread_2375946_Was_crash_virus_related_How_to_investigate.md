---
title: "Was crash virus related? How to investigate?"
date: 2017-10-28
forum: Security
---

### Post by darter on 2017-10-28
I've been using 16.04 for about 8 months. Two days ago I decided to install a "hibernate" function using apt get. I tried it out one evening  and in the morning my system would not boot correctly. Sorry I did not take written notes but my video had a scrambled look and I think there was a reference to a memory error with my Radeon card (?) . 

I have dual monitors and a  R7700 card. I figured that perhaps the wake from hibernate could  not deal with the two monitors.  I think that it also reported that a monitor was not reporting something back correctly - maybe its own type?   Anyway, I then used GRUB and did boot successfully to an earlier kernel and I used Me-TV to record a show etc.  Later on I shut down the system and then it had trouble booting to any kernel version (which seemed odd since I didn't change anything after that good boot). 

Anyway, I eventually decided that I would simply pull the drive and install Ubuntu  16.04 fresh onto a brand new drive with the intention of copying any data from the "damaged" system onto the new installation.  Here where it gets a bit weird. The UUIDs on the damaged system's partitioned now included some choice profanity! So perhaps  a prankster/virus  had altered it? But how can I figure out what really happened? I am able to use a Live CD to boot to Linux and I can read my filesystem on the damaged drive. I can read all the data, as needed.  I have been copying data to USB drive.  

But what really happened here?  Can a virus actually write to or damage a video card? Any ideas on how I might reconstruct what really occurred? Since I can read the drive shouldn't I be able to locate the putative virus?

---

### Post by alwayshacked on 2017-11-08
I've been fighting hackers on my own systems and others for a few years now. Even with things like AV installed, IDS/IPS with snort, firewall rules locked down so every device is on its own vlan and subnet and everything having a default drop rule on its own firewalls and others, so I can basically attempt to account for every packet going in and out, the systems still get hacked. I suspect a web browser zero day is then being used to attack hardware and using cpu virtualisation as well. Firstly no AV will ever check the firmware on a chip, so hard drive controllers can have their microcode modified, been going on since the 90's, bios's can be modified, here's an opensource one [https://libreboot.org/](https://libreboot.org/), and considering its possible to reset the cpu parameters for each core which dont get checked when you reboot your machine, pretty much anything is possible and also impossible to foresically detect unless the hackers want you to detect.

EG. the cpu parameters only get checked when you start up, not when rebooted. Some AV companies now use CPU virtualisation to read memory when accessing banking websites.
You average home router has a default always let out policy, the ony thing you cant control with BT's router is switching off their public wifi hotspots even if you switch off wifi for your own personal use. There's an IPv6 network coming down your adsl connection as well, and things like TalkTalk's TV film service where you can buy film's can be bought from a BT network, but you cant watch it from a BT network, I've tried.

Personally I think all device's are woefully insecure considering how many attack vectors there are, and knowing countries will spend million's buying zero days off hacker's instead of selling for a pittance to tech companies who offer bug bounties, the whole hacking arena can be very lucractive. I've heard suggestions some of the best earn £10k a day!

So to answer your question, if legit software can update your graphic's card's is it possible illegit software could also update your graphic's card especially since fuzzer's have become common place at automating the bug hunting process?

If yoru cpu supports virtualisation, then it may not have even got onto your disk other than to damage it, it could have all been done in memory with cpu virtualisation to evade your normal measures.

This is what I like about the linux guys, they think it cant be hacked so dont even take normal security measure's, yet I dont see ASLR being deployed in any meaningful way which I find quite frustrating considering how easy it is to pull passwords out of ram with a bit of poking and peeking.

---

