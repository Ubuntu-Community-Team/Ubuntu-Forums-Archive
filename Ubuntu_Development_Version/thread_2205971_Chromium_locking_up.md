---
title: "Chromium locking up"
date: 2014-02-16
forum: Ubuntu Development Version
---

### Post by NM5TF on 2014-02-16
anyone else having problems with Chromium locking up....not the whole OS as has
been reported in other threads....just Chromium locking up with 2-3 tabs open & just
sitting idle for an hour or so.....this has been happening for a while now....

I do NOT see this happening with FireFox, just Chromium....

I also do daily update/upgrades.....haven't been doing dist-upgrades, but may have
to try that next....

has a bug report already been opened ???

if not, I will do so from my launchpad account....

tommy

edit: sudo agt-get dist-upgrade did NOT fix problem

---

### Post by Bucky Ball on 2014-02-16
*Post moved to own thread.*

You greatly improve your chances of getting support by posting your own thread rather than tagging on to one that has nothing to do with it and an unrelated thread title. 

First thing's first, are you using 14.04 LTS? Sorry if this is obvious and why you posted in this section, but need to check as you don't mention it. This section of the forums is for 14.04 only. All other support questions should be posted in other areas.

---

### Post by NM5TF on 2014-02-16
yes I am using 14.04 LTS.....that's why I posted it in that section...also, the thread was titled
"problems I have encountered in 14.04" so I figured that was an appropriate place to post....my bad
I guess

thanx for moving/starting a new thread

tommy

---

### Post by VMC on 2014-02-16
> **NM5TF said:**
> anyone else having problems with Chromium locking up....not the whole OS as has
been reported in other threads....just Chromium locking up with 2-3 tabs open & just
sitting idle for an hour or so.....this has been happening for a while now....

...

Not sure it this is the same issue or related, but I use Chrome, and **only** Ubuntu 14.04 do I see Chrome not responding for several minutes. Then all at once It starts again showing the requested pages.
Xubuntu, GNOME don't have this problem.

---

### Post by NM5TF on 2014-02-16
> **VMC said:**
> Not sure it this is the same issue or related, but I use Chrome, and **only** Ubuntu 14.04 do I see Chrome not responding for several minutes. Then all at once It starts again showing the requested pages.
Xubuntu, GNOME don't have this problem.

looks like we have same CPU/GPU combination....not sure if that is related to problem or not...

and yes, it ONLY happens with 14.04 using Chromium...based on Chrome AFAIK.....does NOT
happen running Ubuntu 12.04.4 or Mint 16....

however, Chromium never does unlock...I have to close it & re-open it to continue...

tommy

---

### Post by Bucky Ball on 2014-02-16
Are you both running Pepper Flash?

---

### Post by VinDSL on 2014-02-16
No probs here.

I've been DJ'ing on Plug.DJ for 14 hours - with no lockups -- same browser instance...

---

### Post by VMC on 2014-02-16
> **Bucky Ball said:**
> Are you both running Pepper Flash?
No. I'm not running it on either Xubuntu or Gnome-Ubuntu and they both work without a problem.

---

### Post by NM5TF on 2014-02-16
> **Bucky Ball said:**
> Are you both running Pepper Flash?

no...using Shockwave Flash 11.2 r202

tommy

---

### Post by Bucky Ball on 2014-02-16
Wondering if that would make a difference, but may just confuse the issue. Pepper Flash is exclusive to Chromuim browser and installs in that, is not system wide, and give you Flash 12.2, the latest, and will continue to upgrade.

The Flash you're using now is the last version that will be supported in Ubuntu. Adobe are giving security updates for it for the next few years I believe, but that is it. There will be no going beyond 11.2 ... unless you use Pepper Flash in Chromium.

Just throwing that in ...

PS: Before dist-upgrade, *always* run

sudo apt-get update
sudo apt-get upgrade

... just in case you didn't (I like to run these two separately, especially on a testing release, so I have a better idea of what error messages, if any, each throws up). ;)

---

### Post by NM5TF on 2014-02-17
> **Bucky Ball said:**
> 

PS: Before dist-upgrade, *always* run

sudo apt-get update
sudo apt-get upgrade

... just in case you didn't (I like to run these two separately, especially on a testing release, so I have a better idea of what error messages, if any, each throws up). ;)

as I mentioned in my 1st post.....

daily I run:

sudo apt-get update
sudo apt-get upgrade

now will also run

sudo apt-get dist-upgrade

will also take a look at Pepper flash

tommy

---

### Post by NM5TF on 2014-02-17
OK...will see what happens now after doing this:

```
sudo apt-get install pepperflashplugin-nonfree
```

followed by this:

```
sudo update-pepperflashplugin-nonfree --install
```

