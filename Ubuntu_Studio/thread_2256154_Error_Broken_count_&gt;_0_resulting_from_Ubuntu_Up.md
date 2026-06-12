---
title: "Error: Broken count &gt; 0 resulting from Ubuntu Update"
date: 2014-12-10
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2014-12-10
Ubuntu Studio 14.04 was updating today and the following error occurred:  Error: Broken count > 0. There is red circle with white horizontal bar at top right of desktop. 

> The Package system is broken:

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

I have not added any third part repositories. Should I disable all those in the Software Updater > Settings >  "Other Software" like "Canonical Partners"? 

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


When I launch synaptic it says there are two broken packages and suggested identifying them by using "broken" in the filter. Here is a screen shot of what I see when the do so (attached).

Other info provided:

> The following packages have unmet dependencies:

bind9-host: Depends: libbind9-90 (= 1:9.9.5.dfsg-3ubuntu0.1) but it is not installed
            Depends: libdns100 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
            Depends: libisc95 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
            Depends: libisccfg90 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
            Depends: liblwres90 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
dnsutils: Depends: libbind9-90 (= 1:9.9.5.dfsg-3ubuntu0.1) but it is not installed
          Depends: libdns100 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
          Depends: libisc95 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
          Depends: libisccfg90 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed
          Depends: liblwres90 (= 1:9.9.5.dfsg-3ubuntu0.1) but 1:9.9.5.dfsg-3ubuntu0.1 is installed


I have done some web searching for the errors with no luck so far. Any help appreciated.

EDIT

I just tried running the command

> apt-get install -f 


And this was the  result:

> 
(Reading database ... 269818 files and directories currently installed.)
Preparing to unpack .../libbind9-90_1%3a9.9.5.dfsg-3ubuntu0.1_amd64.deb ...
Unpacking libbind9-90 (1:9.9.5.dfsg-3ubuntu0.1) ...
dpkg: error processing archive /var/cache/apt/archives/libbind9-90_1%3a9.9.5.dfsg-3ubuntu0.1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/doc/libbind9-90/copyright', which is also in package libdebconfclient0:amd64 0.187ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libbind9-90_1%3a9.9.5.dfsg-3ubuntu0.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by shaunthesheep on 2014-12-10
I eventually solved this (knock on wood) by launching Package Manager (which reported 2 broken packages), entering the word "broken" in the Filter field and looking down the list. At first it was not clear which were the two culprits. I eventually noticed that two packages were selected with a check and blue flag in the left column and they were the only packages that could be removed. So, I removed them.

The red icon disappeared from the notification area at top right.

---

