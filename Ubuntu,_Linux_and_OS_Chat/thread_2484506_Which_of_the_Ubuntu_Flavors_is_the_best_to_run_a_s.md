---
title: "Which of the Ubuntu Flavors is the best to run a simple Minecraft server?"
date: 2023-03-01
forum: Ubuntu, Linux and OS Chat
---

### Post by lovedlx on 2023-03-01
Not long ago I created a minecraft server in windows, it worked fine without any problem but I wanted something better to take advantage of the power of my laptop (yes, for the server I use a simple laptop since the server is for two people) so I decided to install a linux distribution and since it was my first time trying it I decided to go for the most obvious thing which is ubuntu and after trial and error looking at tutorials on youtube and unfortunately the hard drive of that laptop got corrupted and I had to reformat it completely I managed to install in an ubuntu partition. It worked well, I learned to install java and the commands to run the server correctly but I knew that there were more flavors of ubuntu and that's why I came to the ubuntu forum to see if someone could recommend me a version to take better advantage of the resources of that laptop for the server after a disastrous attempt with lubuntu since it did not fit me well

So being new here and just learning how to use this and using the google translator since English is not my native language, I will be attentive to the answers and recommendations that they give me
that would be all, good night and in case I don't see you good morning and good afternoon

---

### Post by ian-weisser on 2023-03-01
The "best" flavor is the flavor that you prefer to use and understand how to use.

The choice of flavor is mostly about the display environment. Beyond that, the flavors are built on top of the same Ubuntu version -- same kernel, same networking, same systemd, etc.
The Java Minecraft Server from Mojang can easily be run headless (without any display at all), So a choice of display is entirely about your preference.

In other words, all flavors of Ubuntu will run Minecraft Server --more or less-- about the same.
In theory, without the overhead of running a display, Ubuntu Server would be the "best"...but not by much.

My own Minecraft Server runs on Ubuntu Server, but it's not on a laptop. It's on a server.

---

### Post by guiverc on 2023-03-01
To me *flavors* are as Ian has already stated, a different desktop replacing the default used by Ubuntu Desktop.

But an OS is a software stack, at the bottom of is the base Ubuntu system (*for a desktop that base is rather like a Ubuntu Server system actually; sure Ubuntu Server uses netplan where Desktops replace it with Network Manager, but its very alike with only minor changes like the networking example I gave*).

Desktops use specific toolkits/libraries though; GNOME uses GTK (*originally Gimp Toolkit, then GTK+ which was Gimp+Gnome toolkit, with name returning to GTK now*).   That toolkit is used by numerous desktops, including MATE, Xfce (*which is older than GNOME/GTK but was ported to use GTK long ago*), Cinnamon & others...

An alternate toolkit (*actually older than GNOME/GTK connection, but as it was owned by a corporation the FSF helped create GTK as an alternative*) is Qt, currently at Qt5. Qt is used by some desktops, for example KDE Plasma, LXQt etc.

Lubuntu (*you mentioned having issues with*) originally used the LXDE desktop which was GTK2, GTK2 is *deprecated* and the port of LXDE to GTK3 the *developers* blogged about as not going well; as GTK3 was far heavier than GTK2, and the L of LXDE was Light thus the *heaviness *mattered to them... thus they experimented going elsewhere, made another port (of LXDE/pcmanfm) to Qt5 & reported that was where they were moving as Qt was *lighter*. The LXDE *devs* joined with a Razor-Qt team creating a replacement for both desktops which is now called LXQt.

This history you don't need, and if you don't understand it won't matter...

My point is the an OS is a software stack, at the base is the Linux Kernel, it has the GNU code on top, some toolkits/libraries with the GUI/desktop & user-apps at the top..  

You can have an efficient system if all your stack co-exists well (*uses/shares the same resources*), however if your device is lacking resources, you can easily make a very inefficient system that will perform badly.

As an example, modern Lubuntu uses LXQt, and is the *lightest* Ubuntu *flavor* "*out of the box*".  I doubt few would argue with that, however if you were going to use GTK apps on it, that *lightness* will be wasted & you very likely may have been better starting off with Xubuntu (a GTK desktop) as it'll share resources with the apps you're using.

I still use 32-bit hardware with 1GB only of RAM.. I usually bloat my boxes down with many desktops installed, but if I'm using a machine with limited resources I'm far more careful.  This current box is a 2008 dell, but it has 8GB of RAM so I'm less worried about RAM but still consider both RAM & cpu-cycles & try and avoid wasting machine resources.. but I'll be more careful when using a 2003 laptop with single-core pentium M & 1GB ram. I don't care about the additional disk space used by having multiple desktops installed, nor the extra bandwidth as all the additional packages need to be upgraded; but I do consider what I'll do in that session & use that in deciding which desktop I'll login & use for that session (ie. RAM is what matters to me in this example).

On this box with 8GB I can be less careful in my consideration of resources & also consider my tastes, ie. which desktop did I want to use today. I'm using LXQt actually, but I do like Xfce, MATE, and others... I'll use GNOME, KDE Plasma & others when I want a holiday too (*its the same box, it'll just look different on my screen as I do what I normally do, that change to me is a 'holiday*'). All of what I just mentioned (*and more*) are actually installed on this desktop (*I **select** which I'll use at login*).

I'm not suggesting bloating your box like I do... I waste loads of disk space with my *bloated* system, but when I login I decide which I'll use when I consider what I'll do in that session (*ie. I have plenty of disk space on the box, but this old box has a slow core2 cpu so I don't want to waste cycles, and only 8GB of RAM* *and I need much of that to use  the web browser I'm using right now etc*).

[B]SUMMARY

[/B](1) If your box doesn't have loads of resources to spare (*it's old, limited ram etc) *consider the apps you'll use in deciding what will be efficient, fast in your decision (ie. *what is in the software stack of what you'll use*).

(2) If your box has enough resources, consider what will make you happy. I don't think there is a *best* desktop, they all have *pros* and *cons*, there are some I prefer to others, some I only rarely use (*not my cup of tea*) but it's mostly a decision of taste; like what's your favorite ice-cream?

(distant 3) I'd also consider the release (*you didn't mention*). I would not have suggested anyone install Lubuntu 18.04 LTS or the last release using the LXDE desktop, as it was the *end of the road* for the *deprecated* desktop... On hardware with *limited* resources though, and specific apps being used - it made sense, and I still have an old IBM Thinkpad t43 using 18.04 and login most of the time with that LXDE desktop (*when I use it, which isn't often*).

---

### Post by DuckHook on 2023-03-01
Both Ian and guiverc have given you excellent answers. I've nothing more to add to their very complete replies, but I would only raise one additional consideration about security.

In the Linux world, whenever someone mentions "server", our minds automatically jump to security.

If your server will be exposed to the Internet, then it is important to keep its attack surface as small as possible. GUI elements like those required for display environments are large attack surfaces (one of the reasons that Windows gets hacked so often). If your server will be accessed over the Internet, then you may wish to consider a standalone Minecraft Server that runs with no GUI.

---

### Post by Tadaen_Sylvermane on 2023-04-10
While some may debate the right or wrong with docker I keep my Minecraft servers in docker. Extra layer of isolation in theory. Fire up a new world in seconds. No configuration needed. To damn convenient to not consider. With docker distro is irrelevant as well. No need to hunt any specific java down or anything.

---

### Post by chris0nlinux on 2023-04-12
If you want just a Minecraft server and nothing else, I would recommend Ubuntu Server. However, Ubuntu Server does not have a GUI, but you can launch the Minecraft server ,jar file with the --no-gui option and you should be fine.

---

