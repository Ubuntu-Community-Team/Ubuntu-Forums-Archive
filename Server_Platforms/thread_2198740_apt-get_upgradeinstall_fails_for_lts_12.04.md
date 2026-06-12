---
title: "apt-get upgrade/install fails for lts 12.04"
date: 2014-01-10
forum: Server Platforms
---

### Post by wolvw on 2014-01-10
Hi,
on my server I can't apt-get upgrade anymore. After the recent apt-get update, I get the following message:

```
root@srv ~ # apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-server : Depends: linux-headers-3.2.0-57-generic but it is not installed
 linux-server : Depends: linux-image-server (= 3.2.0.57.68) but 3.2.0.58.69 is installed
E: Unmet dependencies. Try using -f.
```

apt-get -f install results in an error too:

```
root@srv ~ # apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-55-generic linux-headers-3.2.0-51 linux-headers-3.2.0-54
  linux-headers-3.2.0-55 linux-headers-3.2.0-55-generic
  linux-image-3.2.0-54-generic linux-headers-3.2.0-51-generic
  linux-headers-3.2.0-54-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-server linux-server
The following packages will be upgraded:
  linux-headers-server linux-server
2 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,104 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of linux-headers-server:
 linux-headers-server depends on linux-headers-3.2.0-57-generic; however:
  Package linux-headers-3.2.0-57-generic is not installed.
dpkg: error processing linux-headers-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.57.68); however:
  Version of linux-image-server on system is 3.2.0.58.69.
 linux-server depends on linux-headers-server (= 3.2.0.57.68); however:
  Package linux-headers-server is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no clue what to do in such situation and hope someone can help me :)

---

### Post by TheFu on 2014-01-10
Thanks for posting exactly what has happened.

Can you please post the output of both:
```
df -h
df -i
```

---

### Post by wolvw on 2014-01-10
Thanks for trying to help!

```
root@srv ~ # df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/md2                  109G   41G   63G  40% /
udev                      7.8G   12K  7.8G   1% /dev
tmpfs                     3.2G  372K  3.2G   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      7.8G     0  7.8G   0% /run/shm
/dev/md1                  496M  222M  249M  48% /boot
```
```
root@srv ~ # df -i
Filesystem                  Inodes   IUsed     IFree IUse% Mounted on
/dev/md2                   7168000  328710   6839290    5% /
udev                       2040299     507   2039792    1% /dev
tmpfs                      2042620     414   2042206    1% /run
none                       2042620       3   2042617    1% /run/lock
none                       2042620       1   2042619    1% /run/shm
/dev/md1                    131072     290    130782    1% /boot
```

Both look good to me.

---

### Post by TheFu on 2014-01-10
Thanks for fixing the formatting!!!!  I saw something this time that I missed before.

linux-headers-3.2.0-57-generic is missing.

Try
**sudo apt-get -f install linux-headers-3.2.0-57-generic**
then try the normal stuff again.

Also, if you've added any PPAs or other non-standard repos to this system, please remove them.
BTW, the df cmds were just a hunch. Lots of folks have a smallish /boot and run out of space there trying to install kernels. Not this time, but ... 
I am a little worried that RAID is used for / (really it worries me for /boot) ... I've always been afraid to do that. For a long time, it didn't work and there seem to be issues still based on forums posts I've seen.  

Always mention that RAID is used on the boot partition and whether any encryption or WUBI is used.

---

### Post by wolvw on 2014-01-10
```
root@srv ~ # apt-get -f install linux-headers-3.2.0-57-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.57.68) but 3.2.0.58.69 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
:(
No PPA is added, sources.list:
```
# Hetzner APT-Mirror

deb http://mirror.hetzner.de/ubuntu/packages precise main restricted universe multiverse
deb http://mirror.hetzner.de/ubuntu/packages precise-backports main restricted universe multiverse
deb http://mirror.hetzner.de/ubuntu/packages precise-updates main restricted universe multiverse
deb http://mirror.hetzner.de/ubuntu/security precise-security main restricted universe multiverse

```

Ubunutu mirrors of my server hoster.
And btw the raid is running happily for half a year now :) .

