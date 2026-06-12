---
title: "leaving windows questions"
date: 2005-09-27
forum: The Cafe
---

### Post by jocke1s on 2005-09-27
Hi there,

I used to be a debian user for some years but got tired with all the
tweaking. SO I moved to XP for various reasons.

I have tried to move back to linux now and then over the years but
I allways end up spending waaaaaaaay too much time configuring things.

I am not able to completely leave windows because
* Some specific work related software
* Dreamweaver
* Swishmax
* Some specific photo archiving/handling systems

But I would like to move over to linux for most other things.
-Surfing
-office
-mail
-icq etc
-music and video
-cd/dvd read/write/listen/view
-p2p
-php
-mysql
-technical writing, gonna try out LyX again, maybe.

Some questions/ponderings and also hopefully "sure thats easy in ubuntu" answers.

-When I tried linux  last time I noticed that my "pretty slim and ridden
of most silly decorations xp installation" was conciderably faster to start and in
almost all cases much more responsive to use. So my question is if this has been
improved in linux nowadays?

-Will ubuntu come with ttf-support out of the box, can I use my fonts from windows easily,
how does linux handle flat screens nowadays and Is there anything that compare to XP's
clear type support?

-I have what I think is a not so well supported printer due to Canon's inability to support
linux. its the 850i. How much work is it to get it working? It seems it do work but will
maybe not be autodetected.

-Burning cd-dvd (data,music,images,video,dvd etc etc). What application can do it all. I
do not want to spend any time/energy/learning on this. Just want something similar to
ashampo or nero. Is there such an application? When I tried it last time I had issues
with access and not being root, mounting drives etc etc.

-If I surf the net and stumble upon flash,wmv,mpg,avi or whatever how well supported is
multimedia of different codecs nowadays. If I want to look at a dvd movie or download
a windows media player film clip is this possible in ubuntu. Or how much work is there
to make it work. Any suggested software?


There are other things as well. But the main problem I had last time was the fact that
xp was much faster and more responsive, xp looks nicer due to better font and clear type
support, some applications I must use are not available for linux and lastly the pain
to configure and install and configure and install and trying to get the basics going.
Basics being -nice desktop -international key support -cd/dvd playing/burning
-movie playing -printing -icq/msn/etc -office -sound

This do sound like I better leave linux alone but xp is ofcourse not without problems
either. I am mostly tired that the system seems to degrade with time and security issues.
Since I use vim and ksh/awk + unix commands at work I miss the ease that I can do things
in unix/linux that are not so easy on xp.

So any insights are most welcomed.

Best regards
J.A

---

### Post by GeneralZod on 2005-09-27
> 
-When I tried linux last time I noticed that my "pretty slim and ridden
of most silly decorations xp installation" was conciderably faster to start and in
almost all cases much more responsive to use. So my question is if this has been
improved in linux nowadays?


This one is a huge point of contention; some people will swear blind that GNOME/ KDE are much faster and snappier than XP; others, like me, often find that the opposite holds.  

I think Linux apps almost invariably start up slower than XP's, unless you pre-link in which case it obviously depends solely on how well-written the app in question is :).  Boot-up speed is also a point of contention; some say Linux is faster, others XP.  For reference, Kubuntu on my laptop takes *well* over a minute to get to the desktop, and then the inclusion of session management (which, in fairness, is simply not provided by XP) means it takes even longer to get to the point where the harddrive isn't grinding away.

