---
title: "You have no idea how confused I am right now!"
date: 2005-09-10
forum: The Cafe
---

### Post by xequence on 2005-09-10
People say RPM based system have dependancy hell... Well, I think ive just experienced it. I just wanted to post my experience...

OK. I wanted to install hacked box because fluxbox takes awhile to load... I downloaded 50 MB of X dev stuff from synaptic. I got the sudo make whatever stuff to work, but I couldent load into hacked box from sessions in GDM. SO I decided to stay with openbox. I have a small python file to install a dock thing at the bottom... I had to download one thing to get something to work, I had to download SO many things in a long line just to get one little 30 KB application installed! And believe me, it was alot of things... I am so confused I can hardly remember half of them. In the end I gave up, after alot of downloading and installing devs and libs of every sort. THe thing that stopped me was I needed one final thing... Some file from enlightenment.com. I have e17 installed, so I thought, weird. It said I didnt have permission when I went to the site i gave me... My terminal history was crazy you wouldent believe it.


My system is probably all bloated up from all this stuff... Doing a server install then installing the barebones things from apt-get sounds interesting ;)

THe moral of this story is, stay with apt-get and synaptic ;)

OH, one more weird thing... I needed to do a python script to install the file. I downloaded python devs and it needed a python script to install python! DOes that make any sense? Its like needing what you are getting to get what you want.

I know I am rambling on, but I just do that when im frusterated ;)

SO, there is my story.

---

### Post by poofyhairguy on 2005-09-10
Whats your sources.list look like?

---

### Post by xequence on 2005-09-10
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Multiverse repositories
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse

## Hoary Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse

##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/

---

### Post by poofyhairguy on 2005-09-10
You need this:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

---

