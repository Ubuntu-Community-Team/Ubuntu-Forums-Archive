---
title: "*sigh*"
date: 2005-03-09
forum: The Cafe
---

### Post by Phosphoros on 2005-03-09
**Warning this is long**

I probably shouldn't write this as pissed as I am right now but I would probably lose my nerve later on.  
I really like Ubuntu, it's the first distro I've ever used that didn't have me wanting to slit my wrists 20 minutes into using it.
In my not so Linux savvy opinion it's hands down the best thing to happen to Linux.

With that said, my problem I suppose is with Linux itself.  I'd love to make the switch to Linux completely and dump Microsoft forever. Sadly,  I don't see that happening for me for a very long time, if ever.
The last two weeks I've been trying to accomplish 6 basic things with Ubuntu Linux.
Here they are
[list=1]
[*]DVD playing with actual DVD Menus
[*]Reading files off my NTFS backup drive
[*]Get Windows Games installed and playing
[*]Install some of the Nifty free software out there for Linux.  Nothing insane just simple stuff.
[*]Get some kind of Webcam Service that works with Yahoo (Any IM client would be nice) since this is what I use to chat with my family on the other side of the country.
[*]Setup my own little web server to play with.
[/list] 

Ok, so, here is how these broke down.
1.) Got DVDs working pretty good with Ubuntuguide.org and some help from people on this forum (searching and finding answers mainly).  This pretty much applies to multimedia in general.  Worked out pretty well.
2.) Have never gotten this to work ever.  Ubuntuguide had a way to do it for reading the windows directory but I just can't seem to figure out how to do it **across** drives I guess. 
3.) Never happened.  In fact I somehow screwed up my Ubuntu trying.  Hell I can't even get simple old Wine to work to run notepad if I wanted too.
4.) For the most part this is simple because Synaptic/sudo apt-get does all the work for me and I like that.  But as I noted in the beginning.  I'm pretty erked right now because of one of these programs.  Beagle.  Great program I'm sure but no thanks on the dependency hell.  I went through the wiki guide, several posts on it, Googled it, blah blah blah, but No matter how many thing I install that it depends on it will not ./configure.  This isn't the first program either to do this to me.  Several have done this junk to me when I have to ./configure make .  This is broken or isn't there, now that's not there, on and on and on.  This happens every single time I try and make something from source. :(
I'm sure many of you are sitting here wondering just how stupid I could be? Sadly I'm not, honest.  I'm the person all my friends come to to fix *their* computer problems.  I'm really not this dumb or perhaps it's this dependency stuff that's getting dumb?  I vote dependency hell.
Just for reference here is the last error before I gave up in beagle.  The one that set me off after 25 minutes of trying to get it to work.  This error happens during the phase in the wiki where you do the automake install etc.... 
```
configure: error: Your mono installation doesn't expose gacutil
```
5.) Webcam service with something other than Gnomemeeting (I think 5 people still use it, hehe).  I searched and searched and finally found a program called Gyach-E. Ok name didn't sound promising but I gave it a try.  The 6 programs you have to install (that somehow equal the one program) went fine.  It needed a couple extra things, no prob, I synapticed them and away I went.
Now the program runs for 3 minutes (I timed it) and crashes.  The author offers NO support or anything, not even a forum.  I know they don't have to but it would have been nice.  So I got rid of it and kept looking.  Nothing.  So no webcamming my family and they don't understand why.  I'm to tired to explain it.  :(
6.) I've followed 6 HOWTOs on setting up a web server.  a few of them are right here on the forums.  I never got MySQL to cooperate.  I would set the password ala ubuntuguide.org and could never again get into it to create a database, no program could get MySQL liquored up enough to let it access it. 
So, here I sit. Trying to decide what to do.  I can't really get rid of Linux since I'm sort of stuck with it.  My first try with Ubuntu was dual boot Windows XP and Ubuntu, sadly now Windows will not install on the hard drive after I used the trick I found here on the forums to get dual booting working (Grub evilness) by switching the drive to LBA mode.  Now, only Linux will install on the drive no matter what I set it at in the BIOS.  LBA, Auto, etc...  I've tried everything.  Even zero fill utilities from Maxtor.  Windows will simply not load after the initial setup in the DOS type screen.  Once it reboots and tries to go into GUI mode, it says "Error loading Operating System".  Who the hell knows?  lol
So, I'm stuck until I get another hard drive but regardless if I could install windows or not.  I just don't want to give up on Linux.  I don't mind fighting to get things to work.  Hell I did that all the time in WindowsXP but at the same time I wasn't trying to install things that took 50000 different dependencies, all a different version.
Maybe I could just leave this drive for Linux and use the new drive for Windows and swap the ide cables when I want to use one.  Then I guess I could continue my frustration with both OSs.  :)
Anyhow, I hope this doesn't get deleted or something and I hope I posted this in the right place. If I didn't, I'm sorry mods.
Well, thanks for reading.  I'm pretty chilled now.  Please also know that I wasn't trying to flame Linux, I just really needed to vent my frustrations.  But I suppose if you really want to let me have it, I can't stop you.  :)

