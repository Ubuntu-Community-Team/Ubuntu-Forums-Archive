---
title: "What details to share and not to in Web ?"
date: 2017-11-12
forum: Security
---

### Post by thehannibal on 2017-11-12
I'm new to Ubuntu, what I wanted to confirm was when somebody asks on the forum to post details about my system like:

1> output of ```
$ inxi -Fxzc0
``` 
2> Screenshot of my Browser (firefox)
3> File manager screenshot, showing my Drives

should I, Is it safe to do so ?

---

### Post by ian-weisser on 2017-11-12
Nothing you have listed is unsafe, though screenshots can be a bit obtuse.

It is *encouraged* to ask what a mysterious command does before running it. NEVER run a command that you do not completely understand.
In the case of 'inxi', it's a harmless script that will gather system data (not personal data), saving you a lot of hassle. The person who asked you to run it, vasa1, is well known and has an excellent reputation in this forum.

There is normally no useful security or system information is an average screenshot. 
I don't post screenshots merely because my system is *likely* to be configured differently than yours - screenshots tend to waste bandwidth for little gain.
And, frankly, you and Chinese Military Intelligence don't need to know what's on my desktop or among my bookmarks.
And most maintenance can be done faster and easier from the shell anyway.

One of the most important things you must learn in this community is that there's a difference between "the best Windows way" , "the best Linux way", and "my way"...and often they do not overlap much. Accept the differences, and make your choices based upon what makes you happiest.

---

### Post by thehannibal on 2017-11-12
I saw that forum moderator tag and knew that the command was safe probably. I was just curious in general.
Thanks for clarifying about the screenshot thing.

And Yes I like the shell way too, I will be careful and search about the command someone asks me to execute **before actually executing it**.

---

### Post by oldos2er on 2017-11-12
Just to add a bit to ian's wise advice, you can run ```
apt show inxi
``` to give you info about that particular command. *inxi* is in the repositories but not installed by default.

```
acsh inxi
Package: inxi
Version: 2.3.37-1
Priority: extra
Section: universe/misc
Origin: Ubuntu
Maintainer: Unit 193 <unit193@ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 625 kB
Depends: gawk, pciutils, procps
Recommends: dmidecode, file, hddtemp, iproute2, kmod, lm-sensors, mesa-utils, net-tools, sudo, usbutils, x11-utils, x11-xserver-utils
Homepage: http://smxi.org/docs/inxi.htm
Task: xubuntu-desktop, ubuntustudio-desktop, ubuntu-mate-core, ubuntu-mate-desktop
Download-Size: 140 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu artful/universe amd64 Packages
Description: full featured system information script
 Inxi is a system information script that can display various things about
 your hardware and software to users in an IRC chatroom or support forum.
 It runs with the /exec command in most IRC clients.

```

I have "acsh" set as an alias for "apt show" in case you were wondering. The "c" is a leftover from when the command used to be "apt-cache show."

---

### Post by thehannibal on 2017-11-12
+1 for the alias, now I don't have to browse for the package anymore.

```
echo "alias ash='apt show'" >> ~/.bashrc
```

New bash alias ash to check details of command

---

### Post by coldraven on 2017-11-13
I have seen screenshots where people forgot to hide the bookmarks toolbar. In one case it showed that the poster had a certain bank account. Without having the posters email address this information is useless but maybe it could be obtained from another posting somewhere. The less info that you show the web the better it is.

---

### Post by thehannibal on 2017-11-13
> **coldraven said:**
> I have seen screenshots where people forgot to hide the bookmarks toolbar. In one case it showed that the poster had a certain bank account. Without having the posters email address this information is useless but maybe it could be obtained from another posting somewhere. The less info that you show the web the better it is.

Exactly why I asked this question, I'm going to try pixelating/blackenig/blurring (or) some sort of obscuring for personal and sensitive data that I share as Images to Web. Usually I don't share too much to Web at all and in case I have to if there is some info that could be compromising I crop the region that is required and post it.

---

