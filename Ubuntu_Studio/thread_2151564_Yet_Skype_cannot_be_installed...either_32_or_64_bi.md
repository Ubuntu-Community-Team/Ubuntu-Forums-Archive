---
title: "Yet Skype cannot be installed...either 32 or 64 bits."
date: 2013-06-05
forum: Ubuntu Studio
---

### Post by Maxei on 2013-06-05
Hi, my laptop is running Ubuntu Studio 12.04, in 64 bit. I cannot solve the problem to install Skype. Here is what I do:

1. I have downloaded three package versions from official site, which are:

skype-ubuntu_4.0.0.8-1_amd64.deb,
skype-ubuntu_4.0.0.8-1_i386.deb,
skype-ubuntu-precise_4.2.0.11-1_i386.deb.

2. Run the package with Gdebi. The first one produces the error: "Cannot install 'ia32-libs". If I try the second or the third package, the error for both: "Cannot install 'libqt4-dbus:i386".

3. If I try to install ia32-libs using Synaptic, it says it needs to remove about 180 packages, most or all the applications that I have!, and would install 130 packages, most are lib-something. Obviously this is insane and unacceptable.

4. If I try to install libqt4-dbus:i386, well, I find out there is already a similar one installed: "libqt4-dbus". So, why then it is not recognized? Since there is no libqt4-dbus:i386 in the Synaptic list, maybe they are the same thing (???).

So, there is the problem: neither 32 bit nor 64 bit official packages of Skype can't be installed, because there are either _conflicts_ or _dependencies_ unmet. I hope someone can help or give hints; I have read several posts but they don't help. Thanks in advance.

By the way, FYI:

"$ dpkg --print-foreign-architectures" gives "i386".

Also, tThere are 10 packages that can be updated (upgraded?), but if I do so, three applications that I need will be removed: ffmpeg, libav-tools, ubuntustudio-video, so I am afraid to break my system with this upgrade, by loosing these packages I may no longuer be able to view dvds or to do encoding...

---

### Post by zequence on 2013-06-05
Install it from the partner repo. You need to enable it first. Either using the gui tool "Software Sources", or manually uncomment the repos in /etc/apt/sources.list

Then, do:

```
sudo apt-get update && sudo apt-get install skype
```

---

### Post by Maxei on 2013-06-05
> **zequence said:**
> Install it from the partner repo. You need to enable it first. Either using the gui tool "Software Sources", or manually uncomment the repos in /etc/apt/sources.list

Then, do:

```
sudo apt-get update && sudo apt-get install skype
```

What do you mean by uncomment the repo /etc/apt/sources.list? By the way, the Canonical Partners repositories are enabled. If I do "$ sudo apt-get install skype-bin"

The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not going to be installed
                  Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
                  Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libssl1.0.0:i386 but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: sni-qt:i386 but it is not going to be installed
                  Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Clearly the problem is not the package, whether is in the repository or in the official site.

---

### Post by zequence on 2013-06-05
Uncommenting a line in a configuration file usuall means removing the "#" or the ";" that it begins with. Commented lines are not read.

You've probably installed something, perhaps from a PPA. Which means, you probably need to remove or restore something in order to be able to install skype in this case.
On a clean system, skype installs just fine on an amd64 Ubuntu Studio 12.04. I just checked.

---

### Post by Maxei on 2013-06-05
Thanks Zequence, but I need more precise information. What do you mean by saying "installing something from a ppa"? Is it not clear to say that the partners repo is enabled? from where else the system will get the skype.bin package if I request to install with apt-get? also, your vague answer "remove something" is unhelpful, what would be that "something"? Sorry, but your comment does not help me as is now. Please tell me what would be the right repo if you have it, and then i will try it. Thanks.
PS. by the way, the install is clean, and there are no problems, other than that.

---

### Post by zequence on 2013-06-05
I'm not being vague. It's just impossible for me to know how you have changed your system. 

As I said, you have installed something, or made some change to the system that won't let you install Skype.
I can't tell you exactly what to do, as I don't know what you have done.

But, I can tell you that on a clean install, you will be able to install skype.

PPA == personal package archive. They are hosted at [http://launchpad.net](http://launchpad.net). A lot of tutorials will ask you to add one.
If there are any files in /etc/apt/sources.d/, then probably you've added a PPA.

---

### Post by Maxei on 2013-06-05
Thanks Zeq,
My system has a /etc/apt/sources.list.d/ directory, which contains 5 files: Medibuntu.list; medibuntu.list.save; ubuntu-wine-ppa-precise.list; webupd8team-java-precise.list; and webupd8team-java-precise.list.save.  Is this what you mean, that I may have installed something that is not original for  Ubuntu Studio? Actually, I remember to have installed java and tried to install wine (this one cannot be installed either, in similar problem to skype). 

Concerning /etc/apt/sources.list, this are the contents; please let me know if there is some ppa that in your opinion has messed up my system; perhaps,like you said, I installed "something" that removed or changed the way apt-get manipulates, so it may not be anymore compatible with the available files. As far as I remember, the programs that I installed were Xine, and maybe some codecs to be able to view DVDs, some audio stuff. Anyways, here is the list of ppas in sources.list:

# deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release amd64 (20120818)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release amd64 (20120818)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release amd64 (20120818)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release amd64 (20120818)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release amd64 (20120818)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Hope this can reveal more about my system. Thanks again Zeq.

---

### Post by zequence on 2013-06-05
this is a PPA, and most probably the one that causes you problems ubuntu-wine-ppa-precise.list.

If you want to give it a shot, it means removing the latest wine.

You need to remove /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:

```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
```

re-read the list of aivailable packages after removing the PPA

```
sudo apt-get update
```

You might need to remove the wine packages. You can skip this step at first. If the rest didn't work, come back here and redo everything from here

```
sudo apt-get remove wine1.4 wine1.5
```

clean up if you uninstalled wine

```
sudo apt-get autoremove
```

then install skype

```
sudo apt-get install skype
```

---

### Post by Maxei on 2013-06-09
Thanks Zequence,
I followed your advice, in the order you mentioned. However, it didn't work. Here's the output:

$ sudo apt-get remove wine1.4 wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wine1.5' can't be removed
Package wine1.4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:
The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:
The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not going to be installed
                  Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
                  Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libssl1.0.0:i386 but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: sni-qt:i386 but it is not going to be installed
                  Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by zequence on 2013-06-09
You got and error: 'Virtual packages like 'wine1.5' can't be removed'

Try doing:

```
sudo apt-get remove wine1.5:i386 wine1.5:amd64
```

---

### Post by Maxei on 2013-06-17
$sudo apt-get remove wine1.5:i386 wine1.5:amd64
Reading package lists... Done
Building dependency tree
Reading state information... Done
Virtual packages like 'wine1.5:i386' can't be removed
Virtual packages like 'wine1.5' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

for some strange reason, that 'virtual package' can't be removed; even if it could, I wonder if that would help solve the problem. Any ideas? thanks.

---

