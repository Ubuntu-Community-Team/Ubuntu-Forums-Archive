---
title: "Inkscape 0.43!"
date: 2005-11-21
forum: Ubuntu Backports
---

### Post by sethmahoney on 2005-11-21
Inkscape 0.43 was released today (hint, hint!)!

[http://gnomedesktop.org/node/2478](http://gnomedesktop.org/node/2478)

---

### Post by jdong on 2005-11-21
jdong@shuttle:~$ ubp inkscape
  inkscape | 0.42.2+0.43pre2-1 |      unstable | source, i386
  inkscape | 0.42-1build1 |        breezy | source, i386
  inkscape | 0.42-1build1ubuntu0.1 | breezy-security | source, i386
  inkscape | 0.42.2+0.43pre2-1 |        dapper | source, i386


Not in Dapper yet.

---

### Post by fosk on 2005-11-21
[QUOTE=jdong]jdong@shuttle:~$ ubp inkscape
  inkscape | 0.42.2+0.43pre2-1 |      unstable | source, i386
  inkscape | 0.42-1build1 |        breezy | source, i386
  inkscape | 0.42-1build1ubuntu0.1 | breezy-security | source, i386
  inkscape | 0.42.2+0.43pre2-1 |        dapper | source, i386
[/QUOTE]

How do you do that???
Is it a bash script you have??? ubp???
Does it look in the repositories (sources.list)?
It looks pretty useful!!!

---

### Post by jdong on 2005-11-21
It's called "madison-lite", 

[http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000331.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000331.html)

follow thread :)

---

### Post by fosk on 2005-11-21
[QUOTE=jdong]It's called "madison-lite", 

[http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000331.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000331.html)

follow thread :)[/QUOTE]

Thank you so much!!!
I am going to read it now!!

---

### Post by jdong on 2005-11-21
In case you breeze past it, in the middle Shot (Piotr) posts an attached script that takes care of most of the work for you. You'll have to create a few folders the first time, but then after that it'll be a wonder to use. It's much faster than pulling up a packages.ubuntu.com.

---

### Post by kperkins on 2005-11-22
How to install Inkscape 0.43 on Breezy Badger
Step 1:
Open up synaptic or apt-get install:
libglibmm-2.4-dev
libgtkmm-2.4-dev 
libSigc++2.0-dev
Step 2:
Get the following packages from Debian testing:
libgc1c2_6.5-1_i386.deb
libgc-dev_6.5-1_i386.deb
 libgtkspell0_2.0.10-3_i386.deb
libgtkspell-dev_2.0.10-3_i386.deb
and install them.
 Download the Inkscape 0.43 source and compile and install it.
Or Alternate Step 2: 
Download this package [http://keithperkins.net/files/inkscape-.43+deps.tar.gz](http://keithperkins.net/files/inkscape-.43+deps.tar.gz)
extract it, and dpkg -i  all the files in the order above, and then do the same for the Inkscape_0.43-1_i386.deb
(Yes I made one)
Or you can, also download just the Inkscape .deb package [http://keithperkins.net/files/inkscape_0.43_1.tar.gz](http://keithperkins.net/files/inkscape_0.43_1.tar.gz)
I posted this in the Customization Forum last night but it hasn't been moderated yet (or their not going to let it in--I've not word on it, and don't know how longit's supposed to take).  I made a .deb for Inkscape .43 and tar/gzipped it up with the deps that aren't in Ubuntu repos, and uploaded to my site.  Also just the .deb if anyone just wants that.
Works fine on my computer--YMMV.
If anyone of the backports people want to use it for the backports go ahead.

---

### Post by Moofed on 2005-11-29
Thanks kperkins, the debs worked great for me!

---

### Post by gonçalo on 2005-11-30
I know this must be sacrilege or something, but I got 0.43 to work with an autopackage installation. I'm still waiting for inkscape to get to dapper so it will be backported though. I'm trying not have mixed debs here. [although I have no idea of the amount of trash autopackage generates]

---

### Post by kperkins on 2005-11-30
Just an addendum--I needed to install libxml-xql-perl, to get some of the plugins/effect to work (and some don't seem to be woring at all).

---

### Post by Jengu on 2005-12-19
Running alien on the static fedora rpm also seems to work fine.

---