---

### Post by bored2k on 2005-03-09
"Welcome to the real world, Neo."

NTFS reading
> 2.) Have never gotten this to work ever. Ubuntuguide had a way to do it for reading the windows directory but I just can't seem to figure out how to do it across drives I guess. 

Let's try and clarify a little bit this step [as seen on ubuntuguide.org]

First of all, open  a terminal window [alt f2 > gnome-terminal is one of the dozens of ways].
> $ fdisk -l
This will show you several useful information:
a. The partitions read by Linux [mounted and unmounted]
b. They're location on /dev/
c. The type of filesystem of them.

So let's say you got this:
> Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *       21676       67186    22937544    c  NTFS -or whatever shows-
/dev/hda2               1       21675    10924168+   5  Extended
/dev/hda3           67187       77545     5220936   83  Linux
/dev/hda5               1         670      337302   82  Linux swap
/dev/hda6             670       21675    10586803+  83  Linux

We can clearly see a NTFS partition type mounted on /dev/hda1 right ? Yes we do, look again .

So know we need to stablish a mount point, but the dir of the mount has to be previously created . So I want to mount my NTFS part. in /winsux/

I first create the dir by > $ sudo mkdir /winsux/
Then I input [if I want read support for every user] >   $ sudo mount /dev/hda1 /winsux -t ntfs -o umask=0222 and that should be it .

---

### Post by bored2k on 2005-03-09
"Windows games under Linux"
> 
3.) Never happened. In fact I somehow screwed up my Ubuntu trying. Hell I can't even get simple old Wine to work to run notepad if I wanted too.

This is more or less [depending on the game] a real pain at times. The best way to do this as you should know is by acquiring a version of Wine tweaked for gaming called Cedega, wich is non-free [not the version you would want at least]. 

You can get for free the CVS version of this application but It is at times difficult to install, and you need a those of luck to get this working . *If the developer's the day you download it left in a unusable state and such [most of the time as it is currently being developed -just released version 4.3], you will have problems running these.

My suggestion - Get Cedega non-free . How ? I don't know. Can you get for free on the web ? I don't know *rolls eyes*.

If you ever get wine or cedega or crossover to work, they all work the same: get you're .exe file, and in a terminal window type cedega [or wine] game_name.exe and it will do its thing.


Linux-gamers.net for more information (they have a lot of info, but its mostly for tweaks AFTER you install the game :\).


**Edit**: If you still want to give Cedega CVS  a try, visit [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45) for the how to.

I currently play Steam Powered games through Cedega -non free, and I am very satisfied with it [Counter-Strikes rocks!].

**Edit 2 **: If you do get Cedega, be sure to place [msvcr70.dll](http://www.dll-files.com/dllindex/dll-files.shtml?msvcr70) in the fake window's /windows/system32/ and you're M$ fonts in /windows/fonts, this will avoid certain little bugs like CounterStrike needing that dll and Steam application needing its native fonts to run correctly.

---

### Post by jdodson on 2005-03-09
first off, welcome to the world of GNU.  second off i don't want to discourage you in any way, but much of what you want to do is non-trivial to get workingin gnu/linux.  to be honest, some of the things you want just won't happen, but some will.

[QUOTE=Phosphoros]
1.) Got DVDs working pretty good with Ubuntuguide.org and some help from people on this forum (searching and finding answers mainly).  This pretty much applies to multimedia in general.  Worked out pretty well.[/QUOTE]

