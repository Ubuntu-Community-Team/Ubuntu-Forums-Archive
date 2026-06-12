---
title: "Installing Wine to Kubuntu"
date: 2009-11-06
forum: Wine
---

### Post by a_z1_9scores on 2009-11-06
Okay, before we start, I&#8217;m a Linux newbie, so be gentle and bear with me. I decided to use Kubuntu (I now see why they say Vista stole from Ubuntu) and I can't seem to install Wine. I know I need a repository thingie called Agape or something like that (It was 2 in the morning). I can't find an installer for that, so I&#8217;m sure I&#8217;ll have to use the terminal. I used the gnome desktop ubuntu 8.10 and got wine working on there, so I know a little. My question is how do I even begin? Thanks for bearing with me.

---

### Post by beastrace91 on 2009-11-06
Go to [here](http://wine.budgetdedicated.com/archive/index.html) and download the latest .deb list for your architecture for Ubuntu 9.04 (they do not have pre-compiled ones yet just for 9.10 - the 9.04 ones should work fine)

Then just double click the .deb file when it is done downloading and it will guide you through installing the package.

Regards,
~Jeff

---

### Post by a_z1_9scores on 2009-11-06
I'm trying that now and I"m getting a host of errors for different versions. Here's the one for wine 1.1.29, but most of the errors look similar to...

> (Reading database ... (Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%(Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 92265 files and directories currently installed.)
Unpacking wine (from .../5587.0.wine_1.1.29~winehq0~ubuntu~9.04-0ubuntu2_i386.deb) ...
dpkg: error processing /var/tmp/kdecache-ubuntu/krun/5587.0.wine_1.1.29~winehq0~ubuntu~9.04-0ubuntu2_i386.deb (--install):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/wine/ole2nls.dll16.so': No space left on device
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg-deb (subprocess): failed in buffer_write(fd) (5, ret=-1): failed to write to pipe in copy: Broken pipe
[B]Errors were encountered while processing:
 /var/tmp/kdecache-ubuntu/krun/5587.0.wine_1.1.29~winehq0~ubuntu~9.04-0ubuntu2_i386.deb[/B]

besides the errors for 1.1.27 and 1.1.32 which reads:

> [COLOR="Red"]Error: Dependency is not satisfiable: libopenal1[/COLOR]

I tried to install the libopenal1 package already, but it didn't work. I'm currently Googling around for answers.

---

### Post by beastrace91 on 2009-11-06
Huh. It appears the Jaunty Wine packages don't want to install on Karmic for you. If you need the latest Wine release you can always compile from source (if you want help with this let me know - its easy just takes a few steps) or you can just install the slightly older "stable" Wine package from the default Ubuntu repos with the command ```
sudo apt-get install wine
``` in konsole.

~Jeff

---

### Post by a_z1_9scores on 2009-11-06
Do I need to download something because I got this when I tried to run the code:

```
ubuntu@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
ubuntu@ubuntu:~$
```

---

### Post by a_z1_9scores on 2009-11-06
Maybe it matters or not but I'm using the live cd. I didn't think of it until now but maybe that affects it.

---

### Post by beastrace91 on 2009-11-06
Yea that does change things a bit... Can you not install Kubuntu to your system? You also know any changes you make are going to be lost when you reboot correct?

Try running the following two commands in order: ```
sudo apt-get update
sudo apt-get install wine
```

Also note that while running in the LiveCD environment you are not going to have all of the system updates that have been released since the iso was posted.

~Jeff

---

### Post by a_z1_9scores on 2009-11-06
I do, but I rarely restart this computer, so that's not a big issue for me. I tried both codes and while the update worked, wine didn't, giving me the same error code. I think I'll try my hand at compiling Wine.

The guides I keep finding use the Adept package manager. Do you know how to compile and install Wine without using Adept, because I can't find any install files for it.

---

### Post by edin9 on 2009-11-06
You will also need to change the path(command) for 'Browse C:\ Drive' in KDE Menu Editor to; ```
dolphin /home/yourusernamehere/.wine/drive_c
``` Or it doesn't work.

---

### Post by beastrace91 on 2009-11-06
Try the following to compile Wine from source (again I would like to recommend actually installing *ubuntu to your hard drive)

```
sudo apt-get install build-essentail
sudo apt-get build-dep wine
```

How ever if your system cannot see a Wine package for some reason that second command might not work properly - if this is the case you are about to be in for a whole headache of manual dependency finding.

After the above two commands run download the latest Wine source from [here](http://sourceforge.net/projects/wine/files/Source/)

Extra the file it gives you and then using terminal (konsole) change directory to the location of the extracted files (to do this use the **cd mydirectory** command)

Once you are in the same directory as the Wine source run the following commands in order ```
./configure
make
sudo make install
```

And you should now have Wine installed and working. Again I would like to say you should be installing *ubuntu to a disc. As it is a rather lengthy process to have to repeat.

~Jeff

---

### Post by a_z1_9scores on 2009-11-07
Hmmm

I had to restart my computer because an application froze. Originally, I was unable to install Firefox, and now I was, so in light of this I went back to the earlier post and tried to install Wine and it worked like a charm. Thanks, Edin and especially Beastrace for the help.

---

### Post by tehsmo on 2009-11-18
I have this same problem, but have not had the fortunate of a crashed application to fix it.  Running Ubuntu 9.10.  When I try to run *sudo apt-get install wine* I get this:

```
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
```And when I run *sudo apt-get build-dep wine* I get this:

```
Package prelink is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  execstack
E: Package prelink has no installation candidate
E: Failed to satisfy Build-Depends dependency for wine: prelink
```In Software Sources, I have every repository checked.  Lastly, here's a copy of my /etc/apt/sources.list.  Should I have karmic-backports enabled?  It's the only thing that's commented out...

EDIT: Tried uncommenting karmic-backports, running *sudo apt-get update*, and installing wine again.  Still no installation candidate.

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by tehsmo on 2009-11-18
On a similar note, I had the exact same issue with rtorrent and with pygame; maybe universe is messed up for me entirely?  Will have to check that out.

EDIT:  went back to my old alma mater and added their mirror to my sources.list, so now the universe section looks like this:

```

deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://lug.mtu.edu/ubuntu karmic main universe

```

And that worked.  So I went and added a "main" before the "universe" in the original line, and commented out my new one, then ran apt-get update twice.  That also seems to work.

---

### Post by beastrace91 on 2009-11-18
You can also download the latest Wine packages from [here](www.winehq.org/download/deb).

Also just so you know its not uncommon for the repos to have issues on occasionally - if it is not working for you at a certain point be sure to give it some time and try again later.

Regards,
~Jeff

---

### Post by YokoZar on 2010-02-01
> **beastrace91 said:**
> Go to [here](http://wine.budgetdedicated.com/archive/index.html) and download the latest .deb list for your architecture for Ubuntu 9.04 (they do not have pre-compiled ones yet just for 9.10 - the 9.04 ones should work fine)

Then just double click the .deb file when it is done downloading and it will guide you through installing the package.

Regards,
~Jeff
Sorry for the confusion that I believe lead to this recommendation.  I've updated the sticky thread in this forum.

There is no reason to download a specific package like this and attempt to install by hand, and compiling from source is really unnecessary.  If you haven't installed Wine yet through Software Center (or synaptic) then you'll run into various issues just trying to double click a .deb.

---

