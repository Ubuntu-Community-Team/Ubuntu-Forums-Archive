---
title: "Can anyone install Cli Companion in 13.04?"
date: 2013-04-01
forum: Ubuntu Development Version
---

### Post by pwc on 2013-04-01
I'm a long time user of Ubuntu but had to skip 12.10 (used Mint) because I never figured out how to install Cli Companion. I was hoping to get back to Ubuntu and have installed 13.04, but still cannot get Cli Companion working.
I tried apt-get(after adding PPA) and also downloaded .deb installer, still no luck. Is there anyone that has figured out how to do this, I'm sure it's something simple I've overlooked. 

I gotta have this in my linux distro, I'm 73 and can't remember sh......, 

Thanks, pwc

---

### Post by stinkeye on 2013-04-01
Dowloaded and installed the **Precise** package from the ppa works here.
No build for Raring or Quantal in the ppa.

Link to ppa...[https://launchpad.net/~clicompanion-devs/+archive/clicompanion-nightlies/+packages](https://launchpad.net/~clicompanion-devs/+archive/clicompanion-nightlies/+packages)
Direct link to Precise deb download...[**_[COLOR="#B22222"]clicompanion_1.1-6~bzr111+p21~precise1_all.deb[/COLOR]_**]("https://launchpad.net/~clicompanion-devs/+archive/clicompanion-nightlies/+files/clicompanion_1.1-6~bzr111%2Bp21~precise1_all.deb")

Raring 64bit
Installed using gdebi.

> **pwc said:**
> 
I gotta have this in my linux distro, I'm 73 and can't remember sh......, 

Thanks, pwc
Yeah, the old brain cells start to prioritize as you get older. #-o
More important to remember what day it is. :)

---

### Post by pwc on 2013-04-04
Thanks for answering stinkeye, I actually got in working without installing Precise pkgs, I had it installed with the .deb file, it just would'nt open.
But after running a script(Ubuntu-after-install) it did open, happily surprising me. Don't know what happened causing it to open, but on my way
with Raring, so far I'm liking it, seems more refined!

thanks again,pwc

---

### Post by VinDSL on 2013-04-04
LoL!  Begs the question...  :popcorn:

What does "CommandlineFU Commands" do?  :D

---

### Post by dino99 on 2013-04-04
is not that an abandonware ?

---

### Post by schragge on 2013-04-04
Well, the last commit on the trunk branch is from [2013-02-19]("https://code.launchpad.net/%7Eclicompanion-devs"). So is the last PPA package for *precise*. I'd rather not call it *abandonware*. True that they don't have PPA packages of it specifically built for *quantal*. But being just a python app seems not so critical. You may always
```
apt-get -b source clicompanion/precise
sudo dpkg -i clicompanion*.deb
```

---

### Post by stinkeye on 2013-04-05
> **VinDSL said:**
> LoL!  Begs the question...  :popcorn:

What does "CommandlineFU Commands" do?  :D
It allows you to search and add command-line snippets from
_[http://www.commandlinefu.com/commands/browse](http://www.commandlinefu.com/commands/browse)_

---

