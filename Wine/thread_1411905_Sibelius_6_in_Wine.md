---
title: "Sibelius 6 in Wine?"
date: 2010-02-20
forum: Wine
---

### Post by Wataru8675 on 2010-02-20
Hi everyone,

I've been aiming to buy Sibelius 6 Student edition sometime soon (since, 1) It's the standard in my Uni, which would make exchanging scores and following others' instructions on how to do things easier and 2) the GNU programs I've tried are simply too unstable for me to be productive with them) but I'd really like to do it on Ubuntu.  The only posts I've seen for Sibelius are ages old (4 years in some cases), so I was wondering if anything's changed that would make it more fluent to use.

I tried downloading the trial just now and get two errors:  "Error 150021 (ERR_AUTH_REGTOOL_CANT_ACCESS_PIPE)" and when I click OK it says, "There was a problem with file permissions.  Are you logged in as administrator?"

Is there any conceivable way around this/to fix this, or am I pretty much SOL on running Sibelius for Ubuntu?

---

### Post by Wataru8675 on 2010-02-22
Bump just in case...

---

### Post by capillotraktor on 2010-03-07
Hi,

The good news first: you are not alone! lol. I'm pretty much in the same situation as you, I do like 90% of what I need to do with Ubuntu but i do need to run Sibelius as it's the de facto standard in my school. The bad news is, I've found no workaround til now. MuseScore is good but not as good as Sibelius (and not compatible), and Sibelius doesn't work with Wine as you've experienced, plus there seems to be no will from Avid nor the Linux community to make up a working port. So i've found myself forced to go back to Windows on my main machine (which actually is not so painful right now, they really did a very good job on Win7, especially compared to Vista), and since I still need a Linux for everything Windows can't seriouly take (like messing with filesystems, etc.) I've set up a second computer with Ubuntu on it.
Well I'm still waiting for a better solution, so if anyone knows about something...

;)

---

### Post by Beowulf.1000 on 2010-03-08
I have Sibelius 6 working well (but only with Sibelius essential sounds so far, have not tried installing Garritan Personal Orchestra that I have on a separate DVD) in Ubuntu 9.10, loads and plays nice.

I am not using Wine. I installed (synaptic package manager) virtualbox and then installed a virtual Windows XP from a legal CD I have of Windows XP. (I suspect Vista might also work). Then Sibelius 6 and also Sibelilus Essential Sounds both  installed nicely.

I feel your pain. Sibelius, and my screenwriting software (Movie Magic Screenwriter), were two apps keeping me booting into Windows. Now I am quite happy knowing I will not have to boot into Windows so much! (Movie Magic Screenwriter 6 also installed nicely using virtualbox and even did the license validation and version update without problems)

If I can be any help helping anybody do what I did just holler.
 Beowulf

---

### Post by asdfoo on 2010-03-09
> **Wataru8675 said:**
> Hi everyone,

I've been aiming to buy Sibelius 6 Student edition sometime soon (since, 1) It's the standard in my Uni, which would make exchanging scores and following others' instructions on how to do things easier and 2) the GNU programs I've tried are simply too unstable for me to be productive with them) but I'd really like to do it on Ubuntu.  The only posts I've seen for Sibelius are ages old (4 years in some cases), so I was wondering if anything's changed that would make it more fluent to use.

I tried downloading the trial just now and get two errors:  "Error 150021 (ERR_AUTH_REGTOOL_CANT_ACCESS_PIPE)" and when I click OK it says, "There was a problem with file permissions.  Are you logged in as administrator?"

Is there any conceivable way around this/to fix this, or am I pretty much SOL on running Sibelius for Ubuntu?


Which version of Wine did you try?  You may need to use a beta/development release.

---

### Post by fire_lock on 2010-12-12
Same problem here... And no, it's not from the wine version - it just don't run. I'm a musician and I need it, so I tried everything (including running it as root from terminal - now my wine runs only from terminal - don't know how to fix =_=). The good news is - Sibelius 6 DEMO runs more than OK. I suspect it's because it doesn't need to access the registry. However, if you try to install the full version you'll always get an error message after install. You'll always get "There was a problem with file permissions. Are you logged in as an administrator?" (and I get this after running it with sudo wine "/the/path/to/sibelius.exe")
Well - if it's somehow useful - here's what bash says:
> 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4f4,0x00000000), stub!


---

