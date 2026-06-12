---
title: "Favorite gagdet, widget, dock, ... whatever"
date: 2006-12-14
forum: The Cafe
---

### Post by BLTicklemonster on 2006-12-14
Okay, so I see a lot of screenshots in a lot of threads with some really cool looking stuff, but hardly ever get a chance to take note of what it is, where it came from, what it takes to get it running, and how to get it to work the way it looks in the screenshot.


So....


I have decided to allow you all to post here (well, Mr Shuttleworth did, I'm just tweaking that a bit) your favorite coolness that you use on your desktop. I keep seeing transparent thingamabobs that do anything from tell you everything about your system to media players (I think that was what they were), and I'd like to find out how you all got them.


The premise is, post a screenshot showing off your stuff, and in your post, please share some info on where you got it, what it took to install it (if you remember, and please, try to remember), and what you did to make it look as cool (and you know it does) as it does.

Me? I got nothing. So I guess I ought to be banned from this thread, huh? :)

---

### Post by jordanmthomas on 2006-12-15
I've really been impressed with [xglsnow]("http://cornergraf.net/projects/xglsnow/")...a beryl plugin.
You need beryl 1.3 (maybe from svn only...not sure)

It is quite possibly the most useless eyecandy I have ever put on my computer.  Here, I have it turned up to 10000 flakes just for effect.

Ignore the jpeg artifacts...my png was too large for the forums

---

### Post by BLTicklemonster on 2006-12-18
Surely there are more people who want to share goodies here?

---

