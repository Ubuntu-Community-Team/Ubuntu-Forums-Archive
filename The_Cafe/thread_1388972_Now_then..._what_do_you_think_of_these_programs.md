---
title: "Now then... what do you think of these programs?"
date: 2010-01-23
forum: The Cafe
---

### Post by Psumi on 2010-01-23
As shown below...

```
#### After mini.iso Main Installation -- DO THESE!!
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:killeroid/ppa
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update

#### Install The Programs, FINALLY!

## Do all the big stuff first...
sudo apt-get install xorg wdm openbox obmenu obconf menu tint2 pcmanfm usbmount

## Do the aftershocks...
## Do install stuff we need to have recommends on.
## ----
##                   ==== HP AIO Stuff ====
## Later on, you'll need to manually install your network scanner.
## Do so by using hp-makeuri IP-ADDRESS and changing CUPS to
## use the hp:// address instead of socket://
## CUPS admin address is localhost:631. Also, make sure that,
## Normal, Grayscale is the printout mode, don't need color,
## and Draft selects FastDraft through CUPS localhost addr.
## ----
sudo apt-get install alsa-utils hplip xsane

## Using no-install-recommends for stuff that has gnome-depends,
## since we don't want cruft in our system.
sudo apt-get install firefox flashplugin-nonfree smplayer leafpad pidgin gstreamer0.10-x xarchiver unrar p7zip-full unzip htop gtk-chtheme --no-install-recommends
```

this is merely a reference sheet, I don't plan to actually execute this file. I type out each of the executing lines by hand. Any programs you might suggest I use instead? I can't give up smplayer, I need it for the features it only has (parole and totem have those features as well though.) I also can't give up firefox for now.

For those of you wondering why I am choosing pidgin (as it requires gconf no matter what) over ayttm, it's because I can't compile 0.6.1 (which is readily available in lucid, but I have issues with lucid.) Ayttm gives me these errors, found in this post: [http://georgia.ubuntuforums.org/showpost.php?p=8709963&postcount=6](http://georgia.ubuntuforums.org/showpost.php?p=8709963&postcount=6)

---

### Post by teresaejunior on 2010-01-23
I've been using vim, and having a ... hard time. But I think geany is almost as light as leafpad and has many, many more features! I also do --no-install-recommends (in /etc/apt/apt.conf)

---

### Post by k64 on 2010-01-23
I simply add the" ppa:ubuntu-desktop/ppa" repository. That's if I want to enable RGBA.

---

### Post by Psumi on 2010-01-23
> **teresaejunior said:**
> I've been using vim, and having a ... hard time. But I think geany is almost as light as leafpad and has many, many more features! I also do --no-install-recommends (in /etc/apt/apt.conf)

I forgot to mention I need GUI mainly =/

> **k64 said:**
> I simply add the" ppa:ubuntu-desktop/ppa" repository. That's if I want to enable RGBA.

How to enable after adding that repo?

---

### Post by teresaejunior on 2010-01-23
I found mc to be better than xarchiver, 'cause I can preview the files inside them both, but xarchiver asks too many questions

Do you really want to extract???
hein, hein, hein???

---

### Post by teresaejunior on 2010-01-23
with GUI you mean vim? geany is GUI and fairly easy to use, but I'm digging deeper...

---

### Post by Psumi on 2010-01-23
> **teresaejunior said:**
> with GUI you mean vim? geany is GUI and fairly easy to use, but I'm digging deeper...

I hate vim with a capitol H. I tried to learn it, and failed miserably, didn't even know how to exit the program, so whenever I used it, I had to quit terminal or restart the system (if I was in terminal-only) so I've never used vim since.

Also, see new note about ayttm.

---

### Post by teresaejunior on 2010-01-23
So I recommend geany inside X and mcedit out of it.

---

### Post by Psumi on 2010-01-23
> **teresaejunior said:**
> So I recommend geany inside X and mcedit out of it.

I'll stick with leafpad, geany looks... too complicated for my tastes. ;)

Plus, geany is about 2 MB in size to download.

---

### Post by teresaejunior on 2010-01-23
I also do consider package size, but when programming or editing web pages, an IDE helps you to identify mistakes, among other things. leafpad is like notepad.exe...

---

### Post by Psumi on 2010-01-23
> **teresaejunior said:**
> I also do consider package size, but when programming or editing web pages, an IDE helps you to identify mistakes, among other things. leafpad is like notepad.exe...

That's what I always used, to be honest. Not that I plan to get back in the web page business.

Added usbmount package, as I need to automount USB Drives. I'd use pmount, but... hal is being removed in lucid, and hal is already being put off in karmic slightly.

---

### Post by teresaejunior on 2010-01-23
See what I've done recently. Switched from
geany > vim
firefox > uzbl
rox > mc
fvwm > wmii
adobe flash > gnash

Suffering a lot, trying to see what I'm able to do... But it's rewarding after some decades!

even worse: trying to go from claws-mail to mutt...

---

### Post by juancarlospaco on 2010-01-23
sudo apt-get install kupfer mp3blaster xterm bmon whowatch

[Here is my noGTK, noQT, noWxWidgets EN/ES single file text editor]("http://www.tecnicoslinux.com.ar/livecd/edipy_1_all.deb")

[Heres an Identi.ca Bash Client]("http://ur1.ca/kgsk")

---

### Post by Psumi on 2010-01-24
Well with the setup I currently have, everything still takes about 160 MB of RAM to function. :D (though on average it's about 130 to 150 instead of 160 as an average.)

I wonder how I took 160 MB of RAM on lxde now when I had more demanding apps on it. :(

---

