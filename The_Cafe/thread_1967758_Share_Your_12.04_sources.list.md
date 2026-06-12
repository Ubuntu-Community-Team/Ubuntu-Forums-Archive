---
title: "Share Your 12.04 sources.list"
date: 2012-04-28
forum: The Cafe
---

### Post by Uncle Spellbinder on 2012-04-28
I know there are easier ways to add repos, but I prefer manually editing sources.list. 

Thgought it might be cool to see what others have done with their  sources.list. What have you added to your repos? What's your sources.list look like?


Mine:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos ######
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos ######

#### Updates
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

#### Security
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse

#### Proposed
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse

#### Backports
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse  

#### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

#### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main



##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd PARTY REPOS ######

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu precise main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main

#### Mozilla Firefox [Beta Channel]
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu precise main 
deb-src http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu precise main

#### Clementine [Development]
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu precise main 
deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu precise main

#### gThumb
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/gthumb/ubuntu precise main 
deb-src http://ppa.launchpad.net/webupd8team/gthumb/ubuntu precise main 

#### SMPlayer
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu precise main 
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu precise main

#### Glx-Dock / Cairo-Dock - http://www.glx-dock.org
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise  main
deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main

#### LibreOffice - http://www.documentfoundation.org/download/
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
```

---