### Post by fire_lock on 2010-12-17
I'm sorry to double post, but is this thread dead? Because I follow it with great interest - I need this Sibelius 6 in Linux, without having to use virtualbox - after all - my netbook won't take it (it's ASUS EeePC 901a with 12 GB HDD). Besides - I don't want to deal with micro$oft anymore, at least on my netbook. For the desktop PC - I have no choice - but for this thing... Well, you get the idea :)
So, anyone? Any news? Someone else with the same problem? Some clever tricks? Anything! Just don't kill the topic! :D

---

### Post by gacb on 2011-01-24
Now that I'm used to MuseScore, I wouldn't go back to Finale or Sibelius. I find it easier to work with, and can import/export more formats.

If the makers of Sibelius, Finale and other for profit enterprises were a bit more farsighted, they would make exporting to XML/MusicXML/Lilypond less painful.

---

### Post by mathiaho on 2011-01-28
Hi

I am also a sibelius user.

I have tried to make Sibelius 6 work under wine, but I haven't been successful. I think sib 6 is not possible under wine in its current state. 

Sibelius 5, on the other hand, works great. If you're interested, I've made an how-to. Just search for "sibelius 5" in this forum.

You could of course use virtualbox. Just know that virtualbox is a virtual computer inside your computer, on which you can install any OS, including windows.You will need a windows license (unless you pirate).

If you use virtualbox, you won't be windows-free :P

I hope this helps.

And, oh, if anyone gets sibelius 6 to work under wine, please show us how!

---

### Post by baekgaard on 2011-01-29
Hm... haven't tested it extensively here, but I got the demo version running (latest 6.x, just downloaded today). Sound isn't working out-of-the box but there can be many reasons for that -- I think that could be a peculiarity of my setup.

Download winetricks first. Run it and try to install dmsynth, dsound and dotnet20. They may not all be required, but this is what I did.

I had one hang/crash of Sibelius trying to load a non-existent demo song or something, but I was able to create a score and enter some notes and chords etc.

Pls report back here also and on winehq, thanks.


-- Per.

---

### Post by mathiaho on 2011-02-10
Hey!

Very exciting, baekgaard! Have you tried installing wineasio? 

Take a look at this post:

[http://ubuntuforums.org/showthread.php?p=8341286#post8341286](http://ubuntuforums.org/showthread.php?p=8341286#post8341286)

That could take care of sound problems.

Normally I'm against pirating, but I guess it's OK to see if it works before you buy the software. Just in case there's a difference between the demo and the full version.

---

### Post by handy on 2011-02-10
I'll certainly be interested to see if anyone does get Sibelius.6 working using this info'. I certainly hope so as it will allow so many students (at least) to be able to do without Win/Mac.

---

### Post by gaboalonso on 2011-07-31
6 months later, i'm bumping this to see if anyone had had any luck running Sibelious.


Cheers!

-Gabe

---

### Post by mathiaho on 2011-07-31
Depends on the version you're trying to run.
Sibelius 5 works like a charm.
Sibelius 6, I don't know.

If you own Sibelius 6, try to install it, and report to winehq: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18415](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18415)

Good luck!

---

### Post by badmilbad on 2011-08-02
I have been running Sibelius 6 for more than 8 months. In wine, fully functional...

I realized that in order to pass this issue :

"Error 150021 (ERR_AUTH_REGTOOL_CANT_ACCESS_PIPE)" 
"There was a problem with file permissions.  Are you logged in  as administrator?" 

all you need to do is have Sibelius 5 installed. 

At least that work for me...

Right now I'm trying to make Sibelius 7 run.
 
Good luck...

---

### Post by ibs on 2011-08-30
badmilbad: I tried installing Sibelius 5 and then Sibelius 6. It didn't work for me. Could you explain in better detail how you made Sibelius 6 work? For example which extra packages or dll files you had to install by using winetrick s or something else.

---

### Post by badmilbad on 2011-09-05
I'm using the last Wine version set to Vista ('cause I'm trying to run Sibelius 7), but it firts worked with Xp. I installed Sibelius 5 following the steps listed in Wine's Appdb ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10843)). Once I made 5 run, I just installed Sibelius 6 on top it. 
Right now (Sibelius 6 working), I have the following packages installed trought Winetricks:
dotnet11
dotnet20
gdiplus
gecko120
vcrun2008

So I guess all the packages listed in HowTo are not really necessary.

Hope it works...

---

