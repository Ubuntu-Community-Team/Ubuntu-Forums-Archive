---
title: "I want to try Debian Testing..."
date: 2010-04-11
forum: The Cafe
---

### Post by Uncle Spellbinder on 2010-04-11
I'd like to try Debian testing again. Been a couple years for me. sometime the next couple weeks, I'd like to try and install. I had issues previously with my wireless keyboards not being recognized when trying to install, we'll see how that goes. 

A couple questions for you Debian users. 

1) I went here: [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/) 
I only need CD 1 here, correct? [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

2) Once installed, in the sources.list, should "squeeze" be changed to "testing" to keep it a rolling release?

3) And is [this](http://debgen.simplylinux.ch/) a good place to use to generate a sources.list?

It generated the following...
```
#############################################################
################### OFFICIAL DEBIAN REPOS ###################
#############################################################

###### Debian Main Repos
deb http://ftp.us.debian.org/debian/ squeeze main contrib non-free 

###### Debian Update Repos
deb http://security.debian.org/ squeeze/updates main contrib non-free 
deb http://ftp.us.debian.org/debian/ squeeze-proposed-updates main contrib non-free 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Debian Multimedia - http://www.debian-multimedia.org/
## Run this command: apt-get update && apt-get install debian-multimedia-keyring && apt-get update
deb http://www.debian-multimedia.org/ squeeze main

#### Debian Unofficial - http://debian-unofficial.org/
## Run this command:  apt-get install debian-unofficial-archive-keyring 
deb http://ftp.debian-unofficial.org/debian squeeze main contrib non-free restricted

#### Unofficial Maintainers - http://unofficial.debian-maintainers.org/
## Run this command: apt-get install dmo-archive-keyring
deb http://unofficial.debian-maintainers.org/ squeeze/backports main contrib non-free restricted
```



Not sure what this is but it generated this as well:
*Alternate layout for Synaptic*
```
#############################################################
################### OFFICIAL DEBIAN REPOS ###################
#############################################################

###### Debian Main Repos
deb http://ftp.us.debian.org/debian/ squeeze main contrib non-free 

###### Debian Update Repos
deb http://security.debian.org/ squeeze/updates main contrib non-free 
deb http://ftp.us.debian.org/debian/ squeeze-proposed-updates main contrib non-free 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: apt-get update && apt-get install debian-multimedia-keyring && apt-get update
deb http://www.debian-multimedia.org/ squeeze main # Debian Multimedia - http://www.debian-multimedia.org/

## Run this command:  apt-get install debian-unofficial-archive-keyring 
deb http://ftp.debian-unofficial.org/debian squeeze main contrib non-free restricted # Debian Unofficial - http://debian-unofficial.org/

## Run this command: apt-get install dmo-archive-keyring
deb http://unofficial.debian-maintainers.org/ squeeze/backports main contrib non-free restricted # Unofficial Maintainers - http://unofficial.debian-maintainers.org/
```

---

### Post by NightwishFan on 2010-04-11
Yes, you only need CD 1 to install a desktop, however you will have to add a few packages from the net to get some basic functionality. Such as networkmanager, synaptic, cpufrequtils..

The sources site looks correct to me. I would add main contrib non-free, security updates and debian multimedia. Yes, change 'squeeze' to 'testing' to get a rolling release

---

### Post by Uncle Spellbinder on 2010-04-12
@ NightwishFan
 
Thanks. It appears *main contrib non-free* is already under "Debian Main Repos" and *debian multimedia* is under "3rd Party Binary Repos". Or am I misunderstanding you?

---

### Post by NightwishFan on 2010-04-12
I posted before the edit where the code box appeared. It looks ok except for the '......'. The synaptic layout perhaps has more compatibility for editing with Synaptic?
```
deb http://ftp.....debian.org/debian/ squeeze main contrib non-free 
```

---

### Post by Uncle Spellbinder on 2010-04-12
> **NightwishFan said:**
> I posted before the edit where the code box appeared. It looks ok except for the '......'. The synaptic layout perhaps has more compatibility for editing with Synaptic?
```
deb http://ftp.....debian.org/debian/ squeeze main contrib non-free 
```
Got it changed correctly, I think. "Testing" where "Squeeze" was and "..." corrected: 

```
#############################################################
################### OFFICIAL DEBIAN REPOS ###################
#############################################################

###### Debian Main Repos
deb http://ftp.us.debian.org/debian/ testing main contrib non-free 

###### Debian Update Repos
deb http://security.debian.org/ testing/updates main contrib non-free 
deb http://ftp.us.debian.org/debian/ testing-proposed-updates main contrib non-free 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Debian Multimedia - http://www.debian-multimedia.org/
## Run this command: apt-get update && apt-get install debian-multimedia-keyring && apt-get update
deb http://www.debian-multimedia.org/ testing main

#### Debian Unofficial - http://debian-unofficial.org/
## Run this command:  apt-get install debian-unofficial-archive-keyring 
deb http://ftp.debian-unofficial.org/debian testing main contrib non-free restricted

#### Unofficial Maintainers - http://unofficial.debian-maintainers.org/
## Run this command: apt-get install dmo-archive-keyring
deb http://unofficial.debian-maintainers.org/ testing/backports main contrib non-free restricted
```



*Alternate layout for Synaptic*
```
#############################################################
################### OFFICIAL DEBIAN REPOS ###################
#############################################################

###### Debian Main Repos
deb http://ftp.us.debian.org/debian/ testing main contrib non-free 

###### Debian Update Repos
deb http://security.debian.org/ testing/updates main contrib non-free 
deb http://ftp.us.debian.org/debian/ testing-proposed-updates main contrib non-free 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: apt-get update && apt-get install debian-multimedia-keyring && apt-get update
deb http://www.debian-multimedia.org/ testing main # Debian Multimedia - http://www.debian-multimedia.org/

## Run this command:  apt-get install debian-unofficial-archive-keyring 
deb http://ftp.debian-unofficial.org/debian testing main contrib non-free restricted # Debian Unofficial - http://debian-unofficial.org/

## Run this command: apt-get install dmo-archive-keyring
deb http://unofficial.debian-maintainers.org/ testing/backports main contrib non-free restricted # Unofficial Maintainers - http://unofficial.debian-maintainers.org/
```

---

### Post by NightwishFan on 2010-04-12
It looks good to me though personally I never used "Proposed Updates". I am not exactly sure what they are. Something that is being tested to be included as an update I would think.

---

### Post by Uncle Spellbinder on 2010-04-12
Thanks for your assistance on getting me re-introduced to Debian, NightwishFan. Really appreciate it. Bookmarked this thread for future reference. 

Also bookmarked [http://linuxadventures.net/](http://linuxadventures.net/) ;)

---

### Post by NightwishFan on 2010-04-12
I collaborate on Linux adventures, feel free to ask questions or make suggestions on our forums or to email the site owner. (His email is on the bottom). Thanks for the interest, glad to be of help.

---

### Post by blueshiftoverwatch on 2010-04-12
Nvm, I'll ask this on a Debian forum.

---

### Post by Uncle Spellbinder on 2010-04-12
Well, same issue I've had for a while now. When it gets to selecting keyboard layout, nothing happens. Keyboard is not responsive at all. :-k

---

### Post by NightwishFan on 2010-04-12
that is quite odd, as Ubuntu shares the debian core, and debian testing is more up to date than ubuntu 9.10 :o

---

### Post by blueshiftoverwatch on 2010-04-12
> **NightwishFan said:**
> that is quite odd, as Ubuntu shares the debian core, and debian testing is more up to date than ubuntu 9.10 :o
Ubuntu's packages are up to 6 months old by the end of a release's lifespan. Wheras Debian Testing's can update in as little as every 10 days.

---

### Post by Uncle Spellbinder on 2010-04-13
Really weird. Wouldn't work with Debian stable ("Lenny") either.  Tried all three of my keyboards (all wireless), none work. Never had this issue with any other distro I've installed. Guess I'll need to buy a cheap wired keyboard.

---

### Post by oOarthurOo on 2010-04-15
For wireless keyboard issues a post on the Debian forums or debian-user mailing list is recommended.

Also drop those strange unofficial deb repos from the end. Never heard of them.

Look up the thread on forums.debian.net the how-to on Liquorix kernel IF you are running testing.

---