### Post by pichalsi on 2006-12-18
you probably know this but LiquidWeather is one of the coolest :) [http://liquidweather.net/](http://liquidweather.net/)

---

### Post by BLTicklemonster on 2006-12-18
Dang, KDE. I stay away from that one, but if you want "stuff", I guess you need to run KDE. Thanks, I never heard of that. 

You see, I think people come by here and know all kinds of stuff, but blow this off, figuring everyone already knows about all this stuff, but I personally don't know much about it at all. 

Screenies, remember to post screenies of them in action, if you can!

---

### Post by BuffaloX on 2006-12-18
.
**gDeskCal**

Is a themable monthly calendar, that sits on your desktop,
It's much like rainlendar, which I used before I switched to Linux.
Rainlendar is actually available for Linux now, but I prefer gDeskCal.
You can enter simple appointments by just doubleclicking the date.
Perfect for personal use.
It also works with evolution, neat. :D 

[http://www.pycage.de/#gdeskcal]("http://www.pycage.de/#gdeskcal")


**Gkrellm **
a very nice skinnable system monitor.
It can read temps from:
lm sensors, hddtemp, Nvidea Geforce.
Not many monitors read from all of those.

It has loads of plugins, especially you should try the scope, which shows audio activity.
Plugins I use Include:
CPU Mhz (glx86info)
Keyboard state for caps scroll and num lock (GKleds)
Simple analogue clock (atrax clock 2)

It comes with many built in monitors I use:
Disk IO, CPU usage, hdd activity, eth activity, uptime, mail notifier.

[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html")

---

### Post by dbbolton on 2006-12-18
all the ones i've tried have failed miserably.

---

### Post by BuffaloX on 2006-12-18
Oh I missed the thing about installing.
Well Gkrellm is actually in Synaptix, so just take it from there.

Gdeskcal is allso in repository, but it seems to be an old version.
To install just do the usual:

./configure
make
sudo make install

It probably also says so in the readme...
If you get errors with ./configure, check what it says is missing, and install it from synaptix.

In short they are both very easy to install.

I searched for ages for the calendar before finding it. Probably because of its name.
Its probably not near as widespread as it should be because of that.
Gkrellm also took me some time, but that was because there are so many system monitors to choose from. But as far as I can see, gkrellm is the only one that work with all sensors in my system.

---

### Post by BLTicklemonster on 2006-12-18
[http://www.lynucs.org/index.php?screen_id=197252359344145d26c6f5f&p=screen&PHPSESSID=d683a6ea69c30b9ad51042e497706e3c](http://www.lynucs.org/index.php?screen_id=197252359344145d26c6f5f&p=screen&PHPSESSID=d683a6ea69c30b9ad51042e497706e3c)

right up there on the right, see it? That's what I'm talking about. I had the gkrellm thing, but it's a bit odd.

---

### Post by maniacmusician on 2006-12-18
I've never liked gkrellm. Had it for a while when I was running Xubuntu. I've since switched to KDE, but I don't really find myself using superkaramba much either. 

I installed Beryl stable and that was pretty neat. Then I upgraded to SVN and it turned into a monster (mem hog, jerky 3d, etc) and that's with a 7600GT. And I don't feel like going through the hassle of downgrading because I'm so busy it's crazy. I don't even have time really to make this post.  So I guess I'm waiting till the next stable version appears and I'll jump onto that. [sigh]

In short; I havn't found any such "gadgets" to actually be useful for more than a couple of hours of amusement.

---

### Post by BuffaloX on 2006-12-18
> **BLTicklemonster said:**
> [http://www.lynucs.org/index.php?screen_id=197252359344145d26c6f5f&p=screen&PHPSESSID=d683a6ea69c30b9ad51042e497706e3c](http://www.lynucs.org/index.php?screen_id=197252359344145d26c6f5f&p=screen&PHPSESSID=d683a6ea69c30b9ad51042e497706e3c)

right up there on the right, see it? That's what I'm talking about. I had the gkrellm thing, but it's a bit odd.

That thing is conky, there are several threads about it.
You can find lots of info about it if you search the forum.

I would much prefer Gkrellm to be a horizontal monitor, I have been looking at the code, but not done anything with it yet, except removing annying .0 from all temps which are integer numbers anyway. (at least when using celcius they are)

---

### Post by BLTicklemonster on 2006-12-18
Yep. I agree, but there are some that are really cool looking. I think a weather one would be nice.

---

### Post by Kuoi on 2007-04-26
I get the following errors when I want to start gdeskcal ...

> Traceback (most recent call last):
  File "/usr/local/bin/gdeskcal", line 15, in <module>
    import code.i18n
  File "/usr/local/lib/gdeskcal/code/i18n.py", line 1, in <module>
    import values
  File "/usr/local/lib/gdeskcal/code/values.py", line 13
SyntaxError: Non-ASCII character '\xc3' in file /usr/local/lib/gdeskcal/code/values.py on line 14, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details


Can somebody tell me what that means ?

Kuoi

---

### Post by nikoPSK on 2007-10-05
for me it's awn and compiz. I love the weather plug-in for awn. I don't have too much bling because then it will either start looking like vista or osx.:p

---

### Post by sp0onman on 2007-10-06
mine would have to be AWM and the widescape weather plugin for screenlets(the only one i use because its simple and doesnt take up alot of desktop space).

---

### Post by santiagoward2000 on 2007-10-06
Do I have to choose one? I'm using screenlets, cairo-clock and kiba-dock... and Compiz-Fusion, of course!

[IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot.png[/IMG] [IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-1.png[/IMG]

[IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-2.png[/IMG] [IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-3.png[/IMG]

[IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-4.png[/IMG] [IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-5.png[/IMG]

[IMG]http://ubuntuforums.org/g/images/348163/medium/1_Screenshot-6.png[/IMG]

Sorry if I posted too many pictures, I'm just so proud! :lolflag:

---

### Post by jimrz on 2007-10-06
Deskbar ("entry in panel" view) though, sadly, with  the new version in gutsy it will be going away. Has anybody heard of any plans to fork the applet now that it is turning into more of a full blown app and losing the one characteristic that has made it so appealing and useful?

---

### Post by Bungo Pony on 2007-10-06
The only things I have running on mine are Beryl and a gDesklet called "SideCandy Popmail" which just tells me if I have new email. I recently tried cairo-dock, but I didn't like it taking up the desktop space. I'll eventually get conky working properly.

---

### Post by nikoPSK on 2007-10-06
unfortunately cairo clock just makes it too vista-ish so I don't use it XD

---

### Post by santiagoward2000 on 2007-10-06
Can I consider my gaim-text a widget? It looks so cool!!! (I've already posted a screen before)

---

### Post by drivel on 2007-10-06
I'm using screenlets,but found some bugs,so I've removed it

---

