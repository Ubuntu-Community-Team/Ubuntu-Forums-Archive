---
title: "p2p"
date: 2004-12-01
forum: The Cafe
---

### Post by Infatuated_iPod on 2004-12-01
Are their any p2p programs for linux?

--> i found one, but i dont understand how to install it.. 

Installation
Since the Qtella package uses automake and autoconf, compilation and installation of Qtella is quite easy. All you need are the Qt libraries compiled with thread support. You can check whether these libraries exists by typing "locate qt-mt". If locate does not list the libraries you need to download Qt from [http://www.trolltech.com](http://www.trolltech.com) and compile it with thread support first. If Qt is compiled with thread support, you are able to compile and install Qtella as follows:

1. tar xzf qtella-VERSION.tar.gz
2. cd qtella-VERSION
3. ./configure
4. make
5. make install (as root)

You are now able to run Qtella by typing "qtella". When starting Qtella for the first time you should open the configuration tab first. Here you can configure the directory names for completed and incompleted downloads, the maximum number of uploads, etc. 


----> those are the instructions, i really dont get it.. :( can someone help me.

---

### Post by oddabe19 on 2004-12-01
1. means you extract the file to that current directory... basically the same as right clicking the telling it to 'extract here'
2. you change to the directory of that new folder... 'cd qtella-whattheversionis'
3. then you type ./configure and hit enter, a WHOLE bunch of stuff will fly by... unless you get errors it should be good.
4. then you type 'make' this compiles it and could take a long time.
5. this is where you do 'sudo make install' where it installs the file.

all this is done in a terminal of course.

and as for p2p programs... i personally don't use any... but if you open synaptic and do a search for p2p with description and name, i'm sure plenty would show up.  and it's easier then compiling it yourself.

---

### Post by Infatuated_iPod on 2004-12-01
this p2p is not for me... i am just tryint to convince my brother to try liunux, so if he has p2p it would woo him even more... haha

---

### Post by Infatuated_iPod on 2004-12-01
I did a search and nothing came up.. :(

... ok so i extracted the file to that directory, 
then i typed in "cd qtella-version" in the terminal and it says that there is no such file or directory.. i am stumped. This is the first time i ever tried to do anything like this, so i apologize for my beginerness...

---

### Post by zenwhen on 2004-12-01
[QUOTE=Infatuated_iPod]I did a search and nothing came up.. :(

... ok so i extracted the file to that directory, 
then i typed in "cd qtella-version" in the terminal and it says that there is no such file or directory.. i am stumped. This is the first time i ever tried to do anything like this, so i apologize for my beginerness...[/QUOTE]

I think GTKgnutella would be a better and simpler choice.

---

### Post by Infatuated_iPod on 2004-12-01
No matter what program i use i still dont know how to install it...

--> What does "cd" mean and how do you do it? 

"Linux - Open a shell and cd (change directory) to the directory where you downloaded the installer. At the prompt type: sh ./LimeWireLinux.bin"

--- how do you do that? I am a complete bigginer, so please give me the simplests instructions you can think of.

---

### Post by jiyuu0 on 2004-12-01
just up

kazaa:
[http://kitech.com.my/ubuntu/4.10/index.html#limewire](http://kitech.com.my/ubuntu/4.10/index.html#limewire)

emule:
[http://kitech.com.my/ubuntu/4.10/index.html#amule](http://kitech.com.my/ubuntu/4.10/index.html#amule)

$ cd /folder
*means browse to /folder

---

### Post by piedamaro on 2004-12-01
Open synaptic, search for amule (for the edonkey network) and install it (it's done automatically).
Other programs are, as already said, gtk-gnutella, gifttoxic (kazaa and gnutella), dcgui or dcgui-qt for direct connect.
You'll find _everything_ with synaptic, and you can install them with few clicks, see the ubuntu documentation or search this forum, on how to use synaptic.

---

### Post by kmc77 on 2004-12-01
Overnet is a decent p2p.  
But I find myself using Bittorrent as my primary file transfer app.

---

### Post by Infatuated_iPod on 2004-12-01
I seatched for amule and nothing happened..

---

### Post by oddabe19 on 2004-12-01
cd= change directory.

if i want to goto /root instead of /home/oddabel i would do
cd /root
and that would take me there.

you don't goto 'qtella-version' you goto 'qtella-whatever the version number is' ie. 'qtella-1.0'

and easy way to do this is to do 'cd qtella- *hit tab key for completion*'

and it'll auto complete the rest of the folder name.

in order to get P2P programs (to search in synaptic) you need to enable the universe repos in /etc/sources.list or in synaptic.

---

### Post by shad0w on 2004-12-01
Just install Java and get limewire, it's probably the best gnutella p2p program you'll find for linux. Amule and the Edonkey network are nice, but it's really meant for larger files (I'm assuming you want to download/share files that are under 10mb.) With limewire's new firewall-to-firewall transfer, downloads and searches are much faster. The gnutella network just topped 1,000,000 members, btw.

---

### Post by TravisNewman on 2004-12-01
[QUOTE=oddabe19]
and easy way to do this is to do 'cd qtella- *hit tab key for completion*'

and it'll auto complete the rest of the folder name.[/QUOTE]

*blinks* I've been using Linux for 6 years and never knew that. #-o You just saved me quite a bit of time oddabe.

---

### Post by Infatuated_iPod on 2004-12-01
Alright, thanks everyone.... i got the universe working and found gtk-gnutella on it... so everything is running good, now thanks for all your help everyone.

---

### Post by piedamaro on 2004-12-01
[QUOTE=panickedthumb]*blinks* I've been using Linux for 6 years and never knew that. #-o You just saved me quite a bit of time oddabe.[/QUOTE]
Did you use linux for 6 years without bash-completion?! How did you manage to survive? *LOL*

You could be interested in "bash completion" an extension which adds programmable bash completion, e.g. you write ./configure --<TAB> and it prints the avilable config options.
There is also bashish ( :P ), which adds themeing capabilities to bash, for ex. you can have a command prompt which mimics the ol' good C64!


> 
The gnutella network just topped 1,000,000 members, btw.

On ed2k network (edonkey, emule, mldonkey, overnet, shareaza), there are 2,21 milions of person connected atm, and I'm connected with europeans only and it's late night.

Also is not that bad with small files, the problem is that usally it takes a bit of time for a download to start (contrary to direct connect, or gnutella, but I think dc is better).

Shame on me, in my previous post I forgot to mention bittorent, and its great client azureus.

---

### Post by poofyhairguy on 2004-12-02
[QUOTE=piedamaro]
Shame on me, in my previous post I forgot to mention bittorent, and its great client azureus.[/QUOTE]

Or Bit Tornado. Its one of the reasons I went for a debian distro in the first place, because I knew it was in sid. I love its Gui, and I can usually tweak it to get everything out of my Dsl. I have only found its pacakges for Gentoo, Mandrake and Debian and I use it daily. Made Ubuntu a no brainer (I find FOR ME mandrake is buggy and gentoo is painful).  

sudo apt get install bittornado-gui

And this site:

[http://torrent.hackz.nl/](http://torrent.hackz.nl/)

is all you need.

---

### Post by jugo23 on 2005-10-15
Is there any alternative to QT? I need a c++ compiler framework i believe... And it seems that you have to buy QT or use the 30day eval.

---

### Post by majikstreet on 2005-10-15
I personally use GTK-Gnutella, VERY nice!

---

### Post by xequence on 2005-10-15
Uh, a p2p programs comes with ubuntu. Gnome bittorent is a bittorent client.

Bittorent is the best for anything, hands down, except if you just want one song. But you can still just get select songs from an album torrent.

> And this site:

[http://torrent.hackz.nl/](http://torrent.hackz.nl/)

is all you need.

Ill have to check it out =O

All I need is... Torrentspy.com, torrentbox.com, and demonoid.com ;)

---

### Post by Orunitia on 2005-10-15
Limewire works too. Not sure if they have a deb, I think I just alien'd a RPM last time.

---

### Post by xequence on 2005-10-15
[QUOTE=Orunitia]Limewire works too. Not sure if they have a deb, I think I just alien'd a RPM last time.[/QUOTE]

[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Make sure you have java installed first.

---

### Post by Orunitia on 2005-10-15
[QUOTE=xequence][http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

Make sure you have java installed first.[/QUOTE]


That works too. :)

---

### Post by majikstreet on 2005-10-15
I just discovered the raw power of bittorrent. I downloaded the Breezy live cd in about 2hrs. I am downloading the install and I just started about 10-15 minutes ago and I'm already 30% done!


Amazing! Azureus was too slow for me, so I used gnome-btdownlaod (aka gnome-bittorrent)

---

### Post by gingermark on 2005-10-16
Can anyone recommend a Bittorrent client as simple as GNOME Bittorrent or Bittornado that supports multiple file transfers? I've tried Azureus and it just kills my CPU, but it seems to me crazy that with the other programs if you seed a file you can't download another.

Oh, I tried QTorrent as welll - and it doesn't seem to work too well.

---

### Post by Knome_fan on 2005-10-16
ktorrent is pretty nice.

Btw., I never had any problem to seed and download with bittornado or gnome torrent.

---

