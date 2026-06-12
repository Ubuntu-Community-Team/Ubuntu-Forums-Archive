---
title: "G3 Torrent for Ubuntu Linux!"
date: 2005-03-06
forum: The Cafe
---

### Post by Quest-Master on 2005-03-06
After upgrading to Hoary and finally getting the joys of wxPython with GTK2, I instantly downloaded the source for G3 Torrent, unfortunately, primarily a Windows open-source product and with no official Linux support.

However, I found a Linux build for it, and, unluckily, that did not work either. The errors I reached with it were fixable though, and soon enough, I was able to get G3 Torrent running on this Hoary desktop. It might work with Warty, but I personally did not use any wx apps. on Warty because they all use GTK1.x which is quite ugly, and does not deserve a place on my beautiful GNOME desktop.

So, with some modifications, I've finally reached the goal of attaining a GTK2, feature-loaded, graphically-advanced, yet still fast and lightweight BitTorrent client for Ubuntu. Azureus is the choice of most users, and was mine before, but we all know how much memory Java and Azureus eat together. :)

G3 Torrent takes up much less, primarily because it is coded in Python, but it still has just about all the features Azureus has, and perhaps even some more. Be sure to try it out if you are sick of Azureus but use BitTorrent frequently.

And, without further ado, here is the package: [http://208.53.170.194/~pixelrev/g3torrent-v1.10-ubuntu.tar.gz](http://208.53.170.194/~pixelrev/g3torrent-v1.10-ubuntu.tar.gz)

There could perhaps be some bugs, and if there are, please e-mail them to me at [email]zainalam@gmail.com[/email] (or the maintainer of the general Linux G3 Torrent package, LeoXV).

Hope it might come of use to some of you guys here. :)

~ Zain

---

### Post by tim1 on 2005-03-06
It might not have the features that g3torrent has but be sure to also check out gnome-bt which provides a nice GTK2 bittorrent download dialog and is in the hoary desktop seed.

greets, tim

---

### Post by Quest-Master on 2005-03-06
[QUOTE=tim1]It might not have the features that g3torrent has but be sure to also check out gnome-bt which provides a nice GTK2 bittorrent download dialog and is in the hoary desktop seed.

greets, tim[/QUOTE]
 Gnome-BT isn't bad at all either, but again, for things like multiple files in a torrent, and other things which are helpful when downloading many torrents, feature-filled clients usually do a better job.

---

### Post by kleeman on 2005-03-06
Hey Quest-master thanks a lot! Works OK on warty btw although as you say the gtk1 look isn't great. Still it beats azureus on the resource hog front!

---

### Post by Quest-Master on 2005-03-06
[QUOTE=kleeman]Hey Quest-master thanks a lot! Works OK on warty btw although as you say the gtk1 look isn't great. Still it beats azureus on the resource hog front![/QUOTE]
 I'm still curious as to why when wx was packaged for Warty, it was not with GTK2. I mean, GTK2 has been around for quite a while, and so has the wx with GTK2 enabled. I dunno, I guess someone just decided to make a weird choice or something.

Also, I've heard GTK1 isn't that bad if you are able to theme it properly. Of course.. I prefer not to go through all that trouble, so I just avoided any GTK1 apps till yesterday when I upgraded to Hoary.

---

### Post by kassetra on 2005-03-06
[QUOTE=Quest-Master]I'm still curious as to why when wx was packaged for Warty, it was not with GTK2. I mean, GTK2 has been around for quite a while, and so has the wx with GTK2 enabled. I dunno, I guess someone just decided to make a weird choice or something.

Also, I've heard GTK1 isn't that bad if you are able to theme it properly. Of course.. I prefer not to go through all that trouble, so I just avoided any GTK1 apps till yesterday when I upgraded to Hoary.[/QUOTE]

First off, thank you for this!  Azureus, Firefox, and VMWare all running at the same time causes me mucho ram grief, let me tell you (especially if I have them all up overnight.)

Some notes on GTK1 & GTK2 ... The reason (as far as I can tell) for the GTK1 wx package in warty...?  wx for GTK2 wasn't "stable enough" ... (don't quote me on this however)