RAID is used on the boot partition and no encryption or WUBI is used. ;)

---

### Post by TheFu on 2014-01-10
Well, it isn't one the the easier issues to solve, it seems. Looks like a corrupt/broken package.  Found this:
[http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1) which might help.

Otherwise, I'd backup the system, backup the list of installed packages and reload from scratch.  Of course, there is probably an easier way, but your timeline may require action sooner than better answers can be posted here. ;( Sorry.

If you have a backup of the /var/apt from prior to the latest corruption, might try to restore that and go again.

---

### Post by David_Schuler on 2014-01-21
Hi,

had the same problem.
This solved it for me:
[http://askubuntu.com/questions/252704/i-cannot-install-any-package-linux-image-server-linux-server-dependencies-erro](http://askubuntu.com/questions/252704/i-cannot-install-any-package-linux-image-server-linux-server-dependencies-erro)

In my case the commands were:
```

wget launchpadlibrarian.net/158193365/linux-server_3.2.0.58.69_amd64.deb
dpkg -i linux-server_3.2.0.58.69_amd64.deb


```
Cheers
David

---

### Post by wolvw on 2014-01-21
Thanks David! That really helped a lot. I tried your approach but got another dependency issue with linux-headers-server_3.2.0.58.69. So I tried installing that package first like you described:
```
wget http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-server_3.2.0.58.69_amd64.deb
dpkg -i linux-headers-server_3.2.0.58.69_amd64.deb
```
 and that worked, and after that your solution also worked for me.
```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-server_3.2.0.58.69_amd64.deb
dpkg -i linux-server_3.2.0.58.69_amd64.deb
```
Now I'm happy I delayed the reinstallation of my Server :D

---

### Post by TheFu on 2014-01-21
I fear you've just delayed the root issue.  That is good, for now.

After the next kernel gets released, please see if there are any ill effects and report back here.  When it comes to kernel-connected packages, using the generic package *(-current or -generic or ) is usually the better answer.  At this point you can probably get the meta-packages installed that will make those future issues be handled cleanly, automatically.

```
Run **uname -r** to determine which kernel type is installed. Headers for your running kernel are needed.

    {something}-generic-pae = sudo aptitude install linux-headers-generic-pae
    {something}-generic = sudo aptitude install linux-headers-generic
    {something}-server = sudo aptitude install linux-headers-server

Only 1 of needs to be installed.
```

It appears you need **sudo aptitude install linux-headers-server**. Might need a --reinstall option to get the dependencies worked out. aptitude is smarter at dependency solutions than apt-get, so this is a good time to use that tool too.

Or you can wait until the issue shows up again.

---

### Post by wolvw on 2014-01-21
Hi TheFu, I don't wanna wait for the issue to reappear, so I followed your instructions and everything went alright I guess. uname -r showed 3.2.0-56-generic and I was curious if apt-get would get it right (instead of aptitude), so I issued the following command:
```
root@srv / # apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-55-generic linux-headers-3.2.0-51 linux-headers-3.2.0-54
  linux-headers-3.2.0-55 linux-headers-3.2.0-55-generic
  linux-image-3.2.0-54-generic linux-headers-3.2.0-51-generic
  linux-headers-3.2.0-54-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,356 B of archives.
After this operation, 32.8 kB of additional disk space will be used.
Get:1 http://mirror.hetzner.de/ubuntu/packages/ precise-updates/main linux-headers-generic amd64 3.2.0.58.69 [2,356 B]
Fetched 2,356 B in 0s (0 B/s)                      
Selecting previously unselected package linux-headers-generic.
(Reading database ... 195806 files and directories currently installed.)
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.58.69_amd64.deb) ...
Setting up linux-headers-generic (3.2.0.58.69) ...
```

---

### Post by TheFu on 2014-01-21
Aptitude is the recommended tool from Debian. Recommended over apt-get. It doesn't feel any different most of the time, but it has solved some strange dependency issues for me a few times.

Did you run **autoremove** as recommended in the output?  I would.

---

### Post by wolvw on 2014-01-21
Yep I did :D

---