i experienced the same things you have.  dvd playback works well.  i almost always watch dvds on my t.v. so for me this is not a huge setback.  there are a few player programs you could try, VLC, totem-xine, gxine, xine, mplayer(console program).

[QUOTE=Phosphoros]2.) Have never gotten this to work ever.  Ubuntuguide had a way to do it for reading the windows directory but I just can't seem to figure out how to do it **across** drives I guess.[/QUOTE]

you can read NTFS drives.  but natively you can not write to NTFS drives.  this has to do with the filesystem, etc.  check captive NTFS, that project may be of help if you want to write to a NTFS drive.  the problem here is windows lack of open specifications, it hurts us all.
 
[QUOTE=Phosphoros]3.) Never happened.  In fact I somehow screwed up my Ubuntu trying.  Hell I can't even get simple old Wine to work to run notepad if I wanted too.[/QUOTE]

what kind of video card are you running?  did you get the drivers setup right?  what is your glxgears FPS numbers?  what games are you trying to run?  did you try cedega?

[QUOTE=Phosphoros]4.) For the most part this is simple because Synaptic/sudo apt-get does all the work for me and I like that.  But as I noted in the beginning.  I'm pretty erked right now because of one of these programs.  Beagle.  Great program I'm sure but no thanks on the dependency hell.  I went through the wiki guide, several posts on it, Googled it, blah blah blah, but No matter how many thing I install that it depends on it will not ./configure.  This isn't the first program either to do this to me.  Several have done this junk to me when I have to ./configure make .  This is broken or isn't there, now that's not there, on and on and on.  This happens every single time I try and make something from source. :(
I'm sure many of you are sitting here wondering just how stupid I could be? Sadly I'm not, honest.  I'm the person all my friends come to to fix *their* computer problems.  I'm really not this dumb or perhaps it's this dependency stuff that's getting dumb?  I vote dependency hell.
Just for reference here is the last error before I gave up in beagle.  The one that set me off after 25 minutes of trying to get it to work.  This error happens during the phase in the wiki where you do the automake install etc.... 
```
configure: error: Your mono installation doesn't expose gacutil
```
5.) Webcam service with something other than Gnomemeeting (I think 5 people still use it, hehe).  I searched and searched and finally found a program called Gyach-E. Ok name didn't sound promising but I gave it a try.  The 6 programs you have to install (that somehow equal the one program) went fine.  It needed a couple extra things, no prob, I synapticed them and away I went.
Now the program runs for 3 minutes (I timed it) and crashes.  The author offers NO support or anything, not even a forum.  I know they don't have to but it would have been nice.  So I got rid of it and kept looking.  Nothing.  So no webcamming my family and they don't understand why.  I'm to tired to explain it.  :([/QUOTE]

some programs i gave up trying to install in ubuntu.  i get most things to run, but sometimes installing a program is just not worth the time it takes.  that is just at times the nature of using gnu/linux.  if you are not comfortable tracking down dependicies, you might not be able to get everything to work.  i have only had non-success with a few programs i really did not need to run anyway.  i don't mean to invalidate your feelings or anything, but it might not be worth the hassle.  i think hoary(the next version of ubuntu) installs beagle easier via synaptic than warty, or at least that is what i heard.

[QUOTE=Phosphoros]6.) I've followed 6 HOWTOs on setting up a web server.  a few of them are right here on the forums.  I never got MySQL to cooperate.  I would set the password ala ubuntuguide.org and could never again get into it to create a database, no program could get MySQL liquored up enough to let it access it.[/QUOTE]

installing apache2/php and mysql is one thing.  getting them to work is something totally different.  i would suggest running the mysql client as sudo or root and setting up a user as the mysql guide states, the grant syntax.  allow the user adequate access to create databases.  read the mysql docs, they are very helpful.

