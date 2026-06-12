---
title: "Anyone else use LXDE enviroment?"
date: 2009-09-29
forum: The Cafe
---

### Post by millstone on 2009-09-29
I just installed LXDE enviroment, and it's amazingly fast.:D
Anyone else use it? What's your opinions on it?

---

### Post by inobe on 2009-09-29
fast and swift

it can be best enjoyed as a stand alone environment, adding it as a session conflicts with gnome network manager.

no one will risk removing network manager to replace with lxnm "lightweight x11 network manager.

---

### Post by ~sHyLoCk~ on 2009-09-29
> **millstone said:**
> I just installed LXDE enviroment, and it's amazingly fast.:D
Anyone else use it? What's your opinions on it?

I love LXDE. It's fast and light.

---

### Post by nicefinger on 2009-09-30
I use it too .. Hereafter this will be my Environment. 
[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1248322&page=1](http://ubuntuforums.org/showthread.php?t=1248322&page=1)[/COLOR]

---

### Post by NormanFLinux on 2009-09-30
There is Lubuntu... but it hasn't been updated for some time.

---

### Post by Jesus_Valdez on 2009-09-30
I use it on my Ubuntu and I log in from time to time, I don't have anything against it,  I don't have anything pro-LXDE though.

---

### Post by Bölvaður on 2009-09-30
yes, it is alright I guess

---

### Post by earthpigg on 2009-09-30
Yes, yes I do.

:D

|
|
\/

---

### Post by jaxxstorm on 2009-09-30
IceWM >>>> LXDE :P

---

### Post by shafin on 2009-09-30
Used it, liked it, but then, I liked gnome more. So I'm back to gnome.

---

### Post by earthpigg on 2009-09-30
> **shafin said:**
> Used it, liked it, but then, I liked gnome more. So I'm back to gnome.

the only significant drawback with LXDE, to me, is the lack of a graphical menu editor. 

[alacarte]("http://en.wikipedia.org/wiki/Alacarte") can be used to ***add*** menu items, but not to remove/move/etc them.

---

### Post by markp1989 on 2009-09-30
i have tried lxde, dont use there packeages, but i do use openbox, pcmanfm, fbpanel,wicd on my laptop. 

i dont know what it was about lxde, i liked it, but it just didnt feel like home.

its probably only me who thinks this about lxde

---

### Post by RiceMonster on 2009-09-30
I'm not fond of it. I'd much rather use plain Openbox.

---

### Post by XubuRoxMySox on 2009-09-30
[SIZE="6"]I'm a fanboy![/SIZE] It's *much* lighter than even Xfce, has much fewer dependencies, and works on ancient hardware. Speed and ease; simplicity and beauty. I use a minimal Ubuntu/LXDE mixture on my old 'puter that is shared by several kids at the dance studio. They don't know it's Linux - they just know it's superfast and supersimple.

There are a handful of LXDE-based distros out there now. The nicest implementation of LXDE with minimal Ubuntu that I've played with is called [Masonux]("http://sites.google.com/site/masonux/"). Light, fast, simple.

-Robin

---

### Post by SomeGuyDude on 2009-09-30
FWIW, LXDE isn't really a full-on "desktop environment" so much as Openbox with some things to make it more user friendly. It's Openbox/PCManFM/LXPanel plus the LX tools (lxappearance, which I use for GTK settings). So the reason it's so fast is that you're actually, gasp, using Openbox! ;)

---

### Post by PhoHammer on 2009-09-30
> **inobe said:**
> fast and swift

it can be best enjoyed as a stand alone environment, adding it as a session conflicts with gnome network manager.

no one will risk removing network manager to replace with lxnm "lightweight x11 network manager.

That is the story of the demise of mine and LXDE's relationship...
I had gnome installed and the network manager went buggy when I put some LXDE on
it
Then I go into a big mess and eventually uninstalled LXDE...

I want to try it again, though

---

