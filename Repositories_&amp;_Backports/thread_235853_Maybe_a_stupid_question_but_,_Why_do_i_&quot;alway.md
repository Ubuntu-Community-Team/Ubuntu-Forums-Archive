---
title: "Maybe a stupid question but , Why do i &quot;alway's&quot; have to sudo update all the time.?"
date: 2006-08-13
forum: Repositories &amp; Backports
---

### Post by jason.b.c on 2006-08-13
Seems like everytime i want to install something ( the  "sudo apt-get install" ) way from the terminal i always have to **Sudo apt-get update** before it can find the package to install...

Why is it that ubuntu dosen't remember what it already knows from the many  sudo apt-get update's that i've done before...???   So irritating..!!:mad: 

I'm serious.! , It takes like a good half-an-hour to forty-five minuetes just to finish so i can get the package i want to install..:confused:

---

### Post by 23meg on 2006-08-13
You don't have to do it every time you install something; you just have to do it every time you change your sources.list file.

---

### Post by sean_ on 2006-08-13
Well, I'm not sure how to do it, but you can change permissions. But, type su, if it says invalid password, read this: [http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by jason.b.c on 2006-08-13
> **23meg said:**
> You don't have to do it every time you install something; you just have to do it every time you change your sources.list file.

I'm not changing my sources.list file , Just trying to do a: **sudo apt-get install <file name>**

Then i get a terminal error message like **package not found ** or something like that..

---

### Post by 23meg on 2006-08-13
> **jason.b.c said:**
> I'm not changing my sources.list file , Just trying to do a: **sudo apt-get install <file name>**Perhaps you mean package name, right? What follows the "sudo apt-get install" bit has to be the name of a package that exists in the repositories defined in your sources.list file, not the name of a file on your local system. If you're getting a "package not found" error it means that the package simply doesn't exist in the repositories. Why don't you copy and paste from the terminal the command you enter along with the exact error you're getting?

---

### Post by jason.b.c on 2006-08-13
> **23meg said:**
> Perhaps you mean package name, right? What follows the "sudo apt-get install" bit has to be the name of a package that exists in the repositories defined in your sources.list file, not the name of a file on your local system. If you're getting a "package not found" error it means that the package simply doesn't exist in the repositories. Why don't you copy and paste from the terminal the command you enter along with the exact error you're getting?

Well i know for a fact that this exists..!   It's an option inside of **automatix**.....**Gamepads**