As far as GTK1 not being bad if you theme it properly, all I have to say to that is WHA?  heh.  I've themed it correctly and it STILL looks horrendous compared to GTK2 apps (and I know why and it's not something that's exactly "fixable") ... so I moved as many apps to GTK2 versions as possible... like moving from XMMS->BMP ... I'm waiting for VMWare 5 (which is GTK2)... but while I'm waiting I'm stuck with one ugly app (which is another reason for me to test QEMU!)...

---

### Post by cdhotfire on 2005-03-10
how do i use this exatly?

---

### Post by bored2k on 2005-03-10
[QUOTE=cdhotfire]how do i use this exatly?[/QUOTE]
 Extract the .tar.gz file, enter a terminal , inside that dir type
python g3torrent.py

---

### Post by bored2k on 2005-03-10
First of all I want to thank Quest-Master and his *horny* Mario for giving me this info. This one goes right into my testing chamber alongside newly released Bittorrent 4.0 [wich is the bomb] . I wish they update it so it can use the newly bittorrent 4.0 :D

For anyone interested in knowing how it looks like, here are some sshots of the main window and configurations screens:
[[IMG]http://img164.exs.cx/img164/5528/g32mk.th.jpg[/IMG]](http://img164.exs.cx/my.php?loc=img164&image=g32mk.jpg) [[IMG]http://img164.exs.cx/img164/6268/g3b0wm.th.jpg[/IMG]](http://img164.exs.cx/my.php?loc=img164&image=g3b0wm.jpg)

btw, that .torrent, its for *backup* ...

---

### Post by bored2k on 2005-03-10
[QUOTE=kassetra]First off, thank you for this!  Azureus, Firefox, and VMWare all running at the same time causes me mucho ram grief, let me tell you (especially if I have them all up overnight.)

Some notes on GTK1 & GTK2 ... The reason (as far as I can tell) for the GTK1 wx package in warty...?  wx for GTK2 wasn't "stable enough" ... (don't quote me on this however)

As far as GTK1 not being bad if you theme it properly, all I have to say to that is WHA?  heh.  I've themed it correctly and it STILL looks horrendous compared to GTK2 apps (and I know why and it's not something that's exactly "fixable") ... so I moved as many apps to GTK2 versions as possible... like moving from XMMS->BMP ... I'm waiting for VMWare 5 (which is GTK2)... but while I'm waiting I'm stuck with one ugly app (which is another reason for me to test QEMU!)...[/QUOTE]
 The vmware 5 beta is downloadable off vmware's site and in one of the pages -im not naming- g3 torrent can be useful :rolls eyes:.

---

### Post by kleeman on 2005-04-08
Hmm I upgraded to Hoary and now g3torrent is not working properly. At the commandline I get:
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/richard/g3torrent/scrape.py", line 117, in run
    h = urlopen(self.url)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 364, in open
    response = meth(req, response)
  File "/usr/lib/python2.4/urllib2.py", line 468, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourldecompress instance has no attribute 'code'

Exception in thread Thread-3:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/usr/lib/python2.4/threading.py", line 422, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/richard/g3torrent/BitTorrent/Rerequester.py", line 114, in rerequest
    h = urlopen(url)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 364, in open
    response = meth(req, response)
  File "/usr/lib/python2.4/urllib2.py", line 468, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourldecompress instance has no attribute 'code'

and the interface looks wrong.....
Any ideas? Is it a python 2.4 issue?

---

### Post by Quest-Master on 2005-04-08
I upgraded to Hoary and it still works for me.. I haven't upgraded to the latest one yet though. I'll have to check on this when I get back home.

---

### Post by LeoXV on 2005-04-14
Is it a python 2.4 issue? Yeah, it is.
Try this fix [http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10a-ubuntu.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10a-ubuntu.tar.gz)


[http://rufus.sourceforge.net/](http://rufus.sourceforge.net/)

---

### Post by kleeman on 2005-04-14
Ah thanks works great now!

---

### Post by viuks on 2005-05-23
Please help!
```
$ python g3torrent.py 
Traceback (most recent call last):
 File "g3torrent.py", line 15, in ?
   import wx 
ImportError: No module named wx 
```

---

### Post by sapo on 2005-05-23
Good Bye Azureus!

Azureus is good... but it uses too much ram...  :) 

And thanx for the package  :)

---

### Post by jdong on 2005-05-23
This is going into Backports. :)

---

### Post by GeirG on 2005-05-23
[QUOTE=viuks]Please help!
```
$ python g3torrent.py 
Traceback (most recent call last):
 File "g3torrent.py", line 15, in ?
   import wx 
ImportError: No module named wx 
```[/QUOTE]


