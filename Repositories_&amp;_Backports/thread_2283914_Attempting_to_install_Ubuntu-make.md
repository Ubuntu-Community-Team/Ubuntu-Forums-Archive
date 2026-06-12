---
title: "Attempting to install Ubuntu-make"
date: 2015-06-25
forum: Repositories &amp; Backports
---

### Post by jason58 on 2015-06-25
Greetings!

I'm in the process of trying to get Ubuntu-make going so I can add Android Studio. But, unfortunately, I'm stumbling along the way. I'm running 14.04.

After adding the PPA, when I try to do 'sudo apt-get install ubuntu-make'

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ubuntu-make : Depends: python3-bs4 but it is not installable
               Depends: python3-progressbar but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Huh.. Alright. I have Python 3.4.0 running. So I tried 'sudo apt-get install python3-bs4' and get:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package python3-bs4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'python3-bs4' has no installation candidate

```

The same thing happens for python3-progressbar, and I can't find any further information on this. Any direction would be appreciated!

Thanks!

---