[QUOTE=Phosphoros]So, here I sit. Trying to decide what to do.  I can't really get rid of Linux since I'm sort of stuck with it.  My first try with Ubuntu was dual boot Windows XP and Ubuntu, sadly now Windows will not install on the hard drive after I used the trick I found here on the forums to get dual booting working (Grub evilness) by switching the drive to LBA mode.  Now, only Linux will install on the drive no matter what I set it at in the BIOS.  LBA, Auto, etc...  I've tried everything.  Even zero fill utilities from Maxtor.  Windows will simply not load after the initial setup in the DOS type screen.  Once it reboots and tries to go into GUI mode, it says "Error loading Operating System".  Who the hell knows?  lol
So, I'm stuck until I get another hard drive but regardless if I could install windows or not.  I just don't want to give up on Linux.  I don't mind fighting to get things to work.  Hell I did that all the time in WindowsXP but at the same time I wasn't trying to install things that took 50000 different dependencies, all a different version.
Maybe I could just leave this drive for Linux and use the new drive for Windows and swap the ide cables when I want to use one.  Then I guess I could continue my frustration with both OSs.  :)
Anyhow, I hope this doesn't get deleted or something and I hope I posted this in the right place. If I didn't, I'm sorry mods.
Well, thanks for reading.  I'm pretty chilled now.  Please also know that I wasn't trying to flame Linux, I just really needed to vent my frustrations.  But I suppose if you really want to let me have it, I can't stop you.  :)[/QUOTE]

yeah, i have heard of people having the dual boot problems like you are having.  i really can't offer any help as i don't run windows xp.  keep hacking, i am sure there is a way to get win xp booting for you again.  i would recommend to do things in waves.  first off install ubuntu and get used to the desktop, how things feel, surf pages.  then in a week or so do something on your list, like dvd playback.  find the best program you like and use that.  then keep doing things.  i think people get all in a tizzy because they make a huge all at once switch.  this leaves most people frustrated and eventually they switch back.  change takes time, i started by replacing all my XP programs with free alternatives, like firefox, openoffice, gaim, vi, etc.  so the switch was not that bad.  albiet it was tough initially, it got much easier than the all at once switch.  anyways, keep hacking, the next time you install things it will be easier, and keep getting easier as time goes on.

---

### Post by TravisNewman on 2005-03-09
OK I don't really have much time to go into any detail, but a few points.

Reading NTFS partitions: what problems are you having exactly? Whenever I want to access an NTFS partition I just "mount /dev/hdb1 /windows" and I can access everything. Not saying it MUST work that way for you-- I've had plenty of oddball problems that nobody else has.

Windows Games: You sure your video drivers are installed correctly? I doubt it has much to do with that, since you can't even get notepad to work. This could be a wine specific issue. You should try Cedega if you haven't. It uses it's own Wine installation, so any problems with your current one won't affect it.

Software Installation: about a year ago I had NO freakin' clue what I was doing wrong. I could only get about 3-5% of the ./configure scripts to run and then only about half of them would successfully compile and install. It just takes a bit of learning. Do it, over and over, whenever you find problems try to find the answer to that specific problem, move on to the next part. You'll soon be compiling with the big boys ;) I just compiled wxMusik from source, and a year ago I thought I could NEVER do that. Weird dependency issues. I'd suggest Linux From Scratch. I've only set up a very basic system, but you'll learn a lot.

