---
title: "Linux vs. windows on older hardware"
date: 2005-01-31
forum: The Cafe
---

### Post by nocturn on 2005-01-31
I was talking to my best friend this weekend.   He has been using Linux for a while now, and most computers at his home run Linux.
In general, he is very pro-Linux.

A couple of months ago he started working at a school, partly doing their IT.  
This weekend he raised the topic of the hardware specs required to run Linux against those of Windows 2K/XP.

He is running Ubuntu at home on his own system just fine, but his mother uses a modest PII-350 with 64 MB RAM, and it seems that Gnome/KDE is terribly slow on it.
The hardware specs at his school hang arround PII's of 200 MHZ and up, most with only 64 MB RAM.  Most Linux desktop environments do not run very well on it, while he says W2K is quite useable after bootup.  The main issue seems to be the low amount of RAM in them.

I also think (guess) that Xfree is quite the memory hog on such systems, I do not know if Xorg is much better.

I can agree with him on one thing though, on those older systems, OpenOffice is unusable (I have a PII laptop...).

What are your experiences with this?  What is the lowest hardware spec you can run Linux comforatbly on?   Does Windows perform better on it?

---

### Post by angrylittleman on 2005-01-31
For older hardware, as you mention, Unbuntu may not run well.  I would try installing xfce on it in combination with ROX (pinboards are great!) and seeing how that works.  For older hardware, I run DSL.  Along with Ubuntu, it is a great, well thought out distro that just smokes on older hardware.  I run that on 2 of my old laptops, a 333 AMD with 128 mb RAM and a P77 with 32 mb of RAM.  It runs desktops on both of them and works well.  Hope this helps.


--ALM

---

### Post by nocturn on 2005-01-31
Thanks.  A P77, that's cool.  The oldest machine I have in production is a P90 at my parent's house running Ipcop (firewall).

---

### Post by Viro on 2005-01-31
[QUOTE=angrylittleman]For older hardware, as you mention, Unbuntu may not run well.  I would try installing xfce on it in combination with ROX (pinboards are great!) and seeing how that works.  For older hardware, I run DSL.  Along with Ubuntu, it is a great, well thought out distro that just smokes on older hardware.  I run that on 2 of my old laptops, a 333 AMD with 128 mb RAM and a P77 with 32 mb of RAM.  It runs desktops on both of them and works well.  Hope this helps.


--ALM[/QUOTE]
 I think it should be a P75 :) I don't think there were any P77's that were ever produced since there aren't any multipliers that will get you that frequency.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=nocturn]
What are your experiences with this?  What is the lowest hardware spec you can run Linux comforatbly on?   Does Windows perform better on it?[/QUOTE]

My 400mhz celeron. Gnome chokes on it. XFCE runs fine and looks great.

My only complaint for it is that it does not mount new things (cds, pen drives) on the desktop like Warty's gnome does.

---

### Post by Jad on 2005-01-31
I have two machines at home, the old one PIII 1G, 384RAM, it run much better and smoothly on linux. but very slow with XP.
its a test machine, so I have installed to many Linux distributions on it, and all was   running just fine.

---

### Post by domzo on 2005-01-31
I'm running Ubuntu on a PIII 600 with 256mb Ram. 

It ran Win98 ok (for a while - it got progressively slower as it got clogged up with stuff). Suse 9.2 runs like a dog (a slow dog... ) whereas Ubuntu runs like a dream.

---

### Post by az on 2005-01-31
"He is running Ubuntu at home on his own system just fine, but his mother uses a modest PII-350 with 64 MB RAM, and it seems that Gnome/KDE is terribly slow on it.
The hardware specs at his school hang arround PII's of 200 MHZ and up, most with only 64 MB RAM. Most Linux desktop environments do not run very well on it, while he says W2K is quite useable after bootup. The main issue seems to be the low amount of RAM in them."


Out of all the Windows, I think Windows2000 has the most responsive desktop.  I refer to response to clicks and window drawing.

Gnome has a much slower responsiveness, but that does not make it neccesarily slow.  If you get over the lag in opening windows and do not spend your days navigating the filesystem with nautilus, you may have  a quicker system with linux.  For example, on win98, I constantly found pauses for up to two minutes doing various things.  I do not think this had to do with swapping, since I would not neccessarily be doing a lot of things at the same time.

The fact that you can cut down on the bells and whistles and run a bare desktop (Icewm with Rox filer and a web browser) will make Linux run circles around Windows.  I speak from experence with Debian linux, since most other distros like Fedora or Mandrake are so terribly slow.

Windows machines can remain responsive (to clicks) with a surprisingly low amount of memory, but this is at the expense of stability.  I would not reccommend either OS, these days, with less than 64 megs or ram.  More is better.


Another thing you can do with linux is running remote apps.

I can run apps from my faster computer on my 167MHz laptop.  I am using a 802.11b wireless card and there is almost no difference in responsiveness.

I can run a whole virtual X session or just one client application.  This thin client approach would be great for the classroom.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=azz]
Out of all the Windows, I think Windows2000 has the most responsive desktop.  I refer to response to clicks and window drawing.
[/QUOTE]

When my Windows friends ask me about Ubuntu, I say "Its the first OS that is overall better than W2K pro." 

And that might not be true (Mepis was probably the first), but they get the point.

---

### Post by CowPie on 2005-01-31
[QUOTE=poofyhairguy]My 400mhz celeron. Gnome chokes on it. XFCE runs fine and looks great.