> jason@Hp-Vectra-VL:~$ sudo apt-get install gamepads
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gamepads
jason@Hp-Vectra-VL:~$

   [-X

---

### Post by Frank Golden on 2006-08-13
> **jason.b.c said:**
> Well i know for a fact that this exists..!   It's an option inside of **automatix**.....**Gamepads**

   [-X

Are you using Breezy or Dapper? 

Edit:Nevermind just noticed your
sig.

Can you post your sources.list

---

### Post by 23meg on 2006-08-13
It looks like you're having problems accessing the Multiverse repo, which the package "gamepads" is perhaps in. I saw a few thread titles describing problems with Multiverse recently; perhaps there's a problem with the US mirror of it these days. I don't know because I didn't read those threads but do a search and you'll get to the details. Maybe using a different mirror will help.

Edit: I [did a search for "gamepads"]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gamepads&searchon=names&subword=1&version=all&release=all") in packages.ubuntu.com and there seems to be no such package in the official repos. Perhaps it's in a third party repo which isn't in your sources.list at the moment.

---

### Post by jason.b.c on 2006-08-13
> jason@Hp-Vectra-VL:~$ sudo gedit /etc/apt/source.list
jason@Hp-Vectra-VL:~$




I'm getting a blank window again....What's the correct way..?

---

### Post by 23meg on 2006-08-13
It's "source**s**.list" rather than "source.list".

---

### Post by Frank Golden on 2006-08-13
> **jason.b.c said:**
> I'm getting a blank window again....What's the correct way..?
Hi Jason,
   The command you list is missing a "s".
Should be sudo gedit /etc/apt/sources.list
not sudo gedit /etc/apt/source.list.
Linux or any command line for that matter is not tolerant of
spelling errors. Linux is also case sensitive, for instance
the command to change directories to the desktop will fail
if you don't capitalze the "D" in desktop. People often post
here about having trouble cd'ing the Desktop.

---

### Post by msak007 on 2006-08-13
"Gamepads" is probably just a label for the package(s) that Automatix installs. For example, the "Security Suite" option in Automatix is not the actual package name, but a label for the apps that Automatix installs if you choose it (in the Kubuntu Automatix, for example, it installs ClamAV and Guarddog). In that case, it's known what package(s) are installed but some entries in Automatix don't tell you what specific packages will be installed, and give you a description. Not sure what package "Gamepad" installs (I don't have it as an option), you may want to pose this question in the Automatix forum or have the thread moved there by a mod.

Also to answer your above post, you forgot the "s" at the end of source - it's "/etc/apt/source**s**.list"

EDIT: I see 2 people already answered your question about sources.list in the time it took me to write this reply :). Sorry for the redundancy.

---

### Post by jason.b.c on 2006-08-13
Alright so here's my sources.list...

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 


So can someone tell me what's missing from it so that i can get **gamepads** and so i don't have to keep on **sudo updating** all the freakin time..?

---

### Post by jason.b.c on 2006-08-14
So does my sources.list look right or ..???

---

### Post by 23meg on 2006-08-14
Your problem essentially has nothing to do with "sudo apt-get update". Perhaps we can help better if you state what exactly it is you're trying to do. Are you trying to install a tool to get your gamepad functioning, adjust its settings etc. ? Because there seems to be no such package as "gamepads" anywhere but perhaps the software you're looking for has some other title and maybe exists in some other repository. In any case```
apt-cache search gamepad
```will show you related software that's in the repositories listed in your sources.list .

---

### Post by msak007 on 2006-08-14
That's what I already said in my previous post but I don't think he read it - it's not a problem with his sources.list. He's simply trying to install the "Gamepads" option that Automatix installs, but for some reason trying to do it from the terminal rather than using Automatix to do it. Automatix always replaces your sources.list temporarily, grabs what it needs, then gives you the option of restoring your sources.list or keeping the one it used permanently. "Gamepads", as I've already stated, is not an actual package name - it's just the label for the package(s) Automatix installs and the scripts it runs to get gamepads running.

---

### Post by jason.b.c on 2006-08-14
> **msak007 said:**
> That's what I already said in my previous post but I don't think he read it - it's not a problem with his sources.list. He's simply trying to install the "Gamepads" option that Automatix installs, but for some reason trying to do it from the terminal rather than using Automatix to do it. Automatix always replaces your sources.list temporarily, grabs what it needs, then gives you the option of restoring your sources.list or keeping the one it used permanently. "Gamepads", as I've already stated, is not an actual package name - it's just the label for the package(s) Automatix installs and the scripts it runs to get gamepads running.

Yes i read it...!!!!!!

I've tried and tried to install it through automatix..! , It won't install...

> jason@Hp-Vectra-VL:~$ apt-cache search gamepad
gngeo - NeoGeo emulator
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
jason@Hp-Vectra-VL:~$



---

### Post by jason.b.c on 2006-08-14
> **23meg said:**
> Your problem essentially has nothing to do with "sudo apt-get update". Perhaps we can help better if you state what exactly it is you're trying to do. 

Install things without having to sudo apt-get update all the darn time...

Install things through the package manager without getting error messages saying:    "Could not this"  ---  "Could not that"  ---  "run sudo apt-get update to reslove these problems"...

---

### Post by 23meg on 2006-08-14
Under normal conditions you simply don't have to do "sudo apt-get update" all the time; I said this in my first post. And in a later post I told you that you're probably having problems with Multiverse and that you should try another mirror.

---

### Post by jason.b.c on 2006-08-14
> **23meg said:**
> Under normal conditions you simply don't have to do "sudo apt-get update" all the time; I said this in my first post. And in a later post I told you that you're probably having problems with Multiverse and that you should try another mirror.

What other mirror..???    Another U.S. mirror..?   I don't know how to use another mirror...

---

### Post by 23meg on 2006-08-14
Replace the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) bits in your sources.list with [one of these]("https://wiki.ubuntu.com/Archive/OfficialMirrors?highlight=%28mirrors%29").

---

### Post by jason.b.c on 2006-08-14
> **23meg said:**
> Replace the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) bits in your sources.list with [one of these]("https://wiki.ubuntu.com/Archive/OfficialMirrors?highlight=%28mirrors%29").

I don't know if that will really work , I'm in the U.S.A.   dosen't that mean i'm supposed to use a US mirror..??

Wouldn't it take longer to update then..?

---

### Post by mdsmedia on 2006-08-14
> **jason.b.c said:**
> I don't know if that will really work , I'm in the U.S.A.   dosen't that mean i'm supposed to use a US mirror..??

Wouldn't it take longer to update then..?I wouldn't have thought that using a mirror outside the US would make much difference...timewise. And it's a possible solution to your problem.

No it doesn't mean you're supposed to use a US mirror, although using a local mirror is usually recommended. In this case it may be the US mirror which isn't working, so a possible solution would be...use another mirror ;)

I sometimes get similar error msgs. After a few days they're not there. Usually that indicates the mirror is having problems.

---

### Post by jason.b.c on 2006-08-31
*BUMP*

I'm getting sick and freakin tired of this....!!

---

