---
title: "Distro hunting for netbook"
date: 2009-12-30
forum: The Cafe
---

### Post by emeraldgirl08 on 2009-12-30
My brother has an Asus eee 2gsurf netbook. I've never used one of these before and I was very curious about what OS it would be running. It seems it's some type of KDE linux OS. I also noticed that someone downloaded a lot of exe programs to the netbook. It's a little confusing b/c I see some Windoze type of signatures on it. Like the Silver XP theme is going on. 

I think the KDE is more hardware intensive than many other distros out there and that XFCE or LXDE may be a better platform to run. I'm fairly new here so if anyone has any suggestions as to what OS may be snappy and work excellent on his netbook I'd appreciate it!

Oh he's new to Linux and seems open to learning some terminal commands. I tried installing VLC through the command terminal but it is a little different than what I'm used to with Ubuntu or #!. His specs I'm not too sure about either...I think he told me it has 512 mb of RAM and the processor is probably less than 1ghz. Maybe around 700-900 mhz.

---

### Post by HappinessNow on 2009-12-30
> **emeraldgirl08 said:**
> My brother has an Asus eee 2gsurf netbook. I've never used one of these before and I was very curious about what OS it would be running. It seems it's some type of KDE linux OS. I also noticed that someone downloaded a lot of exe programs to the netbook. It's a little confusing b/c I see some Windoze type of signatures on it. Like the Silver XP theme is going on. 

I think the KDE is more hardware intensive than many other distros out there and that XFCE or LXDE may be a better platform to run. I'm fairly new here so if anyone has any suggestions as to what OS may be snappy and work excellent on his netbook I'd appreciate it!

Oh he's new to Linux and seems open to learning some terminal commands. I tried installing VLC through the command terminal but it is a little different than what I'm used to with Ubuntu or #!. His specs I'm not too sure about either...I think he told me it has 512 mb of RAM and the processor is probably less than 1ghz. Maybe around 700-900 mhz.OT: Nice Avatar. :P

---

### Post by Methuselah on 2009-12-30
The distro that comes with the eeepc 2G surf is pretty stagnant.
However, you won't find many thins as lite and tailored to it as what comes with it.

The one I ended up changing to is Archlinux running an XFCE window manager.
I tried LXDE at one point but it crashed everytime you right-clicked so I removed it and kept XFCE.
The system worked quite well but note that Archlinux does not give you a complete system out-of-the-box.
Be prepared to follow documentation and set things up from scratch if you go the Archlinux route.
However, as resources are limited on the eeepc, it's ease of customisation really helped me.

If you want a more out of the box distribution I think you'll find most of the netbook remixes too heavy on resources and the installation footprint too large.
However, there are eeebuntu, and easy peasy to try as well.

---

### Post by snowpine on 2009-12-30
My eee has a 160gb hard drive, so I am less limited. :) If I only had 2gb, I would probably use the eee-pc flavor of SliTaz. It's a tiny (but fun!) distro that only uses about 100mb of disk space.

My understanding is that the pre-installed distro is called Xandros, and that it's been heavily criticized for lack of updates and security flaws.

---

### Post by emeraldgirl08 on 2009-12-30
> OT: Nice Avatar. :P

Thanks :)

Yes I know the 2gb isn't much. I do know that it has SDHC support so that could be the /home folder. That opens up a little bit of breathing room :)

I'm no expert on linus yet so this would be a good learning experience for me! I'm wondering how Crunchbang Lite would work on it? I'm thinking of borrowing it and running a LiveCD session with it. I am not sure if it supports USB boots and am not sure how to invoke BIOS yet. I will after a little search engine-ing tho :)

---

### Post by HappinessNow on 2009-12-30
> **emeraldgirl08 said:**
> Thanks :)

Yes I know the 2gb isn't much. I do know that it has SDHC support so that could be the /home folder. That opens up a little bit of breathing room :)

I'm no expert on linus yet so this would be a good learning experience for me! I'm wondering how Crunchbang Lite would work on it? I'm thinking of borrowing it and running a LiveCD session with it. I am not sure if it supports USB boots and am not sure how to invoke BIOS yet. I will after a little search engine-ing tho :)
Highly recommend any Puppy derivative. :P

