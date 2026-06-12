---
title: "Package Count [Solved]"
date: 2019-08-15
forum: Ubuntu, Linux and OS Chat
---

### Post by cruzer001 on 2019-08-15
Just curious about the difference in pkg count between my gnome-desktop install and the ubuntu-gnome-desktop count.

Mine is the full gnome desktop built from a mini install with several extra packages.  It only shows 1755 packages installed.  That just sounds really low to me.

```
dpkg -l | grep '^ii ' -n
```

---

### Post by Frogs Hair on 2019-08-15
Budgie development with the gnome stack shows 1936.

---

### Post by cruzer001 on 2019-08-15
Nice..The package count is a ballpark figure since additional installed  packages are not broken down, but I would also call yours a low count. I run Budgie on a really old single core laptop.  Its not fast, but it is very usable.  

Still hope to hear from some ubuntu-gnome people.

---

### Post by #&amp;thj^% on 2019-08-15
> **cruzer001 said:**
>  It only shows 1755 packages installed.  That just sounds really low to me.

```
dpkg -l | grep '^ii ' -n
```
I know your just interested in "Ubuntu-Gnome" but I'm a bit surprised to see  the numbers reported here.
On Arch I see, 1660 pkg's, and I have 4 DE's installed here. (Please no Flames needed here just a comparison is all)
This Install is 5 years old.
```
head -n1 /var/log/pacman.log
[2014-12-10 13:38] [PACMAN] Running 'pacman -r /mnt -Sy --cachedir=/mnt/var/cache/pacman/pkg --noconfirm base'

```

---

### Post by cruzer001 on 2019-08-15
> **1fallen said:**
> I know your just interested in "Ubuntu-Gnome" but I'm a bit surprised to see  the numbers reported here.
On Arch I see, 1660 pkg's, and I have 4 DE's installed here. (Please no Flames needed here just an comparison is all)
And I appreciate your input, IMO Arch will always lowball Ubuntu and it flavors.  Sure your not hanging out a bit of flame bait :D

---

### Post by #&amp;thj^% on 2019-08-15
> **cruzer001 said:**
> Sure your not hanging out a bit of flame bait :D
I know my intentions, but as always subject to readers perspective.:o
Always here to help, not to add conflict. :p

---

### Post by cruzer001 on 2019-08-15
All is cool :)

---

### Post by Bashing-om on 2019-08-15
cruzer001; Hey Hey :)

Non-gnome but my count from a core install:
> 
sysop@x1804mini:~$ dpkg -l | grep '^ii ' -n
1290:ii 


[INDENT]sheds a bit of light
[/INDENT]

---

### Post by cruzer001 on 2019-08-15
Hi Bashing-om

Thanks for the input.  That must be [Ubuntu Core.]("https://ubuntu.com/core")

Still wondering about Ubuntu-gnome :)

---

### Post by Dennis N on 2019-08-15
> Still wondering about Ubuntu-gnome
Synaptic Package Manager also informs you of the number of installed packages.  
Ubuntu Gnome 18.04 - 2095 packages installed, 63,933 listed.
Obviously, the number is going to vary.

---

### Post by cruzer001 on 2019-08-16
Hello Dennis N

Yes Synaptic will give the package count, but (unfortunately) not everybody uses it these days, thus the code.

Even though the package count will vary I truly thought vanilla ubuntu-gnome would weigh in heavier than that.  

Curiosity satisfied, thanks Dennis :)

---

### Post by P-I H on 2019-08-16
I made a standard installation of Ubuntu 19.10 yesterday on an Asus laptop. I get the following values
from Synaptic: 62565 packages listed and 1625 installed
from the command: 1630:ii

---

### Post by tea for one on 2019-08-16
> **cruzer001 said:**
> Just curious about the difference in pkg count between my gnome-desktop install and the ubuntu-gnome-desktop count.

Mine is the full gnome desktop built from a mini install with several extra packages.  It only shows 1755 packages installed.  That just sounds really low to me.

```
dpkg -l | grep '^ii ' -n
```

From a **live** session of virgin Ubuntu 19.04 and using the terminal code, the answer is 1820

---

### Post by echotech2 on 2019-08-16
Last couple if lines from your command....

```
3001:ii  zip                                           3.0-11build1                                 amd64        Archiver for .zip files
3002:ii  zlib1g:amd64                                  1:1.2.11.dfsg-0ubuntu2                       amd64        compression library - runtime
3003:ii  zlib1g:i386                                   1:1.2.11.dfsg-0ubuntu2                       i386         compression library - runtime
3004:ii  zlib1g-dev:amd64                              1:1.2.11.dfsg-0ubuntu2                       amd64        compression library - development

```  

I think I have a bunch of whatever your command does.

---

### Post by cruzer001 on 2019-08-17
Thanks for the input.

There does not seem to be a big difference between [just Gnome]("https://packages.ubuntu.com/bionic/gnome") and [Ubuntu Gnome]("https://packages.ubuntu.com/bionic/ubuntu-desktop").  They are both heavy weights, package count is not that different.  I did expect the count to be higher, but thats what I wanted to find out.

@echotech2
3004 is the number of packages installed on your system.   Possibily you have installed multiple desktops, that could account for the high package count.
or
You have installed everything including a coffee maker :)

---

### Post by echotech2 on 2019-08-18
I don't think I have the coffee maker installed, but I do have K3b installed which was a whole bunch of stuff. &#55357;&#56833;

---

### Post by cruzer001 on 2019-08-18
> **echotech2 said:**
> I don't think I have the coffee maker installed, but I do have K3b installed which was a whole bunch of stuff. &#65533;&#65533;
K3b use to be my go to program, the extra kde packages didn't seem to get in the way or slow anything down.  These days its a rare thing for me to burn a disk, just have too many thumb drives laying around.  I would take a look at systemd startup, could have kde processes that can be killed.
```
systemd-analyze blame
```
[https://www.freedesktop.org/wiki/Software/systemd/](https://www.freedesktop.org/wiki/Software/systemd/)

And for what its worth, marking this as solved.

---

### Post by cruzer001 on 2019-08-24
Update

I now have a basic gnome desktop with packages like FireFox, Nemo, GnomeMPV and default system tools.  Total Package count 951.  Uses 511M of ram when idle.

I started with [gnome-sessions]("https://packages.ubuntu.com/bionic/gnome-session")

---