it is available from 14.04 repositories...

found the information here:

[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

tommy

---

### Post by Bucky Ball on 2014-02-17
Don't forget, from this page, to then use one of these to actually install it:

sudo update-pepperflashplugin-nonfree --install --beta --unverified
sudo update-pepperflashplugin-nonfree --install --unstable --unverified

The commands you give only install the installer, not Pepper by the looks of the link you posted. ;)

---

### Post by NM5TF on 2014-02-17
according to chromium plugins this is what I have now...

Adobe Flash Player (2 files) - Version: 12.0.0.44
Shockwave Flash 12.0 r0
Name:	Shockwave Flash
Description:	Shockwave Flash 12.0 r0
Version:	12.0.0.44
Location:	/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl


am I missing something ???

---

### Post by Bucky Ball on 2014-02-17
Seems not. Is it still locking up or it hasn't been long enough to know yet?

I use Synaptics and according to that it is a simple matter of installing pepperflashplugin-nonfree and that is it. No need to do anything else. Your very first command did that so I guess all is well.

---

### Post by NM5TF on 2014-02-17
4 tabs open now...so far no lock up....will let it sit idle overnite...

going to bed now....

if still working in morning will mark as solved....

tommy

---

### Post by Bucky Ball on 2014-02-17
If it all works out, interesting bug report for 14.04 that should be passed on to Launchpad if you wouldn't mind. If Chromium browser gets moody in 14.04 without Pepper, we need to know about that. Interesting. :-k

Look forward to further updates on this ...

---

### Post by NM5TF on 2014-02-17
seems to be fixed now....has been idle with 4 tabs open for 8 hours with no lock up...

thanx for tip on Pepper Flash Bucky Ball !!!

marking it solved

still don't understand why it happened...but happy it's working correctly

tommy

---

### Post by Bucky Ball on 2014-02-17
heh ... *shrugs* Testing releases and all that, shifting sands. I had no idea it was going to make any diff, but just an idea. Seems to be a lot of that in +1. ;)

Only use Firefox myself but have installed Pepper for a couple of friends who want to watch iView tv, which you need modern flash for here, more's the pity.

Good luck and enjoy.

---

### Post by NM5TF on 2014-02-17
Launchpad bug report filed this morning......

[https://bugs.launchpad.net/ubuntu/+source/chromium/+bug/1281171](https://bugs.launchpad.net/ubuntu/+source/chromium/+bug/1281171)

thanx for help

tommy

---

### Post by QDR06VV9 on 2014-02-17
Now if you really want some fun;)
Now, if you want to install Pipelight on Ubunt 14.04 Trusty Tahr, Ubuntu 13.10 Saucy Salamander, Ubuntu 13.04 Raring Ringtail, Ubuntu 12.10 Quantal Quetzal, Ubuntu 12.04 Precise Pangolin, Linux Mint 16 Petra, Linux Mint 15 Olivia, Linux Mint 14 Nadia, Linux Mint 13 Maya, Pear OS 8, Pear OS 7 and Elementary OS 0.2 Luna, you have to add the pipelight ppa to your system (also, remove the other repos providing pipelight and related packages, in order to avoid issues), update the local repository index and install the pipelight package.
How to [Here]("http://linuxg.net/ubuntu-14-04-trusty-tahr-may-come-with-pipelight-support/")
Been Using it for about a month now Works A Treat!:D

---

### Post by zika on 2014-02-17
> **runrickus said:**
> Now if you really want some fun;)
[COLOR=#555555][FONT=Arial]Now, if you want to [/FONT][/COLOR][COLOR=#555555][FONT=Arial]install Pipelight on Ubunt 14.04 Trusty Tahr, Ubuntu 13.10 Saucy Salamander, Ubuntu 13.04 Raring Ringtail, Ubuntu 12.10 Quantal Quetzal, Ubuntu 12.04 Precise Pangolin, Linux Mint 16 Petra, Linux Mint 15 Olivia, Linux Mint 14 Nadia, Linux Mint 13 Maya, Pear OS 8, Pear OS 7 and Elementary OS 0.2 Luna[/FONT][/COLOR][COLOR=#555555][FONT=Arial], you have to add the pipelight ppa to your system (also, remove the other repos providing pipelight and related packages, in order to avoid issues), update the local repository index and install the pipelight package.
How to [Here]("http://linuxg.net/ubuntu-14-04-trusty-tahr-may-come-with-pipelight-support/")
Been Using it for about a month now Works A Treat![/FONT][/COLOR]:DOr just steal .so file from GChrome .deb file or DL it and instruct (command-line switch) Chromium to use it... Using it for months... ;)
Before couple of weeks there was a need to give version number on CL (from manifest.json) but that is now obsolete, no need for that anymore...

---

