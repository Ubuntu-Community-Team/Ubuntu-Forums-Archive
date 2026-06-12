---
title: "uTorrent : Process already running"
date: 2009-06-30
forum: Wine
---

### Post by Praxtreme on 2009-06-30
Hi,
I have installed uTorrent through wine, but after installation the following window pops up : It seems like uTorrent is already running but not responding. Please close all uTorrent applications and try again.
I am a new Ubuntu user and is clueless :(

---

### Post by Meow27 on 2009-06-30
clear what you have of utorrent 1.8.3

its a bug in the new version

download 1.8.2 here
[http://download.utorrent.com/1.8.2/utorrent.exe](http://download.utorrent.com/1.8.2/utorrent.exe)

---

### Post by BenAshton24 on 2009-06-30
Also, I don't know about the bug that Meow mentioned, you might be able to get round it by killing wine and then starting uTorrent again...
```
wineserver -k
```


Hope this helps, Ben.

---

### Post by Siix on 2009-06-30
You can also open a terminal:

type "su" followed by password.

type "top" and see if utorrent or wine are running. if they are press "q" to pause

type "kill" followed by the PID # on the left.

That should help.

By the way the built-in bittorrent client "transmission" isn't bad at all. Could save yourself a LOT of trouble.

---

### Post by Meow27 on 2009-06-30
nope 1.8.3 doesnt work with Wine not with 1.1.24

itl just start running in the background with no gui doing absolutely nothing but consuming memory.

again use 1.8.2. it works

---

### Post by Praxtreme on 2009-07-01
> **Meow27 said:**
> clear what you have of utorrent 1.8.3

its a bug in the new version

download 1.8.2 here
[http://download.utorrent.com/1.8.2/utorrent.exe](http://download.utorrent.com/1.8.2/utorrent.exe)

Thanks a lot for the quick response, 1.8.2 worked :p

---

### Post by mycelo on 2009-07-02
Or you might try Deluge, which is very similar to uTorrent and open-source, native to Linux.

By the way it's about time they port uTorrent to Linux.

---

### Post by Meow27 on 2009-07-02
> **mycelo said:**
> Or you might try Deluge, which is very similar to uTorrent and open-source, native to Linux.

By the way it's about time they port uTorrent to Linux.

if it works close to perfect with Wine, whats the point?

---

### Post by zemon_ on 2009-07-03
Is this a problem with wine or utorrent?

I was told from the utorrent forums that the installer is a bit buggy at the moment.

If its wine will the new version 1.1.25 fix the bug.

---

### Post by Meow27 on 2009-07-04
from the website
[http://www.winehq.org/announce/1.1.25](http://www.winehq.org/announce/1.1.25)

maybe, you can try, i hear a work around to getting it working is in this url


[http://blog.mymediasystem.net/uncategorized/utorrent-1-8-3-doesnt-install-on-linux-via-wine/](http://blog.mymediasystem.net/uncategorized/utorrent-1-8-3-doesnt-install-on-linux-via-wine/)

scroll down to the update and thats your workaround

---

### Post by WWWFOUR on 2009-07-27
[FONT=Calibri]**[COLOR=red][-X[-X [SIZE=4]"It seems like utorrent is already running but not responding"[/SIZE][/COLOR]**[/FONT]

 
[FONT=Calibri]**[SIZE=4][COLOR=red]:PI have found how to fix it!!![/COLOR][/SIZE]**[/FONT]
[FONT=Calibri]It was not as complicated as others made it **look**. Please bare with me I am going to say how to fix it, and what I did and how it worked for me, then long winded explanation to how I got into this mess shortly after so others don't make the same mistake I did. People in here have helped me with stuff, and now I wish to put in the time myself. Beware it will be like a book. A long winded, but not enough people are getting decent remedies to the situation at hand :0)[/FONT]
 
[FONT=Calibri]First off I have Windows Vista, however based on how I fixed it I don't think it matters if you have XP or even use a MAC instead of Windows. I have seen some hard core techy savvy people in here get into things with ports, settings, and even commands that still do not stop that annoying pop up or can but maybe it isn't necessary "it seems like Utorrent is already running, but not responding" routine. Basically utorrent later versions such as the 1.83 are the problem. Maybe a bug in that. Getting to the point and not skipping detail I did the following 3 steps. [/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][COLOR=red]**[SIZE=3]1.) I uninstalled utorrent 1.83 (*which I did many times but this was the order to my fix*) [/SIZE]**[/COLOR][/FONT]
[FONT=Calibri][COLOR=red]**[SIZE=3]2.) I downloaded freeware titled Registry Fix Pro 1.5....( *which took awhile to find because other freeware really wasn't free like they say for registry cleaners, and this surely was*) I scanned the registry through Registry Fix Pro 1.5, and then after scan I chose fix. This was 100% free, and it did the job. [/SIZE]**[/COLOR][/FONT]
[FONT=Calibri][COLOR=red]**[SIZE=3]3.) Then I googled Utorrent older version 1.7, downloaded that older version and now it works. The message is gone[/SIZE].**[/COLOR] [/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]If I went back to 1.83 I would have had the same issue, so don't do it. Do not change anything just load it like the default. The older version was cool, no more hey do you want the ask tool bar, and this and that routine. Now in my opinion, the later versions after 1.7 such a 1.83 have this bug to it screwing around with registry’s etc and maybe more, and it is something that according to my research does not stand out yet as a fix, or many saying they are not getting the support or feedback and it's a big problem with many. Or same problem occurs, this worked for me. I even downloaded that 1.9 version before I did the fix and that message showed up again, so you need to drop back ten and punt to old school 1.7 if you want it to work again with that message being gone.[/FONT]
 
[FONT=Calibri]Now that’s what you need and you can move on now if you want, but to how I got myself into this mess personally. Note that the later versions such as the utorrent 1.83 what I had logically worked for me. I just decided to get fancy and learn how to make my downloads faster, and 1.83 once downloaded or later stays embedded like a cancer in your computer. You make serious settings changes which that work for some, could be a nightmare for others. However where I went wrong was on looking up on YouTube in step by step how to speed up my downloads. I checked with comments on tutorial videos, and it was all this hey you’re the best, thanks, you rock, OMG you’re a master etc. Well I followed his every step without missing a detail trusting his comments on video made him appear as if he was the Messiah himself. He even had a 4 and a half star rating for the love of Pete. I should have never done it, it Fu(beep)cked everything up, after changing settings it started crash not responding mode. I could not even get in to my utorrent to fix it like other bloggers are like go into setting etc, WELL I CAN'T GET IN TO ANYTHING IN UTORRENT STUPID TO MAKE CHANGES. So if I had left it alone like it was I would not have run into these problems. Apparently others could do it, its just with registries etc you never know, it can work great for some and put others at risk. Also in this YouTube video he says if this does not work for some, don't worry just uninstall utorrent and download again. WRONG! This guy was so wrong on saying that for it is far from the truth. The later versions just dig itself so far into your computer with that bug, the message "it seems like utorrent is already running, but not responding". I uninstalled it 5 times maybe with following tips from these blogs and it didn't do it for me. So finally, in order for it to work I went with utorrent 1.7. Now they do ask if I want to upgrade to 1.83, and maybe I can without a problem but I have not been brave enough to press the yes key as of yet. If anyone after these steps went yes to upgrade and problem was still gone by doing 1.7 first I would like to know if you had success or not. [/FONT]
 
[FONT=Calibri]Anyway, happy downloading.[/FONT]

---

### Post by wingnux on 2009-07-27
Wow, so much trouble when there are TONS of excellent native bittorrent clients!

---

### Post by vinutux on 2009-07-27
using native apps like deluge is more better than a wined app...try deluge instead of wined utottrent

```
sudo apt-get install deluge
```

---

### Post by zemon_ on 2009-07-27
Its easy put settings.dat in the same directory as utorrent.exe

---

### Post by hansamurai on 2009-07-28
I'm able to install 1.8.2 and then update to 1.8.3 without any problems.

---

### Post by silver1499 on 2009-11-01
Download links like this:

[http://download.utorrent.com/1.8.2/utorrent.exe](http://download.utorrent.com/1.8.2/utorrent.exe)

ended up giving me the latest uTorrent client... So if you think yours isn't working, make sure you're installing the actual 1.8.2 client. I googled around and found an actual 1.8.2 client, which ran fine with Wine first shot. 

Tried forever to get Deluge to work for me, but never could get RSS up and running. And I kept having to manually kill it every now and then, which was a pain. 

Transmission is definitely good, again no RSS though. 

I'm as much for open, free software as the next guy, but uTorrent does have other clients beat on features and ease of use (even running through wine). I'm certainly always open for suggestions though.

---

### Post by jaja23bd on 2009-11-02
well i have to install utorrent as some stupid trackers only allowed uTorrent. 
regards

---

### Post by dkerlee on 2009-11-18
I remember looking at this thread and having those problems. This is what works for Ubuntu 9.10 and utorrent 1.8.5.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113)

The the 1.8.5 release is again plagued by the install bug (after installation when you run the program it will either prompt for install again or give an error that utorrent is already running etc. The easiest way to run around this is to update your desktop link files / shortcuts to 'Exec=env WINEPREFIX="/home/mycomputer/.wine" wine "C:\\Program Files\\uTorrent\\uTorrent.exe" /NOINSTALL' or similar. Just include the "/NOINSTALL" option in link or command line argument.

When he says "update your desktop link files" he means, right click on the desktop, create launcher, call it utorrent, paste
```
env WINEPREFIX="/home/mycomputer/.wine" wine "C:\\Program Files\\uTorrent\\uTorrent.exe" /NOINSTALL
```
into the Exec part. Remember to replace 'mycomputer' with your user name so the /home/--username---/ matches up with your home directory.

You can even download a good looking icon from here:
[http://forum.utorrent.com/viewtopic.php?id=1663](http://forum.utorrent.com/viewtopic.php?id=1663)
so the icon will look awesome, and run awesome.

kerlee

---

