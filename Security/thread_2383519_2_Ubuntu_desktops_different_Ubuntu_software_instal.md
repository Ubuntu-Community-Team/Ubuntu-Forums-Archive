---
title: "2 Ubuntu desktops different Ubuntu software installer"
date: 2018-01-26
forum: Security
---

### Post by cam17 on 2018-01-26
I have what should be 2 identical Ubuntu Desktops. One has version 15.12 of the Ubuntu software and the other has version 3.20.5.

if I look at the apps available for example "namebench" a DNS tester it exists on the version 3.20.5 but not the other.

I perform a sudo apt-get update then a sudo apt-get dist-upgrade on both workstation and no difference. The version of Ubuntu desktop I am running is 16.04 LTS as of 26-Jan-2018.

Can anyone confirm the latest version of Ubuntu and Ubuntu software app

---

### Post by cruzer001 on 2018-01-26
Please run the following command on both machines and compare.

```
inxi -Sr
```

---

### Post by flocculant on 2018-01-26
> **cam17 said:**
> I have what should be 2 identical Ubuntu Desktops. One has version 15.12 of the Ubuntu software and the other has version 3.20.5.

if I look at the apps available for example "namebench" a DNS tester it exists on the version 3.20.5 but not the other.

I perform a sudo apt-get update then a sudo apt-get dist-upgrade on both workstation and no difference. The version of Ubuntu desktop I am running is 16.04 LTS as of 26-Jan-2018.

Can anyone confirm the latest version of Ubuntu and Ubuntu software app

ubuntu-software as a package only goes to 3.26.3 for bionic.

Open the application you think the version is 15.12.

Open a terminal and then in terminal run

```
xprop WM_CLASS
```

Mouse over the application - cursor should be cross-hairs, click on the application.

What do you get in the terminal for > WM_CLASS(STRING) = ?

---

### Post by deadflowr on 2018-01-26
Two different packages indeed.
One is the legacy software-center the other gnome-software.
You can just remove the legacy version and then reinstalling ubuntu-software will auto-pull in the gnome-software package.

It looks like the one system was installed prior to the change over from the legacy package to the new package, which happened during the development period of 16.04.

> if I look at the apps available for example "namebench" a DNS tester it exists on the version 3.20.5 but not the other.
That's because the old version did not and does not support snap packages.
The new one does, so you get to see those extra packages like namebench which has a snap package in the snap store.

My two cents

---

### Post by cam17 on 2018-01-26
I believe version 3.20 is correct as I checked 2 other worstations. the suspect machine gives an error when running inxi -Sr "The program 'inxi' is currently not installed. To run 'inxi' please ask your administrator to install the package 'inxi'"
(64 bit)
The other workstations gave infomration such as kernal 4.4.0 -112 generic x86_64 (64 bit)
Desktop unity 7.4.0 distro Ubuntu 16.04 xenial etc..

---

### Post by cruzer001 on 2018-01-26
> "The program 'inxi' is currently not installed. To run 'inxi' please ask your administrator to install the package 'inxi'"

I suspect that machine is not updated.  Run this to compare with inxi output:
```

lsb_release -a && uname -r && cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by cam17 on 2018-01-27
both workstations operating information match.

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
4.4.0-112-generic

The suspect workstation reports "no such file or directory" for the command ls /etc/apt/sources.list.d/*.list

I understand from WIki that the stable release is October 2013 and the Wiki looks like the single workstation running 15.12. the  3 other Ubuntu look different.
only 1 of my Ubuntu software centres looks like "https://en.wikipedia.org/wiki/Ubuntu_Software_Center" several of my other workstations look like the enclosed.

---

### Post by cruzer001 on 2018-01-27
The 4.4.0-112 is a recent kernel (from 2018); it runs on 16.04 (released April of 2016).  Yet you say that it looks like the 2013 release.  Which by the way, there is no current 2013 release.  That release has long since reached its end of life.  Has this suspect machine been upgraded from a past release?

Please post the full output of only the suspect machine.
```

lsb_release -a && uname -r && cat /etc/apt/sources.list && ls /etc/apt
```

Also post the output (of the suspect machine):

```
sudo apt-get -f install
```

Maybe this will shed some light on this mystery :)

---

### Post by cam17 on 2018-01-27
The previosly enclosed ubuntu software centre shows what the majority of my workstations are displaying. Is it correct ? version 3.20

---

### Post by cam17 on 2018-01-27
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
4.4.0-112-generic
```
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial main
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-updates main
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-updates universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-updates multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-security main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```
```
apt.conf.d  preferences.d  sources.list  sources.list.d  sources.list.save  trusted.gpg  trusted.gpg.d

```
```
sudo apt-get -f install
[sudo] password for macneal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by cruzer001 on 2018-01-28
Everything shows as good and correct.  

These version numbers for the software-center and gnome-software are as shown here:

