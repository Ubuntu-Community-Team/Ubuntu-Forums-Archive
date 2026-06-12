---
title: "What terminal commands do you use the most?"
date: 2009-05-05
forum: The Cafe
---

### Post by jordanae on 2009-05-05
I've been using the terminal a lot lately. Once you get used to something like using apt-get or the mv command things can become a lot faster.

So what commands do you use the most? And which commands are the most useful to you?

I use apt-get, netstat, and whereis a LOT O.o

---

### Post by Firestem4 on 2009-05-05
sudo apt-get [install; remove; autoclean; autoremove]
sudo pacman -Syu; -Ru (Arch package manager).


Oh and recently killall plasma; kstart plasma.

---

### Post by JohnFH on 2009-05-05
See here: [http://ubuntuforums.org/showthread.php?t=472090&highlight=terminal+commands]("http://ubuntuforums.org/showthread.php?t=472090&highlight=terminal+commands")

---

### Post by monsterstack on 2009-05-05
Apart from the obvious ls and cat commands, I suppose I use apt-get and friends all the time, so much I eventually just made a bunch of aliases to shorten things a bit. I do loads of text-editing too, and have a bunch of aliases to do stuff such as datestamp them like this:

```
for x in $@; do if [ -e $x ]; then mv $x $(date +'%F')-$x; echo "Renamed $x successfully."; else echo "$x? File doesn't exist, fool."; fi; done
```

---

### Post by joey-elijah on 2009-05-05
I think 'sudo apt-get [install, upgrade, update, remove, autoremove] have become my nervous twitches; i find myself running updates/upgrades about 20 times a day when bored... just in case!

---

### Post by mr_rg on 2009-05-05
127 ls
     61 cd
     43 make
     40 dta_clientg2
     38 gcc
     37 bin2socket
     21 ./mesh
     16 ./text
     12 man
     12 emacs

---

### Post by Tipped OuT on 2009-05-05
sudo
help
history
clear

:P

---

### Post by nobodysbusiness on 2009-05-05
[j]("http://wiki.github.com/joelthelion/autojump") is good.

---

### Post by SuperSonic4 on 2009-05-05
```
141 sudo
93 cd
58 ffmpeg
     29 ls
     29 cp
     24 pacman
     22 wget
     22 rm
     21 mencoder
     21 flac
```

---

### Post by hessiess on 2009-05-05
295 cd
     89 pdflatex
     69 svn
     60 find
     58 python
     48 g++
     47 sudo
     40 exit
     35 quicksvn
     25 ls

---

### Post by Asem on 2009-05-05
I use " top " alot

---

### Post by BazookaAce on 2009-05-05
Do we really need another, "What's your most used Terminal-commands"-thread??

---

