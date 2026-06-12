---
title: "ubuntu software center"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-02-21
is it just me but cant get the software center to open. i am up to date in all updates. if i try to  uninstall from the spm get a message that it will also uninstall the ubuntu-desktop. the version i have is 5.19. no big deal just curious. also if i just reinstall from the spm still have the same problem.

---

### Post by ventrical on 2012-02-21
It's OK here..

---

### Post by rburkartjo on 2012-02-21
ven tks must be something on my end i will just wait until beta1 comes out and see if that fixes the issue

---

### Post by Stinger on 2012-02-21
Did you try to launch software-center from a terminal to see what error you get ?
```
software-center
```

---

### Post by Gregory Lee on 2012-02-21
I have not been getting consistent good results from clicking on an icon in the launchbar.  However, right-clicking on an icon there, then on the menu this invokes, clicking on the name of the application always works for me.

---

### Post by rburkartjo on 2012-02-21
sti didnt work think i found my mistake i did a direct upgrade form 11.10 and had mate installed when i updated. 

see below## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import

think i should delete(# out) all from software sources or just the last one. tks

---

### Post by rburkartjo on 2012-02-21
here is my complete output

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import

---

### Post by Stinger on 2012-02-22
I would recommend that you backup anything you need and do a clean new installation of precise.

It seems like something went wrong when you upgraded oneiric

I tried it myself upgrading my oneiric to precise alpha1 but had to do a fresh install of precise to get things working.

---

### Post by rburkartjo on 2012-02-22
sti tks will do if b1 release next week doesnt fix. that is the only problem i have encountered with 12.04 so cant complain. and usually spm not software center to install anything

---

### Post by Stinger on 2012-02-22
Here is my /etc/apt/sources.list
You can use it to compare.
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20120213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20120213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Another possibility is to clean your installation using [ubuntu-tweak]("http://ubuntu-tweak.com/")
Here is the ppa for the stable version:
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/~tualatrix/+archive/ppa")

And here unstable next ppa ( I use it ):
[https://launchpad.net/~tualatrix/+archive/next]("https://launchpad.net/~tualatrix/+archive/next")
Hope it helps.

---

### Post by rburkartjo on 2012-02-22
tks sti i use ubuntu tweak after all updates. might try to make sure my software sources reflect yours. appreciate the time to offer suggestions

---

### Post by rburkartjo on 2012-02-23
[http://askubuntu.com/questions/81263/how-to-i-fix-software-center-after-installing-the-linux-mint-mate-desktop](http://askubuntu.com/questions/81263/how-to-i-fix-software-center-after-installing-the-linux-mint-mate-desktop)

this is how i fixed went to  (2

and changed to read
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=Precise
DISTRIB_DESCRIPTION="Ubuntu 12.04"

---

### Post by rburkartjo on 2012-02-23
okay i spoke too soon does work but if i reboot i have to change again any idea how to make permanent?

---

### Post by rburkartjo on 2012-02-23
note i am running ubuntu 12.04 but get this output when i run
ray@ray-GC660AA-ABA-SR5123WM:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 12 Fluxbox
Release:	12
Codename:	lisa

---

### Post by cariboo on 2012-02-23
I'd suggest trying:

```
update-manager -d
```

to see if you are given the choice to upgrade to Precise.

---

### Post by rburkartjo on 2012-02-23
car no didnt get the option. i know i have 12.04. just trying to fix everything else is fine. there must be a way all my repos are precise and all the updates i get are for them. just weird. tks

---

### Post by rburkartjo on 2012-02-23
note this output when try to open ubuntu-software from terminal

```
ray@ray-GC660AA-ABA-SR5123WM:~$ software-center &
[1] 3276
ray@ray-GC660AA-ABA-SR5123WM:~$ ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 3, in <module>
    from debfile import DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    from softwarecenter.backend.channel import is_channel_available
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 25, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 184, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 162, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint
```

however when i make the changes as mentioned earlier it opens fine

---

### Post by cariboo on 2012-02-23
I don't use either Mint or the Software Centre, but does Mint modify the Software Centre in any way, and if so, make sure you don't have any Mint repositories enabled, and try an update/upgrade from the command line to see if that fixes the problem.

---

### Post by rburkartjo on 2012-02-24
i know how to fix but cant figure out how
i need to make a script so that so that
lsb-release
changes to
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=Precise
DISTRIB_DESCRIPTION="Ubuntu 12.04"
after startup

so it wont change back to 
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=12
DISTRIB_CODENAME=lisa
DISTRIB_DESCRIPTION="Linux Mint 12 Fluxbox"
editing the above with gedit wont work it always reverts back.
tks

---

### Post by rburkartjo on 2012-02-24
just weird once i make the changes i can log in and out of any type of ubuntu session. unity,classic etc and can use software-center.

---

### Post by cariboo on 2012-02-24
One last thing, /etc/lsb-release should be owned by root, and have permissions of 644, could that be the problem?

---

### Post by rburkartjo on 2012-02-24
car reads rw-r-r that should be 644 or am i incorrect

---

### Post by rburkartjo on 2012-02-24
i have ubuntu 12.04 on its own partition and also a separate home partiton, and another one for linux mint 12. however on my boot menu it shows linux mint 12 flux(however the kernel is for ubuntu 12.04) and another for  linux mint 12. i actually upgraded 11.10 from the command line to 12.04. and when i boot into flux i am using the precise repos. got to be an easy way to fix the only problem i have is with the software center. i am extremely please with 12.04 so far no problems what so ever except the one i mentioned.

---

### Post by rburkartjo on 2012-02-28
fixed it finally. manually changed my lsb-release then launched the software center and removed these packages:mint-meta-mate and linuxmint keyring.

---

### Post by cariboo on 2012-02-28
> **rburkartjo said:**
> fixed it finally. manually changed my lsb-release then launched the software center and removed these packages:mint-meta-mate and linuxmint keyring.

It's good to see you got the problem solved.

---

