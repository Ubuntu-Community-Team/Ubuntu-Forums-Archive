---
title: "do-release-upgrade broken packages"
date: 2013-01-14
forum: Server Platforms
---

### Post by awacs on 2013-01-14
Ubuntu Lucid: unfortunatel, I broke out of do-release-upgrade, and now it complains of broken packages. Also, 'apt-get -f upgrade' fails, thusly:

Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.3 is installed
         Recommends: libc6-i686
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I also tried: 
# dpkg --get-selections | grep hold
#

I'm stuck. What next?

---

### Post by ibjsb4 on 2013-01-14
Take a look through your "sources.list" and maybe even your "sources.list.d" for leftover Lucid sources.

---

### Post by awacs on 2013-01-14
> **ibjsb4 said:**
> Take a look through your "sources.list" and maybe even your "sources.list.d" for leftover Lucid sources.

# grep lucid sources.list
# cd sources.list.d
# ls
#

:-(

---

### Post by ibjsb4 on 2013-01-14
To just look

cat /etc/apt/sources.list

To edit

gksudo gedit /etc/apt/sources.list

gksudo gedit /etc/apt/sources.list.d/*

---

### Post by awacs on 2013-01-15
> **ibjsb4 said:**
> To just look

cat /etc/apt/sources.list

To edit

gksudo gedit /etc/apt/sources.list

gksudo gedit /etc/apt/sources.list.d/*


Yes, as I posted, no 'lucid' in sources.list, and sources.list.d is empty.

---

### Post by awacs on 2013-01-15
Today, I tried:

# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package libc6 needs to be reinstalled, but I can't find an archive for it
.

?

---

### Post by ibjsb4 on 2013-01-15
My last suggestion is apt-get clean, update and install libc6.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=libc6+bugs+upgrade+lucid+10.04+to+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=libc6+bugs+upgrade+lucid+10.04+to+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Good luck

---

### Post by awacs on 2013-01-15
> **ibjsb4 said:**
> My last suggestion is apt-get clean, update and install libc6.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=libc6+bugs+upgrade+lucid+10.04+to+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=libc6+bugs+upgrade+lucid+10.04+to+precise+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Good luck

Thanks for your suggestions. Apt-get clean and update worked, install didn't:

#  apt-get install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

root@salami:/etc/apt#  apt-get -f install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I'm stuck. :-(

---

### Post by awacs on 2013-01-15
And, apt-get -f install tried to install a LOT of packages (with the scary "Yes, Do as I say!" to warn me off), but also broke:

E: Could not perform immediate configuration on 'python-minimal'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

feeding the option APT::Immediate-Configure=false wasn't much better:

E: Couldn't configure pre-depend multiarch-support for libnih-dbus1, probably a dependency cycle.

---

### Post by awacs on 2013-01-20
Nevermind.

I gave up and reinstalled. :-(

---

