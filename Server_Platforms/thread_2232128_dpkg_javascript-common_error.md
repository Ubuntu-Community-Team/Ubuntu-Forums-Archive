---
title: "dpkg: javascript-common error"
date: 2014-06-30
forum: Server Platforms
---

### Post by ionbasa on 2014-06-30
First I am running Ubuntu server 14.04 64bit. 

As of late I cannot install or remove some packages. 

Here is an example of what happens:
```

root@HAL:/home/ionbasa# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libmemcached10 libmemcachedutil2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up javascript-common (11) ...
dpkg: error processing package javascript-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 javascript-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@HAL:/home/ionbasa# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libmemcached10 libmemcachedutil2
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 331 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 167039 files and directories currently installed.)
Removing libmemcachedutil2:amd64 (1.0.8-1ubuntu2) ...
Removing libmemcached10:amd64 (1.0.8-1ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Setting up javascript-common (11) ...
dpkg: error processing package javascript-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 javascript-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@HAL:/home/ionbasa#


```

Most of the time dkpg comes back stating that there was an error processing the package 'javascript-common'

So what is up with javascript-common causing this?

---

### Post by ionbasa on 2014-06-30
So I managed to solve my own problem, I am posting this for informative use incase anyone reads it later down the line:

As it turns out ```
apt-get remove javascript-common
``` results in the same error, the solution was to purge the package using:

```
apt-get --purge remove javascript-common
``` Of note was that for whatever reason when I tried to run ```
apt-get purge javascript-common
``` it did not work, even though the two commands should do the same thing? 

After that I was able to install my needed packages just fine!

---

