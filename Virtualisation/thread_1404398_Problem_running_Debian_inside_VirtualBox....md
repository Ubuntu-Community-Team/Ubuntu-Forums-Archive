---
title: "Problem running Debian inside VirtualBox..."
date: 2010-02-11
forum: Virtualisation
---

### Post by kamitsukai on 2010-02-11
I installed debian inside VirtualBox using the net install image and only installed the base package and nothing else however on boot I get the below error:

```
Loading, please wait...
[        66.572793] BUG: soft lockup - CPU#0 stuck for 61s! [modprobe :90]
```

so it's safe to assume it doesent like something... =]

I'm running VirtualBox-3.1 from the sun virtualbox website installed on CrunchBang  on my Dell Inspiron 1525

Thanks in advance!

---

### Post by kamitsukai on 2010-02-11
I have discovered that disabling everything (network, cdrom, floppy) in Virtualbox will allow Debian to boot

after re-enabling the network Debian no longer works which leads me to believe that I need some kind of network package to get it to work?

I don't know how VirtualBox works but I know for a fact my wifi card isn't supported out of the box in Debian

---

