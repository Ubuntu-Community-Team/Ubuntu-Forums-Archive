---
title: "Hero of Allacrost issues"
date: 2008-09-29
forum: Ubuntu Gamers Arena
---

### Post by KingHanco on 2008-09-29
mitchellhancock@mitchellhancock-desktop:~$ deb [http://debian.ettin.org/allacrost](http://debian.ettin.org/allacrost) etch-backports main
bash: deb: command not found
mitchellhancock@mitchellhancock-desktop:~$ wget [http://debian.ettin.org/key.gpg](http://debian.ettin.org/key.gpg) -O - | sudo apt-key add -
[sudo] password for mitchellhancock: --13:34:40--  [http://debian.ettin.org/key.gpg](http://debian.ettin.org/key.gpg)
           => `-'
Resolving debian.ettin.org... 208.113.179.173
Connecting to debian.ettin.org|208.113.179.173|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,945 (2.9K) [text/plain]

100%[====================================>] 2,945         --.--K/s             

13:34:40 (49.99 KB/s) - `-' saved [2945/2945]

mitchellhancock@mitchellhancock-desktop:~$ apt-get update && apt-get install allacrost-demo
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mitchellhancock@mitchellhancock-desktop:~$

Seem broken on the new Ubuntu. =(

[http://allacrost.sourceforge.net/wiki/index.php/Installation_Instructions](http://allacrost.sourceforge.net/wiki/index.php/Installation_Instructions)

Could it be out of date website?

---

### Post by Perfect Storm on 2008-09-29
> E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

You can only have one package manager in action at the time. Close synaptic. Or you need to put sudo in front of it.

Please follow the guide; [http://gaming.gwos.org/doku.php/guides:64bit:hero_of_allacrost](http://gaming.gwos.org/doku.php/guides:64bit:hero_of_allacrost)

EDIT: Please disable Debian repo in Ubuntu. You'll end up borking your system.

---

### Post by KingHanco on 2008-09-29
1 problem.

libqt4-opengl-dev can't be found.

---

### Post by Perfect Storm on 2008-09-29
Which version of Ubuntu do you use? You need Ubuntu 8.04

---

### Post by KingHanco on 2008-09-29
I have that one. 8.04

Will not find that file.

Another problem.

mitchellhancock@mitchellhancock-desktop:~/Desktop/allacrost-0.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether to enable -O3 compiler optimization... yes
checking whether to enable debugging... no
checking how to run the C preprocessor... gcc -E
checking for X... no
checking whether to enable usage of map editor... yes
checking for Qt4 headers... no
checking for Qt4 libraries... no
configure: error: Qt4 development libraries not found
See `config.log' for more details.
mitchellhancock@mitchellhancock-desktop:~/Desktop/allacrost-0.2.2$

---

### Post by Perfect Storm on 2008-09-29
Give me the output of
```
sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev liblua50-dev liblualib50-dev libluabind-dev libgl1-mesa-dev libglu1-mesa-dev libqt4-dev libqt4-opengl-dev libopenal-dev
```

---

### Post by RootsLINUX on 2008-09-29
**libqt4-dev libqt4-opengl-dev**

That sounds like the packages you are missing. The problem may be that the Debian package fails to mention it as a dependency. Can you open up the package details in Synaptic and see if its listed there?

---

### Post by Winter Knight on 2008-09-30
A few tips:


- What version of Ubuntu are you using? The "new" version could be Hardy (latest stable) or Intrepid (current Beta). It looks like you are using Hardy.

- You need to be root to use apt-get. Or precede the command with "sudo".

- "deb [http://debian.ettin.org/allacrost](http://debian.ettin.org/allacrost) etch-backports main" is not a command you enter on the command line. And it is obsolete. You would add that line to your /etc/apt/sources.list file. If you were going to use apt-get to install Allacrost, you should add the line from the Allacrost download page, but that still won't work, because the latest Allacrost Debian package will not work in Hardy.

- The Debian Allacrost Editor package will not work out of the box on Hardy. The Debian package requires libqt-opengl-dev, which is not available in Hardy. Rather, those files are included with libqt-dev, but dpkg is not smart enough to figure that out. There are ways around this, but it would be easier to compile from source.

- libqt-opengl-dev is not in the Hardy repositories. Some comments above were mistaken. Although, it is available from Hardy-backports, but be careful of getting a version mismatch between QT versions.

I recommend compiling from source. This should do it for you:
cd ~/Desktop/allacrost-0.2.2
sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev liblua50-dev liblualib50-dev libluabind-dev libgl1-mesa-dev libglu1-mesa-dev libqt4-dev libqt4-opengl-dev libopenal-dev (this command is all one line)
./configure && make
./allacrost

If you get any errors about missing packages with the apt-get line, that is probably OK.

---

### Post by RootsLINUX on 2008-09-30
Maybe this is a sign that an enthusiastic Ubuntu user should create a separate .deb that works for Ubuntu. ;)

---

### Post by Perfect Storm on 2008-10-12
> **RootsLINUX said:**
> Maybe this is a sign that an enthusiastic Ubuntu user should create a separate .deb that works for Ubuntu. ;)

You can report this to [https://launchpad.net/playdeb](https://launchpad.net/playdeb)
I'm sure they are up for making a ubuntu .deb

---

