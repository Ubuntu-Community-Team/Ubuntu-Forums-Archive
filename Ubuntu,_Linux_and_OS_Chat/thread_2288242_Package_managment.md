---
title: "Package managment"
date: 2015-07-25
forum: Ubuntu, Linux and OS Chat
---

### Post by smelheim85 on 2015-07-25
Hi,

I've been using Ubuntu type systems for a few years now and I wanted to know, what package management to use.  I'm more of a command line user so I use apt-get for the most part.  I know more people to use aptitude.  I have used it before but I don't see much of a difference.  

What are others preference on which command to use?

---

### Post by sudodus on 2015-07-25
I think more people are using apt-get with Ubuntu. See this list of useful commands, originally posted by ***oldfred***.

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

You get more details, when you read the manual pages

```
man apt-get
```

---

### Post by Bashing-om on 2015-07-25
smelheim85; Hi !

In my growing familiarity with the package management system of ubuntu, I also have abandoned all other front ends to apt.
I use 'apt' exclusively.
Knowing how to use apt there is no need for any other helps.
see:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

To know apt
[INDENT][INDENT]in all it's glory
[/INDENT][/INDENT]

---

