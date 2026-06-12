---
title: "Unmet linux image and server dependencies, please help"
date: 2015-10-09
forum: Server Platforms
---

### Post by curmudge1 on 2015-10-09
<sigh> So this is an  unfortunate effect of a small /boot partition getting full & messing up the linux image & server auto-updates (too bad that doesn't check for space first...)  12.04 LTS  SERVER

I've had no luck with any apt commands, and I did make space with dpkg -purge getting rid of an old version (80, iirc), but apt-get still doesn't fix things... apt-get -f install, apt-get install, etc.  no joy.

Any help would be appreciated.  some things I tried, below, with the responses.

```
dstrom@alphaweb0:/boot$ sudo apt-get install linux-generic linux-image-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.91.105) but it is not going to be installed
 linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
                Depends: linux-headers-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dstrom@alphaweb0:/boot$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-83-generic linux-headers-3.2.0-74 linux-headers-3.2.0-80
  linux-headers-3.2.0-76 linux-headers-3.2.0-82 linux-headers-3.2.0-77 linux-headers-3.2.0-83
  linux-headers-3.2.0-84 linux-headers-3.2.0-79 linux-image-3.2.0-84-generic
  linux-headers-3.2.0-76-generic linux-headers-3.2.0-84-generic linux-headers-3.2.0-79-generic
  linux-image-3.2.0-82-generic linux-headers-3.2.0-74-generic linux-headers-3.2.0-82-generic
  linux-headers-3.2.0-77-generic linux-image-3.2.0-83-generic linux-headers-3.2.0-80-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
1 not fully installed or removed.
Need to get 1,730 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-server amd64 3.2.0.91.105 [1,730 B]
Fetched 1,730 B in 0s (56.0 kB/s)
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.85.99); however:
  Version of linux-image-server on system is 3.2.0.91.105.
 linux-server depends on linux-headers-server (= 3.2.0.85.99); however:
  Version of linux-headers-server on system is 3.2.0.91.105.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
dstrom@alphaweb0:/boot$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       228M  186M   31M  86% /boot
dstrom@alphaweb0:/boot$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is installed
                Depends: linux-headers-server (= 3.2.0.85.99) but 3.2.0.91.105 is installed
E: Unmet dependencies. Try using -f.
```
 
and this, from another search

```
dstrom@alphaweb0:~$ sudo apt-get purge linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
                Depends: linux-headers-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dstrom@alphaweb0:~$ sudo apt-get install --reinstall linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.91.105) but 3.2.0.85.99 is to be installed
                 Depends: linux-headers-generic (= 3.2.0.91.105) but it is not going to be installed
 linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
                Depends: linux-headers-server (= 3.2.0.85.99) but 3.2.0.91.105 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by darkod on 2015-10-09
You still have little space on /boot. Post the output of:
```
uname -r
ls -lh /boot
```

---

### Post by curmudge1 on 2015-10-09
Re space, I figured I would do some autoremoves after fixing the image/server problem.  Here's the info 

```
dstrom@alphaweb0:~$ uname -r
3.2.0-91-generic
dstrom@alphaweb0:~$ ls -lh /boot
total 182M
-rw-r--r-- 1 root root 778K Apr 27 17:58 abi-3.2.0-82-generic
-rw-r--r-- 1 root root 778K Apr 29 12:01 abi-3.2.0-83-generic
-rw-r--r-- 1 root root 778K May  5 15:19 abi-3.2.0-84-generic
-rw-r--r-- 1 root root 778K May 26 12:52 abi-3.2.0-85-generic
-rw-r--r-- 1 root root 778K Jun 14 14:38 abi-3.2.0-86-generic
-rw-r--r-- 1 root root 778K Aug 14 18:49 abi-3.2.0-90-generic
-rw-r--r-- 1 root root 779K Sep  9 07:43 abi-3.2.0-91-generic
-rw-r--r-- 1 root root 138K Apr 27 17:58 config-3.2.0-82-generic
-rw-r--r-- 1 root root 138K Apr 29 12:01 config-3.2.0-83-generic
-rw-r--r-- 1 root root 138K May  5 15:19 config-3.2.0-84-generic
-rw-r--r-- 1 root root 138K May 26 12:52 config-3.2.0-85-generic
-rw-r--r-- 1 root root 138K Jun 14 14:38 config-3.2.0-86-generic
-rw-r--r-- 1 root root 138K Aug 14 18:49 config-3.2.0-90-generic
-rw-r--r-- 1 root root 138K Sep  9 07:43 config-3.2.0-91-generic
drwxr-xr-x 2 root root 3.0K Oct  9 09:11 grub
-rw-r--r-- 1 root root  18M May  1 10:39 initrd.img-3.2.0-82-generic
-rw-r--r-- 1 root root  18M May  5 06:44 initrd.img-3.2.0-83-generic
-rw-r--r-- 1 root root  18M May 20 06:55 initrd.img-3.2.0-84-generic
-rw-r--r-- 1 root root  18M Sep 10 16:26 initrd.img-3.2.0-85-generic
-rw-r--r-- 1 root root  18M Sep 10 16:29 initrd.img-3.2.0-86-generic
-rw-r--r-- 1 root root  18M Sep 10 16:30 initrd.img-3.2.0-90-generic
-rw-r--r-- 1 root root  18M Oct  8 11:35 initrd.img-3.2.0-91-generic
drwxr-xr-x 2 root root  12K Mar 16  2010 lost+found
-rw-r--r-- 1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root 2.8M Apr 27 17:58 System.map-3.2.0-82-generic
-rw------- 1 root root 2.8M Apr 29 12:01 System.map-3.2.0-83-generic
-rw------- 1 root root 2.8M May  5 15:19 System.map-3.2.0-84-generic
-rw------- 1 root root 2.8M May 26 12:52 System.map-3.2.0-85-generic
-rw------- 1 root root 2.8M Jun 14 14:38 System.map-3.2.0-86-generic
-rw------- 1 root root 2.8M Aug 14 18:49 System.map-3.2.0-90-generic
-rw------- 1 root root 2.8M Sep  9 07:43 System.map-3.2.0-91-generic
-rw------- 1 root root 4.8M Apr 27 17:58 vmlinuz-3.2.0-82-generic
-rw------- 1 root root 4.8M Apr 29 12:01 vmlinuz-3.2.0-83-generic
-rw------- 1 root root 4.8M May  5 15:19 vmlinuz-3.2.0-84-generic
-rw------- 1 root root 4.8M May 26 12:52 vmlinuz-3.2.0-85-generic
-rw------- 1 root root 4.8M Jun 14 14:38 vmlinuz-3.2.0-86-generic
-rw------- 1 root root 4.8M Aug 14 18:49 vmlinuz-3.2.0-90-generic
-rw------- 1 root root 4.8M Sep  9 07:43 vmlinuz-3.2.0-91-generic
```

---

### Post by ian-weisser on 2015-10-09
Looks like you can use dpkg to remove the -82, -83, -84, -85, -86, and (optionally) -90 kernels...since you seem to be running -91 successfully. That will free up much space.

Most of those apt errors seem to me like the package database is simply out of date (*linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is installed*). Try a simple apt-get update to refresh the database with current information from your sources.

---

### Post by darkod on 2015-10-09
Don't worry, this is easily fixable if the only issue is the space.

You do need to get the apt-get -f install working first, but you need more free space on /boot to do that. I actually had couple of identical cases few weeks back.

But because apt-get doesn't work you can use it to clean up packages / free space. I usually do that manually. As already mentioned the uname result shows that you are running -91 kernel, so that one you need to keep. You can delete the -82 to -86 kernel files from /boot. As you can see by the file sizes in ls -lh, focus on initrd.img (18MB) and vmlinuz (4.8MB). The command would be like:
```
sudo -i
cd /boot
rm initrd.img-3.2.0-82-generic
rm vmlinuz-3.2.0-82-generic
```

Of course, be very careful with the rm command, make sure you are deleting the correct file. Do that for the other kernels. That should free up enough space for apt-get -f install to run. Once apt-get is running you can do some more clean up. Try that...

---

### Post by curmudge1 on 2015-10-12
thanks, but apt-get install -f has not been working... but I did try it again:

$ sudo dpkg --purge linux-image-3.2.0-85-generic
dpkg: dependency problems prevent removal of linux-image-3.2.0-85-generic:
 linux-image-generic depends on linux-image-3.2.0-85-generic.
dpkg: error processing linux-image-3.2.0-85-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.2.0-85-generic
dstrom@alphaweb0:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       228M  108M  109M  50% /boot
dstrom@alphaweb0:~$ sudo apt-get install  -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-83-generic linux-headers-3.2.0-74 linux-headers-3.2.0-80 linux-headers-3.2.0-76 linux-headers-3.2.0-82
  linux-headers-3.2.0-77 linux-headers-3.2.0-83 linux-headers-3.2.0-84 linux-headers-3.2.0-79 linux-headers-3.2.0-76-generic
  linux-headers-3.2.0-84-generic linux-headers-3.2.0-79-generic linux-headers-3.2.0-74-generic linux-headers-3.2.0-82-generic
  linux-headers-3.2.0-77-generic linux-headers-3.2.0-80-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,730 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.85.99); however:
  Version of linux-image-server on system is 3.2.0.91.105.
 linux-server depends on linux-headers-server (= 3.2.0.85.99); however:
  Version of linux-headers-server on system is 3.2.0.91.105.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
dstrom@alphaweb0:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.85.99) but 3.2.0.91.105 is installed
                Depends: linux-headers-server (= 3.2.0.85.99) but 3.2.0.91.105 is installed
E: Unmet dependencies. Try using -f.
dstrom@alphaweb0:~$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-server
The following packages will be REMOVED:
  linux-headers-3.2.0-74 linux-headers-3.2.0-74-generic linux-headers-3.2.0-76 linux-headers-3.2.0-76-generic
  linux-headers-3.2.0-77 linux-headers-3.2.0-77-generic linux-headers-3.2.0-79 linux-headers-3.2.0-79-generic
  linux-headers-3.2.0-80 linux-headers-3.2.0-80-generic linux-headers-3.2.0-82 linux-headers-3.2.0-82-generic
  linux-headers-3.2.0-83 linux-headers-3.2.0-83-generic linux-headers-3.2.0-84 linux-headers-3.2.0-84-generic
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 16 to remove and 115 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,730 B of archives.
After this operation, 542 MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 377662 files and directories currently installed.)
Removing linux-headers-3.2.0-74-generic ...
Removing linux-headers-3.2.0-74 ...
Removing linux-headers-3.2.0-76-generic ...
Removing linux-headers-3.2.0-76 ...
Removing linux-headers-3.2.0-77-generic ...
Removing linux-headers-3.2.0-77 ...
Removing linux-headers-3.2.0-79-generic ...
Removing linux-headers-3.2.0-79 ...
Removing linux-headers-3.2.0-80-generic ...
Removing linux-headers-3.2.0-80 ...
Removing linux-headers-3.2.0-82-generic ...
Removing linux-headers-3.2.0-82 ...
Removing linux-headers-3.2.0-83-generic ...
Removing linux-headers-3.2.0-83 ...
Removing linux-headers-3.2.0-84-generic ...
Removing linux-headers-3.2.0-84 ...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.85.99); however:
  Version of linux-image-server on system is 3.2.0.91.105.
 linux-server depends on linux-headers-server (= 3.2.0.85.99); however:
  Version of linux-headers-server on system is 3.2.0.91.105.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
dstrom@alphaweb0:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       228M  108M  109M  50% /boot
dstrom@alphaweb0:~$

---

### Post by darkod on 2015-10-12
Can you clean up /boot more? I advised to delete as many large files as possible, basically leave just the current kernel that you are running. In such case /boot will have used 25-30MB and right now it has 108MB used. Try cleaning up more and then try running apt-get update and after that apt-get -f install.

---

### Post by curmudge1 on 2015-10-12
I don't think it's a space issue, there was 109MB available, but I can't see as it would hurt, so I did clean up more out of /boot, and ran apt-get update, then apt-get -f install, still failed with 187MB available:

<apt-get update ran first>
Reading package lists... Done
dstrom@alphaweb0:/boot$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 114 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,730 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.85.99); however:
  Version of linux-image-server on system is 3.2.0.91.105.
 linux-server depends on linux-headers-server (= 3.2.0.85.99); however:
  Version of linux-headers-server on system is 3.2.0.91.105.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
dstrom@alphaweb0:/boot$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       228M   30M  187M  14% /boot
dstrom@alphaweb0:/boot$

---

### Post by darkod on 2015-10-12
Well, initially it was only a space issue. With little luck as soon as you create free space the process can continue. In your case something is bothering it after it got stuck due to not having enough free space.

Try apt-get dist-upgrade which might help pending upgrades to finish. Also one option to complete pending reconfiguration is dpkg-reconfigure -a.

---

### Post by curmudge1 on 2015-10-12
dpgk-reconfigure -a did not work but worth a try...

---

### Post by darkod on 2015-10-12
Also don't forget that some commands that didn't work before might work now. In these cases of full /boot partition, 180MB free is not the same as 100MB free, believe me. As I said I had couple of identical cases few weeks ago. But it managed to get sorted out easily after creating free space on /boot.

That's why you should try again commands you tried earlier because now you have much more free space. That's why I suggested the apt-get dist-upgrade too, if apt-get -f install is not sorting it out.

---

### Post by ian-weisser on 2015-10-12
> **curmudge1 said:**
> 
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.85.99); however:
  Version of linux-image-server on system is 3.2.0.91.105.
 linux-server depends on linux-headers-server (= 3.2.0.85.99); however:
  Version of linux-headers-server on system is 3.2.0.91.105.


You are correct. It's not a space issue anymore.
Now we clean up the fallout from that space issue.
This problem is that apt is still trying to install an **old** version of linux-server (the version it has cached), and the old dependencies for it are simply not available anymore.
We must tell the system to download a fresh copy of linux-server, which will pull in the proper (current) dependencies

This is usually caused by two apt conveniences: 1) apt caches packages for re-install, and 2) apt remembers what you told it in the past - if an install fails, apt will keep trying.

Try:
```
sudo apt-get update                  ## Refresh the package database
sudo apt-get clean linux-server      ## Delete the old version from your package cache, forcing apt to download a current version.
sudo apt-get install linux-server    ## Download and install a fresh copy of the package
```

If that doesn't work, the errors will point us in the right direction.

---

### Post by curmudge1 on 2015-10-14
Guess there's no fixing the packaging system once it's messed up?

--
Dave

---

### Post by Bashing-om on 2015-10-14
curmudge1; Hello;

This is 'buntu. It is always fixable.
What is the result from ian-weisser's advisement ?
> 
If that doesn't work, the errors will point us in the right direction.


so show us what is going on.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

