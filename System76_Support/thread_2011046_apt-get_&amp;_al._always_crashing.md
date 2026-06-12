---
title: "apt-get &amp; al. always crashing"
date: 2012-06-26
forum: System76 Support
---

### Post by fredsea on 2012-06-26
This is a Starling netbook, Star5, Driver 3.0.0. It works great (just one minor issue I'll ask about separately), and everything seemed fine after I updated to Ubuntu 12.04 (the previous update to 11.10 was also flawless).

However, recently, a big error alert popped up in the panel, mentioning an error in opening the package cache, and producing a very long list of duplicate sources, including System76 specific repositories. Any attempt to run Synaptic, Software Center or Update Manager, as well as apt-get from the command line, generate a similar error message, after which they all exit, and there is no way to run any of them. I didn't notice any special event that might have caused this problem. Not to mention that I do get duplicate sources errors in other installations, but they don't prevent apt-get from working.

The full message is attached as a text file (from running Synaptic)

I suppose I could reinstall from scratch (I would appreciate a reminder on how to include System 76 specific drivers and stuff), but maybe there's something less draconian I could do to cure the problem.

Thank you!

---

### Post by josephmills on 2012-06-26
try ```
sudo apt-get --fix-missing --fix-broken update
```
anything ?

also could you paste 
```
ls /etc/apt/sources.list.d/
```
and also 
```
cat /etc/apt/sources.list

```
thanks

---

### Post by fredsea on 2012-06-26
> **josephmills said:**
> try ```
sudo apt-get --fix-missing --fix-broken update
```
anything ?

also could you paste 
```
ls /etc/apt/sources.list.d/
```
and also 
```
cat /etc/apt/sources.list

```
thanks

First of all: THANKS! your first suggestion was magic, as now I can at least start Synaptic! I am still getting the same errors, though. In fact, before the "duplicate repositories" message, this comes up:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/planet76.com_repositories_._en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I seem to have a problem with System 76 stuff. Hoping to get to the bottom of this, I am attaching both sources.list and the listing of sources.list.d (with an additional *.txt extension to match the attachment requirements).

By the way, I appreciate your help sooooo much!

---

### Post by fredsea on 2012-06-26
Ooops! Things are not as good as I said they were. Somehow Synaptic started once, but when I tried again it was back to the same error message, and immediate crash :(

---

### Post by josephmills on 2012-06-26
Ok let start out on the sources list 
in terminal 
```
gksudo gedit /etc/apt/sources.list
```

then make it look like this 
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe
#deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##security
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
```




Next we need to take care of the system 76 stuff 

this is what it looks like
```
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
system76.list
system76.list.distUpgrade
system76.list.save
```


 I need to see inside of them so 
```
cat /etc/apt/sources.list.d/*

```

then paste here plz and thanks :)

---

### Post by fredsea on 2012-06-26
> **josephmills said:**
> 
[...]

Next we need to take care of the system 76 stuff 

this is what it looks like
```
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
system76.list
system76.list.distUpgrade
system76.list.save
```


 I need to see inside of them so 
```
cat /etc/apt/sources.list.d/*

```

then paste here plz and thanks :)
OK, I guess I had a senior moment, because I was sure I answered back :(. OK, sorry about that- I am so  grateful of your support that it feels really bad to botch things this way...

I am attaching the output of the cat command on the sources.list.d/* files

---

### Post by layolayo on 2012-06-26
I had this yesterday morning, sorted with the following:

sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

For reference: [http://ubuntuforums.org/showthread.php?t=1750755](http://ubuntuforums.org/showthread.php?t=1750755)

---

### Post by josephmills on 2012-06-26
[B]EDIT
[/B]


```
cd /etc/apt/sources.list.d/
```
then 
```
mkdir ~/.oldsystem76
```
then 
```
sudo mv system76.list.distUpgrade ~/.oldsystem76

```

```

sudo mv system76.list.save ~/.oldsystem76
```

then on to google. 

```
mkdir ~/.old_google_talk
```
```
mv google-talkplugin.list.distUpgrade ~/.old_google_talk
```
```
mv google-talkplugin.list.save ~/.old_google_talk
```


then 
```
ls /etc/apt/sources.list.d/
```

You should have 2 files now there. 

google-talkplugin.list
system76.list

if correct next step if not post what you got here. 

NEXT:
```
sudo apt-get --fix-missing --fix-broken update
```

If you have any duplicate errors just post them.

---

### Post by fredsea on 2012-06-27
> **josephmills said:**
> [B]EDIT
[/B]


```
cd /etc/apt/sources.list.d/
```
then 
```
mkdir ~/.oldsystem76
```
then 
```
sudo mv system76.list.distUpgrade ~/.oldsystem76

```

```

sudo mv system76.list.save ~/.oldsystem76
```

then on to google. 

```
mkdir ~/.old_google_talk
```
```
mv google-talkplugin.list.distUpgrade ~/.old_google_talk
```
```
mv google-talkplugin.list.save ~/.old_google_talk
```


then 
```
ls /etc/apt/sources.list.d/
```

You should have 2 files now there. 

google-talkplugin.list
system76.list

if correct next step if not post what you got here. 

NEXT:
```
sudo apt-get --fix-missing --fix-broken update
```

If you have any duplicate errors just post them.
That was amazing! I had to tune out to do some paid work, but when I got back and followed your suggestions, I got to update my software right away, and, at least for now Synaptic and friends start without any duplicate repository, or any other kind, error messages.

THANKS!!!!

---

