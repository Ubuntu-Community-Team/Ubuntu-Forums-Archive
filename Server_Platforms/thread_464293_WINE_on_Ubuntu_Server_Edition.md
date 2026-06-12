---
title: "WINE on Ubuntu Server Edition?"
date: 2007-06-04
forum: Server Platforms
---

### Post by Obs on 2007-06-04
So I'm trying to get WINE on my Ubuntu7.04 server machine. I followed all the directions [here]("http://www.winehq.org/site/download-deb"), but once I run sudo apt-get install wine, I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
        Depends: libaudiofile0 (>= 0.2.3-4) but it is not installable
        Depends: libesd-alsa0 (>= 0.2.35) but it is not installable or
                 libesd0 (>= 0.2.35) but it is not installable
        Depends: libgl1-mesa-glx but it is not installable or
                 libgl1 but it is not installable
        Depends: libglu1-mesa but it is not installable or
                 libglu1 but it is not installable
        Depends: libgphoto2-2 (>= 2.3.0) but it is not installable
        Depends: libgphoto2-port0 (>= 2.3.0) but it is not installable
        Depends: libice6 (>= 1:1.0.0) but it is not installable
        Depends: liblcms1 (>= 1.08-1) but it is not installable
        Depends: libsm6 but it is not installable
        Depends: libx11-6 but it is not installable
        Depends: libxau6 but it is not installable
        Depends: libxext6 but it is not installable
        Depends: libxslt1.1 (>= 1.1.20) but it is not installable
        Depends: libxt6 but it is not installable
        Depends: libxxf86vm1 but it is not installable
E: Broken packages



What is wrong?

---

### Post by pkarjala on 2007-06-04
My understanding is that WINE likes a GNOME or KDE install to run.  Ubuntu Server Edition, when installed, does not have either of these window managers.  You'd have to install GNOME or KDE on your server first in order to get WINE working.

---

### Post by Obs on 2007-06-04
> **pkarjala said:**
> My understanding is that WINE likes a GNOME or KDE install to run.  Ubuntu Server Edition, when installed, does not have either of these window managers.  You'd have to install GNOME or KDE on your server first in order to get WINE working.

I figured it was something like that.

But could WINE itself run completely from the terminal without a GUI once installed?

---

### Post by pkarjala on 2007-06-04
From the WINE FAQ at [http://www.winehq.org/site/docs/wine-faq/index#WHAT-DO-I-NEED-IN-ORDER-TO-USE-WINE]("http://www.winehq.org/site/docs/wine-faq/index#WHAT-DO-I-NEED-IN-ORDER-TO-USE-WINE"):

"3.12. Will Wine run under any X window manager? Does it require a window manager at all?

Wine is window manager independent, so the X window manager you choose to run has (almost) no bearing on your ability to run MS Windows programs under Wine. Wine uses standard X libraries, so no additional ones are needed. Wine has its own window management, which acts like MS Windows. It can be turned off to use the native window manager by modifying Managed or Desktop settings in winecfg."

They mention that it's dependant upon X libraries, so if you don't have an X client installed, I'd imagine it won't work.

That said, you might be able to get a better answer from the WINE forums.  :)

---

### Post by dmizer on 2007-06-05
think about the program you want to install in wine ... does it run in command line only?  my guess is that the answer to this ... is no.  therefore, you will need an x server to run the application in wine.  so even if you COULD install wine in command line only, you still wouldn't be able to run the software without installing x.

what are you trying to do such that you want an application to run in wine on your server?

---

### Post by Obs on 2007-06-05
> **dmizer said:**
> think about the program you want to install in wine ... does it run in command line only?  my guess is that the answer to this ... is no.  therefore, you will need an x server to run the application in wine.  so even if you COULD install wine in command line only, you still wouldn't be able to run the software without installing x.

what are you trying to do such that you want an application to run in wine on your server?

The program does run entirely in a command line. It's just a dedicated server command line thing.

---

### Post by pkarjala on 2007-06-05
What program is it?  Is there an equivalent that might already be available in Linux so that you don't have to install WINE to get it to work?

---

### Post by Obs on 2007-06-06
> **pkarjala said:**
> What program is it?  Is there an equivalent that might already be available in Linux so that you don't have to install WINE to get it to work?

No chance, it's an indie game server. 

My sources.list file also appears to be empty, so I can't do an apt-get install ubuntu-desktop or anything. Where can I get some sources?

---

### Post by dmizer on 2007-06-07
your sources.list file is most certainly not empty, unless you actively deleted it after ubuntu was installed.  you could not have installed ubuntu if it was empty.  double check your syntax and make sure that all your "/" are in place, and spelling is EXACTLY correct.

do you even know for sure if the game server will run in wine?  are you sure there's not a port for linux ... you might consider opening a dialogue with the developers of the server.

if it turns out that this game server is indeed windows only, and if this game server is your killer app., you'll find yourself in one of the two following positions:
1) ubuntu of any flavor is not going to be your best server solution.
2) run two servers ... one windows server for your game, and another for all other server tasks.

---

### Post by netlogic on 2007-06-07
The simplest way is just type

1) sudo apt-get install wine fluxbox
fluxbox is the lightest window manager and probably extra 2megs install.
2) ssh -X into the box
3) run winecfg and it should forward winecfg to your desktop and create
a .wine folder on the server.

---

### Post by Obs on 2007-06-07
> **dmizer said:**
> your sources.list file is most certainly not empty, unless you actively deleted it after ubuntu was installed.  you could not have installed ubuntu if it was empty.  double check your syntax and make sure that all your "/" are in place, and spelling is EXACTLY correct.

do you even know for sure if the game server will run in wine?  are you sure there's not a port for linux ... you might consider opening a dialogue with the developers of the server.

if it turns out that this game server is indeed windows only, and if this game server is your killer app., you'll find yourself in one of the two following positions:
1) ubuntu of any flavor is not going to be your best server solution.
2) run two servers ... one windows server for your game, and another for all other server tasks.

It actually has 1 or 2 links, but nothing else. It's completely empty, and people keep telling me to do sudo apt-get installs of various things but the packages are never found.

---

### Post by dmizer on 2007-06-07
well, in order to install packages, you really don't need any more than the following:
```
 deb http://archive.ubuntu.com/ubuntu feisty main restricted
 deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
 
 deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
```

you might also want to add these two lines to install packages located in the universe/multiverse repositories:
```
 deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
```

you might also take a look in /etc/apt/ ... there is a good chance that you have a backup of your default source list called something like "source.list_backup_200702191608" or "sources.list~" or something equally clever.

if you are dead set on trying to get the thing to work in wine, your best bet is to do a fresh gui based install of something light like xubuntu.  every time i've installed a gui desktop on top of a server install, i've wound up with a slow, unresponsive, basically useless desktop.

---

