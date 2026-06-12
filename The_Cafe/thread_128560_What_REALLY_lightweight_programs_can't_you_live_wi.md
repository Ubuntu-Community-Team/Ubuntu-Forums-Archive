---
title: "What REALLY lightweight programs can't you live without?"
date: 2006-02-11
forum: The Cafe
---

### Post by Gadren on 2006-02-11
I checked out a copy of the Linux Cookbook from our library, and have been learning various new commands.  Wince most of the work I'm doing now involves only the CLI, I'm looking around for really lightweight programs that would be interesting and useful.

One of these is [Dillo](http://www.dillo.org/), a Web browser I first saw in Damn Small Linux.  It's certainly not as full-featured as Konqueror or Firefox, but man does it fly, and it's great for little jobs.

What tiny apps could you not live without?

---

### Post by drfalkor on 2006-02-11
XMMS - music player
vlc - movie player
A X terminal..
A X editor, like gedit

and much more :D

---

### Post by xequence on 2006-02-11
LAME.

It is super tiny, like 200KB, but it is so awesomly awesome and fun to watch it encode stuff.

---

### Post by simon_is_learning on 2006-02-11
I must say Thunar. 
The XFCE file manager.
Not in the xubuntu-desktop official but still....

---

### Post by red_Marvin on 2006-02-11
Nethack.

...I am getting addicted to it...

---

### Post by engla on 2006-02-11
I don't run much lightweight stuff.

'cmatrix' is meaningless but very cool. I just love how it looks.

---

### Post by 5-HT on 2006-02-11
As a printer light is no longer functioning, escputil (CLI Epson Stylus printer utility). :)

If you're looking for small CLI based apps, w3m is a nice  CLI web browser and should be installed in by default in Breezy (it's also great for quickly viewing local html files as well, plus makes a nice pager).


EDIT: Forgot about aptitude and vi.

---

### Post by super on 2006-02-11
aterm

---

### Post by Iandefor on 2006-02-11
vi

---

### Post by majikstreet on 2006-02-11
[QUOTE=Iandefor]vi[/QUOTE]
ditto.

links2 with the -g option is COOL! fast as anything, but slightly graphical :D

oh yeah... APT-GET!!! dunno how light it is but I can't live without it..

EDIT:

wow. omfg.. cmatrix is AWESOME!

EDIT2:
thanks for the escputil program.. I also have an epson stylus! but.. how do you do the raw device thing?

---

### Post by racecat on 2006-02-11
[QUOTE=Gadren]I checked out a copy of the Linux Cookbook from our library, and have been learning various new commands.  Wince most of the work I'm doing now involves only the CLI, I'm looking around for really lightweight programs that would be interesting and useful.

One of these is [Dillo](http://www.dillo.org/), a Web browser I first saw in Damn Small Linux.  It's certainly not as full-featured as Konqueror or Firefox, but man does it fly, and it's great for little jobs.

What tiny apps could you not live without?[/QUOTE]

Wow! Thanks for the Dillo referral. It's awesome for some sites I experience slow loads from. I love my bloated Firefox for keeping my online travels organized, but sometimes I need to concentrate on one site and could use the speed. It's perfect.

Bill

---

### Post by fuscia on 2006-02-11
openbox is the best. dillo and elinks are tie for first, regarding browsers. sylpheed-claws is just fine (i'd rather shoot myself than to wait for thunderbird to open). i can't do anything that mousepad can't. feh rocks. xmms is perfect for me. conky's great. if only i could solve my camera problem...

edit: camera problem solved. (i knew you'd be thrilled.0

---

### Post by Iandefor on 2006-02-11
In terms of light weight, I think OO.O is the absolute best!:grin:

---

### Post by sivadnaes on 2006-02-12
On one note, you cannot consider OO.O to be light weight.

My lightweight requirements are simplly put = xubuntu-desktop.  I love the speed and usabilty, while at the same time remaining graphically pleasing.

---

### Post by sizzam on 2006-02-12
fast-user-switch-applet

This is great for scenarios where two users share the same computer.   Provides a gui interface to the Ctrl+Alt+F7/Ctrl+Alt+F8 trick for switching between two X sessions.

It also comes in handy when you are VNCing into the box, you can switch it to the other display easily.

---

### Post by papangul on 2006-02-12
Beaver: multitabbed lightweight text editor
Rox-Filer: As my default 'Desktop File browser'
XNC- my 'System File Browser'
Audacious: my xmms
Opera: best browser for linux

---

### Post by towsonu2003 on 2006-02-12
conky...

---

### Post by lothar_m on 2006-02-12
One of my personal favorites:

Wget

---

### Post by 5-HT on 2006-02-12
[QUOTE=majikstreet]
EDIT2:
thanks for the escputil program.. I also have an epson stylus! but.. how do you do the raw device thing?[/QUOTE]


For me, the raw device is /dev/lp0.

So to check the ink levels for example, I use: ```

sudo escputil -i -r /dev/lp0 
```

Not all the functions require stipulating the raw device, but if they do simple tag on the '-r /dev/lp0' at the end.

There are quite a few options that the man page describes nicely (but be careful about printer head alignment...there's a big warning that it could possible cause damage if not used properly).

I find making aliases for the commands much quicker typing the originals out.

HTH

---

### Post by majikstreet on 2006-02-12
thanks!

that's awesome!

---

### Post by Minyaliel on 2006-02-12
Really, I couldn't live without Kpaint - I always use that for outlines for graphics, web sites and other design things. And it's a great boredom relief ;)

---

### Post by Lord Illidan on 2006-02-12
Command line programs?

wget and vi rock! Same goes for apt-get and mplayer in a terminal. And links2 is awesome!

---

### Post by angkor on 2006-02-12
apt
top
vim
mplayer

Not necessarily in that order. ;)

---

### Post by ebash on 2006-02-12
Graphical editor:
nedit

---

### Post by chimera on 2006-02-12
vi 
wget (I can't get video streamiing in firefox working, so I just have mediaplayerconnectivity plugin spit out the direct links to the videos and dl them with wget)
xmms (THE music player)

---

### Post by ice60 on 2006-02-12
i like wget too just use the command 
```
wget file_download_location file_download_location2 file_download_location3
```

then if you don't complete the download and want to restart it use the c option
```
wget -c file_download_location file_download_location2 file_download_location3
```

i use Privoxy too for an http proxy

i like nauitlus scripts too. i downloaded alot of them all in one go, i'll see if i can find where in abit. here's a screenshot.

---

### Post by ice60 on 2006-02-12
you can get the nautilus scripts from [here](http://g-scripts.sourceforge.net/)

i also like BookMarklets which i use in Opera, i have one which will fast forward/rewind to the next page, one which will open the page i'm on in archive.org, one which will show all the links to the page i'm on etc etc
[http://nontroppo.org/wiki/PowerButtons](http://nontroppo.org/wiki/PowerButtons)
[http://nontroppo.org/wiki/CustomButtons](http://nontroppo.org/wiki/CustomButtons)

here are some of my extra buttons

---

### Post by bored2k on 2006-02-12
gmplayer
pacman/apt

---

