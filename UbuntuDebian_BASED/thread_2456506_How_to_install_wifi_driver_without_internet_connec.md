---
title: "How to install wifi driver without internet connectivity??"
date: 2021-01-12
forum: Ubuntu/Debian BASED
---

### Post by Wayne Twine on 2021-01-12
Hi

I am caught between a rock and a hard place with a fresh installation of Elementary OS (which is based on Ubuntu) on my daughter's Asus Vivo. The wifi does not work because the Realtek rtl88221ce driver needs to be installed.  I obviously can't just download from the repository because I don't have internet connectivity (don't have access to ether-net connection as alternative to wifi).  I have dried downloading code, dkms and deb for the driver on another machine and copied across to the Asus to install there but these need packages such as "make", "build-essential" or "gdebi" in order to install, and these are not installed by default in a fresh installation of Elementary.  I can't install these first in order to install the driver because ... I don't have internet connection .... because wifi isn't working .... because the driver is not installed ... aaaragh! 

Any suggestions before I admit defeat and head back to Windows with my tail between my legs??

Thanks

---

### Post by jeremy31 on 2021-01-12
Moved to Ubuntu/Debian based

---

### Post by Frogs Hair on 2021-01-12
Take a look at the links , you may need a wired connection to complete the job. The linked driver and solution are for Ubuntu.   

[https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)

[https://ubuntuforums.org/showthread.php?t=2398917](https://ubuntuforums.org/showthread.php?t=2398917)

---

