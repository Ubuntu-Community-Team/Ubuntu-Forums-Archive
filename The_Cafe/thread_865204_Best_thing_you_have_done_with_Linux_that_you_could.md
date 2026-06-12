---
title: "Best thing you have done with Linux that you couldnt have done with windows?"
date: 2008-07-20
forum: The Cafe
---

### Post by Fixman on 2008-07-20
I used nautilus-actions to create a script that copies a file to a folder inside /var/www and copies its address (with my ip) to the clipboard, so now if I want to publish an image I must just right click it!

Here it is:

```

#!/bin/bash

r=.${1#*.} ;
n=0 ;

while [ -e /var/www/img/inger/$n$r ] ; do true $[ n++ ] ; done ;
mv $1 /var/www/img/inger/$n$r ;

echo `ipcheck`/img/inger/$n$r | xclip -selection c  ;

```

And this is ipcheck to know my ip:
```
 curl -s www.whatismyip.com/automation/n09230945.asp && echo 
```

No more imagesack :):):):)

---

### Post by keiichidono on 2008-07-20
GnomeDo, it enhances my productivity a lot.

---

### Post by flytripper on 2008-07-20
several things at once without crashing or locking up. i.e. bittorrent+music+a game running+internet+ possibly extracting a zip file... all done at the same time in ubuntu with no crashes/lockups to date. not one.

---

### Post by jflaker on 2008-07-20
Don't have to worry about the version being sunsetted like Windows XP.  XP is a strong and relatively efficient OS (I said "relatively")......but windows is going End of Life very shortly.

What couldn't I do with windows?  Get the next version upgrade without having to take a small loan!  Best of all, unlike Windows, I can share!!!!!

---

### Post by hessiess on 2008-07-20
get a complelty useable computer without spending anything on softwere including the OS.

bake a 350 res fluid sim in blender without it crashing.

---

### Post by Tigin on 2008-07-20
well , i am using ubuntu on my laptop for officework and i am happy with it but the best thing i've done with linux is related with PClinuxOS DFE running on my desktop computer .

I am currently making pre-color correction for the last film i have shoot as a director of photography from the dailies i have , real color correction will be 2 months later after the last edit and effects , i will be ready till that time .:)

:guitar:

---

### Post by wrtpeeps on 2008-07-20
Haven't found anything I couldn't do on windows yet.

The difference is I can do it for free. :lolflag:

---

### Post by AnonCat on 2008-07-20
Surf the net with peace of mind

---

### Post by tashmooclam on 2008-07-20
The best thing I have done is show to some skeptical friends that you do not need Windows to run an inexpensive computer. When I show others, they are a little shocked that the status quo is changing quickly.

---

### Post by Corfy on 2008-07-20
Use LiveCDs.

Between Ubuntu/Kubuntu, SystemRescueCD, and Damn Small Linux, it is amazing what I can do to fix Windows systems that aren't running properly (BTW, I should add I'm the IT department at my office, and we are strictly Windows there, although I am Linux at home... I'm trying to convince them, but I haven't had much luck so far).

