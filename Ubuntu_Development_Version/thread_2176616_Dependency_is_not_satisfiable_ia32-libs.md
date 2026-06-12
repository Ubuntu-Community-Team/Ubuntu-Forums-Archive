---
title: "Dependency is not satisfiable: ia32-libs"
date: 2013-09-25
forum: Ubuntu Development Version
---

### Post by fantab on 2013-09-25
I am trying to install a 32bit proprietory software.deb and Software Center reports:
> Dependency is not satisfiable: ia32-libs

I have skype and few other 32bit applications installed, so I am not sure what is going on. I have multiarch enabled in my repos. 
I had read that 'ia32-libs' are being phased out. could this be the case? What is the possible workaround, if true?

Regards....

---

### Post by mc4man on 2013-09-25
ia32-libs is past "being phased out", it's gone.
It was just a meta-package so your software provider needs to adjust their debian/control file to use the actual package deps, & remove ia32-libs from it.

(if inclined you can unpack your .deb, edit out the ia32-libs dep, rebuild the .deb & try to install, noting that you'll need to manually insure that all needed deps are present.

---

### Post by fantab on 2013-09-25
Thanks for the information.

I tried the i386.deb of the same application and it Installed fine. The problem was with amd64 package. 

Regards...

---

### Post by chrisi.egg on 2014-07-23
I have the same problem.

> if inclined you can unpack your .deb, edit out the ia32-libs dep,  rebuild the .deb & try to install, noting that you'll need to  manually insure that all needed deps are present.

I loaded the ia-32-avast-libs.deb and got the error. 
What should I exactly edit out how can I do the rebuild?

---

### Post by rrnbtter on 2014-07-23
Greetings,
I was having the same problem with Teamviewer. My solution that worked was to do a complete removal of the already installed software using Syanptic and then right click on the deb file and install with Software Center. It almost seems to me that Synaptic does a better job at removal and Software Center does a better job of resolving dependencies. Be sure to choose "completely remove" in Synaptic. Good Luck.

---

### Post by oldos2er on 2014-07-23
Hi chrisi.egg, if you're using 14.10 please start a new thread; if using 14.04 or earlier please post in the regular support areas of the forum.

---

