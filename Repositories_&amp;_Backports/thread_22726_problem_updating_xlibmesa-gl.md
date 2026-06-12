---
title: "problem updating xlibmesa-gl"
date: 2005-03-29
forum: Repositories &amp; Backports
---

### Post by UbuWu on 2005-03-29
The following package cannot be updated on my system:

E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-6_i386.deb:  poging tot overschrijven van `/usr/X11R6/lib/libGL.so.1.2', wat ook in pakket fglrx-6-8-0 zit

(in english: /var...deb: tried to rewrite /usr...1.2, which is also in package fglrx-6-8-0)

Should I do something about this? (maybe it has something to do with the ATI drivers I installed?)

xlibmesa-gl will keep showing up in the list with updates...

---

### Post by Dracontopes on 2005-03-29
There is another thread on this, look for it.

It comes down to this: remove the fglrx package, install xlib package with apt, rebuild modules of the fglrx package. All this must be done in a console.

---

### Post by UbuWu on 2005-03-29
Thanks for the quick reply  8) 

Should have searched for it. For others with the same problem, this is the longer version of what to do (found in another thread):

 1. Stop gdm. From the text based terminal do the following
2. sudo modprobe -r fglrx
3. sudo apt-get remove fglrx-6-8-0
4. sudo /bin/rm -R /lib/modules/fglrx
5. sudo apt-get install xlibmesa-gl (this was giving me problems when trying to update from within synatic). Now it runs fine and updates the system
6. locate the fglrx-6-8-0_8.10.19-2_i386.deb (this was created with alien using the RPM package from ATI)
7. sudo apt-get install <PATH>/fglrx-6-8-0_8.10.19-2_i386.deb. This will install necessary libraries and create the module source under /lib/modules/fglrx
8. change to /lib/modules/fglrx/build_mod
9. sudo sh make.sh. Change to /lib/modules/fglrx
10. sudo sh make_install.sh
11. modprobe fglrx
12. Restart gdm

---

### Post by UbuWu on 2005-03-30
hmm... another update to the package today... guess I will have to do the same again...

---

### Post by Stealth on 2005-03-31
wha? Thats crazy...reinstalling after every update? I've seen 3 already in the past...week I've had Hoary installed now, and I've had to continually downgrade xlibmesa-dev to match version nubmer of xlibmesa-gl. Why does this happen? Can't it just not overwrite the file? This is getting annoying :(

---

### Post by UbuWu on 2005-04-04
Same here...

---

