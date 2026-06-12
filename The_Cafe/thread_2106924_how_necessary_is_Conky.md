---
title: "how necessary is Conky?"
date: 2013-01-20
forum: The Cafe
---

### Post by pbpersson on 2013-01-20
I have played with Conky in the past and it looks cool but I have to admit that once I had it all configured I just ignored it.  I have windows on top of it and never see it. 

On my current configuration I have a system monitor widget in my panel which is always visible and if I want to see system statistics I just click on it to open a full version of system monitor.  It gives me more details that Conky ever did.

So....how many people cannot live without Conky and why?  Is it just something that looks cool but is not really practical?

---

### Post by snowpine on 2013-01-20
Conky is not part of a default Ubuntu installation, so I wouldn't consider it "necessary" at all. :)

---

### Post by sidzen on 2013-01-20
Unnecessary -- just eyecandy -- mostly for those looking over your shoulder or ones ego.

---

### Post by Frogs Hair on 2013-01-20
If you are interested in viewing system information you could try one of the many horizontal themes that appear on the bottom or top.   

[http://gnome-look.org/content/show.php/Horizontal%20Conky?content=807](http://gnome-look.org/content/show.php/Horizontal%20Conky?content=807)

[http://gnome-look.org/content/show.php/Horizontal+conky?content=14024](http://gnome-look.org/content/show.php/Horizontal+conky?content=14024)

[http://anonymous-bot.deviantart.com/art/horizontal-conky-139256868](http://anonymous-bot.deviantart.com/art/horizontal-conky-139256868)

---

### Post by MG&amp;TL on 2013-01-20
I believe some people (with huge monitors) have conky configs that mean that conky reserves space for itself, hence solving the problem with window overlap.

---

### Post by Chris_82 on 2013-01-20
It can be quite useful to yourself if you want to monitor some values without having to open another monitor program.

Most (all?) desktops (gnome, kde, ..) have more than two workspaces: switching to a blank one allows you to see all of conky.
Using your keyboard, all of this is fast, faster than opening a new program.

---

### Post by Version Dependency on 2013-01-20
If you are in need of constant system monitoring, conky is useful.  It's quite nice if you are on a multi-monitor setup as you can dedicate a screen to it.  But, in general, conky is not necessary.

---

### Post by Paqman on 2013-01-20
Faaaaaaar too much faff to configure. I have a system load indicator tucked away on my top panel and that does just fine. There's no real need for most of the detail I see people packing into conky displays, they just do it because they can.

---

### Post by Old_Grey_Wolf on 2013-01-20
Conky is not necessary at all. Some people find it useful though. The conky I use takes up very little screen space, and is not geeky or impressive in any way.

I use it because I use virtual machines quite often. Having the RAM usage, load on the processor cores, and temerature visible helps me determine if I can start another VM, or if I need to shut one down before starting a new one.

I am not a very good programmer, so having the running process IDs displayed is useful if I need to kill a process.

Conky can also uses less resources than other monitoring applications. As a test, I started Conky and System Monitor.
[INDENT]Conky is using 0.12% of CPU and 0.08% of RAM
System Monitor is using 3.09% of CPU and 0.5% of RAM

and, I noticed that

LibreOffice was using 0.69% CPU and 1.63% of RAM[/INDENT]

Other people may have their own reasons for using it.

---

### Post by stinkeye on 2013-01-20
I find it very useful as do many others.
You can do a lot more with it than just display system statistics.

In combination with other programs you can display almost anything you want on your desktop.
Doesn't have to be hidden behind maximized windows either.
eg I have conky under a transparent unity panel monitoring CPU HDD and GPU temps, memory usage and network stats.Also includes a countdown timer when triggered.
[ATTACH]230411[/ATTACH] 
If you like to tinker it is an enjoyable way to learn and delve under the hood of linux.

---

### Post by Spike-X on 2013-01-20
While it's not necessary, as such, I find it handy to keep an eye on various bits and pieces without having to open System Monitor or any of that. I have mine running in two lines across the top of my screen, so it doesn't take up that much space (it's a bugger to format when you don't want to use a monospace font, though!). I also have it displaying album art and song information in one corner when I have music playing, because it looks cool.

[[IMG]http://img.photobucket.com/albums/v235/Spike-X/th_Screenshotfrom2013-01-19.png[/IMG]](http://smg.photobucket.com/albums/v235/Spike-X/?action=view&current=Screenshotfrom2013-01-19.png)

I do find some people get a bit carried away with it, but it's their computer, not mine.

---

### Post by mips on 2013-01-21
> **Old_Grey_Wolf said:**
> Conky is not necessary at all.

+1

"If" I do use it it's very minimal, ram, cpu, network & hdd usage as well as temperature. But I have not used it in ages.

---

### Post by Jakin on 2013-01-21
Just depends if you like to know how apps and system calls are using your resources; Might help troubleshoot some things.

Its a plus, that its highly customizable.

---

### Post by sujoy on 2013-01-21
very usefull when used with dzen2 to drive the panel for my xmonad.

screenshot here .. [http://binarycodes.deviantart.com/art/Curiosity-319384304](http://binarycodes.deviantart.com/art/Curiosity-319384304)

Nothing fancy but shows me the clock and a few other stuff and mostly stays out of the way yet always visible. :)

---

### Post by Gremlinzzz on 2013-01-21
:popcorn:Very
its a known cure for boredom!

---

### Post by montag dp on 2013-01-21
Not necessary, but handy.  I like having a basic system monitor visible, and it's more convenient and customizable than leaving the standard system monitor open all the time.  Plus it's nice to have extra things like CPU temp, fan speed, and battery discharge rate easily visible (especially in KDE since there's no gnome-power-statistics program).

---

### Post by hydn79 on 2013-01-21
Not necessary at all. But is is really cool. For me with just 4GB of RAM its nice to see RAM free by just showing the desktop. I have solid state drive so hate having to swap. I have swappiness set low and a one point ran without swap enabled. But having conky help me keep tabs and act accordingly.

---

### Post by blackbird34 on 2013-01-21
Only really necessary to prove geek cred it seems... I prefer the System Load Indicator (or occasionally, the top command) too, but then i'm not doing anything impressive with my Buntu :D

---

### Post by Petro Dawg on 2013-01-21
I started using conky last summer (July or so) due to over heating issues with my Laptop, which are now for the most part solved.  It was very useful to have my system temps "right there" to easily see at any time.  

I have since spent many hours, if not days, customizing and adding features from scratch mostly just to learn how to work with the Linux terminal in more depth.  I would say working with Conky has made me a much more proficient  Linux user as I can now access nearly anything from terminal, can write simple bash scripts, and use powerful commands like grep and awk to some degree which also have their uses elsewhere.  I'm not a programmer, so I probably wouldn't have learned how to do must of that stuff without tinkering with Conky.

However, I must say, out of all the nearly limitless items I can display with Conky, the only things I have running now are my severe weather alert indicator (which is absolutely invisable unless there is an actually an alert) and my email notifier (which only displays those accounts currently with an unread email), so I can have my email checked without having to have Thunderbird always running.  I find, for me, these things are nearly necessary.

---

### Post by Max Blyss on 2013-01-21
While Conky is definitely not *necessary*, and most DE's have in - panel sysmonitors or extensions for same, it is very *convenient* and *potentially* stylish.

A little while after I started using 'Buntu, I started using Conky to help me to get the gist of editing config files, which I hadn't had to do to change anything in Winduhs, and it definitely made it more convenient to observe resource usage / processes.  I guess I'd say that it can be a great familiarization tool as well, esp. when you're new to Linux.

Now that I have an adequate-to-my-needs amount of Ubunt-knowhow, I just keep a small one up because it looks cool, and it's something to mess with during PC boredom spells.

---

