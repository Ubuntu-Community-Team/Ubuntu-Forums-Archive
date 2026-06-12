---
title: "virtualbox 3.2 on ubuntu 10.10 dependency"
date: 2010-12-13
forum: Virtualisation
---

### Post by josvanr on 2010-12-13
Trying to install virtualbox 3.2 on ubuntu 10.10. Followed
the instructions on the virtualbox site but...

I know it has been posted before but here the problem seems to be
the other way around:


sudo apt-get install virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.5 is to be installed
E: Broken packages




ie in previous posts a downgrade was necessary. What can I do? 
(aptitude gives the same error)


josvanr

---

### Post by tgm4883 on 2010-12-15
Whats the output of 

```
rmadison libqtcore4
```


Can you post your sources.list?

---

### Post by josvanr on 2011-01-17
problem disappeared after update..

---

