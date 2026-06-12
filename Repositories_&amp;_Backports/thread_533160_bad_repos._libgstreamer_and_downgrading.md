---
title: "bad repos. libgstreamer and downgrading"
date: 2007-08-23
forum: Repositories &amp; Backports
---

### Post by praveenmarkandu on 2007-08-23
hi
here is my problem. i installed pidgin 2.1.1 and the sound didnt work. so i asked on their irc channel and they say my gstreamer versions are all wrong possibly due to some repos i added. stupid me.
i want to install the libgstreamer0.10-dev but when i sudo apt-get install it this is what comes up:
```
cookiemonster@thebigcookie:~$ sudo apt-get install libgstreamer0.10-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgstreamer0.10-dev: Depends: libgstreamer0.10-0 (= 0.10.12-0ubuntu2) but 0.10.12.2-0ubuntu1 is to be installed
E: Broken packages

```
on the pidgin irc channel they told me to remove libgstreamer0.10-0 and told me downgrading is hard.
when i try to remove libgstreamer0.10 it tells me there are like 200 different things that depend on this. important things like gnome-panel and so on. i dont want to screw up my ubuntu and i know if i carry on i will. so can anyone guide me on how get the verion of libgstreamer that i want and do it safely? TIA

---

### Post by bapoumba on 2007-08-24
What is your sources.list?
```
cat /etc/apt/sources.list
```

---

