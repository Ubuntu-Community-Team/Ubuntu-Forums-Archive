---
title: "My problem *me=not leet* *me=noob*"
date: 2010-06-05
forum: Wine
---

### Post by leetbob666 on 2010-06-05
Hello i'm new to UBUNTU!

Well, I like my games haha..

I have wine and PlayonLinux installed.

I am trying to play Source games from Steam and Hl2 mods.

1.I need to update my graphics card drivers and I only know that I have an Ati graphics card.

2.How could I install mods into steam. Where is the default Steam folder installed because the mod I am trying to get doesn't have a .exe or anything so I need to find the steam folder and I am too stupid to find it.

3.If you can help me I love you <3 :)

---

### Post by Shazzam6999 on 2010-06-05
If you installed Steam through Wine then it's in your home folder under .wine. Use ctrl-h to show hidden folders, find the .wine folder, and there should be a program files folder in there and in that should be the steam folder.

You can find your gpu with the lspci command in a terminal.

---

### Post by themusicalduck on 2010-06-05
Have you already installed drivers for your card?

They're normally installed from System > Administration > Hardware Drivers.

---

### Post by leetbob666 on 2010-06-05
I don't know lspci command is i'nm that stupid.

In hardware drivers it says "No proprietary drivers are in use on this system" 

So what do I do?


Sorry for being such a pain.

---

### Post by themusicalduck on 2010-06-05
If someone says to run a command, then you open a terminal (Applications > Accessories > Terminal) and type the command into there.

Try running this command to find out what your graphics card is ```
lspci | grep VGA
``` copy it and to paste it into the terminal use ctrl+shift+v.

---

### Post by leetbob666 on 2010-06-05
A crappy Ati Radeon X1200


Where can I get drivers for it.

---

### Post by Sef on 2010-06-05
> A crappy Ati Radeon X1200


Where can I get drivers for it.


