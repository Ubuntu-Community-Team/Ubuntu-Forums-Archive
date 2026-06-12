---
title: "install xampp"
date: 2011-09-22
forum: Server Platforms
---

### Post by olking on 2011-09-22
I have downloaded xampp 1.7.7 and it is in my download folder
when I type the command which is given in the notes:-

sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt

 this is the result:-

tar xampp-linux-1.7.7.tar.gz: cannot open no such file or directory
 tar Error is not recoverable: exiting now
tar Child returned status 2
tar Exiting with failure status due to previous errors.

Can anyone advise how to solve the problem

---

### Post by ibutho on 2011-09-22
You need to use the right path for the location of xampp e.g.
```
sudo tar xzvf /home/someuser/Downloads/xampp-linux-1.7.7.tar.gz -C /opt
```
or run the commands from the directory where you saved xampp e.g.
```
cd /home/someuser/Downloads
sudo tar zxvf xampp-linux-1.7.7.tar.gz -C /opt

```

---

### Post by seawolf167 on 2011-09-22
Aye, as posted above, when you open a terminal by default its working directory will be your /home directory. You'll either need to cd (change directory) to the directory it exists in

```
cd ~/Downloads
```

or explicitly include that path in your tar command.

---

### Post by olking on 2011-09-22
> **ibutho said:**
> You need to use the right path for the location of xampp e.g.
```
sudo tar xzvf /home/someuser/Downloads/xampp-linux-1.7.7.tar.gz -C /opt
```
or run the commands from the directory where you saved xampp e.g.
```
cd /home/someuser/Downloads
sudo tar zxvf xampp-linux-1.7.7.tar.gz -C /opt

```

Thank you very much that worked beautifully:p

---

### Post by philipballew on 2011-09-23
you are aware all you need to do is ```
sudo apt-get install zenmap
``` for it to install. Is there any particular reason you need bleeding edge?

---

### Post by mörgæs on 2011-09-23
[http://ubuntuforums.org/showpost.php?p=11277327&postcount=3](http://ubuntuforums.org/showpost.php?p=11277327&postcount=3)

---

### Post by PayPaul on 2011-09-26
> **seawolf167 said:**
> Aye, as posted above, when you open a terminal by default its working directory will be your /home directory. You'll either need to cd (change directory) to the directory it exists in

```
cd ~/Downloads
```or explicitly include that path in your tar command.


I'm trying to get into the directory that contains a fractal generator called Quat. So I attempted to get into that directory. If I'm in the home directory it should have been easy. Right?

Nope. No such directory. So I did a *dir* command and this is the result:

paulw@ubuntu:~$ dir
Alien\ Terminator           Music
Audiobooks               Pictures
Desktop                   Podcasts
Documents               pspI\ Photoshop\ Plugin\ Prog\ For\ GIMP
Downloads               Public
Dynamic\ Photo\ Hdr\ 4.01      Quats
examples.desktop           Steeleye\ Span\ -\ Below\ The\ Salt
fract0.png               Templates
fract111.png               Ubuntu\ 11-4\ Live\ Cd\ Created\ On\ 092211
fract11\ Net1.png           Ubuntu\ One
fract21\ Net2.png           Videos
jUploadr-1.1.2-linuxGTK-amd64  WinAmp\ 562\ For\ Windows
Luminance\ HDR
paulw@ubuntu:~$ cd /Quats
bash: cd: /Quats: No such file or directory
paulw@ubuntu:~$

Quats is in there but terminal can't find it. I've got a tar.gz file and also the decompressed folder from it. I want to install the program but can't even make the apt-get install command work because I can't get into the directory it's in.

---

### Post by seawolf167 on 2011-09-26
> **PayPaul said:**
> I'm trying to get into the directory that contains a fractal generator called Quat. So I attempted to get into that directory. If I'm in the home directory it should have been easy. Right?

Nope. No such directory. So I did a *dir* command and this is the result:

paulw@ubuntu:~$ dir
...
Dynamic\ Photo\ Hdr\ 4.01      Quats
...
paulw@ubuntu:~$ **cd /Quats**
bash: cd: /Quats: No such file or directory
paulw@ubuntu:~$


Your default working directory is /home, and by typing /Quats you are saying to look in / (root) for Quats which doesn't exist. You have two options; simply type

```
cd Quats
```or 

```
cd /home/paulw/Quats
```

---