I got rid of that by installing libwxgtk2.4-python

Regards,

---

### Post by jdong on 2005-05-23
If you have both wxpython 2.4 and 2.5 installed, the GUI will default to GTK1 instead of GTK2. To force it, add these two lines into g3torrent.py:

```
	import wxversion
	wxversion.select("2.5.3-unicode")

```

It has to go before the ```
import wx
``` line. 


You can **do the same trick with btdownloadgui** (BITTORNADO ONLY) to force it to use a GTK2 gui!

---

### Post by jdong on 2005-05-23
Ok, here's the deal: I have started the initial debianization and patching to get it to build as a .deb package.

I made quite a number of changes already:
[list]
[*]Force GTK2 to be selected   
[*]Have Psyco (if available) JIT compile itself for more speed   
[*]a dirty system.exit() hack to break out of a hang during exit with GTK2 
[/list] 
However, still a bit more work needs to be done, namely to get ***.ini to save in the HOME DIRECTORY**, perhaps creating a ~/.g3torrent folder in the process. I don't have the time tonight to do this, so if someone wants to take a stab at it, go ahead.

My patches are at [http://backports.ubuntuforums.org/backports/sources/g3torrent-debianize.diff.gz](http://backports.ubuntuforums.org/backports/sources/g3torrent-debianize.diff.gz) . Apply against the extracted g3torrent folder from version 1.10. (zcat g3torrent-debianize.diff.gz | patch -p1)

---

### Post by jdong on 2005-05-23
Correction: **I just patched g3torrent fully**. I also made a deb and put it in Hoary Extras Staging in Ubuntu Backports.


The last thing on the TODO is to create a menu entry ;)

---

### Post by jdong on 2005-05-23
Ugh, never mind it still loves to modify itself.... I'll still need further help.

Try adding a torrent. It touches with the ./torrents directory, which needs to turn into ~/.torrents

---

### Post by jdong on 2005-05-23
Ok, I've patched and patched and patched (revision 22 now), and I've finally gotten it to somewhat work. At least I can download and seed now!

YAY!!

Please help test. This will be a buggy sucker.

---

### Post by jdong on 2005-05-23
sorry about all these posts. This is still a buggy bastard, regularly hanging when I challenge it.


I wouldn't recommend this as an Azureus replacement yet -- even it works better right now! LOL

I'll keep on hacking and playing with this package though.

---

### Post by Quest-Master on 2005-05-23
Hey jdong-- thanks for your work on this!

I haven't been able to use it properly yet because for some reason it's not working with my ports correctly. I don't know why this is going on, but yeah, I'll continue playing around with it. Thanks for putting it into Backports though. :)

---

### Post by sapo on 2005-05-23
I m having some problems and now i m back to azureus..

the problems:

1 - When i quit it stays running and i have to kill the process  ](*,) 

2 - its using 100% of my cpu to update the tracker and its slowing down my computer while it updates...

3 - crashes when i click on that RSS feature

4 - if i limit the upload to 10k "global" it uploads at 5k when i tried to limit for each torrent it upload at maximun (13k here) dont know why make the limits work.

---

### Post by ow50 on 2005-05-23
I remember, a while ago I hacked ABC to get it to run. I did manage to get it running, but the dissapointing thing was that the download and upload speeds were all over the place, sometimes over the limit, sometimes under.

I wouldn't get too excited about this, since it would probably require a lot more than simple hacking to get it to run *well*.

---

### Post by jdong on 2005-05-23
[QUOTE=sapo]
 
1 - When i quit it stays running and i have to kill the process ](*,) 
3 - crashes when i click on that RSS feature
.[/QUOTE]
 
1: Is that the version from backports? I use system.exit() to force an exit on the mainwindow closing, so that's fixed.
 
3. Yeah, that's a mess.

---

### Post by McQuaid on 2005-05-24
I don't know if this is of any help, but reading a bit about g3torrent on it's forums that some users have abondoned it as it hasn't been updated for awhile and there are some long standing bugs in the last version.  

