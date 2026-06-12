---
title: "Unable to update or install/uninstall packages"
date: 2014-04-02
forum: Server Platforms
---

### Post by david.bell on 2014-04-02
I was attempting to unisntall a package and got the following error:

```
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I tried apt-get install -f and get this:

```
After this operation, 114 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 134101 files and directories currently installed.)
Unpacking linux-image-3.2.0-60-generic-pae (from .../linux-image-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-60-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I'm not extremely familiar with Ubuntu, so any help would be appreciated.

---

### Post by bapoumba on 2014-04-02
> No space left on device
Guess that is your problem here. Can you make some room ?
```
df -h
```
Will show you where you need to.

---

### Post by david.bell on 2014-04-02
I thought the same thing, but here are my results:

```
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/mscf--unifi-root   78G  3.2G   71G   5% /
udev                          241M  4.0K  241M   1% /dev
tmpfs                         100M  208K   99M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          248M     0  248M   0% /run/shm
/dev/sda1                     228M  225M     0 100% /boot
```

---

### Post by david.bell on 2014-04-02
OK, I think I've found the root of my problem. I just don't know what to do about it. As you see above, my /boot is full. So I tried to uninstall some old kernals. But any attempt to unisntall anything gives me an error saying that a dependency (linux-image-3.2.0-37-generic-pae) isn't installed. But I can't install that dependency because /boot is full. So I seem to have a circular problem. Any suggestions?

---

### Post by bapoumba on 2014-04-02
```
/dev/sda1                     228M  225M     0 100% /boot
```
Your /boot partition on /dev/sda1 is full. You need to remove old kernels, I usually keep the last two working ones.
You'll find here some useful tips and links : [http://ubuntuforums.org/showthread.php?t=2120260](http://ubuntuforums.org/showthread.php?t=2120260)

---

### Post by david.bell on 2014-04-02
FYI, here are my results for ```
sudo dpkg --list 'linux-image*'
```

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                          Descrip$
+++-==================================-================================-=======$
un  linux-image                        <none>                           (no des$
un  linux-image-3.0                    <none>                           (no des$
ii  linux-image-3.2.0-23-generic-pae   3.2.0-23.36                      Linux k$
ii  linux-image-3.2.0-26-generic-pae   3.2.0-26.41                      Linux k$
ii  linux-image-3.2.0-27-generic-pae   3.2.0-27.43                      Linux k$
ii  linux-image-3.2.0-29-generic-pae   3.2.0-29.46                      Linux k$
ii  linux-image-3.2.0-31-generic-pae   3.2.0-31.50                      Linux k$
ii  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                      Linux k$
ii  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                      Linux k$
ii  linux-image-3.2.0-34-generic-pae   3.2.0-34.53                      Linux k$
ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                      Linux k$
ii  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                      Linux k$
in  linux-image-3.2.0-37-generic-pae   <none>                           (no des$
in  linux-image-3.2.0-60-generic-pae   <none>                           (no des$
iU  linux-image-generic-pae            3.2.0.37.44                      Generic$

```

---

### Post by david.bell on 2014-04-02
> [COLOR=#000000]Your /boot partition on /dev/sda1 is full. You need to remove old kernels, I usually keep the last two working ones.[/COLOR]

I tried to uninstall the old ones (using apt-get) but it fails because of the same dependency problem as the initial issue. So I'm in a bit of a circle here. I need to remove old versions to update to 3.2.0-37, but I can't remove old ones without having 3.2.0-37 installed.

---

### Post by Elfy on 2014-04-02
try and apt-get autoclean or apt-get clean to free some space

autoclean will remove old out of date packages

clean will remove ALL the apt cache

---

### Post by bapoumba on 2014-04-02
> **david.bell said:**
> I tried to uninstall the old ones (using apt-get) but it fails because of the same dependency problem as the initial issue. So I'm in a bit of a circle here. I need to remove old versions to update to 3.2.0-37, but I can't remove old ones without having 3.2.0-37 installed.

Hmm, yes, I saw that. Where did you get the kernels from ? It is quite curious you are missing dependencies.
Have a look at your sources.list :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

Edit : @ Elfy : will it clear the /boot partition with the missing deps issue ? autoclean will clear only packages that have been automatically installed and marked as such iirc, and there is a 3.2.0-60 generic-pae. I'm quite confused now :)

---

### Post by Frank P on 2014-04-02
I had exactly the same problem. I tried all the "correct" fixes but nothing worked.
Someone suggested the following and it worked.
**********************
Simply check /boot for vmlinuz* System.map* initrd.img* config* and abi* files. Delete the old ones you do not need anymore. Be sure to delete all 5 files per Kernel-version. Afterwards run update-grub and reboot. This should free up space.

 So if you'd like to delete 51 -> 55, remove all 5 for each version. E.g.:

							sudo rm vmlinuz*51* System.map*51* initrd.img*51* config*51* abi*51*					 


But anyways, be carefull to not delete all of them :wink:

**Attention:** this is not a good solution. It works, but your omitting the package manager which is may lead to problems later. Please follow Bashing-om's solution.				 		
*********************************************************

Try at your own risk

---

### Post by david.bell on 2014-04-02
@Elfy, it wouldn't let me use any apt-get commands. Kept getting the same out-of-space and dependency errors.

---

### Post by david.bell on 2014-04-02
@bapoumba: The kernels all came from apt-get upgrade. Not sure what happened. In the end I used ```
dpkg --remove linux-image-3.2.0-23-generic-pae
``` for each of the older kernels (left the lastest two) to clear up space. After that I was able use apt-get to install the kernel that matched the linux-image-generic-pae version (3.2.0-37). Then everything started working like a charm. Not sure why dpkg would work when apt-get wouldn't.

---

### Post by bapoumba on 2014-04-03
In the open source world (not addressing the licences to make it short), you can write software that rely on or use other software or code that other developers have written.

Say you are a developer and package application A as a .deb (for all debian based distributions as ubuntu), you can avoid writing parts of it as some functionalities are already in package B, so A will need B to run.
In the end, you can have very sophisticated and complicated relationships between packages as your package A depends on B, which in turn may depend on C etc. And all that in a distribution where all packages have compatible version numbers.

The version numbers are important. Say package B got an important update. maybe your package A won&#8217;t be able to run without some major changes too. That means that your package A version 1 depends on B version 1, but to be able to use package B version 2, you&#8217;ll need to rewrite some parts of A, and make it version 2.

Now a distribution is a release of a given set of packages all tied together by their dependencies. Say saucy has B.v1, A.v1 can be in it. If trusty moves to B.v2, then A will have to be v2 in this particular release. Additionally, you can inform that your package A.v2 cannot work at all with B.v1.

Debian has two levels of package managers, the programs that install other programs (once again to make it short, not talking of other package managers than the ones you have used): dpkg, (debian package management system) which works at a low level and APT (advanced packaging tools, but some say that is not the real meaning) which works at an integrated level.

dpkg installs, removes and informs the system of its actions. It does not care about dependencies. APT on the other end, knows about dependencies and deal with them. Think of APT as a series of tools (apt-get, apt-cache etc.) at the interface between the user, the packages and the dependency links within a distribution.
One other thing APT does, is working with repositories where it knows where to get the packages and their required dependencies. dpkg does not do that either.

So what you did is work at a lower level and remove the kernel causing dependency conflicts. dpkg informed the system it was gone, then APT could start working again all happy.

I&#8217;d say it turned out nicely. Sometimes dependency conflicts can be a nightmare, or even hell (look for dependency hell ;)).

Please make sure you clear some additional room on /boot, or you&#8217;ll be facing the space issue again.

When you think this is all solved, please mark your thread as such (in Thread Tools). And thanks for reading if you got down here!

---

### Post by david.bell on 2014-04-03
Thank you for the insight.

---

### Post by bapoumba on 2014-04-03
You are most welcome.

---

