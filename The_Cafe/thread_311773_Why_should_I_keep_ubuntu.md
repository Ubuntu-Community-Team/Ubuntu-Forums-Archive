---
title: "Why should I keep ubuntu?"
date: 2006-12-03
forum: The Cafe
---

### Post by Cyfr on 2006-12-03
Ubuntu is starting to feel bloated for me personally. Things are running slow and not smooth. Im having much more issues now that I have edgy installed.

If I move to say, gentoo, its going to be a hell of a lot of work, but will I be more impressed because I can run what I want? Will I get some more performance and more smooth running of the system once it is set up? Or is it simply psychological because im installing from source and things?

Windows IS bloated, but when I dual boot windows, things seem to run better/faster in it. From the menus appearing quicker and more responsive to the web browser opening and loading pages..

hmm :(

---

### Post by Johnsie on 2006-12-03
If you search these forums you can find ways to speed things up.

---

### Post by .t. on 2006-12-03
You can remove packages you don't use. Install prelink and preload. Gentoo can easily be slower, especially if you use too many CFLAGS, or configure it wrong.

---

### Post by Rhubarb on 2006-12-03
Give Xubuntu a go maybe?

---

### Post by aysiu on 2006-12-03
I promise you IceWM won't ever feel slow to you.

---

### Post by greggh on 2006-12-03
If you want a really lean Ubuntu, just install off the server cd, then install X and whatever WM/DE and programs you want. There you go, an Ubuntu install with only what you want.

---

### Post by Cyfr on 2006-12-03
> **aysiu said:**
> I promise you IceWM won't ever feel slow to you.

What happens when I want to start running applications like aMSN though. They'll run slow wont they :(.. and amsn is the only MSN that works with webcam that I know of (except mercury messenger which uses java and hence screams AHHHHH at me)

edit: Looked at some icewm screenshots and it seems so unprofessional compared to the slick look of gnome :x

---

### Post by burek on 2006-12-03
> **Cyfr said:**
> Ubuntu is starting to feel bloated for me personally. Things are running slow and not smooth. Im having much more issues now that I have edgy installed.

If I move to say, gentoo, its going to be a hell of a lot of work, but will I be more impressed because I can run what I want? Will I get some more performance and more smooth running of the system once it is set up? Or is it simply psychological because im installing from source and things?

Windows IS bloated, but when I dual boot windows, things seem to run better/faster in it. From the menus appearing quicker and more responsive to the web browser opening and loading pages..

hmm :(

try openbox or fluxbox maybe 
obconf is quite cool too

I hope you can manage with Ubuntu; but its true gentoo has made his well known name

---

### Post by aysiu on 2006-12-03
> **Cyfr said:**
> What happens when I want to start running applications like aMSN though. They'll run slow wont they :(.. and amsn is the only MSN that works with webcam that I know of (except mercury messenger which uses java and hence screams AHHHHH at me)

edit: Looked at some icewm screenshots and it seems so unprofessional compared to the slick look of gnome :x
If aMSN slows you down, then you may want to see what's wrong with aMSN. It's usually the desktop environment that makes the difference, not the application. Hell, even Damn Small Linux can run Firefox and still be fast.

As for screenshots, this is what my IceWM looks like. I use the IceBuntu theme to get a Gnome Human look. I also, for applications, use Rhythmbox, Firefox, Thunderbird, and Thunar.

---

### Post by RAV TUX on 2006-12-03
> **Cyfr said:**
> Ubuntu is starting to feel bloated for me personally. Things are running slow and not smooth. Im having much more issues now that I have edgy installed.

If I move to say, gentoo, its going to be a hell of a lot of work, but will I be more impressed because I can run what I want? Will I get some more performance and more smooth running of the system once it is set up? Or is it simply psychological because im installing from source and things?

Windows IS bloated, but when I dual boot windows, things seem to run better/faster in it. From the menus appearing quicker and more responsive to the web browser opening and loading pages..

hmm :(
have you tried fluxbuntu yet?
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by John T. Monkey on 2006-12-03
Why should you keep Ubuntu?

Because it meets all your needs, and because you want to use it?

If either of those aren't correct, and the solutions people have given you above don't help, then maybe you shouldn't.

---

### Post by Cyfr on 2006-12-03
> **aysiu said:**
> If aMSN slows you down, then you may want to see what's wrong with aMSN. It's usually the desktop environment that makes the difference, not the application. Hell, even Damn Small Linux can run Firefox and still be fast.

As for screenshots, this is what my IceWM looks like. I use the IceBuntu theme to get a Gnome Human look. I also, for applications, use Rhythmbox, Firefox, Thunderbird, and Thunar.


Ok you convinced me. What do I need to apt-get once I have a server install?

---

### Post by greggh on 2006-12-03
> **Cyfr said:**
> Ok you convinced me. What do I need to apt-get once I have a server install?

apt-get install x-window-system-core xterm (xdm,wdm,gdm,kdm, or none) (DE or WM)

---

### Post by aysiu on 2006-12-03
> **Cyfr said:**
> Ok you convinced me. What do I need to apt-get once I have a server install?
Actually, I don't know. I don't use IceWM with a server install. I actually use it on top of Ubuntu. As long as Gnome isn't running, it won't slow you down by just being installed. In fact, I use IceWM with a number of Gnome services running (not Metacity, Nautilus, or Gnome Panel, though).

This script will get you set up with IceWM nicely--install it for you and give you a nicer default configuration than the normal IceWM.

Just download it to your desktop and then paste these commands into the terminal: ```
cd Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh 
./setupicewm.sh
``` Then log out of Gnome, select your session as IceWM, and log back in again.

---

### Post by Christmas on 2006-12-03
You can try Kubuntu. I think its interface (opening menus, resizing, minimizing etc) is faster. It has also a great configuration tool (kcontrol) through which you can customise it and turn on/off lots of features. You won't get faster times loading programs though. But at least you can use Konqueror as a web browser (which is demonstrated to be faster than Firefox, and as far as I remember as fast as Epiphany).

If you have a server install and want KDE:
> sudo apt-get install x-window-system-core kdm kde-core
For GNOME:
> sudo apt-get install x-window-system-core gdm gnome-core
Tested on Dapper (should be the same on Edgy). I don't know exactly for XFCE, but you can try "sudo apt-get install x-window-system-core kdm xfce4".

---

### Post by greggh on 2006-12-03
If you want icewm then

apt-get install x-window-system-core xterm icewm

add gdm if you want a login manager

---

### Post by aysiu on 2006-12-03
> **greggh said:**
> If you want icewm then

apt-get install x-window-system-core xterm icewm

add gdm if you want a login manager
That's probably a little *too* barebones for Cyfr.

---

### Post by JurB on 2006-12-03
> **Cyfr said:**
> Windows IS bloated, but when I dual boot windows, things seem to run better/faster in it. From the menus appearing quicker and more responsive to the web browser opening and loading pages..

hmm :(

Ok, the menu thing... [this]("http://www.ubuntuforums.org/showthread.php?t=215119") thread shows you how to make those menus appear in a flash, it's just some stupid default gnome setting that has to be changed. I at first also tought that gnome was slooow, but with this tweak things are much quicker.

---

### Post by XVampireX on 2006-12-03
[www.archlinux.org](www.archlinux.org) if you want a binary gentoo :)

---

### Post by lhtown on 2006-12-03
My computer is a Gateway Profile 4 Pentium 4 with an Nvidia graphics card. After I installed the Nvidia drivers, it "feels" a lot faster.

---

### Post by Albi on 2006-12-03
xfce should do it..i find it to be a lot more user friendly than the other light weight ones...icewm would be a nightmare for newbs if they wanted to customize it

---

### Post by Albi on 2006-12-03
Double post sry...might as well edit though to include useful info

Xfce- just works, everything is already set up for you
IceWM- default is okay, no desktop though and menu entries are convoluted, hard to customize
Fluxbox- same as icewm, a bit easier to customize since you everything is more or less in one directory, but the feel isnt as complete
KDE- kde-core isn't that bad actually, a bit heavier than xfce, but if you get carried away with it it becomes slow

---

### Post by ryu kun on 2006-12-06
IceWM is really fast. Thanks for the suggestion, Aysui.

However, it is not easy to configure it, as Albi mentioned. There is an application called IceWM Control Panel which is famous of its impossible installation. :P

---

### Post by aysiu on 2006-12-06
> **ryu kun said:**
> IceWM is really fast. Thanks for the suggestion, Aysui.

However, it is not easy to configure it, as Albi mentioned. There is an application called IceWM Control Panel which is famous of its impossible installation. :P
Try this script.

If you already have Ubuntu (i.e., Gnome) installed, this script will give you a Ubuntu-friendly configuration for IceWM.

Just download it to your desktop and then paste these commands into the terminal: ```
cd ~/Desktop
tar -xvzf icewm.tar.gz
chmod +x setupicewm.sh
./setupicewm.sh
``` Then log out of Gnome and into IceWM.

---

