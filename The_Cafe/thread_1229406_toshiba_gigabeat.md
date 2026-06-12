---
title: "toshiba gigabeat"
date: 2009-08-02
forum: The Cafe
---

### Post by nathang1392 on 2009-08-02
i have a toshiba gigabeat f-10 that i bought a few years ago. it has always worked fine until the other say i turned it on and it said "no system found on hdd." i dont know what caused the sudden problem. i didnt drop it or anything like that. i cant get support from toshiba. if anyone is familiar with the problem please help me diagnose.

---

### Post by Tipped OuT on 2009-08-02
*nuked*

---

### Post by nathang1392 on 2009-08-02
umm... a toshiba gigabeat is a mp3 player. but thanks for the effort.

---

### Post by Blu Fox on 2009-08-02
> **Tipped OuT said:**
> It either means your hard drive has been nuked (no operating system on it) or your boot table is corrupt.

Try re-installing Ubuntu/ Windows on your laptop, that should be the dead end fix. (Although there's better choices)

You do know he's talking about an mp3 player, right? 

From what I looked at so far around the googles, it's not an isolated issue. Some say it's a firmware issue or operating system on the mp3 player got nuked. I'm not sure, I'll have to do more research on it.

---

### Post by Tipped OuT on 2009-08-02
> **Blu Fox said:**
> You do know he's talking about an mp3 player, right? 

From what I looked at so far around the googles, it's not an isolated issue. Some say it's a firmware issue or operating system on the mp3 player got nuked. I'm not sure, I'll have to do more research on it.

Oh, lol my mistake xD

---

### Post by Tipped OuT on 2009-08-02
> **nathang1392 said:**
> umm... a toshiba gigabeat is a mp3 player. but thanks for the effort.

Yeah sorry dude.

---

### Post by Blu Fox on 2009-08-02
Found a site that has a couple of guys with the same issue and fixed it

[Hope this helps out]("http://www.fixya.com/support/t136614-no_system_found_hdd")

---

### Post by nathang1392 on 2009-08-02
i have read around on alot of sites that what i should do is to remove the back cover and disconnect the hd and then reconnect it. i was wondering if anyone knew how to take the cover off, as there arent any visible screws.

---

### Post by gletob on 2009-08-02
I love my gigabeat. there are small phillps head screws hidden under the covers on the top of the player.  Example Where the hold and dock connector are.

You just stick your fingernail in the crack on the cover and pry them off.  Remove the four screws. Then open the back of the Gigabeat with the screen laying on a desk.  after the cover is off you will see the hard drive disconnect it and plug the usb cable into your gigabeat with the HD disconnected.  Connect the hard drive and your device will be recognized as a mass storage device.  Now the location of the original firmware files I do not know and my gigabeat HD fried a long time ago.  But you can add these:
[FONT=monospace]
[http://www.rockbox.org/twiki/pub/Main/GigabeatFXPort/GBSYSTEM.zip](http://www.rockbox.org/twiki/pub/Main/GigabeatFXPort/GBSYSTEM.zip)
Extract that to the root of the drive.

add this to the /GBSYTEM/FWMING folder
[http://download.rockbox.org/bootloader/gigabeat/FWIMG01.DAT](http://download.rockbox.org/bootloader/gigabeat/FWIMG01.DAT)

Then download the newest daily build of rockbox for the Gigabeat F here
[http://build.rockbox.org/](http://build.rockbox.org/)

and extract the .rockbox file to the root of your gigabeat reboot and you will have Rockbox running on your gigabeat.

I'm sorry I don't know where to find the original firmware but these instruction will get your player funtioning again.  And rockbox is great it plays mp3,ogg,flac,unprotected aac, mpg video, and others.

[COLOR=Red]EDIT: This site goes into more detail on disasembly
[http://www.angelfire.com/bug2/gigabeat/](http://www.angelfire.com/bug2/gigabeat/)

[COLOR=Black]They have a good forums so you can ask questions.  You can get themes at themes.rockbox.org

P.S. If you find that your HDD is bad you can go on ebay and get something similar to this and get a CF card.
[http://cgi.ebay.com/CF-to-Zif-1-8-HDD-SSD-IDE-Adapter-for-iPod-Video-EEEPC_W0QQitemZ280375993815QQcmdZViewItemQQptZPCA_Cables_Adapters?hash=item4147b625d7&_trksid=p3286.c0.m14](http://cgi.ebay.com/CF-to-Zif-1-8-HDD-SSD-IDE-Adapter-for-iPod-Video-EEEPC_W0QQitemZ280375993815QQcmdZViewItemQQptZPCA_Cables_Adapters?hash=item4147b625d7&_trksid=p3286.c0.m14)

A good way to make sure this works is to make sure it says Ipod Video, the two MP3 players use the same HDD interface in fact Toshiba manufactured the original Ipod drives for Apple.
[/COLOR][/COLOR] [/FONT]

---

### Post by drawkcab on 2009-08-02
As long as you can get the damn thing open, you can replace the harddrive if nothing else.  Replacement drives for a gigabeat should be relatively inexpensive nowadays.

---

### Post by nathang1392 on 2009-08-03
horray. thank you gletob. between dis assembly and rock box i got it to work. thank you for all of your help.

---

### Post by gletob on 2009-08-03
> **nathang1392 said:**
> horray. thank you gletob. between dis assembly and rock box i got it to work. thank you for all of your help.

Your very welcome if you need any help then feel free to PM with questions about rockbox.

Your thread inspired me to fix my Gigabeat so I've got one of those CF to ZIF converters on the way and a 4 Gb CF card.

---

