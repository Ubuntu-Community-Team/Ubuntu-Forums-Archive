---
title: "A four headed machine"
date: 2005-05-27
forum: The Cafe
---

### Post by costoa on 2005-05-27
As someone that use to work in public education I've seen how little money there is for computer equipment and support. I came up with a variation on a few other people's ideas to minimize both costs and wonder if it's possible.

Imagine a typical four seat (square table with divider, four chairs) computer workstation setup. Normally there would be four computers, four monitors, etc. My idea would be to use one computer with four video cards and three usb hubs, each with an usb keyboard/mouse. The "primary" seat would have it's monitor hooked up to the AGP video card (preferred to save on CPU load) or onboard video, keyboard/mouse on the PS/2 ports and an usb hub by the keyboard (more one this later). This seat would be used for setup and as well as a regular workstation (with the three finger salute disabled). The other three seats would have their monitors hooked up to a PCI video card and have an usb hub by the monitor for the keyboard, mouse and an optional flash drive to transfer files out of the network. A medium end CPU could easily carry the load for four sessions surfing the web or using OpenOffice. CPU time could be equally shared so no one person could slow the other three down too much. Not only would the cost be much lower (my guess is about 65% less) than four separate systems the noise would also be much lower. This entire setup could be done with very common and cheap pc parts.

Now for the support end. There would be no hard drive. Since RAM is so cheap put in 1G or more and make a big ram disk. It would be booted off a special live distro cd but only to copy everything needed over to the ram disk. In theory the live boot cd could be removed after booting is finished. An another option would be to lock the live cd and drive in the case for security reasons. A second cd burner could be added for the user's use. User files would be stored on a SMB or NFS share and could be transfered via a flash drive connected to the usb hub at every seat. USB hubs would segregated for security reasons. The user login would attach them to their file shares and custom user interface settings. If the network goes down the workstation would stay up. If there's no network server then users could store their files on thier own flash drive. If the workstation goes down you would just need to hit the hardware reset switch and reboot. BTW, since there's no hard drive it would make the machine rather secure. The only extra work needed at boot time would be to identify which usb hub goes with which video card. This could be done by having the monitor display it's sequence number and someone hitting the corresponding number on the mated keyboard. An extra 30 seconds of work. Picture one usb hub feeding four usb hubs, one to each seat. A fifth could be added for a printer or scanner.

AFAIK you can assign multiple virtual sessions to different video cards. No shared logins. To the entry level end user they wouldn't know the difference from this compared to a standard GNU/Linux box.

Not that I would support it but this could be used to create four virtual MS Windows "machines" in one box by running rdesktop at startup and RDPing to a Windows 200x Terminal Server. Again, I'd rather not bring MS into this. =)

You could even make four Mac OS 9 machines out of this by VNCing into a Mac box running GNU/Linux and mac-on-linux. Could be slow and most likely would massively violate Mac OS 9's EULA.

The only extra parts needed over a standard PC would be: three PCI video cards ($40 each / $120 total), four usb hubs ($15 each / $60), and three usb keyboards and mice ($30 each / $90) or about $270USD. Add in an extra 1G of ram for the ram disk over the 512M for the system at $40 per 512M stick and the total would be $350 total. You would save buying three motherboards, three CPUs, 3 sticks of 512M ram, three cheap hard drives, three cdroms, three cases and power supplies.

One machine for four simultaneous users with less maintenance than a typical GNU/Linux box. Could it work and would it be a pleasant machine to use? I'm thinking about building a test machine if the feedback is positive.

---

### Post by UbuWu on 2005-05-27
It is possible. Have a look at this: [http://ubuntuforums.org/showthread.php?t=24045](http://ubuntuforums.org/showthread.php?t=24045) 
Could be hard to set-up.

And here is how to do it: [http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/](http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/)

---

### Post by WildTangent on 2005-05-27
if you do it, make sure you call it The Hydra ;) theoretically itll work, but i strongly disagree with the no hard drive idea, and booting off a live cd...thats a little retarded if you ask me. i dont see how it can be a security risk...

-Wild

---

### Post by pdk001 on 2005-05-28
i have no clue

---

### Post by costoa on 2005-05-28
[QUOTE=WildTangent]if you do it, make sure you call it The Hydra ;) theoretically itll work, but i strongly disagree with the no hard drive idea, and booting off a live cd...thats a little retarded if you ask me. i dont see how it can be a security risk...

-Wild[/QUOTE]

I like the name idea alot. As for the cd boot the idea is if something software-wise goes bad a reboot fixes it. You could have a HD to cache everything though (with it being rewritten at every boot).  My idea is to have the machine require as little as possible **skilled** maintance. I want it so any reboot monkey can get the machine back up. =)

Security is higher with a live distro because any hacks are deleted when the machine reboots. There's a bank in Australia that's thinking about requiring customers to do their online banking solely from a custom live GNU/Linux distro to avoid phishing, dns hacks, keyboard captures, etc. While this is much more of a problem for the MS Windows world it still helps keep a GNU/Linux box a little more secure.


