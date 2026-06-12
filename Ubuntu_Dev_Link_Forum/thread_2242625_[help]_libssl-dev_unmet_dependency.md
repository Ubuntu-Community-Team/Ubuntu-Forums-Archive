---
title: "[help] libssl-dev unmet dependency"
date: 2014-09-03
forum: Ubuntu Dev Link Forum
---

### Post by samuel19 on 2014-09-03
Hello,

I'm trying to install the package libssl-dev, but I get the following error:

**Results after running apt-get upgrade**

Reading package list... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.12) but 1.0.1-4ubuntu5.17 is installed
                Recommends: libssl-doc but it is not installed
E: Unmet dependencies. try using -f.

**Results after running apt-get -f install**

Reading package list... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
 libssl-dev
Recommended packages:
 libssl-doc
The following package will be upgraded:
 libssl-doev
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,574 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency probems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.12); however:
 version of libssl1.0.0 on system is  1.0.1-4ubuntu5.17. 
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport written because the error message indicates its a followup error from a previous failure.
 E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm at a loss on what to do next.

Any help getting this installed would be appreciated.

---