The general trend, though, (this is for KDE at least - I don't really follow GNOME) is for speed to increase with each release, with perhaps the occassional regression.  I think far faster boot-up times are also being worked on (google for "initng").

> 
-Will ubuntu come with ttf-support out of the box, can I use my fonts from windows easily,
how does linux handle flat screens nowadays and Is there anything that compare to XP's
clear type support?


If I recall, yes - in fact, the core fonts .ttfs are apt-get-able from some repository.

> 
-I have what I think is a not so well supported printer due to Canon's inability to support
linux. its the 850i. How much work is it to get it working? It seems it do work but will
maybe not be autodetected.


Don't know about this one; sorry.

> 
-Burning cd-dvd (data,music,images,video,dvd etc etc). What application can do it all. I
do not want to spend any time/energy/learning on this. Just want something similar to
ashampo or nero. Is there such an application? When I tried it last time I had issues
with access and not being root, mounting drives etc etc.


I'm going to show my KDE bias and say that K3B can do most, if not all, of these things.  Automatic conversion of video to DVD formats is something I'm unsure about as I have never tried it.

Burning CD's "Just Works" nowadays - no messing around with permissions! You may need to install cdrdao, but this is easily apt-get-able

> 
-If I surf the net and stumble upon flash,wmv,mpg,avi or whatever how well supported is
multimedia of different codecs nowadays. If I want to look at a dvd movie or download
a windows media player film clip is this possible in ubuntu. Or how much work is there
to make it work. Any suggested software?


If you install w32codecs (for WMV etc) and libdecss (for encrypted DVDs - warning - this is legally dubious, depending on where you live!), then you should be able to play damn-near anything - check out the ubuntuguide.org for more details - it's quite straight-forward.  I *think* that installation of these two items automatically grants this ability to any installed media player.  mplayer-plugin for Firefox/ Mozilla is what I use; I think Totem has a browser plugin, also.  I'd suggest just trying these all out and seeing which ones you like best.

Hope this helps,
Simon

---

### Post by UbuWu on 2005-09-27
[QUOTE=jocke1s]
-Burning cd-dvd (data,music,images,video,dvd etc etc). What application can do it all. I
do not want to spend any time/energy/learning on this. Just want something similar to
ashampo or nero. Is there such an application? When I tried it last time I had issues
with access and not being root, mounting drives etc etc.
[/QUOTE]

Both Gnomebaker and K3B can do it all and are easy to use.

---

### Post by blastus on 2005-09-27
[QUOTE=jocke1s]I am not able to completely leave windows because
* Some specific work related software
* Dreamweaver
* Swishmax
* Some specific photo archiving/handling systems[/QUOTE]

Work Related Software:
Get your company to buy you a laptop and the necessary software. If they want you to do work at home then they should supply the hardware/software. However, if you are a contractor and an architect, developer, or a member of a project, that's a tough one. In that case you are pretty much forced to buy and use Microsoft software whether you like it or not, even if it is just to test that your stuff works on Windows.

Other Software:
I haven't used Dreamweaver or Swishmax but you might want to check out [NVU](http://www.nvu.com/). I'm not sure what you mean by photo archiving but there is the [GIMP](http://www.gimp.org/) (a reasonable alternative to Photoshop) and photo viewing software (like Kuickshow.) 

As for the other software you need to ask yourself how much you are willing to change and how much you are willing to compromise or live without. I have wanted to move to Linux for a long time now, so I have been very particular about the software I use on Windows so that I do not become dependent on software that is either not available on Linux or is but doesn't have certain features. 

Realistically it may not be possible to completely get rid of Windows (because its so damn everywhere) but if your long-term strategy is Linux then you will seek to reduce your dependence on Windows as much as possible. For me, I'm still dependent on Windows for games and so that I can test that my stuff works on Windows.

---

### Post by jocke1s on 2005-09-29
Hi there,
Replying to my own post here.
I did a breeze install to try things out. It worked like a charm. No problems
at all really (to begin with).
I am actually very impressed!
My printer worked after selecting a proper driver. NICE!
Fixed some font stuff and got a decent looking firefox, not as good as XP
cleartype but good enough.
Screen is a bit sluggish, need nvidia drivers...... OK here my first trouble
starts. Upgraded the nvidia stuff, restarted X and got the NVIDIA splash screen. NICE.......
Next day X wont start. Don't ask me how, I did upgrade when prompted for it in the upper right corner of gnome desktop. Maybe thats it.
After this I tried many times to get nvidia working but to no avail.
This is where I usually end up in Linux, downloading nvidias latest driver from their homepage, downloading kernel sources, recompile kernel, fix and trix and after a couple of days-weeks-months It will work.
I don't have the energy for it this time though. *too much work*
Gave up on nvidia, started to look for w32codecs or any other way to play 99.9999% of any video file on the internet. But can't find it. I know there are some issues about legality and stuff. So how to proceed????
Actually burned a cd, tried gnomebaker first --- didn't work. Just locked
Installed k3b instead- works great!!!
Installed thunderbird and set up my mail - no prob.
Did some other stuff too. NICE system!
BUT!!
I need nvidia (or something to boost graphics performance)
I need multimedia support for most common video formats and DVD playback (even If I have to pay for it)
I also want E17 :)
To start with. It might sound very strange to demand stuff like this. But I am not really demanding anything. I know breeze isn't released yet and I will reinstall when It does. Wanna have reiserfs which I don't have now.
Some nice pointers to
-nvidia in current breeze, running 2.6.12-9-686
-w32codecs and dvd,video playback in general
-E17 :) Just for fun
Won't give up yet, everything still looks and feels much much more mature and good looking than last years
Best regards
JA.

