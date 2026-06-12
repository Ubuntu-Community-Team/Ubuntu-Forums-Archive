---
title: "What repositories do you use?"
date: 2005-02-25
forum: The Cafe
---

### Post by jdong on 2005-02-25
To learn Python, I've decided to write a WAIH (Warty After-Install Helper) clone.
You can track its development in the Backports SVN: [http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/)

 One module generates APT sources.list files. I've got my list of sensible repositories to implement here: [http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/branches/apt-helper/REPOS](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/branches/apt-helper/REPOS)

Do you guys have any other suggestions?

---

### Post by TravisNewman on 2005-02-25
Debian? That's a bit risky, I dunno if I'd suggest that but it can be a fun ride ;)

anyway, my sources-- remember, you asked for it ;)

```

# Monodevelop, muine, tomboy, etc
# deb http://www.getsweaaa.com/~tseng/ubuntu/debs/ ./ 

# alternate for muine, tomboy
# deb http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu/ warty-updates main universe 

# Warty Backports
# deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe 
# deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports-staging main universe 
# deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras universe 
# deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras-staging universe 

# Quakeforge - newer packages in the sources below
# deb http://www.quakeforge.net/packages/debian/ unstable contrib non-free 

# Some gaming stuff: the quakes, psemu, etc-- possibly questionable legality
deb http://www.fbriere.net/debian/dists/stable/ ./ 
deb-src http://www.fbriere.net/debian/dists/stable/ ./ 
deb http://www.fbriere.net/debian/dists/testing/ ./ 
deb-src http://www.fbriere.net/debian/dists/testing/ ./ 
deb http://www.fbriere.net/debian/dists/unstable/ ./ 
deb-src http://www.fbriere.net/debian/dists/unstable/ ./ 

# Mostly outdated stuff, but it has gst-ffmpeg_0.8.2-1_i386
deb http://pkg-gnome.alioth.debian.org/debian/ unstable main  

# Oliver Grawert's repo. Gotta love it. mrburns, pimp,
# startup-settings, evnotify, graveman, xdesktopwaves, gcursor
deb http://www.grawert.net/ubuntu/ warty universe 
deb http://apt.cerkinfo.be/ unstable main contrib non-free 

#Videolan and some codecs and libraries missing/borked in hoary
deb 	http://download.videolan.org/pub/videolan/debian woody main
deb-src http://download.videolan.org/pub/videolan/debian woody main
deb 	http://download.videolan.org/pub/videolan/debian sarge main
deb-src http://download.videolan.org/pub/videolan/debian sarge main
deb 	http://download.videolan.org/pub/videolan/debian sid main
deb-src http://download.videolan.org/pub/videolan/debian sid main

#java
deb	ftp://neacm.fe.up.pt/pub/ubuntu-java/ binary/
deb-src ftp://neacm.fe.up.pt/pub/ubuntu-java/ source/

#hardened kernels
deb     http://people.ubuntu.com/~pitti/linux-hardened/  /
deb-src http://people.ubuntu.com/~pitti/linux-hardened/  /

```

---

### Post by jdong on 2005-02-26
Cool. Thanks.

BTW, the APT helper script is coming together quite nicely. Python is an instant-productive language.

Right now, the program is able to get user selections and spit out a sources.list to stdout.

Working on a backup & write-to-disk extension right now.


When I feel that it's stable for people to test, I'll tag out a version. :D

---

### Post by Yukonjack on 2005-02-26
Hehehe that is some sources.list you have there panickedthumb. :)

---

### Post by TravisNewman on 2005-02-27
That's after it's been cleaned up too!! I got sick of waiting so long for apt-get update.

---

### Post by Ironi on 2005-02-27
Active:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

Commented out:
Debian testing, unstable, and experimental
Marillat
Smurf
Kalyxo
Wine

---

### Post by jdong on 2005-02-27
[http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/branches/apt-helper/uh_apt_helper.py](http://backports.ubuntuforums.org/backports/projects/ubuntu-helper/branches/apt-helper/uh_apt_helper.py)

Well, the program's basically done. Currently, it only dumps the end result to stdout (the screen), for safety.

I still gotta add more sources, but it's a piece of cake to do so! I deliberately made it simple to customize.

I'll comment the code a bit more, add the actual file writing capability, and release a beta by Friday. :D

---

