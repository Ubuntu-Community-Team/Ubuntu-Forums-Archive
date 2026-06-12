---
title: "Just a heads up"
date: 2006-04-29
forum: The Cafe
---

### Post by Kimm on 2006-04-29
Just wanted to give you a little heads up about upgrading to Dapper.

I was reeealy curius about Dapper, especially GNOME 2.14, so.. as I wasnt to keen on updating to an operative system in Beta stages, but still wanted the latest GNOME, I desided to build it.
After a long build, I had something that at first looked like a fully funktional GNOME.

When I then rebooted the computer, I was faced with a gdm that had a crappy theme, no problem I said to myself... I can just change that, but aparently I had to login as root to do that, no more gksudo.
Then I tried switching virtual desktop, only to face a desktop **without a toolbar**, that made things difficult switching back.

My Epiphany would not work, a myriad of others apps would not eighter, aparently D-Bus was f00ked, not even a recompile and reboot fixed that one.

This is when I desided to dist-upgrade, that should fix GNOME and D-Bus and everything, so that I did.
Little did I know that broken packages would slow down my dist-upgrade signficantly, I was dist-upgrading from 18:00 (or 6 pm) to 02:30 (or 2:30 am) the next day... that was painfull. I had to do apt-get -f install countless time, and install fake empty packages so that broken packages would install.

so, my point is, unless you want to get your hands dirty, dont install dapper from dist-upgrade, use a CD-Image.
Although I have to say... I realy like Dapper now, and I dont regret my dist-upgrade, even though it took some time.

---

### Post by Rikostan on 2006-04-29
It's amazing how many different experiences we have with the upgrade. I did an upgrade to the **U**buntu Dapper beta from **K**ubuntu breezy and had no issues at all. I also did an upgrade on another machine from Flight 6 of Dapper and that went smooth too.. but of course that wasn't near as much of an upgrade as the other one was.

---

### Post by Kimm on 2006-04-29
Ah, so true

After the upgrade I had some trubble with the proprietary NVIDIA driver too, even though the kernel was left unupdated.

I solved that by removing my custom kernel, the driver, installing the Ubuntu kernel with headers and then installing nvidia-glx package.

Now I have some trubble with the uslapsh theme... I seem to have the Xubuntu usplash (have xubuntu-desktop installed aswell), I dont mind much, but it would be nice to have the original Ubuntu theme, so If someone could help with that, I'd apretiate it.

I also like the new VLC with gtk2, it seems to encode better now too...

---

### Post by byen on 2006-04-29
[QUOTE=kimm]Now I have some trubble with the uslapsh theme... I seem to have the Xubuntu usplash (have xubuntu-desktop installed aswell), I dont mind much, but it would be nice to have the original Ubuntu theme, so If someone could help with that, I'd apretiate it.[/QUOTE]
You might want to try [this to get that fixed]("http://www.ubuntuforums.org/showthread.php?t=113250"). Goodluck and thanks for the headsup on Dapper Upgrade issues :)

---

### Post by Kimm on 2006-04-29
Thanks byen, that fixed it.

I think I'll recompile this kernel... I dont like 2.6.15, it seems to slow down significantly under pressure (like building from source)

---

### Post by Compucore on 2006-04-29
i am just wondering here. Is there a huge difference between Dapper, breezy or hoary when you compare it graphical wise? Its like when I look between Hoary and my breezy versions that I have here on two seperate machine. Beside breezy having some more apps available to install. There is not that much of a difference between the two GUI's I find. 

Compucore

---

### Post by nalmeth on 2006-04-29
Yeah, fresh install is the best way to go.
Move your /home to it's own partition

---

### Post by Compucore on 2006-04-29
With Breezy badger and woary hedghog. Is already done that way over here from day one on installation over here. Meaning that both system have their home accounts on seperate partitions over here. Found it easier that way when installing both versions. And leave the main file sections for both on another seperate partitions. So that way they are working when boot up occurs. I don't know many people doing that way over here.I guess when I had worked with AIX as for doing things like updating cetain things where I used to work. Everything like that was on a seperate partition. I guess it was the luck of the draw when I had learnt it so many moons ago. And stuck with me since then. You always learn something new everyday.

Compucore


[QUOTE=nalmeth]Yeah, fresh install is the best way to go.
Move your /home to it's own partition[/QUOTE]

---

