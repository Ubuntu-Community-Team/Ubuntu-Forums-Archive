---
title: "Din synthesiser: anyone got it working with 10.10?"
date: 2011-02-06
forum: Ubuntu Studio
---

### Post by keithpeter on 2011-02-06
Hello All

[http://www.dinisnoise.org/](http://www.dinisnoise.org/)

This looks (and sounds according to the samples on the site) really interesting.

Has anyone managed to get din installed with Ubuntu 10.10 and with the ubuntu studio audio and audio plugins packages with the current jackd version? The gory details are below...

I downloaded the .deb but there are dependency problems. The dpkg dialogue went like this...

```
keith@t60:~/Downloads$ sudo dpkg -i din-1.4.2.i386.deb
[sudo] password for keith: 
Selecting previously deselected package din.
(Reading database ... 223019 files and directories currently installed.)
Unpacking din (from din-1.4.2.i386.deb) ...
dpkg: dependency problems prevent configuration of din:
 din depends on libircclient1; however:
  Package libircclient1 is not installed.
 din depends on libjack0 (>= 0.118+svn3796); however:
  Package libjack0 is not installed.
dpkg: error processing din (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 din

```

Attempting to install libjack0 and libircclient1 results in

```
keith@t60:~/Downloads$ sudo apt-get install libjack0 libircclient1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libjack-jackd2-0 : Conflicts: libjack-0.116
                    Conflicts: libjack0 but 1:0.118+svn3796-7ubuntu1 is to be installed
 libjack0 : Conflicts: libjack-0.116
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Running apt-get -f install results in

```
keith@t60:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  jackd1 jackd1-firewire libircclient1 libjack0
Suggested packages:
  libjackasyn0
The following packages will be REMOVED
  jackd2 jackd2-firewire libjack-jackd2-0
The following NEW packages will be installed
  jackd1 jackd1-firewire libircclient1 libjack0
0 upgraded, 4 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 316kB of archives.
After this operation, 901kB disk space will beworking freed.
Do you want to continue [Y/n]? 

```

I don't particularly want to downgrade the jack version unless ardour and puredata work ok with the downgraded version.

I've asked on the din irc chat channel and the suggestion was to compile from source, but they were not Ubuntu users.

Thanks...

---

### Post by babarosa on 2011-02-06
Hi,

you can try this version: [https://launchpad.net/~puredyne-team/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~puredyne-team/+archive/ppa?field.series_filter=maverick)

---

### Post by Pablo_F on 2011-02-06
Hi, 

jackd2 is not more up to date than jackd1. It is another implementation of jack, but they are both under development. It is not a downgraded version, even if it may seem so.  

Furthermore, jackd1 works better with ardour, particularly the jack transport in ardour with jackd2 is buggy. See [http://tracker.ardour.org/view.php?id=2856](http://tracker.ardour.org/view.php?id=2856)

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2011-02-06
I have din compiled from source with jackd2, it works fine but uses up 100% of one of my cpu cores (!). According to the guys on IRC it is normal, so beware unless you have a multicore CPU.

---

### Post by keithpeter on 2011-02-06
> **babarosa said:**
> Hi,

you can try this version: [https://launchpad.net/~puredyne-team/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~puredyne-team/+archive/ppa?field.series_filter=maverick)

Thanks, I will. I found out about din from the puredyne mail list just now.

---

### Post by keithpeter on 2011-02-06
> **cchhrriiss121212 said:**
> I have din compiled from source with jackd2, it works fine but uses up 100% of one of my cpu cores (!). According to the guys on IRC it is normal, so beware unless you have a multicore CPU.

Yup, its running 'clicky' on this old laptop, so I guessed it was a heavy program.

---

### Post by keithpeter on 2011-02-06
> **Pablo_F said:**
> Hi, 

jackd2 is not more up to date than jackd1. It is another implementation of jack, but they are both under development. It is not a downgraded version, even if it may seem so.  

Furthermore, jackd1 works better with ardour, particularly the jack transport in ardour with jackd2 is buggy. See [http://tracker.ardour.org/view.php?id=2856](http://tracker.ardour.org/view.php?id=2856)

Cheers, Pablo

Thanks for clarification, I had not realised this...

---

### Post by AutoStatic on 2011-02-07
Most recent version of din is also in the KXStudio-Team PPA: [https://launchpad.net/~kxstudio-team/+archive/ppa](https://launchpad.net/~kxstudio-team/+archive/ppa)

Best,

Jeremy

---

