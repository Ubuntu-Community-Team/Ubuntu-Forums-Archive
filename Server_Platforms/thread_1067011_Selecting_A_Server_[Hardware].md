---
title: "Selecting A Server [Hardware]"
date: 2009-02-11
forum: Server Platforms
---

### Post by Semiraghe on 2009-02-11
I feel that I should lead off with this is my first post at these forums and that I am relatively new to the idea of Ubuntu.  I have taken a system admin class in college (focused on Free BSD), so hopefully I won't be getting in over my head.

Anyway, my request is for help in selecting a server machine on which I can install Ubuntu.  I know that I could put it on any machine, but since I don't have a spare machine to put it on at the moment I need to get another one.

I'm looking to buy a new machine fully assembled instead of building one.  The reason for this is I don't want to be fighting hardware problems that I may have caused in addition to software problems I may have caused.

Things I'm looking to do with the machine is route the rest of my machines through it so that it can act as a firewall.  Right now this consists of a XP machine and PS3 and probably the occasional windows/mac laptop of friends that come over.

I would also like to set it up to be a web server and media server.  The web server for just a family website if I get around to it and a media server so that I can stream music and video off of it to any machine.  It would be mostly music, but I might rip the few DVDs I have to it later.

I'm looking for a machine that can be put into a RAID setup so that I don't have to back the data up.  Right now 100gigs is probably enough space if that helps keep cost down, but I would rather look at around 200gigs of space if that is possible.

Cost is the probably the biggest factor right now as this is just something I'm looking to do in my spare time for fun.  If you can suggest machines or brands that I should look at I would greatly appreciate it.  Also, if you would like more information that what I have provided I will try to give it to you.

Thanks in advance for all the help, I look forward to being involved in the community. 

-Semiraghe

---

### Post by cariboo on 2009-02-11
For what you want, almost anything will work, as long as it has two nics. You said you had BSD experience so you won't want a gui, so the graphics card doesn't matter. If you want to setup something like a shoutcast server you are going to need a sound card that is easy to setup, if you can find an old SoundBlaster 16, that would be perfect.

Raid is not going to save you from doing backups. Raid1 is mirrored data so if the data is corrupt on one drive, it will be corrupt on the other drive. The only time Raid1 will save you is if one drive dies.

My suggestion would be to buy two hard drives that are exactly the same and use one for your data and put the other one in an enclosure and use it for backups. BSD and Linux are both unix like OSs so most of the commands are the same, so setting up an automated backup should be a piece of cake for you.

Jim

---

### Post by punx45 on 2009-02-11
i do basically what you describe (minus the routing) with a P3, 512 MB ram, small system disk and 300GB media drive.   Even  that can serve a low traffic phpBB board with ease. so like the previous poster said, you can use just about anything.   if you dont plan on using a GUI you can use just about any mother board, and wont have to worry about compatibility.   i would suggest researching the chipset for the onboard lan if you choose to use  that, and research any NICs you plan on buying as well.   other than that, i would prioritize ram and disk speed/space since those will probably be the most used parts of the system, and go for gigabit ethernet too.

i dont know what kind of budget you are working with, but you can get 1TB disks now for around $100.   not much more than smaller disks.

---

### Post by Semiraghe on 2009-02-11
Well thank you for the suggestions.  I was originally looking at some of the server systems on newegg, but based off what you guys have said its probably better to just get a cheap system and add the second network card and hard drive.

I know its a lot to ask but if I linked a few systems I was looking at would any one be willing to give your input on them.  I will look some systems up on newegg and other places.  Thanks again for all your help.

-Semiraghe

---

### Post by punx45 on 2009-02-11
yeah sure

---

### Post by Semiraghe on 2009-02-12
Sorry about the late reply, but was kind of busy getting some stuff done.  I did want to thank you guys for your replies, and let you know that I didn't need help picking out a system.  My boss gave me an old Dell PowerEdge 1800 that he had, so I'm going to be setting that system up.  Thanks again for the help though, and I'm sure I will see you around.

---

