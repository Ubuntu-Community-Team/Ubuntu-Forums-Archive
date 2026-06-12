---
title: "Wireless Disabled after update on Pan7"
date: 2010-03-25
forum: System76 Support
---

### Post by fpe101 on 2010-03-25
Hello,
I own a pangolin7 running ubuntu 9.1 and my wireless is disabled after running a system update. Fn-F11 does not enable it but my other function keys are working fine. I can connect wirelessly to my network from other computers. Any help would be appreciated.

---

### Post by thomasaaron on 2010-03-25
Please try running...

sudo apt-get install linux-backports-modules-karmic

...and then rebooting.

---

### Post by fpe101 on 2010-03-25
When I run that command I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-karmic: Depends: linux-backports-modules-karmic-generic (= 2.6.31.21.34) but 2.6.31.20.33 is to be installed
E: Broken packages

---

### Post by thomasaaron on 2010-03-26
OK, Try running...

sudo apt-get install -f
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
sudo apt-get install linux-backports-modules-karmic

---

