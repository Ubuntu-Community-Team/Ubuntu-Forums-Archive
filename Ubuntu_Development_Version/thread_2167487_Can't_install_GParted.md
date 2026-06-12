---
title: "Can't install GParted"
date: 2013-08-13
forum: Ubuntu Development Version
---

### Post by Hungry Man on 2013-08-13
apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'gparted' has no installation candidate

---

### Post by Slug71 on 2013-08-13
Have you tried installing it from the Software Center?

---

### Post by deadflowr on 2013-08-13
Have tried running an apt-get update to see if your connection to the repos is good?

---

### Post by Hungry Man on 2013-08-13
> There isn&#8217;t a software package called &#8220;gparted&#8221; in your current software sources.

That's what the software center says.

apt-get update runs fine.

Perhaps this is related to [http://ubuntuforums.org/showthread.php?t=2166511](http://ubuntuforums.org/showthread.php?t=2166511) and I deleted some repo? I just tried installing wine and got the same error.

---

### Post by cortman on 2013-08-13
Hungry Man, o/ :)

I think you need to run apt-get update, then try installing.

---

### Post by Slug71 on 2013-08-13
What version(13.04?) of Ubuntu are you running?


Update: If 13.04, it's definitely there. Just checked.

---

### Post by deadflowr on 2013-08-13
If your sources.list is borked up then maybe try building a new one.
Look here
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

then replace the old with a new one.

---

### Post by Hungry Man on 2013-08-13
I'll try generating a new one.

---

### Post by Hungry Man on 2013-08-13
> Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US    Fetched 26.8 MB in 2min 6s (211 kB/s)                                          
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/sauscy/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/sauscy/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.



But gparted was installing and I got this error

> ldconfig deferred processing now taking placeW: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



Gparted did install though.

Here's the new sources list.

> ################################################################################ OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted universe multiverse 


###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse 


###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner


###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) sauscy main


##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


###### 3rd Party Binary Repos


#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


#### JDownloader PPA - [https://launchpad.net/~jd-team](https://launchpad.net/~jd-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) saucy main


#### Oracle Java (JDK) Installer PPA - [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) saucy main


#### Wine PPA - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) saucy main






---

### Post by Slug71 on 2013-08-13
Ah you're on Saucy. you should have posted in "Ubuntu +1" since there was likely a breakage with one of the last updates. You're on a development release.

---

### Post by Hungry Man on 2013-08-14
Nope, I wasn't on Saucy when this topic started lol when I changed the sources list it upgraded me to it for some odd reason (I picked 13.04, I must have misclicked). Anyways, I solved it (by reformatting lol) so there it is.

---

### Post by Slug71 on 2013-08-14
> **Hungry Man said:**
> Nope, I wasn't on Saucy when this topic started lol when I changed the sources list it upgraded me to it for some odd reason (I picked 13.04, I must have misclicked). Anyways, I solved it (by reformatting lol) so there it is.

Weird. Glad you got it sorted though. Even if it's not the way you would have liked.

---

### Post by Mark Phelps on 2013-08-14
I believe Saucy is still in tha Alpha stages -- which means you're going to get breakage on a regular basis.  You should really not use the pre-release versions unless you're an expert and easily able to deal with bugs.  Also, when using a pre-release version, you should post in the Development section, not here.

---

### Post by deadflowr on 2013-08-14
> **Mark Phelps said:**
> I believe Saucy is still in tha Alpha stages -- which means you're going to get breakage on a regular basis.  You should really not use the pre-release versions unless you're an expert and easily able to deal with bugs.  Also, when using a pre-release version, you should post in the Development section, not here.

This thread actually started as a raring thread, but when generating a new source.list, the OP messed up and choose saucy instead of raring.
It's unclear what version the OP is using now, as we know that he reformatted the system and started fresh.

---

### Post by stoneguy on 2013-08-15
Saucy's gparted is 0.16.1, so it handles F2FS if that's something anyone wants to play with.

---

### Post by jbicha on 2013-08-15
> **Hungry Man said:**
> 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-proposed main restricted universe multiverse

Please disable the saucy-proposed line since saucy is not yet a stable release. You can disable it by adding a # to the beginning of the line. More explanation of "why" on the [wiki]("https://wiki.ubuntu.com/ProposedMigration").

---

