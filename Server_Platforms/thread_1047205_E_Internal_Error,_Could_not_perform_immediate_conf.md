---
title: "E: Internal Error, Could not perform immediate configuration (1) on libc6"
date: 2009-01-22
forum: Server Platforms
---

### Post by silbro on 2009-01-22
Hi all

I have a problem I cannot solve. I don't  even understand what exactly the problem seems to be. What I wanted to do is install a  zabbix-agent on a 8.06 Ubuntu server installation. I added a repository and commented all the others out so it will get the newest zabbix client. (This worked for me on a 32bit system, this is a 64 bit system though) I used this source 

> deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jaunty main universe

what I then did is type
```
apt-get install zabbix-agent
```

it of course asked me if I want to install the packages needed and I say yes. It installed some packages and then stopped with an error saying: 

> Internal Error, Could not perform immediate configuration (2) on libstdc++6

Then I tried again:

```
apt-get install zabbix-agent
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: findutils (>= 4.4.0-2ubuntu2) but 4.2.27-1ubuntu1 is to be installed
  zabbix-agent: Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
                Depends: libopenipmi0 but it is not going to be installed
                Depends: ucf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

so I did as it told me:

```
apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  findutils
Suggested packages:
  mlocate
The following packages will be upgraded:
  findutils
1 upgraded, 0 newly installed, 0 to remove and 213 not upgraded.
1 not fully installed or removed.
Need to get 0B/474kB of archives.
After unpacking 336kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (1) on libc6

```

I also  tried the following:

```

/var/cache/apt/archives# dpkg --install libc6_2.9-0ubuntu9_amd64.deb
(Lese Datenbank ... 75484 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von libc6 2.3.6-0ubuntu20.5 (durch libc6_2.9-0ubuntu9_amd64.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Entpacke Ersatz fÃ¼r libc6 ...
dpkg: warning - unable to delete old directory `/sys': Device or resource busy
dpkg: AbhÃ¤ngigkeitsprobleme verhindern Konfiguration von libc6:
 libc6 hÃ¤ngt ab von findutils (>= 4.4.0-2ubuntu2); aber:
  Version von findutils auf dem System ist 4.2.27-1ubuntu1.
dpkg: Fehler beim Bearbeiten von libc6 (--install):
 AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 libc6

```

```

/var/cache/apt/archives# apt-get install findutils
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mlocate
The following packages will be upgraded:
  findutils
1 upgraded, 0 newly installed, 0 to remove and 213 not upgraded.
1 not fully installed or removed.
Need to get 0B/474kB of archives.
After unpacking 336kB of additional disk space will be used.
E: Internal Error, Could not perform immediate configuration (1) on libc6

```

I'm kinda lost to what I should do. Because I have searched for that error and found some forum entries. I still don't understand where the problem seems to be. This is also a productive system, so I cannot experience till it crashes :) I'd be really really gratefull if someone can help me! thank you very much in advance.

Silvio

---

### Post by silbro on 2009-01-27
Well I just found out some stuff.

The library I cannot remove is being used by a program it seems. So I'll be making a backup of the system. Then try again and see if it helps stopping the program that might be using that library. Makes sense to me and if I'm successfull I'll post the info.

---

### Post by Kevbert on 2009-01-27
By the look of it you need some 32 bit library files in order to run 32 bit programs on your 64 bit system. The details on how to get these is [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by silbro on 2009-01-28
Thank you for the information. I will try this as well. I will post my results once I get to do this this week.

:popcorn:

---

### Post by silbro on 2009-05-04
Just for the information. I didn't solve this problem succesfully. I used another Ubuntu Server version and started from scratch.

---

### Post by nautilus on 2009-10-08
Well, I just had the same issue.  Doing a:

```
cd /var/cache/apt/archives
sudo dpkg -i --force-depends tzdata_2009n-0ubuntu0.8.10_all.deb libc6_2.8~20080505-0ubuntu9_i386.deb libc6-amd64_2.8~20080505-0ubuntu9_i386.deb  findutils_4.4.0-2ubuntu3_i386.deb
sudo apt-get -f install
```

... got me back to where I wanted to be.  Seems there is a circular dependency between findutils and libc6.

---

### Post by brookiemonsta on 2010-03-16
I just had a similar problem when updating from Karmic Koala to Lucid Lynx just now. Nautilus' solution worked a treat.

The error I had was

```
 E: Internal Error, Could not perform immediate configuration (1) on initramfs-tools
```Typing the following:

```
cd /var/cache/apt/archives
sudo dpkg -i --force-depends initramfs-tools* 
apt-get -f install
```worked for me. I was then able to carry on with the apt-get dist-upgrade installation.

Elsewhere on the forums people have reported having [badly broken systems]("http://ubuntuforums.org/showthread.php?t=1316871") or having to completely reinstall because of similar problems. Thankfully that was not necessary!

Thanks for the pointers guys.

---

