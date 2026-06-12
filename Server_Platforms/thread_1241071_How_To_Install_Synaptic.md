---
title: "How To Install Synaptic?"
date: 2009-08-15
forum: Server Platforms
---

### Post by antdgar on 2009-08-15
Hi,

I've just installed Ubuntu 9.04 on my dedicated server

Just wondering how to install Synaptic Package Manager (GUI)?

I have tried:
```
apt-get install synaptic
``````
E: Couldn't find package synpatic
```Any ideas?

---

### Post by RedSingularity on 2009-08-15
Your error code output says "synpatic".  It is spelled "synaptic" like you have above.

---

### Post by antdgar on 2009-08-15
Oh sorry. This happens:

```
apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies.
  synaptic: Depends: libapt-inst-libc6.8-6-1.1
            Depends: libapt-pkg-libc6.8-6-4.6[/B]
E: Broken packages
```

Do you know how I can install synaptic?

---

### Post by Bachstelze on 2009-08-15
Which version of Ubuntu are you running?

---

### Post by wojox on 2009-08-15
If you installed a GUI on your server synaptic is already installed. 
If it's just a terminal type 
```
aptitude
```

---

### Post by antdgar on 2009-08-15
I'm using Ubuntu Server 9.04

I think I have a GUI... I am using NX. But I cannot see synaptic in any menus.

How can I get a terminal?

The closest thing I have is 'root terminal'. When I click that it just says 'starting root terminal' in the taskbar, and then disappears. I guess it crashes. This is on a fresh install.

I can do commands from my Windows PC though, through SSH. I need GUI so aptitude will not be enough, sadly. I'm very noob with command line, as you can tell.

Basically I'm trying to install WINE.

---

### Post by jocko on 2009-08-15
> **antdgar said:**
> Oh sorry. This happens:

```
apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies.
  synaptic: Depends: libapt-inst-libc6.8-6-1.1
            Depends: libapt-pkg-libc6.8-6-4.6[/B]
E: Broken packages
```Do you know how I can install synaptic?
Have you updated the package information after you installed?
```
sudo apt-get update #sync package information with the repos
sudo apt-get upgrade #install any updates that are available
sudo apt-get install synaptic
```

---

### Post by antdgar on 2009-08-15
I did the updates (I just put in the commands and pressed 'Y' when it asked)

And after doing your final command, I got this:
```
sudo apt-get install libapt-inst-libc6.8-6-1.1 libapt-pkg-libc6.8-6-4.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apt-utils instead of libapt-inst-libc6.8-6-1.1
apt-utils is already the newest version.
Note, selecting apt instead of libapt-pkg-libc6.8-6-4.6
apt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by jocko on 2009-08-15
> **antdgar said:**
> I did the updates (I just put in the commands and pressed 'Y' when it asked)

And after doing your final command, I got this:
```
sudo apt-get install libapt-inst-libc6.8-6-1.1 libapt-pkg-libc6.8-6-4.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apt-utils instead of libapt-inst-libc6.8-6-1.1
apt-utils is already the newest version.
Note, selecting apt instead of libapt-pkg-libc6.8-6-4.6
apt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```
Ok, that's why I couldn't find those packages (I removed the last part of the post a minute after I posted it, as I couldn't find those packages).
And you still can't install synaptic? Same errors?

---

### Post by antdgar on 2009-08-15
> **jocko said:**
> And you still can't install synaptic? Same errors?
Yep, I can't install synaptic. Same errors >.<

Hm, when I put in 'aptitude' it says:
[IMG]http://i187.photobucket.com/albums/x268/antdgar/Picture5-5.png[/IMG]
I don't know if this holds any relevance

---

### Post by jocko on 2009-08-15
> **antdgar said:**
> Yep, I can't install synaptic. Same errors >.<
That's just weird... I can't see how anyone could ever install synaptic then... I don't have those libapt packages installed (but I do have apt and apt-utils), and synaptic is fine...

I'm sure that synaptic would get properly installed as part of ununtu-desktop or xubuntu-desktop (but that brings the entire gnome or xfce desktop environments, which I guess you don't want to have on your server).

---

### Post by jocko on 2009-08-15
> **antdgar said:**
> Yep, I can't install synaptic. Same errors >.<

Hm, when I put in 'aptitude' it says:
[IMG]http://i187.photobucket.com/albums/x268/antdgar/Picture5-5.png[/IMG]
I don't know if this holds any relevance
That's certainly relevant! According to that picture you have only 3 uninstalled packages???? There should be close to 30000 uninstalled packages if you have all online repos activated (now you seem to only have the tiny repo on the cd?).
Show the output of:
```
cat /etc/apt/sources.list
```

---

### Post by antdgar on 2009-08-15
> **jocko said:**
> That's certainly relevant! According to that picture you have only 3 uninstalled packages???? There should be close to 30000 uninstalled packages if you have all online repos activated (now you seem to only have the tiny repo on the cd?).
Show the output of:
```
cat /etc/apt/sources.list
```

Hmm, well my server is in France. So I don't have a CD. The server company installs the OS automatically. It just says 'Ubuntu 9.04 server edition'.

```
[cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty main restricted
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates main restricted
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty universe
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty universe
deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates universe
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty multiverse
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty multiverse
deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates multiverse
deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [ftp://mir1.ovh.net/ubuntu/](ftp://mir1.ovh.net/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/freenx-team/ppa/ubuntu](http://ppa.launchpad.net/freenx-team/ppa/ubuntu) jaunty main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```

---

### Post by jocko on 2009-08-15
Ok, I tried your sources.list, and it seems to contain an entire ubuntu repo with more than 20.000 packages, so there's nothing wrong there... Then I don't know how to help you...

---

### Post by antdgar on 2009-08-15
> **jocko said:**
> Ok, I tried your sources.list, and it seems to contain an entire ubuntu repo with more than 20.000 packages, so there's nothing wrong there... Then I don't know how to help you...
No problem! I'll learn aptitude/terminal commands :)

Thank you.

---

