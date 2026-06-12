---
title: "Aptitude attitude request for package help"
date: 2012-06-05
forum: Server Platforms
---

### Post by IanCBray on 2012-06-05
*** UBUNTU-NOOB-ALERT ***
SINCEREST APPOLOGIES for my inadvertant hijacking of Radom's
thread... which is why I reposted it here.  SORRY, RADOM!!

Hello, Ev'body... 
I'm having some strangeness happen with aptitude too... 
I guess it's more precise to say I find aptitude strange... 
Don't get me wrong-- I'm sure once I get used to it... 
I'll MUCH prefer apt to source-downloading, compiling, waiting... 
waiting... grabbing a sandwich... waiting... but for NOW... 
I'M stuck. Moderators-- please forgive me if I digress, 
I've read and re-read posts on apt to try to learn the 
package installer but I can't figure out what -I- have 
done in order to -undo-.

HW: Dell Inspiron 1100 512MB Ram 20GB HD A32 Bios Updated
( CRAZY--I KNOW )
SERVER 12.04 Installed AND works pretty well!!!
I don't -need- X-windows which is why I chose SERVER
I'm -VERY- vision-impaired and would rather use my cmdline.

I'm trying to get DOSBOX installed on this LT because 
I need an OldSchool environment for testing... LONG STORY...

when I do:

```
sudo apt-get install -f dosbox
```

I am told I have incomplete dependancies and/or 
held packages.

Here:
```

ian@puck:~$ sudo apt-get install -f dosbox
[sudo] password for ian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
dosbox : Depends: libsdl-sound1.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ian@puck:~$

```

Ok... I'm fine with installing libsdl-sound1.2 but when I try... I get yet MORE depend flags...
```

ian@puck:~$ sudo apt-get install -f libsdl-sound1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libsdl-sound1.2 : Depends: libmikmod2 (>= 3.1.10) but it is not installable
Depends: libsmpeg0 but it is not installable
Depends: libspeex1 (>= 1.1. but it is not installable
Depends: libvorbisfile3 (>= 1.1.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ian@puck:~$

```

OK... so I look at HELD pkgs:

```

ian@puck:~$ sudo aptitude search ~ahold

```

I have to " >> heldpkgs.doc " cause I get 575 lines of pkgs that I don't know what to do with. Did skroo-up the install?? 

I'm attaching the heldpkgs.doc if you wanna look-see.

I've tried '--fix-broken install' and 'update' flags and I guess I... no... I know I don't know what to do now. I'm not used to aptitude yet... I'm just used to Old Slackware & Mandrake & Gentoo... This is my first UBUNTU Box... Where do I go? What do I look at? Suggestions? 

Thanks in advance!
Respecftully, Ian

---

### Post by volkswagner on 2012-06-05
if you want to install a package don't use -f unless you are certain this will fix a broken situation.

If you believe or want to find out if you have broken packages run:

```
sudo apt-get install -f
```

Thus specify no package.  If you want to test/simulate to see what will happen without commit add -s.

```
sudo apt-get install -f -s
```

No changes will be made with the above command.

If you just want to install dosbox run:

```
sudo apt-get install dosbox
```

Of course you should update you list first before installing:

```
sudo apt-get update
sudo apt-get install dosbox
```

---

### Post by IanCBray on 2012-06-05
> **IanCBray said:**
> *** UBUNTU-NOOB-ALERT ***
SINCEREST APPOLOGIES for my inadvertant hijacking of Radom's
thread... which is why I reposted it here.  SORRY, RADOM!!

[QUOTE=volkswagner;12001607]if you want to install a package don't use -f unless you are certain this will fix a broken situation.

If you believe or want to find out if you have broken packages run:
```
sudo apt-get install -f
```

Thanks, Volkswagner... there are none 'broken' I guess but 
'held' and dosbox won't install.

```
ian@puck:/www$ sudo apt-get install -f
[sudo] password for ian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ian@puck:/www$

```
> 
Thus specify no package.  If you want to test/simulate to see what will happen without commit add -s.

```
sudo apt-get install -f -s
```
No changes will be made with the above command.
If you just want to install dosbox run:
```
sudo apt-get install dosbox
```
Of course you should update you list first before installing:
```
sudo apt-get update
sudo apt-get install dosbox
```


I've done all above... including the '-s' option you mentioned.
I may have misspoke (typed) when I said BROKEN... they're HELD.
and when I run the:
```
sudo apt-get install dosbox
```
I get the response (shown previously):
```

ian@puck:~$ sudo apt-get install dosbox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dosbox : Depends: libsdl-sound1.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ian@puck:~$

```
Here is apt-get install -f  (No PKG Output)
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And for " sudo apt-get update "
I have tonz of output... here's that final 10 lines...

```

Ign http://ubuntu.mirror.iweb.ca natty-updates/main Translation-en_US
Ign http://ubuntu.mirror.iweb.ca natty-updates/main Translation-en
Ign http://ubuntu.mirror.iweb.ca natty-updates/universe Translation-en_US
Ign http://ubuntu.mirror.iweb.ca natty-updates/universe Translation-en
Ign http://ubuntu.wallawalla.edu natty-updates/main Translation-en_US
Ign http://ubuntu.wallawalla.edu natty-updates/main Translation-en
Ign http://ubuntu.wallawalla.edu natty-updates/universe Translation-en_US
Ign http://ubuntu.wallawalla.edu natty-updates/universe Translation-en
Fetched 16.9 MB in 45s (373 kB/s)
Reading package lists... Done
ian@puck:~$ 

```

