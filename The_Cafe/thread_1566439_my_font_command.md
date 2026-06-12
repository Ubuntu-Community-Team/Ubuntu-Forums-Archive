---
title: "my font command"
date: 2010-09-02
forum: The Cafe
---

### Post by searchfgold6789 on 2010-09-02
Command to get all the fonts :)
Version 2.5 :)

[SIZE=1](All of these fonts are English, or symbols. It does not include the fonts shipped with Ubuntu 10.04 :) A blue screen will come up saying that some fonts are not free and redistributable. Acknowledge this and press enter at the next blue screen which is asking you if you've downloaded these non-free fonts before. At the next screen, if you want to keep the files for these fonts somewhere, simply enter in the directory and press enter, otherwise leave it blank.)[/SIZE]
[COLOR=DarkOrange][SIZE=5][SIZE=3]The Command[/SIZE][COLOR=Black]
[SIZE=2](Works 100% now)
Here it is: (copy and paste into the terminal)[/SIZE]
[/COLOR][/SIZE][/COLOR] ```
sudo apt-get install ttf-adf-baskervald mathematica-fonts ttf-aenigma ttf-adf-accanthis ttf-adf-berenis ttf-adf-gillius ttf-adf-ikarius ttf-adf-irianis ttf-adf-libris ttf-adf-mekanus ttf-adf-oldania ttf-adf-romande ttf-adf-switzera ttf-adf-tribun ttf-adf-universalis ttf-adf-verana ttf-alee ttf-atarismall ttf-baekmuk ttf-beteckna ttf-breip ttf-dustin ttf-engadget ttf-essays1743 ttf-evertype-conakry ttf-f500 ttf-farsiweb ttf-femkeklaver ttf-fifthhorseman-dkg-handwriting ttf-sil-gentium ttf-georgewilliams ttf-inconsolata ttf-isabella ttf-jura ttf-konatu ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-levien-museum ttf-levien-typoscript ttf-liberation ttf-linex ttf-linux-libertine ttf-marvosym ttf-mgopen ttf-mph-2b-damase ttf-mplus ttf-ocr-a ttf-oflb-asana-math ttf-oflb-euterpe ttf-okolaks ttf-oldstandard ttf-opendin ttf-radisnoir ttf-sjfonts ttf-staypuft ttf-summersby ttf-symbol-replacement ttf-tomsontalks ttf-tuffy ttf-ubuntu-title ttf-unifont ttf-xfree86-nonfree python-fontforge fontforge-extras 

``` Hey, who needs hard disk space anyway? ... Yeah, okay.
Enjoy. :popcorn: And post below for any questions at all or if you used this and appreciated it :)

---

### Post by inso_741 on 2010-09-02
thanx a lot!!!

---

### Post by whiskeylover on 2010-09-02
Thanks

---

### Post by nilarimogard on 2010-09-02
Hey you said all the fonts but there are a lot more fonts in the repositories than the ones you've posted :D

---

### Post by whiskeylover on 2010-09-02
That command screwed up my installation in a virtualbox. The system hangs at boot showing the login wallpaper, but no login options, just the purple wallpaper.

Also, the "sudo apt-get ..." fails at 

```
Setting up ttf-root-installer...
```

Anybody know whats wrong and how to fix it?

---

### Post by searchfgold6789 on 2010-09-03
Try this.
Go into a live CD
```
sudo fdisk -l
```Find out your main system partition (referred to as sdXX from now on); If you only have one hard disk with only Ubuntu on it, this will probably be sda4
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
sudo apt-get remove ttf-root-installer potrace autotrace perl-tk pango-graphite xserver-xorg-core xfs 
sudo apt-get install xserver-xorg-core xfs
```I really hope this fixes your problem. I am goiung to remove ttf-root-installer from the command.
But if that doesn't work, leave the terminal open and type
```
sudo synaptic
```go into the edit menu I think there is an option there for you to see broken packages and attempt to fix them.
I wish you good luck.
You may see errors in the terminal along the way such as "Cannot resolve host ubuntu"; I believe these errors to be normal.

---

### Post by searchfgold6789 on 2010-09-03
> **nilarimogard said:**
> Hey you said all the fonts but there are a lot more fonts in the repositories than the ones you've posted :D
It's a work in progress, as you can see :/ plus I only did the English ones

---

### Post by whiskeylover on 2010-09-03
> **searchfgold6789 said:**
> Try this.
Go into a live CD
```
sudo fdisk -l
```Find out your main system partition (referred to as sdXX from now on); If you only have one hard disk with only Ubuntu on it, this will probably be sda4
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
sudo apt-get remove ttf-root-installer potrace autotrace perl-tk pango-graphite xserver-xorg-core xfs
```I really hope this fixes your problem. I am goiung to remove ttf-root-installer from the command.
But if that doesn't work, leave the terminal open and type
```
sudo synaptic
```go into the edit menu I think there is an option there for you to see broken packages and attempt to fix them.
I wish you good luck.
You may see errors in the terminal along the way such as "Cannot resolve host ubuntu"; I believe these errors to be normal.

I can still press Ctrl-Shift-F1 and get to the terminal, so I'm gonna try removing it without using a live CD first :)

---

### Post by whiskeylover on 2010-09-03
> **whiskeylover said:**
> I can still press Ctrl-Shift-F1 and get to the terminal, so I'm gonna try removing it without using a live CD first :)

Okay, I removed all those packages, and now X wont boot up. I'm trying the live CD now or even give me a terminal. I'm trying the Live CD now.