Web Server: have you tried just apt-getting Apache, MySQL, and PHP? If yes, and they still didn't work, I'd try the XAMPP install script from here: [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")
Very easy to use.

As far as Windows not installing on that drive properly, I don't get that-- are you sure the drive is set up as a master on the primary IDE? That's something I'd like to play with in person ;)

If you do get a new drive:
I have windows on the first partition of my second drive, and linux (about 5 distributions, and FreeBSD and Solaris-- I've been experimenting a lot) on my first drive. You DON'T need to swap out any ide cables after everything is installed. Set your Windows drive up as the master, don't even put in the linux drive. Install Windows. Shut down. Move the Windows drive to slave, put in the Linux drive as master, install Linux. Now here's the key. Change your /boot/grub/menu.lst so that the windows entry looks like this:

```

title         "Windows XP" # or whatever version you have
map (hd0) (hd1)             # These lines make Windows think that it is 
map (hd1) (hd0)             # installed on the master drive.
rootnoverify (hd1,0)       # assuming your windows partition is the first partition 
                                       # of the second drive
makeactive
chainloader +1

```

---

### Post by bored2k on 2005-03-09
[QUOTE=Phosphoros]  Now, only Linux will install on the drive no matter what I set it at in the BIOS.  LBA, Auto, etc...  I've tried everything.  Even zero fill utilities from Maxtor.  Windows will simply not load after the initial setup in the DOS type screen.  Once it reboots and tries to go into GUI mode, it says "Error loading Operating System".  Who the hell knows?  lol
[/QUOTE]


I have had that problem about ... a gazillion times now as my drive got more or less crappy after several power failures [the fatal one during an AuroX 10beta install *that night I almost had a hard attack... I had just bought my "Noir" computer :(].

Here is how I -mostly always- get it to install again [For my brothers not me ! :$] :

I load up Hiren's Boot CD v6 [don't ask where to get it] and open the tool "MBR Tool", wich can be found for boot disks for free on the net, I whipe my mbr to zero.

If I suspect something fishy about my drive: with a bootable tool disk like the one Norton has to check disks [forgot the name, it think it's Rescue] I have it checked.

If i suspect even more crappiness, I check the drive through HDD Regenerator [free tool also included on Hiren's but easily downloadable for diskette].

I load a bootable partitioner, or you could use qtparted from Linux [unmounted NTFS drive of course] and erase the partition and let Windows format it. I have also noticed XP does not like to be something extended or like [hda5] or so, so I always try to make it hda1 or the closest .

*These are the many ways I fight XP suckyness @ install time, they eventually work.*

---

### Post by bored2k on 2005-03-09
That's some **thick**  quick replies lol .

---

### Post by Phosphoros on 2005-03-09
Holy cow guys.  That was more info than I've ever gotten.

I see a matrix reference in there.  BLEH!  hehe

I'm going to take a bit and go through all these replies but I want to thank you all for taking the time to pour out the info.  I'll answer the questions after I've gone through everything.

You guys are great.  :)

---

### Post by kassetra on 2005-03-09
[QUOTE=Phosphoros]Holy cow guys.  That was more info than I've ever gotten.

I see a matrix reference in there.  BLEH!  hehe

I'm going to take a bit and go through all these replies but I want to thank you all for taking the time to pour out the info. I'll answer the questions after I've gone through everything.

You guys are great.  :)[/QUOTE]

We really try to help everyone.  :)  Next time, why don't you ask us before you get frustrated?  That might save you some grief.  :)

---

### Post by gw90se on 2005-03-09
I know the feeling sometimes. Learning something completely new can be a heck of a curve.  Fortunately for me, I am not a gamer, so I don't have to deal with those issues. I actually run 2 computers through a KVM switch, so I keep Linux up and running and just turn on the MS machine if I need it.

---

### Post by Phosphoros on 2005-03-09
**Kassetra**,
Well I had asked about Gyach-e.
I found all the info on DVD/Multimedia via search here.
The stuff with the MySQL and general webserver questions I drowned in results from the search engine.  I thought my head would explode so I just stepped away.
On the hard drive issue, again search turned up a few things that I tried.  But still, my Maxtor is possessed or it just really loves Ubuntu.
I guess I just didn't want to look like a doofus and ontop of that the Ubuntu forums are growing pretty fast.  I just thought I'd try and do it on my own and google and searching here.  I guess I just really needed to vent.  Apologies. 

**bored2k**,
Thanks for all the info on mounting my NTFS hard drive (There's a mental imagine).  I will definately give that a try.
Thanks for the Cedega tips.
Also, I have Hiren's boot disk, but it's all in german or something  Perhaps I got the wrong version.  I also used a knoppix 3.7 cd to QTparted the drive, making sure of course it wasn't mounted.  Still a no go.  I'll try your other tips, but that means wiping out my Ubuntu, so maybe I'll try it or maybe I'll just get the second hard drive and say "PFFT!".  :)

**jdodson**
Ya, DVDs play just great now after some extra tinkering on my part.  I have just about every single DVD player out there (that could be installed Via synaptic or was DL-able and was a .deb) so I have a wide variety of choices.  Only disk that won't play on my system is Aliens vs. Predator.  It just quits after the 20th Century Fox logo.  Oh well.  No big loss really.
As to NTFS drives, I understand the no writing to NTFS and that's fine. I can imagine the nightmare that would be if you could.  I just want my Gigs of Mp3's and Gigs of wallpapers and my tons of Docs and PDFs.  Hopefully with the tips I got here today that will be a reality soon!  

My Video card is a Leadtek Geforce FX 5900XT.
My fram rates are 
```
22391 frames in 5.0 seconds = 4478.200 FPS
22138 frames in 5.0 seconds = 4427.600 FPS

```
The only games I'm really interested in playing at the moment are Star Wars:Knights of the Old republic and KOTOR2 when it comes out (Perhaps it's out now).  I was playing World of Warcraft but got bored silly waiting for their servers to behave and cancelled.  On a positive note I did get Quake3 and Enemy territory running no problem but that was all the installers.  Couldn't get GTKRadiant running though but my mapping days are pretty much over until a game worth mapping for comes out.
Also, I ahven't tried Cedega.  Well, I *tried* but it wasn't happy.  I just sort of backed away slowly from my computer and had a cookie.  Seemed safer. 

