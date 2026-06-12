---
title: "firestarter install error"
date: 2006-10-04
forum: Server Platforms
---

### Post by frogotronic on 2006-10-04
Here's my error on install:

```
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Any suggestions?

---

### Post by moore.bryan on 2006-10-04
*which kernel are you running?*

---

### Post by frogotronic on 2006-10-05
> **moore.bryan said:**
> *which kernel are you running?*

Sorry,

2.6.15-27-386

---

### Post by moore.bryan on 2006-10-05
*no worries... when you compiled the kernel, did you make sure iptables was permitted.  i know 2.6.17 and 2.6.18 have issues with that; i'm just not sure about 2.6.15...*

---

### Post by frogotronic on 2006-10-05
> **moore.bryan said:**
> *no worries... when you compiled the kernel, did you make sure iptables was permitted.  i know 2.6.17 and 2.6.18 have issues with that; i'm just not sure about 2.6.15...*

Hi,
I didn't compile the kernel.  Or, rather if I did I am unaware that I did.  I'm pretty new to Ubuntu (GNU/Linux).

However, typing the following gives

```
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I take this to mean that iptables are permitted?

- CH

---

### Post by moore.bryan on 2006-10-05
*yep, you're allowed...  so, you are trying to install firestarter? don't you already have it?*

---

### Post by frogotronic on 2006-10-05
> **moore.bryan said:**
> *yep, you're allowed...  so, you are trying to install firestarter? don't you already have it?*

Confession time...

I had firestarter working and all was well.  Then I got the bright idea to try to install SoftwareSuspend2 (I am using a DELL Inspiron 8100 laptop) and ss2 said that it needed a dependency of libc6 2.4-1ubuntu10; which was an upgrade from the dapper release of 2.36 to the edgy version.  So I did the download and upgrade for the libc6 and that's when the trouble started.

Many things broke, and would no longer respond.  I had to eventually uninstall Firestarter and then I downgraded my libc6 back to the dapper drake version.

Okay...so I think everything is okay now, BUT when I try to reinstall firestarter, I get the install error.

My guess is that there is some kind of residual config file lying around that is buggering up the install OR, some packages were removed during the upgrade to libc6 2.4 that I should have, but didn't write down and now I "reaping" the benefits.

](*,)

---

### Post by moore.bryan on 2006-10-05
[I]not a problem, but you should have put all that out in the beginning!  ;-)
try this and post what the response is...
```
sudo aptitude reinstall -fy firestarter
```
[/I]

---

### Post by frogotronic on 2006-10-06
> **moore.bryan said:**
> [I]not a problem, but you should have put all that out in the beginning!  ;-)
try this and post what the response is...
```
sudo aptitude reinstall -fy firestarter
```
[/I]

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  firestarter
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 200
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 200
Errors were encountered while processing:
 firestarter

---

### Post by moore.bryan on 2006-10-06
*well, at least that tells us a little more... it looks like there's a problem with something being loaded.  can you completely uninstall firestarter (i.e. sudo aptitude remove -fy firestarter)?  you could also use synaptic to completely remove... that may give some more error details.  if my hunch is correct, you won't be able to uninstall... *

---

### Post by frogotronic on 2006-10-06
> **moore.bryan said:**
> *well, at least that tells us a little more... it looks like there's a problem with something being loaded.  can you completely uninstall firestarter (i.e. sudo aptitude remove -fy firestarter)?  you could also use synaptic to completely remove... that may give some more error details.  if my hunch is correct, you won't be able to uninstall... *

Nope, unistall is fine

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  firestarter
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1946kB will be freed.
Writing extended state information... Done
(Reading database ... 162004 files and directories currently installed.)
Removing firestarter ...
 * Stopping the Firestarter firewall... 

```


But you are correct a package failed to install when I try to install firestarter.

---

### Post by moore.bryan on 2006-10-07
*after you completely uninstall, try to reinstall... post errors...*

---

### Post by frogotronic on 2006-10-07
> **moore.bryan said:**
> *after you completely uninstall, try to reinstall... post errors...*

PROBLEM SOLVED!!!

I checked all the firestarter recommended dependencies and installed some of the developer files. Seems to have solved the problem.  Thanks for all your help.

For the record:

```
# sudo aptitude install -fy firestarter
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  firestarter
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/391kB of archives. After unpacking 1946kB will be used.
Writing extended state information... Done
Selecting previously deselected package firestarter.
(Reading database ... 164684 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...

```

---

### Post by moore.bryan on 2006-10-07
*just glad it finally worked for you... enjoy.*

---

