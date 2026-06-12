---
title: "Request: gaim-otr"
date: 2005-06-09
forum: Ubuntu Backports
---

### Post by NemoTheLobster on 2005-06-09
I use this at work on my Gentoo box, would be great to have it at home too.

Thanks guys for all the great work!

---

### Post by Mez on 2005-06-10
It's not been built for debian yet - maybe you should ask MOTU?

[edi]

Sorery... my mistake - it is in breezy, but to backport to hoary takes too much hassle (build a package from scrathc) which isnt backporting

---

### Post by jcohen on 2005-06-29
I would also like to see gaim-otr in hoary. I've been using gaim-otr with debian testing for a while and it's a great product. It's currently included in debian sarge, etch and sid as well as ubuntu breezy. why not backport it to hoary?

---

### Post by jamo on 2005-06-30
I converted the rpms for Fedora 4 on the official site with alien. They work very well, there is not even the need to run ldconfig.

---

### Post by jcohen on 2005-07-07
gaim-otr can also be easily built from breezy sources. Here are instructions:

1) First, you'll have to edit your sources to include breezy source packages:

gedit /etc/apt/sources.list and add "deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse" without the quotations.

2) Run apt-get update to refresh your list of packages

sudo apt-get update

3) Get build dependencies for libotr and gaim-otr

sudo apt-get build-dep libotr
sudo apt-get build-dep gaim-otr

4) Build libotr

sudo apt-get source -b libotr

5) Install libotr, libotr-bin and libotr-dev

sudo dpkg -i libotr1_2.0.2-1_i386.deb libotr1-bin_2.0.2-1_i386.deb libotr1-dev_2.0.2-1_i386.deb

6) Build gaim-otr

sudo apt-get source -b gaim-otr

7) Install gaim-otr

dpkg -i gaim-otr_2.0.2-1_i386.deb

If the install of libotr of gaim-otr fails and lists unmet dependencies just install them  with sudo apt-get install package. Unfortunately, you can't automatically satisfy dependencies with a locally created package. dpkg isn't made to do that.

8) You may want to comment out the breezy source line in case you want to add build-dependencies for other packages which you want to install from source. Because of changes in packages since Hoary was released many times build-dependencies can not be satisfied using Breezy sources. 

Simply add a # in front of the deb-src line you just added like so. You'll need to sudo gedit /etc/apt/sources.list and change the file like so:


#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse

---