---

### Post by volkswagner on 2012-06-05
What does your sources file look like?

```
cat /etc/apt/sources.list
```

I see you have natty listed, but you say you're running 12.04.  Was this updated from previous versions?

What is the output of:
```
cat /etc/issue
```

---

### Post by IanCBray on 2012-06-05
> **volkswagner said:**
> What does your sources file look like?
```
cat /etc/apt/sources.list
```

I see you have natty listed, but you say you're running 12.04.  Was this updated from previous versions?
What is the output of:
```
cat /etc/issue
```

Volkswagner,

NO this is a SERVER 12.04 install... No Upgrade.
Dell Inspiron 1100 LapTop.
I chose SERVER b/c DESKTOP would not init the vidoe...
All I got was a BLANK SCREEN.

I'm pretty sure my sources.list is a mess... 
You'll find my outputs below.

cat /etc/apt/soureces.list
cat /etc/issue 

Thanks
OUTPUT OF:
```

ian@puck:~# cat /etc/apt/sources.list
deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release i386 (20120424.1)]/ precise main restricted
# UNIVERSE!!
#
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
### MULTIVERSE
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
#
deb http://mirrors.us.kernel.org/ubuntu/ natty-updates main universe
deb http://www.gtlib.gatech.edu/pub/ubuntu/ natty-updates main universe
deb http://www.club.cc.cmu.edu/pub/ubuntu/ natty-updates main universe
deb http://ubuntu.wikimedia.org/ubuntu/ natty-updates main universe
deb http://ubuntu.wallawalla.edu/ubuntu/ natty-updates main universe
deb http://ubuntu.mirrors.pair.com/archive/ natty-updates main universe
deb http://ubuntu.mirror.iweb.ca/ natty-updates main universe
deb http://ubuntu.media.mit.edu/ubuntu/ natty-updates main universe
deb http://ubuntu.arcticnetwork.ca/ natty-updates main universe
deb http://mirrors.xmission.com/ubuntu/ natty-updates main universe
deb http://mirrors.rit.edu/ubuntu/ natty-updates main universe
deb http://mirrors.ecvps.com/ubuntu/ natty-updates main universe
deb http://mirrors.easynews.com/linux/ubuntu/ natty-updates main universe
deb http://mirrors.ccs.neu.edu/ubuntu/ natty-updates main universe
deb http://mirrors.cat.pdx.edu/ubuntu/ natty-updates main universe
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ natty-updates main universe

ian@puck:~#cat /etc/issue
Ubuntu 12.04 LTS \n \l

ian@puck:~#

```

---

### Post by volkswagner on 2012-06-06
That sure is a mess, plus there is no mention of the version you are running.

Did you edit that file?  Did you make a backup before you did.  I think you should restore your backup or replace that sources.list with the correct info for 12.04 Precise Pangolin.

Depending how fresh the install is and how much stuff broke by installing the wrong package you may be in for a reinstall.

I am not running 12.04 so I don't have a clean sources.list to offer.

Perhaps someone can chime in if you need a correct sources.list, based on your location.

Again if you don't have too much time/data invested I'd suggest reinstall and don't mess with your source.list without understanding the impact it will have on your system.

---

### Post by IanCBray on 2012-06-06
> **volkswagner said:**
> That sure is a mess, plus there is no mention of the version you are running.
Did you edit that file?  Did you make a backup before you did.  I think you should restore your backup or replace that sources.list 
 
I DO (did) have a backup-- and I restored it thinking that was my
problem-- but NOTHING I tried worked.
I -DID- ALSO edit the file manually and even replaced it with a
cut-and-paste 'sources-list generator' I found attached to a-
nother forum.
> 
Depending how fresh the install is and how much stuff broke by installing the wrong package you may be in for a reinstall.


It WAS only 4 days fresh when I first posted... mayby 6 MAX.
I have a sneaky suspicion that when I opted IN for 
'MANUAL PKG SELECTION' is when I hosed it... whunoze!!

> I am not running 12.04 so I don't have a clean sources.list to offer.
No worries... I appreciate the attention, however!  I  
actually tar-ed my /etc directory and moved it offline 
to make my re-configuring easier... I figure doing a
side-by-side & line-by-line eval of my conf-files couldn't
hurt-- likely I'll learn sump'n!

> 
Perhaps someone can chime in if you need a correct sources.list, based on your location.
Again if you don't have too much time/data invested I'd suggest reinstall and don't mess with your source.list without understanding the impact it will have on your system.

CONSIDER IT DONE -- No... really... I did that just now!!
Finished it this early afternoon... did the
```

suto apt-get update
suto apt-get upgrade
suto apt-get install dosbox

```
and I'm off to the races again!
Now... if I can just figure out rsyslogd.  ROFL!
I'd appreciate any linkys to good rsyslogd how-toos!

With this-- I guess we can consider ths [SOLVED].

Thanks for ev'body's help and time!
Respectfully,
Ian  C. Bray

---