**PanickedThumb**
Is this the same panickedthumb from the Desktopsidebar forums? :)
Thank you for the tip and code on grub and running two drives.  That will help immensely.  
Yep, Drive is master, everything is setup correctly.  I'm not sure if Windows is seeing it right though since it's erroring loading the Winxp GUI install.  Obviously something is funky I'm just not sure what it is anymore.  I've done jsut about everything I can dream up.
I may give the web server dealy another try later today.  Just apt get and see how things go, I was jsut having so many permission issues and maybe I'm thick or something but there documentation is like reading a manual on astrophysics.  Unless you get it, you don't.
The software installation thing is more than likely me.  Being a newb and not understand half the junk I'm pasting into gnome-term in most of these HOWTOs it can be hard getting a handle on what to do when.  But I remember my first week with Windows 95 and my dialup modem.  *shudder* 

Again thank you for all the info and thanks for taking my little Linux Break-down(tm) in stride.
This is a great community for sure.  I promise, this won't happen again.  I'll just ask my questions without a fit.  HONEST!  :)

---

### Post by Phosphoros on 2005-03-09
[QUOTE=gw90se]I know the feeling sometimes. Learning something completely new can be a heck of a curve.  Fortunately for me, I am not a gamer, so I don't have to deal with those issues. I actually run 2 computers through a KVM switch, so I keep Linux up and running and just turn on the MS machine if I need it.[/QUOTE]


That sounds like a cool idea.  Erm... what's a KVM switch if I may ask?

---

### Post by bored2k on 2005-03-09
Didn't i email you a hirens download link ??? i thought i did

---

### Post by TravisNewman on 2005-03-09
Keyboard/Video/Monitor
Basically, you can use the same Keyboard, Video, and Monitor on multiple PCs. I use one myself, though I just use the monitor part of it because Linux doesn't get along well with it.

---

### Post by TravisNewman on 2005-03-09
> Is this the same panickedthumb from the Desktopsidebar forums? 
I'm sure you mean Codename: Dashboard ;) But yes, that's me! I'm getting famous! I haven't actually been to those forums in quite a while. Things started dying down, and there wasn't much going on. I think I'll go see what they've been up to while I've been gone!

---

### Post by Phosphoros on 2005-03-09
[QUOTE=panickedthumb]Keyboard/Video/Monitor[/QUOTE]


Boy, I feel silly now.

---

### Post by bored2k on 2005-03-09
[QUOTE=Phosphoros]Boy, I feel silly now.[/QUOTE]
 So did you ever get anything working?

---

### Post by jdodson on 2005-03-09
[QUOTE=Phosphoros]
**jdodson**
Ya, DVDs play just great now after some extra tinkering on my part.  I have just about every single DVD player out there (that could be installed Via synaptic or was DL-able and was a .deb) so I have a wide variety of choices.[/QUOTE]

good.

[QUOTE=Phosphoros]Only disk that won't play on my system is Aliens vs. Predator.  It just quits after the 20th Century Fox logo.  Oh well.  No big loss really.[/QUOTE]

have not tried that one.  the games i run in cedega are starcraft, war3 and halflife2.  as far as anything else, i am not sure.

[QUOTE=Phosphoros]As to NTFS drives, I understand the no writing to NTFS and that's fine. I can imagine the nightmare that would be if you could.  I just want my Gigs of Mp3's and Gigs of wallpapers and my tons of Docs and PDFs.  Hopefully with the tips I got here today that will be a reality soon![/QUOTE]

yeah i hope so too.  i have a friend who was able to get it working, not sure what was diffrent in both your setups though.  ubuntuguide seemed to work well for him.

[QUOTE=Phosphoros]My Video card is a Leadtek Geforce FX 5900XT.
My fram rates are 
```
22391 frames in 5.0 seconds = 4478.200 FPS
22138 frames in 5.0 seconds = 4427.600 FPS

```[/QUOTE]

