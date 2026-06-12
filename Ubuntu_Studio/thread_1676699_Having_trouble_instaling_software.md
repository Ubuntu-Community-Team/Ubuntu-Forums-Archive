---
title: "Having trouble instaling software"
date: 2011-01-27
forum: Ubuntu Studio
---

### Post by ingrown.potato on 2011-01-27
I just installed Ubuntu Studio on my desktop and I'm a little confused about how to download software. I am used to Ubuntu Karmic which has that software center. Is there a software center for Ubuntu Studio, or do I have to compile any program I want myself? 
Thanks for helping!

---

### Post by cchhrriiss121212 on 2011-01-27
There is no need to compile if you don't want to. Studio has synaptic package manager in the system>admin menu, which does the same job. You can also install software center if you prefer it.

---

### Post by ingrown.potato on 2011-01-27
I kind of want to learn how to compile just for the learning experience, how do I do so? 
Are they're any good guides? 

Also what is a sympactic package manager?

---

### Post by grahammechanical on 2011-01-27
Synaptic is the download manager that was in use before Ubuntu Software Centre was brought out. It has a more basic interface. You can search for programs, mark them for installation or de-installing. It works fine. Many users are used to it. You will find it at System>Administration>Synaptic Package Manager.

Regards

---

### Post by ingrown.potato on 2011-01-28
How would I go about compiling programs on my own?

---

### Post by cchhrriiss121212 on 2011-01-28
First you download the source code, usually this is in a tar.gz file which needs to be extracted. After extracting you will have a folder with a "README" or "INSTALL" text file, it is a good idea to check these for installation notes as all software will have different install methods.
The most common method to install will be this (in a terminal window):
cd /packageX
./configure
make
sudo make install

After that you are done. This approach is inefficient on Debian based systems, as all software should be handled through the package manager to allow easy removal or upgrading.

See this for more info:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