My only complaint for it is that it does not mount new things (cds, pen drives) on the desktop like Warty's gnome does.[/QUOTE]
 I heard that you could use gnome-volume-manager at startup to do that...but I couldn't figure out how to start things up in XFCE so I went back to gnome (in gnome its under "sessions)

---

### Post by adbak on 2005-01-31
If you like Ubuntu and would like to have it run on older machines, you can always use BeatrIX.  It's based on Ubuntu, it's ISO is only 200MB, and it says it can work on IBM-compatible machines made in the last 10 years.  I should try it on my parents' PIII 350MHz 128MB RAM box that is currently running Warty.  Gnome is rather sluggish, but on par with what Windows 98 was when it was installed, but I use FluxBox when I am on that computer.

---

### Post by nocturn on 2005-02-01
[QUOTE=adbak]If you like Ubuntu and would like to have it run on older machines, you can always use BeatrIX.  It's based on Ubuntu, it's ISO is only 200MB, and it says it can work on IBM-compatible machines made in the last 10 years.  I should try it on my parents' PIII 350MHz 128MB RAM box that is currently running Warty.  Gnome is rather sluggish, but on par with what Windows 98 was when it was installed, but I use FluxBox when I am on that computer.[/QUOTE]

Thanks, BeatrIX looks very cool indeed.  
It stills seems to need more then 64 MB though.  I also wonder if OO writer will run on the old hardware...

I guess it will do fine with 128 MB of RAM.

---

### Post by Marquis_de_Carabas on 2005-02-01
Before I got this computer a few months ago I was running a 133Mhz DX4 with 2GB of hard drive space and 16Mb of RAM. Any form of multi-tasking was a distant dream, but it ran Windows 95, MS Word, Opera (web browsing was still slow, but after turning pictures off it wasn't so bad), and a variety of old games (anyone remember Syndicate? Day Of The Tentacle? Sam & Max? Classics one and all).

I did at one stage attempt to get Linux installed on it, but it proved insanely difficult, mostly because I had a weird SCSI-through-parallel-port CD ROM and couldn't find any Linux drivers (to be fair, there were no Windows drivers either - I was forced to use DOS ones). I did manage to get Slackware installed at one stage, but Gnome was unbelievably slow (not just for click-response, even something like Mines was too slow to be workable) and I couldn't get my modem to work, so I gave up after several weeks spent attempting to get it to work. (My first Linux experience was trying to install Slackware on a 10-year old computer - is anyone else surprised that I came back? :) )

Turning an ancient box into a general-purpose computer (i.e. not just a firewall or whatever) is easier with Windows, at least in my experience. But then if you actually know what you're doing with Linux (I'm still a noob, but was much more of a noob then - it took me a couple of hours to figure out why the "dir" command wasn't working), and are aware of things such as Fluxbox and IceWM, it seems entirely possible.

---

### Post by axcairns on 2005-02-01
I tried a couple of different distros (Gentoo and FC2) on my old celeron 300 laptop with 160MB memory without a lot of success.  Neither could produce a responsive Gnome desktop. XFCE was quite responsive (but not zippy) but I ran into a couple of other problems. Firstly, neither distro could handle my onboard soundcard reliably despite many weeks of tweaking. Secondly, the 4GB hard drive quickly got close to filling up, preventing me from upgrading to FC3.

After those experiences (bear in mind this was before I had heard of Ubuntu) I decided to try Windows XP on it. I was surprised how smoothly it went - sound works reliably, disk space free (even after adding Office, Firefox, Thunderbird etc) is still over 2GB after 4 months and the desktop is as responsive as XFCE ever was.

I wouldn't try XP on anything under 128MB though. I tried it once on 64MB as a server and, even after disabling half the system, it ran like a dog. 

Sorry all, XP is staying on this laptop. Never fear though, my XP1800+ desktop is running Warty!

Cheers,

Allan

---

### Post by Rui Pais on 2005-02-01
Well, if you have 2 computers with different ages/speeds you can use the slow one just to log on your speed baby. It's special nice if you have several users of your computers that could or want to work at same time. 

I had an old pentium classic, 200Mgh, 128 ram and a P4, 3,2 Ghz, 1 G ram, both with network cards on a small house network. 
On the P4 i did a gdmsetup and enabled XDMCP. On the old creature i edit /etc/X11/gdm/gdm.conf and add, under 0=standart, '1=Terminal -query 10.0.0.3' (thats the ip that my DHCP gives to my fast machine). and that's all.  You can even use only 0=Terminal..., but i use 2 grafical consoles to my wife easily change and turn it off.

That slow thing turns up, starts an old and unmantained (by me, i mean) redhat9, and splashs a login on my fast computer and WORK as a fast computer. There is no special computer around, my family logs on on the one there is not occupied. I just keep one computer up-to-date, just track errors and bugs on one, and it's like having two pentiums 4 high speed for the price of one. (And I don't enlarge the size of waste on planet putting that old can on trash to give my wife and kid the machine and the speed they deserve)  =D>

---

### Post by Typhoon on 2005-02-01
I have a Compaq Armada 1598DT: Mobile Pentium MMX, 267.276 MHz (according to cat /proc/cpuinfo); 64mb.

It runs Debian Sarge with Icewm very nicely. I doubt that it would ever be descibed as "zippy", but it serves its purpose very well: dial up connections, digital camera connections (through USB), emacs/LaTeX authoring when away from home.

I have tried it with Gnome desktop, but the wait isn't worth the bother.

Typhoon

---

