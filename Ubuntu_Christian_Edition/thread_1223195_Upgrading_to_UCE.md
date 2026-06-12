---
title: "Upgrading to UCE"
date: 2009-07-25
forum: Ubuntu Christian Edition
---

### Post by s1mp13m4n on 2009-07-25
I am using Ubuntu 9.04 already.  How do I install UCE from Ubuntu 9.04?  Thanks for the help.

---

### Post by david_kt on 2009-07-26
> **s1mp13m4n said:**
> I am using Ubuntu 9.04 already.  How do I install UCE from Ubuntu 9.04?  Thanks for the help.


For 32 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

For 64 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

DK

---

