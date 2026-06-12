---
title: "Inkscape crashes when trying to edit one particular file"
date: 2009-06-02
forum: Ubuntu Studio
---

### Post by fredbird67 on 2009-06-02
I'm trying to make my own black-and-white/grayscale icon theme.  Everything's been going fine up until I ran into this one file that keeps causing Inkscape to crash whenever I use the "Effect --> Color --> Grayscale" function on it.  I get that message that Inkscape has encountered an internal error and will close (don't remember the exact wording).

From what I saw in another thread, I went into /var/log/syslog, and the most recent thing I have in there that involves Inkscape is as follows:  

inkscape[5057]: segfault at 0 ip 080d3495 sp bfab5f60 error 4 in inkscape

Where do I go from here?  I'm running Ubuntu 9.04.

Thanx in advance,
Fred in St. Louis, MO USA

---

### Post by fredbird67 on 2009-06-03
Update:  I tried something else, to no avail, either.  I thought I'd see if I could copy that file to my flash drive and then whip out a live PCLinuxOS CD, copy its contents to RAM, install Inkscape on it, and see if I could do it that way.  No dice there, either, because when attempting to copy, I got this message:  "Error making symbolic link: Operation not permitted".

Just what kind of nonsense is going on here?  I've checked the file permissions, and they're set to read & write across the board, and I'm really at a loss as to what's going on here...

---

### Post by fredbird67 on 2009-06-03
OK, consider this one SOLVED!

The file in question was hardlinked to two other files in the same directory.  I copied one of the other ones to my flash drive, exited out of Ubuntu and into a live CD of PCLinuxOS, copied the CD's contents into RAM, installed Inkscape, and I was able to do the edit! :-)

I saved it, which goes without saying, exited out of PCLOS and back into Ubuntu...and was able to copy it back into that folder, and Ubuntu never once complained! :-)

Now on with the rest of the icon set, all 10,357 or so files in it! LOL

---

