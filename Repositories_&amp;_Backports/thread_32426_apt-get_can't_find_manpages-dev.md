---
title: "apt-get can't find manpages-dev"
date: 2005-05-07
forum: Repositories &amp; Backports
---

### Post by Guest1234 on 2005-05-07
Hi I have ubuntu 5.04 and want to install manpages-dev so I'll have man pages about c/c++ commands.
So I looked in synaptic and only found manpages(which was already installed) but not manpages-dev.
So I tried to do it manually by typing:
sudo apt-get install manpages-dev
But it told me that the package was missing.

So I went here: [http://packages.debian.org/testing/doc/manpages-dev](http://packages.debian.org/testing/doc/manpages-dev)
and downloaded the manpages-dev package, and then put it in my home directory.
I edited the sources.lst file and inserted the following line:
deb file:/home/myusername/ 

afterwards I typed:
sudo apt-get install manpages-dev

But it told me that the sources.lst file is not valid(or something like that).

What am I doing wrong, and isn't the manpages-dev package supposed to come with the cd-rom?

PS
I didn't manage to configure my internet connection in linux, so I can't retrieve packages from the internet(other than by downloading them from windows).

---

### Post by enquiry on 2005-05-07
The correct way to install a deb file is by typing:
sudo dpkg -i yourfile.deb

To avoid dependency problems you might also do it like this (if you have an internet connection, that is):
sudo dpkg -i yourfile.deb && apt-get -f install

---

### Post by Guest1234 on 2005-05-09
Thanks I installed the manpages-dev that I downloaded from the debian and I have man pages for C commands but I still don't have for C++ commands, from where can I download a package for C++ commands?

PS
I still don't have an internet connection in Linux.

---

### Post by Guest1234 on 2005-05-10
Does anybody know where can I download a package of C++(g++) man pages( I already have C(gcc) man pages)?

Because when I try to type: "man fstream" or even something basic like "man cout", I get something like: "manual entry does not exist".

Or at least the name of the package that I need?

---

### Post by Guest1234 on 2005-05-10
i've managed to configure my internet connection in ubuntu, so now I can download and install packages directly from ubuntu.
I've added in synaptic package manager the universe repository, and I tried looking in the Documentation sections for a package for g++ libary functions man pages but I couldn't find, any knows which package I should install?

---

