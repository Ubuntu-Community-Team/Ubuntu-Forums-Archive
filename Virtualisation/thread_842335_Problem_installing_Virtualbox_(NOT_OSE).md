---
title: "Problem installing Virtualbox (NOT OSE)"
date: 2008-06-27
forum: Virtualisation
---

### Post by Deicist on 2008-06-27
I originally had Virtualbox OSE installed form the repositories, then decided I wanted to install the 'full' version...so I downloaded the correct package from virtualbox.org, uninstalled OSE and ran the package.  I get this error:

```

dpkg: error processing /home/paul/Desktop/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb (--install):

trying to overwrite '/lib/modules/2.6.24-16-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-16-generic

dpkg-deb: subprocess paste killed by signal (Broken pipe)
 
```

Can anyone help me with this?

---

### Post by Caalador on 2008-06-27
Have a look at whether you have un-installed the old virtualbox-ose-guest modules.

I'm having headaches moving from OSE to full though. Primary one being that my XP vdi image which was made in OSE, cannot be run in 'full' version.

---

### Post by Deicist on 2008-06-27
i tried to, but 'apt-get remove' doesn't find the package, and synaptic doesn't show it in my list of installed packages.  not sure what i've done wrong there.

---

### Post by Caalador on 2008-06-27
Try 

```
aptitude remove virtualbox-ose-modules-2.6.24-16-generic
```

That's the specific module causing issues. Sorry dude, no other ideas! Although I had the same issue, I just had to remove everything with "virtualbox-ose" in it.

---

