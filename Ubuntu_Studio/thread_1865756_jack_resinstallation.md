---
title: "jack resinstallation"
date: 2011-10-20
forum: Ubuntu Studio
---

### Post by hagai_sela on 2011-10-20
Hi,
I tried compiling jack from source. I don't need the source distribution so I want to go back to the version supplied with my distro (ubuntu 11.04).
I uninstalled the source version and reinstalled the jack packages jackd2 and libjackd-jackd2-0. now when I run jackd I get this error:


/usr/bin/jackd
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
could not open driver directory /usr/local/lib64/jack: No such file or directory

could not find any drivers in driver directory!
Failed to create server object

How can I fix this?

Thanks,
Hagai.

---

### Post by sgx on 2011-10-20
I would suggest installing 10.04 for using jackd audio. It seems to be the most stable workable option for audio production. Make sure to have a separate /home partition, to make future installations able
to bypass your /home folder, and the user data and specific settings you chose, many of which will be ready to use again, saving lots of time.

jackd is pretty simple when installed from synaptic, but the devs have changed important items between version jackd 1 and version2, or between released linux versions configuration details, which has caused tons of problems. If complete removal, and reinstallation, both done by synaptic, does not work,
it may be faster to start a better installation for the long run.

12 gig for root partition, and the rest for /home partition is pretty good.
This allows room for storing samples and drumkits, and a .wine setup in case you need them, and a permissions issue cones up.
Cheers

---

### Post by hagai_sela on 2011-10-21
Thanks.
I have too much important stuff on my machine, downgrading to 10.04 is not an option.

---

### Post by sgx on 2011-10-21
> **hagai_sela said:**
> Thanks.
I have too much important stuff on my machine, downgrading to 10.04 is not an option.

I had an issue with a newer qjackctl, that went away when I replaced it with an older version 3.6xxx. After uninstalling libjack, jackd,
and qjackctl, check for .jackdrc textfile in the user home folder, and rename it, check in
/usr/lib and /usr/bin, and removed anything missed by synaptic.

Then do a full V1 reinstall, and if an older qjackctl is not in synaptic,
there is one here:

[http://packages.debian.org/stable/sound/](http://packages.debian.org/stable/sound/)

sudo dpkg -i qjackctlxxx.deb

Remember, jackd2 is different from jackd1, it is not an upgrade! Many good distros use v1 because of problems with V2. A clean start with V1, and not the newest qjackctl might be successful.

Many distros can install on usbstick, and liveCDs, so testing alternatives
can be done while preserving your current system. Macpup 5.28
is excellent, a 170 meg download, so it fits on old small sticks
you may have gathering dust.

All important things should have multiple backups, one stored at a separate location, against fire, flood and theft. Are you prepared?
Cheers

---