---

### Post by tseliot on 2005-09-29
You can try my guides which are meant for newbies:

w32codecs
[http://ubuntuforums.org/showthread.php?t=70227]("http://ubuntuforums.org/showthread.php?t=70227")

nvidia drivers with a Breezy kernel
[http://ubuntuforums.org/showthread.php?t=52924]("http://ubuntuforums.org/showthread.php?t=52924")

---

### Post by UbuWu on 2005-09-29
Have you read this: [http://ubuntuguide.org/](http://ubuntuguide.org/)
Although it is for hoary, most things will also apply for breezy. There are instructions for installing nvidia drivers also.

---

### Post by blastus on 2005-09-29
I second UbuWu's post about the Ubuntu Starter Guide. It's what got me going.

---

### Post by poofyhairguy on 2005-09-29
Three things:

1. You will always have to spend more time to configure Linux. With XP Dell/HP/whoever does the work for you.

2. Cleartype (Ilike it less and I'm picky):

[http://ubuntuforums.org/showthread.php?t=20976&highlight=cleartype](http://ubuntuforums.org/showthread.php?t=20976&highlight=cleartype)

3. If you are like me, way to make xserver not crash:

[http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech](http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech)

Good luck.

---

### Post by drizek on 2005-09-29
im using SUPER right now and it boots in about 45 seconds to a full working KDE desktop. Windows boots in about 30 seconds, but it takes a while before it is actually ready to use. I personally find that very annoying. Also, SUPER will use initing in the future, which should cut down the boot time by at least 7-10 seconds. As far as application performance goes, both windows and SUPER run very well on my machine. However, linux(any distro) is MUCH more consistent about it. Some are faster than others, but they are all consistently the same speed. After a while of using windows, menus start to take FOREVER to load. For example, rightclick on you desktop and hover over the New menu under xp. It will take at least 2-3 seconds to load. and on a slightly more used system it could take 5 or more seconds. in KDE, the equivelant menu loads instantly, and it always will(at least until i format this partition and try another distro ;)).

---

### Post by jocke1s on 2005-09-30
Thanks for the support!
Tried the nvidia guide but I didn't get it to work. I'll give it a more serious try this weekend. Should I reinstall kernel or do some cleaning up in modules or something? If I get 7667 nvidia to work do I have to worry each time I do updates that I will end up with a broken X-server? hmmmm... messy
Also great tip about the cleartype font and mouse.
What is SUPER? Sounds interesting.
Also, how about prefetching? Any ideas?
Some other questions:
In XP I use xampp to VERY easily install apache+php+mysql+phpmyadmin etc
is there a metapackage or something to install the above apps in ubuntu or do I just pick what I need and install?
--
Some more praise :)
Since my debian days things are sooo much better. X is still problematic in some ways it seems but
-locales
-sound
-print
-usb
etc
just works! Thats impressive.
Regard
JA.

---

### Post by drizek on 2005-09-30
super is an optimized one-cd suse distro. its still very new and somewhat buggy, but it should be quite decent in a few weeks.

---

### Post by GeneralZod on 2005-09-30
[QUOTE=jocke1s]Should I reinstall kernel or do some cleaning up in modules or something? If I get 7667 nvidia to work do I have to worry each time I do updates that I will end up with a broken X-server? [/QUOTE]

It *is* a bit messy, but only kernel upgrades tend to break it.  Just make sure that whenever there is a kernel upgrade, you re-install the nvidia binary driver - this can be done by simply finding the package in synaptic and clicking "Mark for Reinstallation", and "Apply".  Messy, but very easy :)

---

### Post by tseliot on 2005-09-30
[QUOTE=jocke1s]Thanks for the support!
Tried the nvidia guide but I didn't get it to work. I'll give it a more serious try this weekend. Should I reinstall kernel or do some cleaning up in modules or something? [/QUOTE]
If you have any problems you can post them in my thread (the guide) and I (and other users) will try to help you

---

### Post by tseliot on 2005-09-30
And if you need Java:

[http://ubuntuforums.org/showthread.php?p=378870&posted=1#post378870]("http://ubuntuforums.org/showthread.php?p=378870&posted=1#post378870")

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=jocke1s]Thanks for the support!
Tried the nvidia guide but I didn't get it to work.[/QUOTE]


what Nvidia hardware do you have? Driver support was dropped for old models in more recent drivers versions....

---

