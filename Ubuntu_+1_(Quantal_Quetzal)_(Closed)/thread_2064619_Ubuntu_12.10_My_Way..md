---
title: "Ubuntu 12.10 My Way."
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-09-29
WARNING!
This thread is in no way a how to for you to follow,the next commands can ruin your computer.
This was my weekend project to have fun.
We all have differences and that's acceptable in most communities.
Some of us like Unity and some preffer Gnome.
There is Gnomebuntu (Official) but to me is too Gnomy,it brings back the memory of the painful Evolution Mail Client so hard embedded in the system that it is impossible to get rid of it.That's why we asked for Thunderbird,Remember?
Then Ubuntu Unity is always at the cutting edge of Tehcnology.The latest gadgets,latest version of everything but some of us can't take Unity for what is worth and the tone of apps it brings,half of them with no use for most of us and it becomes over bloated.
There are a tone of articles,post,blogs and ways to install either Unity or Gnome but I wanted to have some fun and called it my weekend project or Ubuntu My Way.

(WARNING!) Do not try this unless you have 10 Hard Drives like me with ubuntu in every one of them,hehehehe:

sudo apt-get install gnome-shell (choose gdm)
sudo reboot (at login choose gnome)
sudo apt-get remove unity*
sudo apt-get purge unity*
sudo apt-get install nautilus
sudo apt-get autoremove
sudo apt-get autoclean

Some of these commands can be altered at your wish.I also removed some apps that have no use for me but they may be important to you.

sudo apt-get remove brasero* empathy* contacts* aisleriot* gnome-games-data* gwibber* libreoffice* landscape* onboard* deja-dup* gnome-orca* synaptic* remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get purge brasero* empathy* contacts* aisleriot* gnome-games-data* gwibber* libreoffice* landscape* onboard* deja-dup* gnome-orca* synaptic* remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get autoremove
sudo apt-get autoclean

Please,if you are to use this in any way,use as a project for fun and chill out with a couple of cold ones like I did.
I also change the buttoms to the left and installed Pidgin,Brasero,Unetbootin,Simple Image Reducer,TeamViewer7,WinFF but those are the apps that are important to me,we all have differences,REMEMBER THAT!

The result is here:

---

### Post by ventrical on 2012-09-29
What ever happened to Freezy?

---

### Post by jbicha on 2012-09-29
Um...

The Ubuntu GNOME Remix Beta was the first milestone to include Evolution as it had been accidentally left out. Surprisingly, nobody said anything; I had to figure out that it was missing on my own...

Anyway, it's a recommends so you can remove it and replace it with Thunderbird if you like.

Also, "apt-get purge" does "apt-get remove" first so you don't need to run "remove" separately.

I prefer my GNOME Shell X on the left too (but I don't bother adding back minimize and maximize).

---

### Post by serdotlinecho on 2012-09-29
On my slow netbook....:lolflag:

---

### Post by kuvanito on 2012-09-29
> **serdotlinecho said:**
> On my slow netbook....:lolflag:
that's so cool!
I like it
I'll be working that way tomorrow sunday :)
Thanks for the pics......:guitar:

---

### Post by kuvanito on 2012-09-29
> **jbicha said:**
> Also, "apt-get purge" does "apt-get remove" first so you don't need to run "remove" separately.
Thank You!
One less command to type and it keeps gettin better,Thank You Again :guitar:

> **jbicha said:**
> I prefer my GNOME Shell X on the left too (but I don't bother adding back minimize and maximize)
Yeah I know,it just a test,I may go like you,just the X :):):)

---