Some other devels have taken on the project in a different form now called rufus

 [http://rufus.sourceforge.net/](http://rufus.sourceforge.net/) 

I did a search on their forums and someone has made it work with linux:

[http://sourceforge.net/forum/forum.php?thread_id=1259409&forum_id=440415](http://sourceforge.net/forum/forum.php?thread_id=1259409&forum_id=440415) 

I don't know if this might solve some of the issues your having but hopefully it would and it seems like this is now the more active version of g3torrent.

---

### Post by jdong on 2005-05-24
No good; Rufus exhibits the same problems under Linux.

---

### Post by LeoXV on 2005-06-18
[QUOTE=jdong]No good; Rufus exhibits the same problems under Linux.[/QUOTE]

Hehe :D

Do you need  the wxPython 2.6 support?

---

### Post by LeoXV on 2005-06-18
[QUOTE=sapo]I m having some problems and now i m back to azureus..

the problems:

3 - crashes when i click on that RSS feature[/QUOTE]

CHANGELOG.TXT 0.4.5 - January 28, 05
d0c - Rewrote RSS reader to use threads to avoid blocking by the feedparser

---

### Post by LeoXV on 2005-06-18
[QUOTE=sapo]I m having some problems and now i m back to azureus..

the problems:

1 - When i quit it stays running and i have to kill the process  ](*,) 
[/QUOTE]

print 'Destroying window'
self.Destroy()        
time.sleep(10.0)  ## sleep ten seconds.. update tracker
sys.exit(1)

---

### Post by LeoXV on 2005-06-18
[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10b-ubuntu.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10b-ubuntu.tar.gz)

wxPython 2.6
New g3rss.py (threads)
g3rpcserver.py (serve_forvever thread)
g3torrent.py (sys.exit(1)) "fix crazy stats" Thanks jdong.

---

### Post by angrykeyboarder on 2005-06-20
[QUOTE=Quest-Master]After upgrading to Hoary and finally getting the joys of wxPython with GTK2, I instantly downloaded the source for G3 Torrent, unfortunately, primarily a Windows open-source product and with no official Linux support.

However, I found a Linux build for it, and, unluckily, that did not work either. The errors I reached with it were fixable though, and soon enough, I was able to get G3 Torrent running on this Hoary desktop. It might work with Warty, but I personally did not use any wx apps. on Warty because they all use GTK1.x which is quite ugly, and does not deserve a place on my beautiful GNOME desktop.

So, with some modifications, I've finally reached the goal of attaining a GTK2, feature-loaded, graphically-advanced, yet still fast and lightweight BitTorrent client for Ubuntu. Azureus is the choice of most users, and was mine before, but we all know how much memory Java and Azureus eat together. :)

G3 Torrent takes up much less, primarily because it is coded in Python, but it still has just about all the features Azureus has, and perhaps even some more. Be sure to try it out if you are sick of Azureus but use BitTorrent frequently.

And, without further ado, here is the package: [http://208.53.170.194/~pixelrev/g3torrent-v1.10-ubuntu.tar.gz]("http://208.53.170.194/%7Epixelrev/g3torrent-v1.10-ubuntu.tar.gz")

There could perhaps be some bugs, and if there are, please e-mail them to me at [email="zainalam@gmail.com"]zainalam@gmail.com[/email] (or the maintainer of the general Linux G3 Torrent package, LeoXV).

Hope it might come of use to some of you guys here. :)

~ Zain[/QUOTE]

G3 Torrent was the 2nd client I tried (after the original bittorrent) on Windows. I used it for quite a while till I discovered Azureus, which I like better because of the extra features. It's also got the best damn GUI I've ever seen on a Java app. When I tried it on Linux I was again blown away. I've run it under both GNOME and KDE and have been amazed at how well it adapts to each GUI environment.

G3 is good, but I like Azureus better. I did recently (just for the heck of it) try to mess around with G3 on Linux but lost patience.

Thanks for your work though. You wouldn't wanna do a .deb package for us, wouuld you? :-)

---

### Post by LeoXV on 2005-06-21
[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10c-ubuntu.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10c-ubuntu.tar.gz)

if last_gui_update + max(0.25, self.btconfig['gui_update_rate']) < time.time() and not self.IsIconized():

Minimize G3Torrent to the tray and see if the CPU usage drops..

---

### Post by jdong on 2005-06-21
glad to see someone actively working on this... Once you get it pretty much working... I'll see about debianizing it again and bumping the current Backports version.

---

### Post by LeoXV on 2005-06-21
[http://sourceforge.net/projects/mhash/](http://sourceforge.net/projects/mhash/) python-mhash  high performance SHA-1

---

### Post by jdong on 2005-06-21
Can you guys try to move **all the config files that g3torrent tries to write to** into expandhome("~/.g3torrent")?

It's necessary if we ever want to Debianize G3Torrent.

Nice work, BTW.

---

### Post by LeoXV on 2005-06-22
[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt) (Rufus)

echo 'rufus=${HOME}/.Rufus' >> $NAME
echo 'rufusfolder=${HOME}/Rufus' >> $NAME
echo 'torrents=${HOME}/Rufus/torrents' >> $NAME
echo 'download_dir=${HOME}/Rufus/incoming' >> $NAME
echo 'completed_dl_dir=${HOME}/Rufus/incoming/completed' >> $NAME
echo 'completed_tor_dir=${HOME}/Rufus/torrents/completed' >> $NAME

---

### Post by pt123 on 2005-07-09
[QUOTE=LeoXV][http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt) (Rufus)

echo 'rufus=${HOME}/.Rufus' >> $NAME
echo 'rufusfolder=${HOME}/Rufus' >> $NAME
echo 'torrents=${HOME}/Rufus/torrents' >> $NAME
echo 'download_dir=${HOME}/Rufus/incoming' >> $NAME
echo 'completed_dl_dir=${HOME}/Rufus/incoming/completed' >> $NAME
echo 'completed_tor_dir=${HOME}/Rufus/torrents/completed' >> $NAME[/QUOTE]
 Is there a place to download the latest version as th sourceforge links are all dead

---

### Post by DancingSun on 2005-07-12
Will this work in Ubuntu AMD64?

---

### Post by littlepr on 2005-07-17
Quest-Master,

You are the man! I have been looking for an Azureus replacement for a while and finally found you and your g3torrent. Thanks a lot buddy.

---

### Post by LeoXV on 2005-07-25
[QUOTE=sapo]I m having some problems and now i m back to azureus..

the problems:

1 - When i quit it stays running and i have to kill the process  ](*,) 


scrape.py
import socket
socket.setdefaulttimeout(20)    #fix (maybe)

---

### Post by jdong on 2005-07-25
I liked my "raise 'boo'" hack better, LMAO

---

### Post by LeoXV on 2005-07-25
feedparser.py
***************
try:
    import timeoutsocket # [http://www.timo-tasi.org/python/timeoutsocket.py](http://www.timo-tasi.org/python/timeoutsocket.py)
    timeoutsocket.setDefaultSocketTimeout(20)
except ImportError:
    import socket
    if hasattr(socket, 'setdefaulttimeout'):
        socket.setdefaulttimeout(20)
import urllib, urllib2

scrape.py
***************
import socket
print socket.getdefaulttimeout()
socket.setdefaulttimeout(10) 
print socket.getdefaulttimeout()

20.0
10.0

Default is already 20 :D  (feedparser.py)

---

### Post by strikeforce on 2005-07-26
*Edit Never mind I just saw LEO is here :P

---

### Post by LeoXV on 2005-08-16
Gui + taskbar  fix

    while not self.doneflag.isSet():
            # UpdateGUI every 'gui_update_rate'            
            if last_gui_update + max(0.25, self.btconfig['gui_update_rate']) < time.time():
                if not self.IsIconized(): # LeoXV  
                    self.InvokeLater(self.UpdateGUI, [])            
                
                if self.IsIconized() and self.last_taskbar_update + 15 < time.time(): # LeoXV
                    self.InvokeLater(self.UpdateGUI, [])
                    self.InvokeLater(self.UpdateIcon, [])
                    self.last_taskbar_update = time.time()
                    
                last_gui_update = time.time()

---

### Post by LeoXV on 2005-08-16
Problem connecting to tracker - <urlopen error timed out>
socket.setdefaulttimeout(10)   = download speed 49-52 KB/s
socket.setdefaulttimeout(20)   = download speed 40-48 KB/s

---

### Post by LeoXV on 2005-08-22
[http://ubuntuforums.org/showpost.php?p=313526&postcount=5](http://ubuntuforums.org/showpost.php?p=313526&postcount=5)
[http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/rufus/rufus-0.5.9.tar.gz)

[http://sourceforge.net/forum/forum.php?thread_id=1339274&forum_id=440415](http://sourceforge.net/forum/forum.php?thread_id=1339274&forum_id=440415)

---

### Post by LeoXV on 2005-08-22
[QUOTE=jdong]Can you guys try to move **all the config files that g3torrent tries to write to** into expandhome("~/.g3torrent")?

It's necessary if we ever want to Debianize G3Torrent.

Nice work, BTW.[/QUOTE]

[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/install.txt)
[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10d-ubuntu.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10d-ubuntu.tar.gz)  (~/.g3torrent)

---

### Post by LeoXV on 2005-09-01
[http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10e-ubuntu.tar.gz](http://www.kolumbus.fi/jukka.lehtomaki/ubuntu/g3torrent-v1.10e-ubuntu.tar.gz)

Fixed wxGTK debug mode bugs.  
 
wx._core.PyAssertionError: C++ assertion "wxAssertFailure" failed in  
../src/gtk/clipbrd.cpp(631): error retrieving data from clipboard  
 
PyAssertionError: C++ assertion "(bitmap.GetWidth() == m_width &&  
bitmap.GetHeight() == m_height) || (m_width == 0 && m_height == 0)" failed in  
../src/generic/imaglist.cpp(81): invalid bitmap size in wxImageList: this might  
work on this platform but definitely won't under Windows.

---

### Post by kleeman on 2005-09-01
Works great thanks Leo (thats a pope's name right?  :) )
One minor glitch: I had to uncheck the default folder choices in the preferences menu
as they aren't created automatically and they cause the program to fail if they are not there....

---

### Post by LeoXV on 2005-10-17
[QUOTE=kleeman]Works great thanks Leo (thats a pope's name right?  :) )
One minor glitch: I had to uncheck the default folder choices in the preferences menu
as they aren't created automatically and they cause the program to fail if they are not there....[/QUOTE]

chmod +x install 
/.install
g3torrent

---

### Post by hazote on 2006-06-19
hi
when i was under win ( :s )
i was using G3torrent

i'm very happy to find this under linux ( ubuntu )
sorry for my english...
it is a great job !!

but i have a probleme:
i have dl the version g3torrent-v1.10e-ubuntu.tar.gz

do chmod and ./install
all ok

but impossible to launch g3torrent
running : g3torrent
i have the error : 
"Traceback (most recent call last):
  File "/usr/share/g3torrent/g3torrent.py", line 16, in ?
    import wxversion"

could u help me pliz ? ( i'm under dapper)

---

### Post by xXx 0wn3d xXx on 2006-06-19
Thanks, it works great.

I made a debian file that can be found [ here. ](http://files.filefront.com/g3torrent_g3torrent_1_i386deb/;5167118;;/fileinfo.html)

---

### Post by hazote on 2006-06-20
i have the same prob!
i'am under dapper / gnome

i think this is cause of dependencies python

where i can find them please ?

i have installed :
libwxgtk2.4-python_2.4.3.1
libwxgtk2.4_2.4.3.1
libpng10-0_1.0.18
wxPython-src-2.6.3.2
Python-2.4.3

and get the same error :
Traceback (most recent call last):
  File "/usr/share/g3torrent/g3torrent.py", line 16, in ?
    import wxversion
ImportError: No module named wxversion

---

### Post by zenwhen on 2006-06-20
This link is dead. Could we get a mirror?

---

### Post by cshake on 2006-06-20
Thanks Leo!
I couldn't get azureus to work (java crashing...) and this is better anyway.
All I need is global speed capping, some sort of gui to manage multiple torrents, and selected file downloading from torrents, and this delivers.
On second thought, I am having problems with the speed cap, is there a fix?

Oh, and Own3d: your package only has a readme file in it... was it supposed to have more?

---

### Post by psyke on 2006-07-10
i would like to try out g3, but the tar.gz link is still leading nowhere and the deb pkg just includes one README and nothing else...

someone still working on that?

---

### Post by Rackerz on 2006-07-10
Yeah, can we get the file please :D. Sounds like a good torrent app.

---

### Post by redDEADresolve on 2006-09-20
yeah i have no idea how to download or run this app.

All I know is that it looks like its the answer to all my linux torrent woes.

---

### Post by samir85 on 2006-09-20
As far as I know, the g3torrent project is dead. Anyway, there's a bittorrent client called Rufus which builds upon g3torrent.

see here [http://rufus.sourceforge.net/](http://rufus.sourceforge.net/)

---