our cards are pretty similar, i have a chaintech and get the same FPS glxgear results.  you seem to have that end setup fine.  congratulations, most people can not get that far.

[QUOTE=Phosphoros]The only games I'm really interested in playing at the moment are Star Wars:Knights of the Old republic and KOTOR2 when it comes out (Perhaps it's out now).  I was playing World of Warcraft but got bored silly waiting for their servers to behave and cancelled.  On a positive note I did get Quake3 and Enemy territory running no problem but that was all the installers.[/QUOTE]

KOTOR2 has been released for awhile now.  i "heard" that KOTOR works in cedega, but take it as hersay, i have no actual knowledge if it does or not.

[QUOTE=Phosphoros]
Also, I ahven't tried Cedega.  Well, I *tried* but it wasn't happy.  I just sort of backed away slowly from my computer and had a cookie.  Seemed safer. [/QUOTE]

HA!  yeah it would be.  but if you want windows games to work in gnu/linux it is the best option available, albiet not a very fun one.

---

### Post by bigzak on 2005-03-10
[QUOTE=panickedthumb]Keyboard/Video/Monitor[/QUOTE]

I thought it was Keyboard/Video/Mouse, as most have two PS/2 ports?

---

### Post by Slapdash on 2005-03-10
Can I also use this thread to post a question please ;)
How,... when I have mounted my NTFS drive in make shortcut or quicklaunch so that I dont have to type/ mount it all over again each time I reboot?

---

### Post by bored2k on 2005-03-10
> **Slapdash]Can I also use this thread to post a question please  said:**
> 
 I created a script that does just that for my system.

a. The drive I want to mount is in /dev/hda1 [if not, you just change values]
b. The mount point needs to be already created [/media/windows]

1. I create a text file with the name mount.sh [the .sh extension will make it better for reading purposes on text editors - colors for commands, etc.], wich will contain these values
> #!/bin/sh
sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222

2. I save the file [duh!].

3. Make it executable for every user, by typing
[QUOTE]sudo chmod 777 mount.sh

Now you just have to > sh mount.sh from now on and it works.
You can create a shortcut that has the sh mount.sh command, but notice I need sudo, so you wouldva have to have your computer run sudo commands with no passwd for this [not safe] .


[CENTER]**Edit**[/CENTER] 
You can also have it automount without typing any commands by [as root, or sudo] modifying  /etc/fstab [text file] and adding the following line at the end:
>  /dev/hda1       /media/windows    ntfs    umask=0222      0       0

---

### Post by gw90se on 2005-03-10
[QUOTE=bigzak]I thought it was Keyboard/Video/Mouse, as most have two PS/2 ports?[/QUOTE]

You beat me to it :) 

I don't have any problem with my KVM, but I do use PS2 devices, not USB.

---

### Post by bored2k on 2005-03-10
[QUOTE=jdodson]KOTOR2 has been released for awhile now.  i "heard" that KOTOR works in cedega, but take it as hersay, i have no actual knowledge if it does or not.[/QUOTE]
Here's some of the things the man page of my spankin' new  :smile: Cedega :smile:  4.3 has to say:
>  Cedega 4.3 - Released March 8, 2005.
New Features
Cedega 4.3

       · TransGamers can now enjoy playing Star Wars Battlefront, [b]Star Wars
       Knights of the Old Republic II: The Sith Lords[/b], and Sid Meier's
       Pirates! Live the Life.

Other changes involve mostly fixes for Half-Life 2, World of Warcraft, BF 1942, Painkiller, EVE Online, SW: Galaxies, Anarchy Online, Civilization III.

---

### Post by TravisNewman on 2005-03-10
D'oh, I meant Keyboard, Video, Mouse. I just typed incorrectly.

And I also use PS2, but it still freaks out my keyboard. Mouse is fine though

---

### Post by Phosphoros on 2005-03-10
[QUOTE=bored2k] Cedega 4.3 - Released March 8, 2005.
New Features
Cedega 4.3

· TransGamers can now enjoy playing Star Wars Battlefront, Star Wars
Knights of the Old Republic II: The Sith Lords, and Sid Meier's
Pirates! Live the Life.[/QUOTE]