---

### Post by shababhsiddique on 2009-12-30
:(   baaaaaaaaaa  I wan ma laptop....
uuuuuuuuuuuuuu

---

### Post by pwnst*r on 2009-12-30
Moblin by a landslide.

On a Lenovo X200 Tablet:

[img]http://i50.tinypic.com/2ry0n09.jpg[/img]

---

### Post by Psumi on 2009-12-30
> **pwnst*r said:**
> Moblin by a landslide.

Same here.

---

### Post by drawkcab on 2009-12-30
Puppeee ftw

---

### Post by xuCGC002 on 2009-12-30
NOT puppy. You run as the root account at all times, which is drastically unsafe.
 
Moblin is lightweight and easy to use, I reccomend that. Ubuntu Netbook Remix is rather resource heavy, i'd rather you not use something like that.

---

### Post by Dark Aspect on 2009-12-30
[Arch Linux]("http://www.archlinux.org/"), [Puppy Linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm") or [Damn Small Linux]("http://www.damnsmalllinux.org/")

Arch might be a little much for 2 GB so I would clear out the /var/cache/pacman/pkg folder often and use Xfce. Additionally, you could try to boot off USB with a heavier distro and use the 2 GBs for a backup OS.

---

### Post by deadalus.globalnode on 2009-12-30
I would go Slackware with fluxbox, but if you think that would be to intensive I would probably go Xubuntu or DSL. (D** Small Linux).

---

### Post by markp1989 on 2009-12-30
> **emeraldgirl08 said:**
> Thanks :)

Yes I know the 2gb isn't much. I do know that it has SDHC support so that could be the /home folder. That opens up a little bit of breathing room :)

I'm no expert on linus yet so this would be a good learning experience for me! I'm wondering how Crunchbang Lite would work on it? I'm thinking of borrowing it and running a LiveCD session with it. I am not sure if it supports USB boots and am not sure how to invoke BIOS yet. I will after a little search engine-ing tho :)

i put arch on my sisters 2gb surf (about a year ago, im scared to upgrade because i know pacman doesnt like it when it runs out of space during an update, if iwas to upgrade,  i would move the pacman cache directory to my 8gb sd card. ) 

arch+toofishes kernel+openbox and your good, light and fast :D

i use a similar setup on my 4gb eee 900. just with xmonad (sp?) insted of openbox 

i have also striped down the init scripts so that i can boot in about 10 sec :)

---

### Post by Dark Aspect on 2009-12-30
> **markp1989 said:**
> im scared to upgrade because i know pacman doesnt like it when it runs out of space during an update, if iwas to upgrade,  i would move the pacman cache directory to my 8gb sd card. ) 


[IMG]http://img121.imageshack.us/img121/2991/ubuntug.png[/IMG]

---

### Post by Roasted on 2009-12-30
Has anybody actually tried KDE on a netbook? If it were me I'd try that first just cause I like KDE. I assume the cheap performance of integrated video on netbooks would be hard pressed to run KDE or even Gnome. But I think my next choice up would be XFCE (Xubuntu).

However, I haven't used Moblin. I should check it out.

Note to self - Just found out there's a Kubuntu Netbook Edition. Win.

However I checked out Moblin. Looks pretty darn promising to be real smooth on netbooks. I'd check that out.

---

### Post by HappinessNow on 2009-12-30
> **emeraldgirl08 said:**
> My brother has an Asus eee 2gsurf netbook. I've never used one of these before and I was very curious about what OS it would be running. It seems it's some type of KDE linux OS. I also noticed that someone downloaded a lot of exe programs to the netbook. It's a little confusing b/c I see some Windoze type of signatures on it. Like the Silver XP theme is going on. 

I think the KDE is more hardware intensive than many other distros out there and that XFCE or LXDE may be a better platform to run. I'm fairly new here so if anyone has any suggestions as to what OS may be snappy and work excellent on his netbook I'd appreciate it!

Oh he's new to Linux and seems open to learning some terminal commands. I tried installing VLC through the command terminal but it is a little different than what I'm used to with Ubuntu or #!. His specs I'm not too sure about either...I think he told me it has 512 mb of RAM and the processor is probably less than 1ghz. Maybe around 700-900 mhz.try BoxPup for the Eeepc

