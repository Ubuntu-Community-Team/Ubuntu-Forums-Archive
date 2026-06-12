---
title: "Python-apt-common updated"
date: 2013-10-23
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-10-23
While editing the [common problems wiki page,]("https://wiki.ubuntu.com/U%2B1/common-problems") I checked /usr/share/python-apt/templates/Ubuntu.info and found it had been updated and now points to the devel repositories. My sources list still points to the trusty repositories, could this be, because I've already got an entry pointing to trusty?

---

### Post by ventrical on 2013-10-24
I am assuming that it may only be temporary and that perhaps it may make a transition throughout the cycle.

---

### Post by grahammechanical on 2013-10-24
I mentioned this in another thread. On my saucy install with the devel repositories the OS has been updated to Trusty and an recent update has edited ubuntu.info to include references not only to trusty but also to devel. The repositories are still listed in the Other Software tab but they are now recorded as Ubuntu Development Series, Recommended Updates, Unsupported Updates, Important Security Updates and Independent. There is nothing ticked in Ubuntu Software tab. For the record I have not manually edited ubuntu.info. I have just gone with the flow.

This installation may be a curiosity because I jumped in before the devs were ready, but it is not broken. I have a standard saucy install that I am going to upgrade to trusty and see what happens to ubuntu.info and the software sources.

I think we have a development branch that will roll on into 14.10 development with little if not nothing for us to do.

Regards.

---

### Post by ventrical on 2013-10-24
+1  I have two installs that I converted to /devel/ as suggested in the thread you started about 3 or 4 weeks ago and they are fully updated but I did edit two of the Ubuntu.info files to the one previously suggested but they have been replaced by /devel/

  Certainly this release is a horse of a different colour :)

*note* Also I had to manually  tic off the repositories using Software and Updates tool.

Regards..

---

