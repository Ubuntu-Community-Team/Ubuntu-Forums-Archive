---
title: "Guide: Interstate Outlaws"
date: 2007-08-24
forum: Ubuntu Gamers Arena
---

### Post by Perfect Storm on 2007-08-24
*Until the new UGA is up and running, I'll post my Gaming guides in this forum. When UGA's ready these guides will be transfer to UGA and deleted from the forum. This is just in quickstep form but will be ellaborated when moved.*

Check UGA for news.

This is tested on Ubuntu (gnome) 7.04 x86, nvidia card - glibc 2.5 and python 2.5 version.

Download glibc 2.5 and python 2.5 version of Outlaws to your Desktop.
[http://www.interstateoutlaws.com/forum/index.php?showtopic=120](http://www.interstateoutlaws.com/forum/index.php?showtopic=120)

```

mkdir -p ~/.Games/Outlaws
cd ~/Desktop
tar zxfv Outlaws-0.1.1a-linux-glibc25.tar.gz
cd Outlaws-0.1.1a
mv * ~/.Games/Outlaws
cd  ~/.Games/Outlaws
nano Launch-Outlaws.sh
```

add following:

```
#!/bin/bash

cd ~/.Games/Outlaws      

python outlaws.py
```

save and exit.
Next;

```
chmod +x Launch-Outlaws.sh
alacarte
```

Name: Outlaws
icon: ~/.Games/Outlaws/outlaws.png
Command: sh /home/**<USERNAME>**/.Games/Outlaws/Launch-Outlaws.sh
Comment: FPS in cars <or whatever you prefer>

---

### Post by cogadh on 2007-08-24
If I may suggest a very minor change, you can combine the first two steps into one by doing this instead of two separate "mkdir" commands:
```
mkdir -p ~/.Games/Outlaws
```

---

### Post by Perfect Storm on 2007-08-24
will do...old habit die hard.

---

### Post by compiledkernel on 2007-08-24
Added.

[http://gaming.gwos.org/doku.php/guides:interstateoutlaws](http://gaming.gwos.org/doku.php/guides:interstateoutlaws)

---

### Post by battles33 on 2007-12-09
hey, could you help me out?
when i type the command to run the game in the terminal, i get this error


sh /home/<username>/.Games/Outlaws/Launch-Outlaws.sh
/home/<username>/.Games/Outlaws/celstart/celstart_static: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

i searched the file on google, found this page [http://rpmfind.net/linux/rpm2html/search.php?query=libpython2.5.so.1.0()(64bit](http://rpmfind.net/linux/rpm2html/search.php?query=libpython2.5.so.1.0()(64bit))
downloaded the x_64 file and aliened it so i could installed the rpm. however i'm still getting the same error when trying to launch outlaws

---

### Post by cogadh on 2007-12-09
That library is available in the repositories, you shouldn't need to alien an RPM to install it. Just run Synaptic and search for Python, you'll find it.

In the future, whenever an application comes up saying it can't find a library, don't go to Google first, go to Synaptic. Nearly every time the correct library is already available in the Ubuntu repositories.

---

### Post by battles33 on 2007-12-09
codadh: i definitely checked synaptic prior to resorting to google. python's already installed. however, a point perhaps worth mentioning is that i have "python" and "python2.4", for "python", it is however 2.5.1-1ubuntu, where the 2.5.1 should of course contain the proper files that that error message is giving me

---

### Post by cogadh on 2007-12-09
If I understood that correctly, you are saying that you have Python 2.4 installed. All you should need to do is install the Python 2.5 package and everything should be fine:
```
sudo apt-get install python2.5
```

---

### Post by battles33 on 2007-12-09
i had both python2.4 and python 2.5 installed. as for python 2.5, i didn't notice it at first, but there's an entry in synaptic for "python" and additionally an actual "python2.5" (where python is installed version 2.5.1-1ubuntu2 and python2.5 is 2.5.1-5ubuntu5). i reinstalled both python and python2.5 (both of these were already there to begin with) and removed python 2.4 in case 2.4 was interfering in some way (tried to remove "python" as well but this one has a lot of dependencies). i also installed anything and everything that was associated with python2.5, which were: -dbg, -dev, -doc and -examples. these didn't help the cause

same error appears when running the command
sh /home/<username>/.Games/Outlaws/Launch-Outlaws.sh
/home/<username>/.Games/Outlaws/celstart/celstart_static: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

---

### Post by cogadh on 2007-12-09
That's really odd. The Python 2.5 package is basically that very library plus a few symlinks to it for compatibility purposes. You could try creating a symlink to the library in the Outlaws directory:
```
ln -s /usr/lib/libpython2.5.so.1.0 /home/<username>/.Games/Outlaws/libpython2.5.so.1.0
```

---

### Post by battles33 on 2007-12-10
still same error. thanks so much for the help though, cogadh

since the error is that the libraries aren't found ("no such file or directory"), i'm thinking that perhaps that file celstart_static is looking somewhere other than /usr/lib for the file, although that kinda doesn't make sense as it is in fact located in the libraries folder haha.

this game looks so great, especially since '72 was so much fun to play way back in the day.. ah well, after my exams are done up i'll spending some time looking into this.

once again cogadh, thanks a million for responding

---