You can get them [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

---

### Post by leetbob666 on 2010-06-05
Thanks.

The laptop company distributes the drivers and Toshiba only has the drivers for Windows?.... FML?

---

### Post by waynefoutz on 2010-06-05
> **leetbob666 said:**
> A crappy Ati Radeon X1200


Where can I get drivers for it.

I have a laptop with the same graphics card.

Bad news. You aren't going to get drivers for it that work with the current version of Ubuntu. If you want to continue to use that card, and use it for games, you need to downgrade to Hardy Heron. If it's in a desktop. simply replace it for a modern card. Hardy Heron:
[http://releases.ubuntu.com/hardy/]("http://releases.ubuntu.com/hardy/") 

You'll get peak performance out of that card with that version. After you install it, click on System, Administration, Hardware Drivers, and enable the ATI Accelerated graphics driver, then reboot. 

ATI stopped updating the driver for that card, and the old driver doesn't work with Ubuntu 9.04 or later. It works great with Hardy Heron (8.04.4) 


As for Steam, I can't get TF2 to run on that card. I can get the older Half life 1 games to run quite nicely.  

The open source drivers in Lucid, 10.04, the latest version, is the best you are going to get with that card. They are the ones installed by default. I can get about 75% of the games to run with the set up you should have now. Steam is coming out with a Linux native Steam client later on this year. Hopefully that will be the fix. 

In the meantime, if first person shooters are your thing, try Urban Terror. [http://www.urbanterror.info/news/home/]("http://www.urbanterror.info/news/home/")It should run with the version of Ubuntu you have installed now. The frame rate isn't all that great with the open source drivers, but it will scream if you downgrade to Hardy and enable the proper driver. I get about 60 fps in Hardy, 15-20 fps with Lucid. I think Urban Terror is about the best Linux has to offer in shooter games right now, the game is similar to Counter-Strike. 

Hope this helps.

---

### Post by waynefoutz on 2010-06-05
> **Sef said:**
> You can get them [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

You install that on Lucid you are going to break your desktop. Doesn't work with the current versions of Xorg.

---

### Post by oldrocker99 on 2010-06-05
As the regretful owner of a x1200 as well, I feel your pain. The installed open-source Radeon and RadeonHD drivers are better than they were a year ago, and they're a lot better now. I could NOT play Neverwinter Nights Linux a year ago, on Jaunty Jackelope, but I can now on Lucid Lynx. 0 A.D., however, returns a "your card does not support..." message, and sits there until I exit.

You gotta take the good with the bad...

:guitar:

---

### Post by waynefoutz on 2010-06-05
> **oldrocker99 said:**
> As the regretful owner of a x1200 as well, I feel your pain. The installed open-source Radeon and RadeonHD drivers are better than they were a year ago, and they're a lot better now. I could NOT play Neverwinter Nights Linux a year ago, on Jaunty Jackelope, but I can now on Lucid Lynx. 0 A.D., however, returns a "your card does not support..." message, and sits there until I exit.

You gotta take the good with the bad...

:guitar:

It all works with Hardy and the fglrx drivers.

---

### Post by diablo75 on 2010-06-05
I'm in the same both on having that same graphics chipset (actually it's a 1250, but I feel your pain).

The good news is that the video performance on the open-source drivers have gotten a lot better in the last year (not for games, per se, but for the operating system itself).  Last year I had Ubuntu 9.04 installed and windows would flicker all the time when you dragged them around on screen.

Only mentioning this because the open source drivers for older ATI chipsets seems to be making headway.

As for gaming... if it's a laptop, dual-boot with Windows.  If it's a desktop... upgrade to an nVidia card.

---

### Post by asdfoo on 2010-06-06
> **waynefoutz said:**
>  Steam is coming out with a Linux native Steam client later on this year. Hopefully that will be the fix. 


This hasn't been announced, people have only speculated that Steam is releasing a linux client.

---

### Post by marcoftheknight on 2010-06-06
I thought the graphics drivers if downloaded they would work on the lucid? Since as long as the driver supports ubuntu then should be fine no matter the version


I think this is the driver your looking for with all the install info which you should read carefully and with info on the OS it supports and the graphics cards series it for ENJOY

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

BECAUSE YOUR NEW I would go first!! to your ubuntu software center search for ENvygn and install it and it will automatically install the right driver if it finds one.

Thanks preformance WILL BE Lower since it isnt the latest driver for the card your choice.

YOu break something dont worry should be able to revert to configuration without the driver enable automatically then follow the steps to removed the driver fully with are in the installation nOTES CHECK BEfore and print it out ! that way your ready for a crash
I have ATI to and am running dual monitors ( one 32in one 19inch with 1080i and 1366X768 two different resolutions trust me ati can be frustrating but dont give up mine works almost perfectly actualy my only problem is the 32inch is my tv and is CRT so it doesnt have the capacity to output what my card can lol my new monitors on its way.(hopefully arrive next week 23inch ultra contrast .

thanks

---

### Post by Shazzam6999 on 2010-06-06
> **leetbob666 said:**
> I don't know lspci command is i'nm that stupid.

In hardware drivers it says "No proprietary drivers are in use on this system" 

So what do I do?


Sorry for being such a pain.
That's my fault sorry, your not stupid, I should have clarified what I meant. 

I have an x1300 and I don't game on my laptop but the open source drivers work really well for everything I do. Although, I don't do anything graphically intensive they seem to work flawlessy... the 4850 in my desktop is a bit of a different story though :).

---

### Post by waynefoutz on 2010-06-06
> **asdfoo said:**
> This hasn't been announced, people have only speculated that Steam is releasing a linux client.

No, it's official. It will be out by the end of the summer. [http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1]("http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1")

---

### Post by waynefoutz on 2010-06-06
> **marcoftheknight said:**
> I thought the graphics drivers if downloaded they would work on the lucid? Since as long as the driver supports ubuntu then should be fine no matter the version


I think this is the driver your looking for with all the install info which you should read carefully and with info on the OS it supports and the graphics cards series it for ENJOY

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

BECAUSE YOUR NEW I would go first!! to your ubuntu software center search for ENvygn and install it and it will automatically install the right driver if it finds one.

Thanks preformance WILL BE Lower since it isnt the latest driver for the card your choice.

YOu break something dont worry should be able to revert to configuration without the driver enable automatically then follow the steps to removed the driver fully with are in the installation nOTES CHECK BEfore and print it out ! that way your ready for a crash
I have ATI to and am running dual monitors ( one 32in one 19inch with 1080i and 1366X768 two different resolutions trust me ati can be frustrating but dont give up mine works almost perfectly actualy my only problem is the 32inch is my tv and is CRT so it doesnt have the capacity to output what my card can lol my new monitors on its way.(hopefully arrive next week 23inch ultra contrast .

thanks

The last version of ATI's Catalyst drivers for this chipset was version 9.3. It does not work with any version of Ubuntu after Intrepid. There was a work around for Jaunty, downgrading the xorg-server to Intreped's 1.5.2, but that was buggy at best. With Karmic there was no work around, but the open source Radeon drivers were a big improvement. Lucid's are even better, but still not very good for gaming. 

If you have this card in a laptop and can't change it, you have two options. If you want to use the ATI drivers and game in Linux, you need to install Hadry Heron, or install the latest version, Lucid, and pretty much leave the default setup alone, and dual boot for Windows games. 

It's a good idea to go here [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and add the xorg-edgers PPA to your software sources if you choose to use Lucid with the open source drivers. This will give you updates as they come out, and they've been working on them and improving them at a pretty good pace.

I've had my laptop about a year and a half, and I'm stuck with this card. When I bought it new, Intrepid was the latest version, then Jaunty came out and broke everything. I went back to Intrepid. When Lucid came out, I tried it for a week. Just about everything worked except Google Earth and a few games. The first person shooters like Alien Arena and Urban Terror looked good, but the framerates were awful. I ended up downgrading to Hardy. I'll run that until the end of life next year, and hopefully by version 11.04 we'll see some more improvements. (Assuming I'm still using this laptop of course.)

---

### Post by marcoftheknight on 2010-06-06
Yah your right prior to 2009 that sux's  IGNORE EVERYTHING I sent on info

---