### Post by NormanFLinux on 2009-09-30
Its an X11 Desktop plus Openbox. LXDE was designed for modularity, low consumption of resources and user friendliness. That makes it an ideal operating system for very old computers and netbooks.

---

### Post by lykwydchykyn on 2009-09-30
Well, technically, if you use a different WM, it's still LXDE, is it not?  That's sort of like saying GNOME is just metacity or Compiz with some stuff added to make it friendlier.

I like LXDE in theory, but in practice it lacks a few too many features for me to want to use it on my main machines.  It pretty well displaces most of the use I ever had for XFCE as "lightweight but friendly desktop", I've used it on the kids' machines since all they do is launch programs (no file management, network browsing, etc).  Does a fine job there.

Also good for when your non-Linuxy coworkers insist on you putting a GUI on your servers.

---

### Post by Little Bit on 2009-09-30
I liked it so much on a demo computer that I use the same thing at home. I have experimented with Gnome and KDE too but I tend to run back "home" to the familiar and simple GUI that I started with. 

Amy

---

### Post by XubuRoxMySox on 2009-10-01
> **PhoHammer said:**
> 
I had gnome installed and the network manager went buggy when I put some LXDE on
it
Then I go into a big mess and eventually uninstalled LXDE...

I want to try it again, though

My LXDE works fine on a minimal Ubuntu install using **wicd** instead of the default network manager.

Now it looks like the folks at LXDE are developing their own network manager for LXDE! That oughtta be cool when it's finished. But for now wicd works for me. **Masonux** has successfully integrated LXDE with the Ubuntu-default network manager somehow. Very nicely done.

-Robin

---

### Post by earthpigg on 2009-10-01
> Masonux has successfully integrated LXDE with the Ubuntu-default network manager somehow. Very nicely done.

i think you are giving me more credit than due. i merely commented out one line of a config file to remove the artificial limitations that the line in question placed on nm-applet.

```
sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop
```

or run a text editor as root, find the "OnlyShowIn" line of any /etc/xdg/autostart/(applet name).desktop file and comment it out.

[source]("http://sites.google.com/site/masonux/home/notes-to-myself").

may or may not work on other gnome or xfce applets. i know it works for gnome-power-manager, as well.

i chalk it up to the NetworkManager developers ***not*** making NetworkManager bloated and reliant on a bunch of other random stuff... much like the way LXDE developers do all their stuff, and very much ***unlike*** the way folks at GNOME often do stuff, for better or worse. 

(if you don't believe me, run *sudo apt-get install gnome-panel* on a system that does not have gnome installed... if it where possible/practical to just run gnome-panel on top of openbox without any ridiculous amount of awkwardness, Masonux would not exist.)

:guitar:

---

### Post by cimh on 2009-10-11
On a netbook (eee) lxde is very impressive - tho I prefer gnome on my desktop.

whats good about it? 
-- Its fast booting - from switch on to desktop 21s (cf gnome 45s) Many people with netbooks like fastbooting as these little guys are often switched off and on to conserve batteries.
-- It uses less resources so its generally faster.

whats not so good?
-- not so many bells and whistles

General thoughts - wicd handles wifi (tho I will follow up earlier comment re nm) - I recommend people also try chromium instead of firefox not only is it miles faster but it has all the new ideas that makes chrome so good. 

My conclusion (for what its worth)
1. If you want fast booting or low resource use and are prepared to spend time setting up the system and dont mind editing config files then just use a windows manager. I like openbox (used to great effect by crunchbang) but others swear by fluxbox, e16 etc

2. If you want fast booting or low resource use but dont mind fiddling a bit to get things working and you want a conventional desktop and menu system use LXDE.

3. You like all the bells and whistles and special effects - and dont want to mess about setting things up then stick with gnome or KDE.

If you dont mind sludging up your system its relatively easy to install lxde, openbox, fluxbox, e16 then you can swap between them relatively seamlessly at login to try them out.

cimh
eee 901: Karmic+LXDE

---