[http://www.murga-linux.com/puppy/viewtopic.php?t=50162](http://www.murga-linux.com/puppy/viewtopic.php?t=50162)

---

### Post by ugm6hr on 2009-12-30
> **xuCGC002 said:**
> NOT puppy. You run as the root account at all times, which is drastically unsafe.

Don't want to turn this into a recurring, but just to put the other side of this....

If you are considering Puppy, check the Puppy forum / wiki for the security rationale of a frugal Puppy install.

---

### Post by crimesaucer on 2009-12-30
> **xuCGC002 said:**
> NOT puppy. You run as the root account at all times, which is drastically unsafe.
 
Moblin is lightweight and easy to use, I reccomend that. Ubuntu Netbook Remix is rather resource heavy, i'd rather you not use something like that.

Moblin looks real cool. My only problem with it is that I don't belong to any of these social networks like twiter and such, and I mostly use console apps like MPD/ncmpcpp, rtorrent, vim, and command line vlc (cvlc). Plus I still like my regular old Firefox/Thunderbird apps, and my Thunar file system, but clutter could end up being as good or better than them..... I wish there were more gtk themes available for moblin, maybe use some RGBA see-through glass themes like murrine or plasma.


I would like to see how Google-Earth looks on moblin.

---

### Post by HappinessNow on 2009-12-30
> **ugm6hr said:**
> Don't want to turn this into a recurring, but just to put the other side of this....

If you are considering Puppy, check the Puppy forum / wiki for the security rationale of a frugal Puppy install.To make it easier on all here is the link to the thread about this:

[http://www.murga-linux.com/puppy/viewtopic.php?t=1246](http://www.murga-linux.com/puppy/viewtopic.php?t=1246)

---

### Post by emeraldgirl08 on 2009-12-30
> **crimesaucer said:**
> Moblin looks real cool. My only problem with it is that I don't belong to any of these social networks like twiter and such, and I mostly use console apps like MPD/ncmpcpp, rtorrent, vim, and command line vlc (cvlc). Plus I still like my regular old Firefox/Thunderbird apps, and my Thunar file system, but clutter could end up being as good or better than them..... I wish there were more gtk themes available for moblin, maybe use some RGBA see-through glass themes like murrine or plasma.


I would like to see how Google-Earth looks on moblin.

You could always remove them and add the stuff you want right? My brother is going to download Moblin sometimes. I have a copy of Jolicloud (which looks similar to Easy Peasy) and am going to have him run a LiveCD of it soon. I'll also give Masonux a run with it and see how that goes for the time being.

Thanks to everyone who contributed to this thread. I appreciate the suggestions and am learning some new things from it :D

---

### Post by Bungo Pony on 2009-12-30
I wiped Suse 11 off my Netbook and installed Xubuntu. I like Xubuntu because it's not so light that it's a piece of crap with no decent software in the repos, but it's not so heavy that it bogs down the resources. It's a nice happy medium :)

I've been wanting to install E17, but with it still not having a decently stable release (let alone the pain of installing it), I'll be holding off until it matures a bit more.

---

### Post by starcannon on 2009-12-30
> **emeraldgirl08 said:**
> My brother has an Asus eee 2gsurf netbook. I've never used one of these before and I was very curious about what OS it would be running. It seems it's some type of KDE linux OS. I also noticed that someone downloaded a lot of exe programs to the netbook. It's a little confusing b/c I see some Windoze type of signatures on it. Like the Silver XP theme is going on. 

I think the KDE is more hardware intensive than many other distros out there and that XFCE or LXDE may be a better platform to run. I'm fairly new here so if anyone has any suggestions as to what OS may be snappy and work excellent on his netbook I'd appreciate it!

Oh he's new to Linux and seems open to learning some terminal commands. I tried installing VLC through the command terminal but it is a little different than what I'm used to with Ubuntu or #!. His specs I'm not too sure about either...I think he told me it has 512 mb of RAM and the processor is probably less than 1ghz. Maybe around 700-900 mhz.
I bought a 2g surf, and found it too cramped(storage wise). So, I put a 16gb SDHC card in it, installed Puppy Linux to the SD card(a little sluggish, but snappy enough for the 2g Surfs purpose), and gave it to a cousin for christmas. He seems to like it for grabbing drivers and researching problems when he is on location doing tech support.

Try Puppy Linux and an SD card, I bought a 16gb Adata card at newegg when I put that one together, it was inexpensive, and made it a very viable little netbook.

GL and HF

---

### Post by garryknight on 2009-12-30
emeraldgirl: You might also want to check out the _[Eee User Forums]("http://forum.eeeuser.com/")_ as people there have installed most of the small-footprint distros.

---

### Post by emeraldgirl08 on 2009-12-30
> **garryknight said:**
> emeraldgirl: You might also want to check out the _[Eee User Forums]("http://forum.eeeuser.com/")_ as people there have installed most of the small-footprint distros.

Thanks Garry! Seems like a good place for some research and questions.

---

### Post by emeraldgirl08 on 2009-12-31
So it turns out the Asus triple e my brother bought has a BIOS password.

	:-?

He's waiting on a response from these ppl regarding the password. Just a reminder to people who buy laptops from ebay...

**Make sure you ask if there is a BIOS password on your future laptop before buying!**

---

### Post by pwnst*r on 2009-12-31
> **emeraldgirl08 said:**
> So it turns out the Asus triple e my brother bought has a BIOS password.

	:-?

He's waiting on a response from these ppl regarding the password. Just a reminder to people who buy laptops from ebay...

**Make sure you ask if there is a BIOS password on your future laptop before buying!**

lol, ebay

---

### Post by Nerd King on 2009-12-31
Arch might be hard work honestly, you might be better off getting a minimal ubuntu CD and installing what you want atop that. In other words you start with CLI and build up. It gives you the same flexibility as Arch, but with Ubuntu's wonderful apt-get and PPAs, ease-of-use, etc. I can get a fluxbox setup running on about 32MB RAM that way if I'm ruthless.

---

### Post by Nerd King on 2009-12-31
[http://forum.eeeuser.com/viewtopic.php?id=75838](http://forum.eeeuser.com/viewtopic.php?id=75838) for help with BIOS password thingy. There are a few suggestions given.

---

### Post by mamamia88 on 2009-12-31
what i tried of moblin i liked.  right now i have netbook remix and windows 7 installed.  just thinking of sticking with windows 7 though seeing how wireless via ndiswrapper has been disconnecting randomly for me

---

### Post by Ginsu543 on 2010-01-01
I'm running full versions of Ubuntu 9.10 with pretty much all the bells and whistles on my netbooks (Dell Mini 9 and Vostro A90) and both are working very well. I can understand going with smaller distros like those mentioned above, but it should also be pointed out that full Ubuntu can happily function on a netbook, UNR or otherwise. You can have your cake and eat it too.

---

### Post by starcannon on 2010-01-03
> **mamamia88 said:**
> what i tried of moblin i liked.  right now i have netbook remix and windows 7 installed.  just thinking of sticking with windows 7 though seeing how wireless via ndiswrapper has been disconnecting randomly for me
One could always go with regular Ubuntu, and the array.org kernel. No ndiswrapper needed; actually, on my triple e's the wifi always worked outta the box with both Ubuntu and Puppy, I only added the array.org kernel to get smooth suspend/resume while booting from an SDHC card.

GL and HF

---

### Post by nanotube on 2010-02-02
> **Ginsu543 said:**
> I'm running full versions of Ubuntu 9.10 with pretty much all the bells and whistles on my netbooks (Dell Mini 9 and Vostro A90) and both are working very well. I can understand going with smaller distros like those mentioned above, but it should also be pointed out that full Ubuntu can happily function on a netbook, UNR or otherwise. You can have your cake and eat it too.

+1 for this. i run the standard ubuntu 9.10 on my a90, and the performance is simply superb. /zzoooom/! :)

---

### Post by mgco on 2010-03-11
I'm currently considering either the Karmic Koala 9.10 or UNR Edition for an Asus Eee PC 900 (4GB+16GB). Would love to hear advice from you guys on this.
 
Thanks!

---

