---
title: "[Need apps] MP3 converter &amp; CD Burner for audio cds"
date: 2005-01-22
forum: The Cafe
---

### Post by CowPie on 2005-01-22
I think I saw something like this in a KDE 3.3 on suse, you right click on an mp3 file and it gives the option to "convert to" 160 kbsp, 128, ogg, etc.  Anything similar in Gnome?

Also what's a good burner?  Can the built in Nautilus burner burn cds for the car? I'm not too eager ot test it and find myself a coaster that can only be played on the computer.  I can't get xcdroast (it can't find any drives period) or k3b to work on Hoary.  2.6.10 kernel.

---

### Post by adbak on 2005-01-23
Nautilus does make good MP3 CDs for cars.  Although I used to fear making coasters, I've since moved to CD-RWs so if it become's a bad CD, I just rewrite over it.

---

### Post by CowPie on 2005-02-02
[QUOTE=adbak]Nautilus does make good MP3 CDs for cars.  Although I used to fear making coasters, I've since moved to CD-RWs so if it become's a bad CD, I just rewrite over it.[/QUOTE]


Thanks, the problem I now have is that the cd is one-minute too long.  How do I convert a 160kbsp mp3 into 128?

---

### Post by Randabis on 2005-02-02
[QUOTE=CowPie]Thanks, the problem I now have is that the cd is one-minute too long.  How do I convert a 160kbsp mp3 into 128?[/QUOTE]
 Lame MP3 encoder maybe?

---

### Post by poofyhairguy on 2005-02-02
[QUOTE=CowPie]
Also what's a good burner?  Can the built in Nautilus burner burn cds for the car? I'm not too eager ot test it and find myself a coaster that can only be played on the computer.  I can't get xcdroast (it can't find any drives period) or k3b to work on Hoary.  2.6.10 kernel.[/QUOTE]

K3b is THE best buring program- no comparison.  In order for you to get it to work, run with the command:

gksudo k3b

---

### Post by Randabis on 2005-02-02
[QUOTE=poofyhairguy]K3b is THE best buring program- no comparison.  In order for you to get it to work, run with the command:

gksudo k3b[/QUOTE]
Meh, I perfer Gnomebaker.

---

### Post by poofyhairguy on 2005-02-02
[QUOTE=Randabis]Meh, I perfer Gnomebaker.[/QUOTE]

One day I too will use Gnomebaker- when it does everything k3b does. 


I hope that day is soon and I can forgo kde libs!

---

### Post by KLineD on 2005-02-03
I prefer the idea of a Gnome CD burning app but since K3B is so great and it can do DVDs (I know .3 version of gnomebaker is supposed to do this also) I'll stick with K3B   and the kdelibs. 

Also I don't know why but I tried gnomebaker, eroaster and graveman just to make an audio CD out of mp3's and none of them could in my hoary system. I can play the mp3's just fine but gnomebaker refused to add them to the track list (although it could create a data CD just fine) and eroaster added them but with a 0:00 length displayed and when I clicked on burn it complained about cdrecord even when started with gksudo and I have cdrecord 2.0 installed. Some ppl said that I needed some other packages in order to get it to work (like mpg123 and others) but isn't the idea of package managment precisely supposed to solve that kind of things? I mean apt could have suggested those packages (or even better, installed them) since they are required for something so basic like creating a CD from mp3's, oggs and such.

When I installed K3B agains all my "just-gnome" idea, it just-worked(TM). Everything got configured and I finally could create my audio CD's from mp3 just fine. I'm not complaining or anything, I love ubuntu, but for hoary it would be nice if it included a nice burning app, comparable to K3B in features and that it just work.

---

### Post by Datchew on 2005-02-05
Hey guys. 

I pulled the package for k3b and got it to run. 
I made a shortcut to it on the desktop and it runs...

I'm worried though about the things it says when i run it in terminal. 
Here's some of the stuff it says
************************************************************************
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/form not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/generic not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/image not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/io not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/media not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/navigation not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/net not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/object not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/table not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/hicolor/ group 48x48/stock/text not valid.
k3b: WARNING: KGenericFactory: instance requested but no instance name passed to the constructor!
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
Mutex destroy failure: Device or resource busy
ICE default IO error handler doing an exit(), pid = 5283, errno = 0
*****************************************************************************88

that's just the last part of it... it's actually about 20 times that long. 
Is it something to worry about or not?

Also, EVERY time i open k3b, it gives me that "this is the first time you've used this program" mumbo jumbo and asks me to ensure my cd-rw's burning speed. 
How do i get that to stop???


 
Thanks much. 
Datchew.

---

