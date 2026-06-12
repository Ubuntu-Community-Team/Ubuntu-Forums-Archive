---
title: "Former Debian and Gentoo user getting ready to switch"
date: 2005-05-03
forum: The Cafe
---

### Post by ChodeNode on 2005-05-03
Hello all,

Please allow myself to introduce.... myself.

I live in Tucson, AZ in the U.S. I started using Linux a little over a year ago. I started off wanting to waste time on a project and started off with the stable build of Debian. I almost quit, but a friend urged me through it and eventually I got it up and running. Getting frustrated with how slow my system performed on this, I upgraded to the Sarge build and was a <I>little</i> happier, but not much. I tried going to the Sid build because I was tired of some programs missing features that were in recent builds and then half my programs wouldn't work and almost dumped it and went back to just Win XP (yeah... I know...).

So I dumped Debian and have been using Gentoo for about 6 months. No problems until my last world upgrade and a few of my apps are now broken and some are erroring on compiling. I'm getting married soon and just don't have time for this crap anymore. A buddy I know from another forum says the nice thing about Ubuntu is it Just Works™. I'm not happy about having to have Gnome in it out of the box, but whatever, I can deal with it. Kubuntu will come shortly after I install this.

I guess my question is since I have prior Debian experience, should Ubuntu already be pretty intuitive for me? Am I going to have to deal with a system so bloated with stuff it slows things down for me? Also, will most stuff still work for me if I copy over my home directories from Gentoo for myself and my fiance and make sure I have those programs still installed? My last distro change went reasonably well, I'm just trying to get as much info as I can on what to expect/do before making the jump.

Thanks all! I look forward to making these forums my home.

---

### Post by poofyhairguy on 2005-05-03
Hello 

[QUOTE=ChodeNode]I'm not happy about having to have Gnome in it out of the box, but whatever, I can deal with it. Kubuntu will come shortly after I install this.[/QUOTE]

Install Kubuntu instead of Ubuntu. Or install the server version of Ubuntu (type server after the install cd boots then enter) and the use this command:

sudo apt-get install kubuntu-desktop

I've done it, its works well with broadband.

Please note that Ubuntu doesn't have a root account by default. You must create one or use sudo. I like sudo a lot.

[QUOTE=ChodeNode]I guess my question is since I have prior Debian experience, should Ubuntu already be pretty intuitive for me? Am I going to have to deal with a system so bloated with stuff it slows things down for me?[/QUOTE]

Yes and Yes (the second one will be what you want if you use the Kubuntu install Cd instead of the Ubuntu one....it will take less time to install what you indicate you use)

[QUOTE=ChodeNode] Also, will most stuff still work for me if I copy over my home directories from Gentoo for myself and my fiance and make sure I have those programs still installed?[/QUOTE]

To install porgrams in Ubuntu (or kubuntu) you should use sypnatic.

Sudo apt-get install synaptic

will get in for you. Then there are thousands of Binary packages in which to pick programs from. You can copy you old data from your other partition (or mount it as /home) and expect it to get the data to work programs from synaptic

Be sure to search in the forums when you have questions, check out the howto page 

([http://www.ubuntuforums.org/forumdisplay.php?f=58](http://www.ubuntuforums.org/forumdisplay.php?f=58))

Use The backports repo for codecs instead of marillat, and do almost exactly what this guide says otherwise:

[www.ubuntuguide.org](www.ubuntuguide.org)

Good luck.


 My last distro change went reasonably well, I'm just trying to get as much info as I can on what to expect/do before making the jump.


[QUOTE=ChodeNode]Thanks all! I look forward to making these forums my home.[/QUOTE]

Cool. We'll try to answer your questions.

---

### Post by ChodeNode on 2005-05-03
Thanks for the response. You just brought up something that reminds me of what I couldn't figure out how to do when I moved to Gentoo though. Maybe you can enlighten me?

I have 2 hard drives, currently partitioned/formatted as such:

hda1 - NTFS, Windows XP OS
hda2 - NTFS, various windows apps

hdb1 - NTFS, data/games drive
hdb2 - /boot
hdb3 - /swap
hdb4 - /

I was wanting to partition out hdb to keep my NTFS, /boot, and /swap, but split partition hdb4 into two drives for /home and /. Would I delete the hdb4 partition, create 2 logical partitions in it and format them to taste? I wasn't sure what to do once a drive already has 4 primary partitions.

---

