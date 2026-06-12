---
title: "apt-mirror program strings in sources.list"
date: 2010-12-15
forum: Server Platforms
---

### Post by R.Bucky on 2010-12-15
I have created an Ubuntu repo mirror with the following entries. What entry would I need to make in my sources.list to have Dropbox or other non Ubuntu native packages installable? 

sources.list
```

deb http://olyubuntu.nwlinux.com lucid main restricted
deb http://olyubuntu.nwlinux.com lucid-updates main restricted
deb http://olyubuntu.nwlinux.com lucid universe
deb http://olyubuntu.nwlinux.com lucid-updates universe
deb http://olyubuntu.nwlinux.com lucid multiverse
deb http://olyubuntu.nwlinux.com lucid-updates multiverse
deb http://olyubuntu.nwlinux.com lucid main

```
mirror.list
```

#### Dropbox - https://www.dropbox.com/
## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
deb-i386 http://linux.dropbox.com/ubuntu lucid main
deb-amd64 http://linux.dropbox.com/ubuntu lucid main

#### Opera - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb-i386 http://deb.opera.com/opera/ lenny non-free
deb-amd64 http://deb.opera.com/opera/ lenny non-free

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb-i386 http://download.webmin.com/download/repository sarge contrib
deb-amd64 http://download.webmin.com/download/repository sarge contrib

#Google Picasa
deb-i386 http://dl.google.com/linux/deb/ stable non-free main
deb-amd64 http://dl.google.com/linux/deb/ stable non-free main

#Handbrake Added 05Dec10
#deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu lucid main

#Standard Repositories
deb-i386 http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse

deb-i386 http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse

#SECURITY
deb-i386 http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-amd64 http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-i386 http://us.archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-amd64 http://us.archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
#Partner Repository
deb-i386 http://archive.canonical.com/ubuntu lucid partner
deb-amd64 http://archive.canonical.com/ubuntu lucid partner


```

---