[https://packages.ubuntu.com/xenial/software-center](https://packages.ubuntu.com/xenial/software-center)

[https://packages.ubuntu.com/xenial/gnome-software](https://packages.ubuntu.com/xenial/gnome-software)

You can verify with:

```
apt-cache policy software-center
```

and

```
apt-cache policy gnome-software
```

If you still see this v15.12 I can only guess that its a leftover form a version upgrade (upgrade from 14.04 to 16.04?).  You could remove the package and reinstall or even reinstall 16.04 to remove any leftover crud.
```

sudo apt-get install --reinstall software-center
```

---

### Post by cam17 on 2018-01-28
This means the other 3 workstations runnimg version 3.20 of software center are incorrect. 

When I run "sudo apt-get policy software-center" I get the message "E: Invalid operation policy" on all workstations."

---

### Post by cruzer001 on 2018-01-28
Oops

Sorry, made a mistake with the commands.  Post #11 has been corrected.  Please try again.

---

### Post by cam17 on 2018-01-29
Thank you for the corrections. Below is the result from the workstations (3) which are running version 3.20. One workstation I installed with 16.04.3  today Jan-29-2018 and it shows Ubuntu Software 3.20.5. 

I have enclosed a image of software update image.

 apt-cache policy software-center
software-center:
  Installed: (none)
  Candidate: 16.01+16.04.20160420
  Version table:
     16.01+16.04.20160420 500
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu) xenial/universe amd64 Packages
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu) xenial/universe i386 Packages
mac@OldRALF:~$ apt-cache policy gnome-software
gnome-software:
  Installed: 3.20.5-0ubuntu0.16.04.8
  Candidate: 3.20.5-0ubuntu0.16.04.8
  Version table:
 *** 3.20.5-0ubuntu0.16.04.8 500
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 [http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu](http://gpl.savoirfairelinux.net/pub/mirrors/ubuntu) xenial/main amd64 Packages

---

### Post by cruzer001 on 2018-01-30
Excellent

Those systems are as they should be, updated to the proper versions.  Is there anything else?

---

### Post by cam17 on 2018-01-30
Why is there 2 different versions as well as different options and look for Ubuntu software application?

---

### Post by cruzer001 on 2018-01-30
If I follow your question:

The software-center and gnome-software are two different packages.  As shown above (by apt-cache command) your machine(s)have the correct versions.

The software-center (which shows not installed) has 16.01+ bla bla.

The gnome-software package (which shows installed) is version 3.20. bla bla.

Could it be that some machines have gnome-software installed and others have the software-center installed.  Making you think they are different versions?  They are not different versions, but different packages.  There is more than one way to install software, you have two of them to work with.  And there are more.  I do not use either of them, but use yet a different one from yours.  One choice will not suite all :)

Make sense?

---

### Post by cam17 on 2018-01-31
The machine that I just recently re-installed has the gnome-software 3.20 by default for 16.04.3. How would I perform a upgrade to the higher version 15.12 and how would I remove that version so I am running the default version?

I installed all desktops the same so I do not understand how this deviation occurred. I only select the package with the "A" off of the task abar and I get different versions for some reason.

---

### Post by cruzer001 on 2018-01-31
Hello

I cannot find a higher version, as I said above, you are currently running the right versions.  There use to be a software-center lower version 15.12.

I am just not seeing what your seeing.  

One last idea.  Run this on the machine you see version 15.12:
```

sudo apt-get update && sudo apt-get install --reinstall software-center gnome-software ubuntu-software
```

If version 15.12 still shows then I have no idea where it is coming from.

You can go back to post #3 and tell us where/what this package is, but I do not see it and I'm out of ideas :(

---

### Post by Frogs Hair on 2018-01-31
16.04 may still include the old ubuntu-software-center especially if you upgraded. The Ubuntu One services associated with that application have been discontinued. There was also a transition when Gnome Software was re-branded as Ubuntu Software. The 3.20 refers to gnome version the OS is using.

---

### Post by cam17 on 2018-02-02
Can you proivide the expected version for Ubuntu software? I am unsure which version you are considering correct.

---

### Post by cam17 on 2018-02-06
Ubuntu security forum cannot provide the expect version of Ubuntu Software?

---

### Post by cam17 on 2018-02-07
I just reinstalled Ubuntu 16.0.4.3 LTS and when I went to the Ubuntu Software store to install an App it asked for 1Ubuntu one login ? You stated that Ubuntu one is not used anymore?

Correction. I had just installed 16.04.3 LTS and when I went to Software App it asked for Ubuntuone sign in. However after performing a update it did not ask for the sign in.

---

### Post by cam17 on 2018-02-08
I would still like to know the expect version of Ubuntu software when do a complete reinstall and go to "About" in Ubuntu software.

---

### Post by Geoffrey_Arndt on 2018-02-08
Cam17 - - The "Gnome Software Center" is the right one to use as Ubuntu phased out the old Ubuntu Software Centre almost 2 years ago.   That's the version with the higher number.   

These are two "distinct" (different) programs for managing software with the 15.xx versions being the OLD ubuntu software center.   The Gnome Software center (v3.xx), _**renamed**_ "Ubuntu Software" is the NEW official Ubuntu software manager.

In reality, there are MANY software centers for all Linux distributions.   Many people use NEITHER of the above software centre's but instead - - they use either the Linux Terminal and APT command, or they use the much venerated "Synaptic Package Manager" . . .

PS:    _**the current and correct "Ubuntu Software" program is version [SIZE=5]3.20.5[/SIZE]**_ . . . .

---

### Post by cam17 on 2018-02-12
This is why I opened the security post as a Security issue. If the old 15.xx version has been obselete for 2 years I could not understand why it still exists on a new install? there is no notification and some software which can been obtained doesn't seem to exist in the Ubuntu software. Is there a reason it still exists on a install?

---

### Post by cam17 on 2018-02-21
Here is a screen shot of the 2 Ubuntu software applications. Its clear a user can become confused between the two.

---

### Post by Frogs Hair on 2018-02-21
See post # 20 . It is safe to remove the ubuntu-software-center.

---

