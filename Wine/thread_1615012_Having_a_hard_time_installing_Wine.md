---
title: "Having a hard time installing Wine"
date: 2010-11-06
forum: Wine
---

### Post by xpwnerlol on 2010-11-06
Hello all, 
I am recently installed Ubuntu 9.04, so I am completely a noob at this still. I tried installing wine and well I just can't ever seem to get it installed. Everytime I type it into Terminal it gives me this 

xpwnerlol@xpwnerlol-desktop:~$ wine
The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: wine: command not found
xpwnerlol@xpwnerlol-desktop:~$ sudo apt-get install wine
[sudo] password for xpwnerlol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (>= 6.22-0ubuntu1~9.04.1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.22-0ubuntu1~9.04.1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Then I type in apt-get -f install 

xpwnerlol@xpwnerlol-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

From what someone told me I am supposed to type in Sudo then I get this


usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

I am completely lost, can anyone help me?

---

### Post by dino99 on 2010-11-07
open synaptic: system admin synaptic
and search "wine"

to have the latest wine, add this ppa to : synaptic repo tab
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then update and select wine to install it, that it

---

### Post by Elfy on 2010-11-07
whoops 

if you used Sudo it would fail - lower case sudo 


then try installing wine after fixing the broken packages

---

### Post by _outlawed_ on 2010-11-07
Via terminal it would be:

Stable:
```
sudo apt-get install wine1.2
```

or

Development:
```
sudo apt-get install wine1.3
```

---

