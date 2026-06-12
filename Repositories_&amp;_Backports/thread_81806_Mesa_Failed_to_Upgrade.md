---
title: "Mesa Failed to Upgrade"
date: 2005-10-25
forum: Repositories &amp; Backports
---

### Post by Single on 2005-10-25
I use fglrx, not mesa, but updater keeps bugging me. And it says that I have 2 broken packages, libgl1-mesa-dev and libgl1-mesa-dri.
Tried reinstall them but they depend on libgl1-mesa, which fails to upgrade.


ng@u053691m:~$ sudo apt-get upgrade libgl1-mesa
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but 6.3.2-0ubuntu6 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but 6.3.2-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.


ng@u053691m:~$ sudo apt-get -f upgrade libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be upgraded:
  libgl1-mesa
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/282kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 106871 files and directories currently installed.)
Preparing to replace libgl1-mesa 6.3.2-0ubuntu6 (using .../libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ng@u053691m:~$

---

### Post by Single on 2005-10-26
The problem is more serious than it seems. The synaptic, apt-get or update manager keeps saying that libgl1-mesa-dev and libgl1-mesa-dri are broken. The only way to fix that is to upgrade libgl1-mesa, but it keeps giving this error

ng@u053691m:~/Desktop/wine-20050930$ sudo apt-get install -f libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libgl1-mesa
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/282kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 106871 files and directories currently installed.)
Preparing to replace libgl1-mesa 6.3.2-0ubuntu6 (using .../libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone who can help?

---

### Post by spoilerhead on 2005-11-15
sitting here with the same problem.
:-/

---

### Post by nEJC on 2005-11-23
bump!

Same here :confused: 
...and what's worse - I can't do any updates untill this is resolved...

doing **sudo apt-get install libgl1-mesa**

results in

```

Unpacking libgl1-mesa (from .../libgl1-mesa_6.3.2-0ubuntu6breezy1_amd64.deb) ...dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_amd64.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looks like error in .deb package / how can we fix it?

---

### Post by jav on 2005-12-05
I have the same problem
and I have no clue how to fix it  :( 


# sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.3.2-0ubuntu6) but 6.3.2-0ubuntu6breezy1 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.3.2-0ubuntu6) but 6.3.2-0ubuntu6breezy1 is to be installed
E: Broken packages

so I check if I don't have libgl1-mesa and libglu1-mesa

#sudo apt-get install libgl1-mesa libglu1-mesa
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
libglu1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


so, everything should be fine?
but it's not :/

so I have no clue to what to do :(

so

---

### Post by TrinitronX on 2006-03-17
Same problem here:
```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu6) but 6.3.2-0ubuntu6breezy1 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.4.1-0ubuntu6) but 6.3.2-0ubuntu6breezy1 is installed

```

I decided to try what it suggested: ```
sudo apt-get -f install
```
Here's what it did:
```
 sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa
The following packages will be upgraded:
  libgl1-mesa
1 upgraded, 0 newly installed, 0 to remove and 1139 not upgraded.
233 not fully installed or removed.
Need to get 0B/162kB of archives.
After unpacking 422kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up python2.4-minimal (2.4.2-1ubuntu3) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling optimized python modules in /usr/lib/python2.4 ...

(Reading database ... 119525 files and directories currently installed.)
Preparing to replace libgl1-mesa 6.3.2-0ubuntu6breezy1 (using .../libgl1-mesa_6.4.1-0ubuntu6_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu6_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Why can't it create "./usr/lib/libGL.so.1.2"?  It has permission since it is running as root... perhaps this must be done while libGL.so.1.2 is not loaded?

What's funny is that I don't even use the mesa drivers, I installed the latest ATI fglrx drivers instead to get 3D accelleration for my Radeon 9800pro card.

Any ideas?

---

### Post by scooter12 on 2006-03-20
Was anyone able to fix this problem? I have tried to create a link to libGL.so.1.2 located in the X11R6 dir and that doesn't work.

Thanks

---

### Post by danboy on 2006-03-23
I'm having the same issue, if anyone resolved it help would be appreciated

---

### Post by lxevolution on 2006-03-23
Same thing is going on here. I'm going to compile and package a cvs source, maybe it will work.

---

### Post by [Leo] on 2006-03-24
I did it!
I tried a lot of times, and finally i find out a way to install libgl1-mesa!

I don't know why, but it seems dpkg doesn't like name "libGL.so.1.2"!
So i unpacked the deb file:
```
sudo dpkg -x package.deb my_dir && sudo dpkg -e package.deb my_dir/DEBIAN
```
After unpacked deb file i moved my_dir/usr/lib/libGL.so.1.2 to my_dir/usr/lib/libGL.so.1.1, i updated the symlink and finally:
```
sudo dpkg -b my_dir libgl1-mesa.deb
```
Then i just typed:
```
sudo dpkg -i libgl1-mesa.deb
```
and it worked!

I hope this would help you! :)

---

### Post by Sir_Yaro on 2006-05-12
thanks a lot!!

---

### Post by lenin69 on 2006-05-31
[QUOTE='[Leo]']I did it!
I tried a lot of times, and finally i find out a way to install libgl1-mesa!

I don't know why, but it seems dpkg doesn't like name "libGL.so.1.2"!
So i unpacked the deb file:
```
sudo dpkg -x package.deb my_dir && sudo dpkg -e package.deb my_dir/DEBIAN
```
After unpacked deb file i moved my_dir/usr/lib/libGL.so.1.2 to my_dir/usr/lib/libGL.so.1.1, i updated the symlink and finally:
```
sudo dpkg -b my_dir libgl1-mesa.deb
```
Then i just typed:
```
sudo dpkg -i libgl1-mesa.deb
```
and it worked!

I hope this would help you! :)[/QUOTE]


....
What?

what the hell means my_dir??

---

### Post by bon on 2006-05-31
i have the same problem, i have been trying to fix it for about a week now and windows is really great but..

---

### Post by bon on 2006-05-31
with alot of programs

---

### Post by sup on 2006-06-08
Thanks, it could have saved me an two-hours headache did I came across this earlier.

my-dir is a directory of your choice, similarly as package.deb is a particular package

---

### Post by lenin69 on 2006-06-10
a ok:-?  txs

but the problem rest the same....

---

