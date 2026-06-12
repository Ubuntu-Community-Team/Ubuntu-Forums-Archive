---
title: "Ubuntu 18.04 - pgl - how to install?"
date: 2018-05-28
forum: Security
---

### Post by maks-kas on 2018-05-28
How do you install 'peer guardian linux' in Ubuntu 18.04?

In my previous version of Ubuntu [16.04 LTS]("https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_16.04_LTS_(Xenial_Xerus)") this worked:

sudo add-apt-repository ppa:jre-phoenix/ppa

sudo apt-get install pgld pglcmd pglgui

In 18.04 LTS I get following message after trying to install pgl:

E: The repository 'http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Can someone help me, please?!

---

### Post by PaulW2U on 2018-05-28
> **maks-kas said:**
> E: The repository 'http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

That message is telling you that the [PPA]("https://launchpad.net/~jre-phoenix/+archive/ubuntu/ppa") has not been updated for Ubuntu 18.04. Actually it doesn't appear to have been updated for 16.10, 17.04 or 17.10 either. The last update was in November 2015, not good. You could force use of the xenial package by editing the repository line but you will be using unmaintained software which may not work properly.

Why not contact the application's author and ask if he is ever going to release an updated version?

Probably best to start looking for an alternative though.

---

### Post by #&amp;thj^% on 2018-05-28
> **PaulW2U said:**
> That message is telling you that the [PPA]("https://launchpad.net/~jre-phoenix/+archive/ubuntu/ppa") has not been updated for Ubuntu 18.04. Actually it doesn't appear to have been updated for 16.10, 17.04 or 17.10 either. The last update was in November 2015, not good. You could force use of the xenial package by editing the repository line but you will be using unmaintained software which may not work properly.

Why not contact the application's author and ask if he is ever going to release an updated version?

Probably best to start looking for an alternative though.

+1 ;)
> PeerGuardian Linux:
Actively developed. However the team is very small and with few spare time. Contributors are welcome!

Peerguardian OS X:
Not developed anymore. We've lost contact with the OS X developer. New contributors are welcome!

PeerGuardian Windows:
Not developed anymore. It's highly recommended to use PeerBlock instead, which is a continuation of PeerGuardian's development in 
Source here:[https://sourceforge.net/projects/peerguardian/](https://sourceforge.net/projects/peerguardian/)
I did manage to get it installed but I'm hesitant to show how i did it>>>Just not a proper install>>> works ok in the terminal.
The Developer needs to have in mind for Bionic that "gksu" has been dropped here  18.04.

---

### Post by maks-kas on 2018-05-29
Thank you for your answers.

" PeerGuardian Linux:
Actively developed. However the team is very small and with few spare time. Contributors are welcome! "

Would this be a good place to ask, why the developers haven't upgraded the repositories since xenial?

Thank you.

---

### Post by renatozx on 2019-01-06
I installed Peer Guardian on Ubuntu 18.04 by putting together these 2 tutorials i found in the internet, don`t use the PPA

I made a howto video:
[https://youtu.be/q3U9f995aI0](https://youtu.be/q3U9f995aI0)

Make a backup of your system before following this tutorial.


Install PeerGuardian Linux (pgl) on Debian 9 or Ubuntu 18.04 & derivatives:
 
Install gedit:
1- sudo apt install gedit


Configure your system to know about the packages
Add these entries to /etc/apt/sources.list:
2- sudo gedit /etc/apt/sources.list


3- paste:
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) stretch main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) stretch main


4- Close gedit


5- Add gpg key to the apt keyring:
gpg --keyserver keyserver.ubuntu.com --recv-keys C0145138
gpg --export --armor C0145138 | sudo apt-key add -


6- Update your system with the package information:
sudo apt-get update


7- Install it:
sudo apt-get install pgld pglcmd pglgui


The gksu package has being removed from Debian 9 & Ubuntu 18.04 LTS.
How to fix?
Possible solution is to install version from previous (17.10, artful) release.
Warning: do not execute the commands below if unsure!


8- Add artful repositories to the system:


cat <<EOF | sudo tee /etc/apt/sources.list.d/artful.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful universe
EOF


9- Update package cache:
sudo apt-get update


10- Install gksu package
sudo apt-get install gksu


11- Remove artful repository from system for safety


sudo rm /etc/apt/sources.list.d/artful.list
sudo apt-get update


Test


Test gksu (should work on Xorg-sessions)


gksu-properties # check that it has "Authentication mode" to "sudo"
gksu date
gksudo date


Notes


After installation the following packages will be marked as obsolete (locally-installed): gksu, libgksu2-0. But they will work as expected.


To uninstall Peer Guardian:
sudo apt-get remove pgld pglcmd pglgui


Source:
[https://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/](https://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/)


[https://askubuntu.com/questions/1030054/how-to-install-an-application-that-requires-gksu-package-on-ubuntu-18-04](https://askubuntu.com/questions/1030054/how-to-install-an-application-that-requires-gksu-package-on-ubuntu-18-04)

---

### Post by FoolInTheRain on 2019-02-24
renatozx,
Thank you for taking the time to explain this.

I haven't tried it yet but I'm completely perplexed by the lack of interest in graphical IP blockers, especially considering the current online hostile environment.

Good job!

---

