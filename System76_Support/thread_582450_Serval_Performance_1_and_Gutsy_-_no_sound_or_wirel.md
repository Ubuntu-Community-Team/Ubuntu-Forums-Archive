---
title: "Serval Performance 1 and Gutsy - no sound or wireless"
date: 2007-10-19
forum: System76 Support
---

### Post by danns on 2007-10-19
I just upgraded to gutsy from fiesty and I no longer have sound nor wireless.  I'm not sure what sound module to load.  As for the wireless, I suspect it takes the ipw3945 module but that is no where to be found on my system.

I did upgrade the system76 driver and even when so far as to remove it, delete the archived packages and re-install.  I had it both install the drivers and I did do a system restore.  Nothing has rectified the problems.

Everything else seems to work fine.

---

### Post by tedrampart on 2007-10-19
a friend of mine had a problem with sound on his daru2 after upgrading to gutsy and running the driver.  he did a fresh install and installed the driver, and it worked fine..

I think there might be something up with upgrading to gutsy vs. a clean install ..

---

### Post by danns on 2007-10-19
Ok, I figured out the problem.  The system was loading the 2.6.22-14-i386 kernel.  I switched to the 2.6.22-14-generic kernel and all was good.  I notice that none of the restricted drivers were in the /lib/modules/2.6.22-14-i386 directory.  I'm not sure why it defaulted to the -i386 as opposed to the generic kernel or if there is an easy way to install the required drivers into the i386 directory.   

There is a directory /lib/modules/2.6.22-14-generic/ubuntu holding all these files.  I'm not sure what installs this directory as looking at the packages in synaptic for the restricted-modules does not reference this directory.  Is this an ubuntu package or what is installed by the system76 driver?

---

### Post by steveneddy on 2007-10-22
I'm glad you got that figured out. I have the same model and I was going to offer you either config files or software, whatever it took, to get you back up and running.

BTW - have you seen the new Serval? Man, that thing is gonna smoke!

:popcorn:

---

