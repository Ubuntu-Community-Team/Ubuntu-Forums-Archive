---
title: "Newer programs and updates leave Ubuntu 9.04 users behind"
date: 2009-12-21
forum: The Cafe
---

### Post by dmillerw on 2009-12-21
Lately I've been seeing some cool programs, and updates that just don't work with Ubuntu 9.04.

This is a problem for me because Karmic is much slower for me then any other version so far.

Is there nothing I can do, am I stuck with programs suffering from bugs that I can never see fixed?

---

### Post by Psumi on 2009-12-21
Also, for those wanting to give support by saying, "Just add a jaunty PPA or find someone that will compile otherwise..."

I tried that once... with xsplash in jaunty. But turns out after installing xsplash in jaunty, I didn't know how to configure it, so it was installed, just it wouldn't work.

---

### Post by Daisuke_Aramaki on 2009-12-21
Have you identified the reasons why 9.10 is sluggish on your box?  Is it a general feeling or has got to do with something specific, say when you are browsing, or watching movies etc.?

---

### Post by dmillerw on 2009-12-21
Its just all-around sluggish, everything I do is slower.

---

### Post by cariboo on 2009-12-21
I just had a look at the thread you started in General Help. It would help if you gave more details. What type of hardware, and what you have tried, to find out why it is running slower, would be a good starting point.

---

### Post by dmillerw on 2009-12-21
Hardware:

Pentium 4 2Ghz processer
NVidia GeForce 6200 256VRAM (I did install the drivers avalible under "Hardware Drivers"
1280MB of RAM

I havn't really tested anything to figure out why it was so slow, probably should have...

---

### Post by earthpigg on 2009-12-21
> **dmillerw said:**
> Pentium 4 2Ghz processer
NVidia GeForce 6200 256VRAM (I did install the drivers avalible under "Hardware Drivers"
1280MB of RAM


yeah, ubuntu-desktop is too much for that system to handle with any responsiveness.

Linux, however, is not. in fact, ***Ubuntu*** is not to much for that system. just that pretty brown GNOME ubuntu-desktop with its pretty applets and all that stuff.

compare how ***long*** these 4 lists are to see what i am talking about:
[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
[http://packages.ubuntu.com/karmic/gnome-core](http://packages.ubuntu.com/karmic/gnome-core)
[http://packages.ubuntu.com/karmic/xfce4](http://packages.ubuntu.com/karmic/xfce4)
[http://packages.ubuntu.com/karmic/lxde](http://packages.ubuntu.com/karmic/lxde)

the differences between the four are a matter of pretty brown eye candy but, again, look at how different the lengths of the four lists are. all will run the same apps. lower on the list means more stuff is left for you to do and not done behind the scenes, but will be more responsive to pointing and clicking and run whatever it is you want to run faster. its give and take. a choice only you can make. 

willing to do a command line install and let us walk you through a few 'sudo apt-get install ...' commands and other minor tweaking that will allow the system to not waste effort on maintaining pretty desktop applets, but devote much more of that RAM and CPU power you ***do have*** to the applications you want to run?

google around. ubuntu-desktop, gnome, xfce, lxde. we will walk you through your choice. o, and ubuntu-desktop is what you are currently using. note that you will ***still*** be using ubuntu whichever you choose.

---

### Post by dmillerw on 2009-12-21
> yeah, ubuntu-desktop is to much for that system with any responsiveness.


Come again?

Anyway, are you basically saying that creating a minimal install of Karmic and then adding the stuff I need will work better then downloading the generic Desktop CD?

If so, could you or someone else walk me through the basic apps required to have a functional Ubuntu install?

---

### Post by dmillerw on 2009-12-21
How well would gnome-core + whatever apps I needed run.

I'd rather not use XFCE or other WM because I've grown quite used to Gnome, I know my system can handle it well. (It does at least now, on 9.04)

---

### Post by myusername on 2009-12-21
> **dmillerw said:**
> Hardware:

Pentium 4 2Ghz processer
NVidia GeForce 6200 256VRAM (I did install the drivers avalible under "Hardware Drivers"
1280MB of RAM/QUOTE]

[QUOTE=earthpigg;8534978]yeah, ubuntu-desktop is too much for that system to handle with any responsiveness.

umm what? his desktop is lightyears better than mine and mine run ubuntu just fine

---

### Post by earthpigg on 2009-12-21
```
sudo apt-get install xorg gnome-core firefox synaptic empathy gdebi gdm network-manager jockey-gtk
```

that will probably get you want, from a command line only install.

replace empathy with pidgin if you like.

gdebi lets you double click on .deb's to install or reinstall them. completely optional.

gdm is the login screen.

jockey-gtk is the 'hardware drivers' app in system -> administration.

add evince if you wish evince - thats the 'document viewer'


modified from what i wrote[here]("http://sites.google.com/site/masonux/home/notes-to-myself"), if you are interested.

if there is anything else you want, but can't find the package name... post back and we will let you know.


> umm what? his desktop is lightyears better than mine and mine run ubuntu just fine

and he will ***still*** be running ubuntu. i run ubuntu, too, even though i haven't used an official .iso outside of VirtualBox in ages.

also, your definition of 'responsive' and 'just fine' may differ from his. individuals have individual needs and desires. nothing wrong with that. it's all about choice. if he says ubuntu-desktop is to slow for him, then ubuntu-desktop is to slow for him. period. in my opinion. :D

---

### Post by TheNessus on 2009-12-21
> **dmillerw said:**
> Hardware:

Pentium 4 2Ghz processer
NVidia GeForce 6200 256VRAM (I did install the drivers avalible under "Hardware Drivers"
1280MB of RAM

I havn't really tested anything to figure out why it was so slow, probably should have...
get the newer 185. driver from the Nvidia website and install it, for your own good.

---

### Post by t0p on 2009-12-21
To respond to the thread's title: it is usual practice for older versions to be "left behind" by new software and updates to the new version.  Older versions get security and incremental updates, but do not receive new versions of apps as a matter of course.

It is possible to get the newer versions of some apps by activating the 'backports' repositories.  But not all apps are found there.

I realise this discussion has gone on to talking about how the OP might best upgrade his machine.  But I thought the point should be made, if only to inform other members reading the thread.

---

### Post by Zlatan on 2009-12-21
Could it be reasonable to do a clean Karmic install? I can guess that sluggishness could come after upgrade from 9.04 to 9.10?

---

### Post by dmillerw on 2009-12-21
Alright thanks for the help, one thing though, can I install and test this on a second computer, then use remastersys to create an install cd for use on my main pc?

---

### Post by earthpigg on 2009-12-21
> **dmillerw said:**
> Alright thanks for the help, one thing though, can I install and test this on a second computer, then use remastersys to create an install cd for use on my main pc?

you certainly can.

> Could it be reasonable to do a clean Karmic install? I can guess that sluggishness could come after upgrade from 9.04 to 9.10? 

very real possibility that will go a long way towards solving your problems.

---

### Post by dmillerw on 2009-12-21
OK, just wanted to say thanks again, and to say that 9.10 is going much faster now that I've created a minimal install, it took a little while to get everything working, but it does.

---

### Post by 00ber n00b on 2009-12-21
You should try arch!  LOL Sorry, couldn't resist.

---

### Post by sudoer541 on 2010-01-20
One strange thing about this:
































































































open source programs such as firefox do not work on old version of ubuntu.
But, nero a closed source app works from ubuntu 5.10 to ubuntu 10.04....weird!!!!!!!!

---