[Australian banks eye bootable Linux CDs](http://asia.cnet.com/enterprise/infrastructure/printfriendly.htm?AT=39223382-39035812t-39000220c)

---

### Post by costoa on 2005-05-28
[QUOTE=UbuWu]It is possible. Have a look at this: [http://ubuntuforums.org/showthread.php?t=24045](http://ubuntuforums.org/showthread.php?t=24045) 
Could be hard to set-up.

And here is how to do it: [http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/](http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/)[/QUOTE]

Thanks for the info and links. They're very helpful. The "backstreet" stuff is a good start for me. The "Useful 10-to-1 desktop" package looks nice except is has a per seat licence which kills it for me (though they might have some good ideas).

My goal would be an altered version of the Ubuntu Live cd. For me a free distribution is a must. I guess that's one of the reasons I like Ubuntu so much (that and stuff works). =)

Thanks again for the info.

---

### Post by JonahRowley on 2005-05-28
It could work, and it does work.  I seem to remember a company marketing just such a thing, and if I remember correctly, they had as many as 8 on a single machine.  I'm not even sure if it would be that difficult to set up.  Obviously you're going to need some dual (or more) head PCI graphics cards (matrox makes these), some USB hubs and a way to reliably match input devices to video outputs, but it just doesn't sound that difficult.  A good idea though, and worth a shot.

---

### Post by porsche08a on 2005-10-13
I know this is an old thread, but I used to do some work for a library system and a few people kept bugging me to look at this system...

[http://userful.com/](http://userful.com/)

It looks similar to what was described by the OP.  I downloaded a demo, but never tried it.

Ryan

---

### Post by Kvark on 2005-10-13
The live CD idea is a bit odd. It is possible to set up a hard drive so that all changes are lost at every reboot. Then users can install programs and do whatever they want since no changes are permanent. The only solution I've seen in action on public computers is Windows with Deep Freeze. It's great cause they have only IE and MSN but I can install Firefox and mIRC.

With linux I imagine it could be done very elegantly by creating a new user account with a new home dir at the start of each session, then delete the account and home dir at the end of the session. The only weird part is that programs would need to be installed to the temporary home dir.

Using an AGP slot for this also seems a bit odd sice there is only ever one per motherboard while there can be multiple PCI Express slots on the same motherboard.

---

### Post by SunBurnt on 2005-11-04
How about pxe booting a diskless hydra setup PC from a server?

Goes as far as you can to eliminate hardware, & puts all software on the server thus reducing IT people & effort to service the setup.

No slow CD drive on hydra client, but a server setup to restore it's HD from a CD is a great idea.

This is what I'm looking to do, anyone interested post back & we'll share ideas.

---

### Post by dutler on 2005-11-06
HP did this for some schools in Brazil, but no US offerings.

---

### Post by airtonix on 2006-05-06
uhhhh actually by even allowing anyone to touch the reboot button and open the drive....woaaah

that right threre is soooo much more of a security risk than doing udp cast of a partimage iso every morining...not to mention the stringy bits of gooey platci you may be fishing out of your drives each night......

---

### Post by airtonix on 2006-05-06
yeah of course they do...

offerings of terror

The us offered a paralell between cuban "terrorists", "stupid people" and linux...recently after the cuban government installed linux on most of their systems.

---

### Post by Lucho on 2006-05-06
You can get something like that here in Brazil. One company sells
what it calls "Six System."  You get a six-headed hydra instead of
four, but you get te picture. Here´s the link:
[http://www.insignesoftware.com/produtos/sixsystem.php]("http://www.insignesoftware.com/produtos/sixsystem.php")

---

### Post by Lucho on 2006-05-06
You can get something like that here in Brazil. One company sells
what it calls "Six System."  You get a six-headed hydra instead of
four, but you get the picture. Here´s the link:
[http://www.insignesoftware.com/produtos/sixsystem.php]("http://www.insignesoftware.com/produtos/sixsystem.php")

---

### Post by ubuntu_demon on 2006-05-06
[QUOTE=Lucho]You can get something like that here in Brazil. One company sells
what it calls "Six System."  You get a six-headed hydra instead of
four, but you get te picture. Here´s the link:
[http://www.insignesoftware.com/produtos/sixsystem.php]("http://www.insignesoftware.com/produtos/sixsystem.php")[/QUOTE]
I'm sure most of us can't understand that :)

---

### Post by Lucho on 2006-05-06
I've never used it, but doesn't Google have a translator that can handle that?
Sorry, I thought that either the site had an English page (I've never looked),
or Google could translate it for you.

---

### Post by n3tfury on 2006-05-06
I could have sworn I saw something just like this on one of the episodes of Go Open ([http://www.go-opensource.org/)](http://www.go-opensource.org/)).  Yeah, I'm sure I did, but meh, not going to pour through 13 episodes.

---

### Post by Fatjoint on 2006-06-15
What you've described is a dumb terminal and have been used for ages.  You commonly saw them as just a keyboard and monitor back in the day.  Many corporations still use them where there is need for data entry, but not heavy computational power (i.e. large spreadsheets, photoshop, etc.).  

As machines have increased in power and technology this changed to a more decentralized workshop, where instead of a mainframe computing the data from a dumb terminal, the end terminals were replaced with PCs.  These PCs could compute and store their own data and mainframe machines were no longer needed.

Well, we're beginning to come full circle as PCs communications and processing power increase to where you no longer need to decentralize to have enough horsepower to go around.  The market is shifting toward empty PCs that leverage server storage and redundancy but rely on their own computing power to perform calculations.

---

### Post by Compucore on 2006-06-15
I remember reading in Linux journal of a Beowolf setup where there was something like 19 computers all with their own ram and no hard drive. *(No monitors for the other 18 only the 1 for the main unit which acted as a master and the other were the client.)* They all booted via a floppy to get the kernel in. Then got the rest from the server to do that. But for each computer to have their own monitor, keyboard, and mouse. I don't know off hand. Unless they do the same where its bare minimal installation of hardware. Where they can use the GUI environment. And boot the kernel in and get the other essentials from the main server itself and run a thin client to do what is needed for the lab itself. I would have to double check to make sure. It was a few years ago that I remember reading up on this. I don't want to yes 100% to it unless I can provide the link for you.

Compucore

---