Whether it is something as simple as running a Memory Check, something as mundane as getting data off a Win98 laptop when it has no CD burner and no network/internet connection and no drivers for the USB port (that was a co-worker's personal computer, not an office computer, BTW), or as complex as getting rid of viruses, it is amazing what I can do with the "free" Linux LiveCDs that I simply can't accomplish with the considerably more expensive Windows.

And this next story isn't "Linux" per se, but it is open source (or free software, if you prefer). A co-worker was having trouble opening a jpeg file in Adobe Photoshop CS a couple weeks ago. Every time he tried, it would give him an error message (something about a bad image header) and shut down Photoshop. I opened it right up in GIMP (running on Windows) without any problems, resaved it, and he was able to work with it from then on. I haven't let him live that one down yet.

I love using free tools to fix problems that can't be fixed by programs that cost hundreds of dollars. :lolflag:

---

### Post by adamogardner on 2008-07-20
get the real driving experience through the command line interface

---

### Post by Jordanwb on 2008-07-20
Well this isn't too ground breaking but... I like how the visuals of KDE can be easily modified without any additional software. I have the taskbar set to full transparency so my background of a Bently Le Mans racecar (and a damn cool looking one too) shows through.

---

### Post by tamoneya on 2008-07-20
use software repositories:
```
sudo apt-get update
sudo apt-get upgrade
```

Windows is so much more difficult.

---

### Post by smartboyathome on 2008-07-21
Infinate symlink loops: they crash everything. :p

---

### Post by barbedsaber on 2008-07-21
Are we having another one of these?ow (4 replies)

---

### Post by L815 on 2008-07-21
Best thing I do with linux that I *didn't really* do with Windows is being more productive.

---

### Post by ryaxnb on 2008-07-21
* Upgrade everything at once.
* Use VNC in the default install
* Use Bash (without kludges)
* Use Grep (again, fast, w/o kludges
* Aptitude!
* Compile from source (yes, I find this somewhat fun)
* Work with PyGTK and PyQt easily.
* Avoid IE completely! (No IE here!)
* Not use the webby UI (goshdarned webby UI)
* Use GNOME (I consider it superior to Windows)
* Run VMs using Xen (not tried yet)
* Run on an old P!!! 500 w/ 12GB HD without choking (using Puppy Linux)
* etc.

---

### Post by tuebinger on 2008-07-21
I've always wanted to use Photoshop to manipulate my photos but couldn't bring myself to buy the program.  Now I can manipulate my photos using GIMP.

---

### Post by Lord Xeb on 2008-07-21
Lets see here:

Compiz

System RAM usage is down around 400-750MB compared to windows where I would be using over one gig with just FF, Trend Micro, and WMP :/ I barely even use 1 gig after having almost 10 programs up and running.

Plug n Play (my camera and stuff)

Custom firewalls without very much hassel and were made to my standards, including things that cannot be found or made with firewallbuilder. 

My computer stays at about 120-130F average compared to windows when it was at 130 average just running firefox

Get my wireless to work right :D

Monitor all my system information just from one panel.

browse the web without getting viruses.

---

### Post by jay019 on 2008-07-21
Read the source code of my OS! :P

---

### Post by poofyhairguy on 2008-07-21
Put it on my PS3 or my router.

---

### Post by Corfy on 2008-08-27
I had a situation this morning where Windows was simply not up to the task but Linux handled it without any problems whatsoever.

What was the situation? I had to read a Compact Flash card with some pictures that were absolutely needed for today at the office.

Three Windows XP computers told us the card was unreadable and "Do you want to format?" No, we don't want to format, we want our pictures.

So I restarted my computer and booted into Ubuntu, and hooked the cardreader and card up. It had no problem reading the card at all, I got the pictures, and now I look like a hero.

I said it before, but I love using free software to do something that high-priced commercial software can't handle.

---

### Post by venator260 on 2008-08-27
Do everything that I would want to upgrade to Vista for with 512M of RAM and not pay anything to do it.

---

### Post by malspa on 2008-08-27
Legally install the same OS on several different machines without having to purchase installation CDs for each one.

---

### Post by Barrucadu on 2008-08-27
Recognise my card reader automagically, without need for a driver disk.

---

### Post by Npl on 2008-08-27
Having the Wallpaper only sometime loading. I wouldnt know how I`d do this in Windows, and Hardy Heron does this by default.

Nah, the big point using Linux is having a easy time compiling stuff, make && make install and youre good to go. Ironically the only thing allowing this is the sheer dominance of one toolchain, who said choice is good? :)

---

### Post by timzak on 2008-08-27
I'll echo others on this one: 

Create a fully functional OS complete with all apps for zero monetary cost--free!

And I'll add one that I never realized I missed from Windows until I started using it in Ubuntu:

Have the day and date integrated into the panel clock, so at a glance of my desktop, I know what day and date it is.  In Windows you must hover your mouse over the time to see the day and date.

---

### Post by Sporkman on 2008-08-27
> **wrtpeeps said:**
> haven't found anything i couldn't do on windows yet.

The difference is i can do it for free. :lolflag:

+1

---

### Post by fwojciec on 2008-08-27
Here's a nice testimonial that I found: [http://www.head-fi.org/forums/f46/my-new-3-watt-dead-silent-usb-linux-music-server-326831/]("http://www.head-fi.org/forums/f46/my-new-3-watt-dead-silent-usb-linux-music-server-326831/")
You'll definitely appreciate it if you're into high-quality audio and such things...

---

### Post by vanden12 on 2008-08-27
> **Corfy said:**
> Use LiveCDs.

Between Ubuntu/Kubuntu, SystemRescueCD, and Damn Small Linux, it is amazing what I can do to fix Windows systems that aren't running properly (BTW, I should add I'm the IT department at my office, and we are strictly Windows there, although I am Linux at home... I'm trying to convince them, but I haven't had much luck so far).

Whether it is something as simple as running a Memory Check, something as mundane as getting data off a Win98 laptop when it has no CD burner and no network/internet connection and no drivers for the USB port (that was a co-worker's personal computer, not an office computer, BTW), or as complex as getting rid of viruses, it is amazing what I can do with the "free" Linux LiveCDs that I simply can't accomplish with the considerably more expensive Windows.

And this next story isn't "Linux" per se, but it is open source (or free software, if you prefer). A co-worker was having trouble opening a jpeg file in Adobe Photoshop CS a couple weeks ago. Every time he tried, it would give him an error message (something about a bad image header) and shut down Photoshop. I opened it right up in GIMP (running on Windows) without any problems, resaved it, and he was able to work with it from then on. I haven't let him live that one down yet.

I love using free tools to fix problems that can't be fixed by programs that cost hundreds of dollars. :lolflag:How do you get ride of a virus on windows with linux?

Also I just love the live cd...Have somthing really safe for shopping, or going over your friends house who says you gave them a virus...Or just being able go a firends house you there computer and not have any info left on there computer...

Also like that I can install 15 apps and walk away...and checking my uptime..

What I dont like is that I cant use Itunes or Fireworks 8 on linux.. Ipod 80gb and my Ipod touch dont work so well in amarok.Also Itunes is by far the best podcast manger I sceen...

Tho I must say banshee is growing on me..

---

### Post by Corfy on 2008-08-27
> **vanden12 said:**
> How do you get ride of a virus on windows with linux?

One of the problems I have often run into with viruses and/or adware/spyware on a Windows computer is you can't delete the file because it is in use (usually, restarting in safe mode doesn't help). When it is particularly nasty, I shut down the process using it, but the process immediately starts up again before I have a chance to delete the file. 

So I pop in a LiveCD, restart the computer, mount the Windows partition or drive, and since Windows isn't running, I can delete any file (or files) I want because none of them are in use. I have used that trick many times.

Also, the SystemRescue CD comes with ClamAV, so you can run an antivirus scan on the drive/partition.

---

### Post by neonl on 2008-08-27
Using bleeding edge software at the same time I use an ultra-simple and ultra-lightweight WM and being able to compile the whole system from source when I want to (right now i use Gentoo + Fluxbox + Thunar + Firefox + OOo + MPlayer + VLC + MPD/Sonata)

---

### Post by LateNiteTV on 2008-08-27
write linux x86 shellcode.

---

### Post by RiceMonster on 2008-08-27
Use linux.

---