EDIT: Fixed. I had to boot into the live environment and reinstall the xserver-xorg-core and xfs packages. Now it works.

Thanks

---

### Post by searchfgold6789 on 2010-09-03
[SIZE=5]I have removed the xorg packages from the command :) it works 100% now[SIZE=3]
Coming up in version 2.5: more fonts!
[SIZE=2]Hmm....maybe it's time I made a font organizer-package-thing for people to download...[/SIZE]
[/SIZE][/SIZE]

---

### Post by searchfgold6789 on 2010-09-09
Also coming up:
my cursor command
and also
my theme command
Then you can have all the ubuntu customization you want under one roof!

---

### Post by morrie on 2010-10-15
How does your system perform with all those fonts installed?  As a designer, in Windows, I have to use a font management program, to keep them out of the system until they are used, otherwise the system takes 11 hours(you know what I mean) to start up.  It's the same story in Mac, which is UNIX, so are you sure you want to install ALL those fonts?

_My question is:_ Does Ubuntu handle fonts in a similar way, or can we just install them all?

(Any word a on a good font management program for Ubuntu?)

---

### Post by searchfgold6789 on 2010-10-20
I haven't seen much in the way of system performance dragging on my system, which has these fonts installed...
One exception would be a slight lag when I go and select a font from the menu. I think this may be the only case where Ubuntu actually loads _all_ of the fonts.
Okay maybe more than slight, but I bet you won't have that much difficulty if you have a more decent CPU than me (mine is only 750 MHz, hence Xubuntu)
I looked online for a font manager for Ubuntu. What I immediately saw suggested that there was none.

---

### Post by Oxwivi on 2010-10-20
Do we need the font smoother with 10.10?

---

### Post by searchfgold6789 on 2010-10-22
All the font-smoothing guides online explain how to do this on early versions of ubuntu. The ubuntu documentation only explains how to turn font smoothing _off_. So you probably won't need to use that if you have 10.10.

---

### Post by gggecko on 2011-04-08
> **searchfgold6789 said:**
> Here it is. :o
The one and only. :o
Command to get all the fonts :)
Version 2.5 :)
Why, you ask?
Because some of us like to have ... lots of fonts to choose from!

[SIZE=1](All of these fonts are English, or symbols. It does not include the fonts shipped with Ubuntu 10.04 :) A blue screen will come up saying that some fonts are not free and redistributable. Acknowledge this and press enter at the next blue screen which is asking you if you've downloaded these non-free fonts before. At the next screen, if you want to keep the files for these fonts somewhere, simply enter in the directory and press enter, otherwise leave it blank.)[/SIZE]
[COLOR=DarkOrange][SIZE=5][SIZE=3]The Command[/SIZE][COLOR=Black]
[SIZE=2](Works 100% now)
Here it is: (copy and paste into the terminal)[/SIZE]
[/COLOR][/SIZE][/COLOR] ```
sudo apt-get install ttf-adf-baskervald mathematica-fonts ttf-aenigma ttf-adf-accanthis ttf-adf-berenis ttf-adf-gillius ttf-adf-ikarius ttf-adf-irianis ttf-adf-libris ttf-adf-mekanus ttf-adf-oldania ttf-adf-romande ttf-adf-switzera ttf-adf-tribun ttf-adf-universalis ttf-adf-verana ttf-alee ttf-atarismall ttf-baekmuk ttf-beteckna ttf-breip ttf-dustin ttf-engadget ttf-essays1743 ttf-evertype-conakry ttf-f500 ttf-farsiweb ttf-femkeklaver ttf-fifthhorseman-dkg-handwriting ttf-sil-gentium ttf-georgewilliams ttf-inconsolata ttf-isabella ttf-jura ttf-konatu ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-levien-museum ttf-levien-typoscript ttf-liberation ttf-linex ttf-linux-libertine ttf-marvosym ttf-mgopen ttf-mph-2b-damase ttf-mplus ttf-ocr-a ttf-oflb-asana-math ttf-oflb-euterpe ttf-okolaks ttf-oldstandard ttf-opendin ttf-radisnoir ttf-sjfonts ttf-staypuft ttf-summersby ttf-symbol-replacement ttf-tomsontalks ttf-tuffy ttf-ubuntu-title ttf-unifont ttf-xfree86-nonfree python-fontforge fontforge-extras 

``` Hey, who needs hard disk space anyway? ... Yeah, okay.
Enjoy. :popcorn: And message me for any questions at all or if you used this and appreciated it :)
[[COLOR=DarkOrange][SIZE=3]To Enable Font Smoothing[/SIZE][/COLOR]]("http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/") (tested on Dapper and Edgy)
[SIZE=3][COLOR=DarkOrange]To get Even More Fonts[/COLOR][/SIZE]
```
sudo gedit /etc/apt/sources.list
```Add the following two lines to the bottom:
[LEFT][COLOR=#000000]```
deb http://ppa.launchpad.net/corenominal/ubuntu gutsy main  
deb-src http://ppa.launchpad.net/corenominal/ubuntu gutsy main
```Type in Terminal:```
sudo apt-get update
sudo apt-get install ttf-aefonts
```(probably just won't work because of some public address non-availability thing) 
[/COLOR][/LEFT]

thanks for all the new fonts I now have. they're really cool,
GGGecko:P

---

### Post by searchfgold6789 on 2011-04-09
> **gggecko said:**
> thanks for all the new fonts I now have. they're really cool,
GGGecko:P

You're welcome :)

---