Woohoo!  I haven't purchased KOTOR2 or even Half-life 2 yet but I heard good things about HL2.  
I love the Battlefield series, I still think BF1942 is better than Vietnam.  EoD for BF1942 was awesome.
Warcraft bored me to tears as do most MMOs after about 3 months.  Sadly I spent years in EQ.  I have no intention of buying another soe product though.  lol

I haven't really looked at Cedega subscription pricing and I think you have to go througha  reg process to see it.  How much is it?  Is it easier to setup if you buy the thing?

---

### Post by bored2k on 2005-03-10
[QUOTE=Phosphoros]Woohoo!  I haven't purchased KOTOR2 or even Half-life 2 yet but I heard good things about HL2.  
I love the Battlefield series, I still think BF1942 is better than Vietnam.  EoD for BF1942 was awesome.
Warcraft bored me to tears as do most MMOs after about 3 months.  Sadly I spent years in EQ.  I have no intention of buying another soe product though.  lol

I haven't really looked at Cedega subscription pricing and I think you have to go througha  reg process to see it.  How much is it?  Is it easier to setup if you buy the thing?[/QUOTE]
 The "thing" is quite easy, you just install it like a normal Debian file.

Monthly subscription is 5 bucks [minimum of 3months], wich gives you a Transgaming account and updates.
The mayor benefit here is [Point2Play](http://www.transgaming.com/), wich gives you a very  pretty GUI frontend for cedega, you just Point...and Play :D. If you are like me and do not want to pay month after month, you still get to use Cedega from terminal. Difference? nothing, you just "cedega game.exe" and install just like WinXP.

If you still don't wanna pay, may the *mule* be with you.

---

### Post by Phosphoros on 2005-03-10
Eeeeyaw!  hehe

Well, it sounds like it's worth it.  I did see a how to here but it had something with chroot 32-bit or whatever.  Was rather confusing so I figured the whole process was complicated.
Thanks for the info bored2k.  :)

Somehow I'd thought it was more expensive.

Time to get a subscription!

---

### Post by TravisNewman on 2005-03-10
If there was a chroot 32-bit involved, it was probably for installing it on Ubuntu for AMD64.

You CAN download builds of Cedega that have been built from their CVS for nothing, and it's not illegal. And you never have to pay. That's what I did and I haven't had any problems. I think the paid version includes something proprietary, but I'm not sure.

---

### Post by bored2k on 2005-03-11
[QUOTE=panickedthumb]If there was a chroot 32-bit involved, it was probably for installing it on Ubuntu for AMD64.

You CAN download builds of Cedega that have been built from their CVS for nothing, and it's not illegal. And you never have to pay. That's what I did and I haven't had any problems. I think the paid version includes something proprietary, but I'm not sure.[/QUOTE]
 It includes Point2Play, wich is a crappy GUI frontend to cedega, its mostly useless, only thing useful is that it has a button to download M$ fonts to the games, wich you can do manually or one of the .gz found -somewhere- ;) .

---

### Post by Phosphoros on 2005-03-11
```
sudo apt-get install msttcorefonts
```

That what your talking about?

---

### Post by bored2k on 2005-03-11
[QUOTE=Phosphoros]```
sudo apt-get install msttcorefonts
```

That what your talking about?[/QUOTE]
 Yes, after downloading that you can just copy the fonts from /usr/share/fonts/truetype/msttcorefonts/ to your cedega fake drive [Transgaming_drive/windows/fonts/] or .transgaming_global/fonts.

---

### Post by Slapdash on 2005-03-11
[QUOTE=bored2k]I created a script that does just that for my system.

a. The drive I want to mount is in /dev/hda1 [if not, you just change values]
b. The mount point needs to be already created [/media/windows]

1. I create a text file with the name mount.sh [the .sh extension will make it better for reading purposes on text editors - colors for commands, etc.], wich will contain these values


2. I save the file [duh!].

3. Make it executable for every user, by typing


Now you just have to  from now on and it works.
You can create a shortcut that has the sh mount.sh command, but notice I need sudo, so you wouldva have to have your computer run sudo commands with no passwd for this [not safe] .


[CENTER]**Edit**[/CENTER] 
You can also have it automount without typing any commands by [as root, or sudo] modifying  /etc/fstab [text file] and adding the following line at the end:[/QUOTE]



THanks A lot bored2K!! I'll try that this weekend.

---

