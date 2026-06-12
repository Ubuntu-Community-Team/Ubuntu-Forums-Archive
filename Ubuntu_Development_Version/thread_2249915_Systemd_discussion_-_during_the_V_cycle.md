---
title: "Systemd discussion - during the V cycle"
date: 2014-10-25
forum: Ubuntu Development Version
---

### Post by Elfy on 2014-10-25
previous discussions during the U cycle are [here]("http://ubuntuforums.org/showthread.php?t=2224798")

---

### Post by zika on 2014-10-25
@ Harry332: [http://ubuntuforums.org/showthread.php?t=2224798&p=13151568#post13151568:](http://ubuntuforums.org/showthread.php?t=2224798&p=13151568#post13151568:)```
:~$ dpkg -l|grep systemd|grep sysv
ii  systemd-sysv                                          208-8ubuntu8 amd64        system and service manager - SysV links
```As soon it was available. ;)
@ Cafstan:   [http://ubuntuforums.org/showthread.php?t=2224798&p=13151636#post13151636:](http://ubuntuforums.org/showthread.php?t=2224798&p=13151636#post13151636:) ```
systemd-shim : Breaks: systemd (>= 209) but 215-5ubuntu1 is to be installed.
```Aptitude is a tool that I would not start U+1 without. ;) If only *>=209* were *>209   *or so many packages were not dependent (still) on systemd-shim. Patience is a clue for all that this early in U+1.

---

### Post by Cavsfan on 2014-10-25
> **zika said:**
> @ Cafstan:   [http://ubuntuforums.org/showthread.php?t=2224798&p=13151636#post13151636:](http://ubuntuforums.org/showthread.php?t=2224798&p=13151636#post13151636:) ```
systemd-shim : Breaks: systemd (>= 209) but 215-5ubuntu1 is to be installed.
```Aptitude is a tool that I would not start U+1 without. ;) If only *>=209* were *>209   *or so many packages were not dependent (still) on systemd-shim. Patience is a clue for all that this early in U+1.

@ziksta ;) Are you running some sort of ppa for systemd? I don't see any version 209 of anything. But yes I am patient.

---

### Post by zika on 2014-10-25
> **Cavsfan said:**
> @ziksta ;) Are you running some sort of ppa for systemd? I don't see any version 209 of anything. But yes I am patient.No PPA for SystemD. Just package-master (of sort) decided that that should be version dependency condition, I suppose.
```
:~$ dpkg -l|grep systemd
ii  libpam-systemd:amd64                                  208-8ubuntu8
                            amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                              208-8ubuntu8
                            amd64        systemd utility library
ii  libsystemd-journal0:amd64                             208-8ubuntu8
                            amd64        systemd journal utility library
ii  libsystemd-login0:amd64                               208-8ubuntu8
                            amd64        systemd login utility library
ii  systemd                                               208-8ubuntu8
                            amd64        system and service manager
ii  systemd-gui                                           1:3-2
                            all          transitional package for systemd-ui
rc  systemd-services                                      204-5ubuntu20.7
                            amd64        systemd runtime services
ii  systemd-shim                                          8-4
                            amd64        shim for systemd
ii  systemd-sysv                                          208-8ubuntu8
                            amd64        system and service manager - SysV links
ii  systemd-ui                                            3-2
                            amd64        graphical frontend for systemd
```

---

### Post by harry332 on 2014-10-26
> **Cavsfan said:**
> @ziksta ;) Are you running some sort of ppa for systemd? I don't see any version 209 of anything. But yes I am patient.

The last version originating from Utopic was 208.
Now, the next version (in vivid proposed) is 215.
See here:
[https://launchpad.net/ubuntu/vivid/+source/systemd/215-5ubuntu1](https://launchpad.net/ubuntu/vivid/+source/systemd/215-5ubuntu1)

I would also like to sum up some info about upstart, sysv and systemd.
Utopic is using upstart, though it is already possible to switch into sysv and eventually to systemd.
This is the case also in Vivid.

So there are 3 options we have now.

1) upstart
 - keeping upstart installed
 - not adding any init links in the kernel booting line

2) sysv
 - keeping systemd-shim (emulates the systemd function)  and cgmanager + libcgmanager0
 - using the kernel boot line: init=/lib/systemd/systemd

3) systemd
 - installing systemd-sysv and removing systemd-shim, cgmanager, libcgmanager, upstart
 - using the kernel boot line: init=/lib/systemd/systemd

With systemd-shim installed, systemd is using sysv booting from sbin/init.
If systemd-sysv is installed (and thus systemd-shim removed) it will overwrite /sbin/init with a link to systemd.

---

### Post by zika on 2014-10-26
> **harry332 said:**
> The last version originating from Utopic was 208.
Now, the next version (in vivid proposed) is 215.
See here:
[https://launchpad.net/ubuntu/vivid/+source/systemd/215-5ubuntu1](https://launchpad.net/ubuntu/vivid/+source/systemd/215-5ubuntu1)

I would also like to sum up some info about upstart, sysv and systemd.
Utopic is using upstart, though it is already possible to switch into sysv and eventually to systemd.
This is the case also in Vivid.

So there are 3 options we have now.

1) upstart
 - keeping upstart installed
 - not adding any init links in the kernel booting line

2) sysv
 - removing upstart, but keeping systemd-shim
 - using the kernel boot line: init=/lib/systemd/systemd

3) systemd
 - installing systemd-sysv and removing systemd-shim, cgmanager, libcgmanager, upstart
 - using the kernel boot line: init=/lib/systemd/systemd

With systemd-shim installed systemd is using sysv booting from sbin/init.
If systemd-sysv is installed (and thus systemd-shim removed) it will overwrite /sbin/init with a link to systemd.In cases 2) (which is as I see and from experience even impossible i.e. end up in 3) since removing upstart installs systemd-sysv automatically) and 3) kernel boot line init= switch is not required to use SystemD. At least that is my experience as I wrote repeatedly. *)
In case 3) You loose more than You've displayed**):```
:~$ sudo apt-get purge systemd-shim -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  indicator-datetime* systemd-shim* ubuntu-desktop* unity-control-center*
  unity-control-center-signon* webaccounts-extension-common*
  xul-ext-webaccounts*
0 upgraded, 0 newly installed, 7 to remove and 10 not upgraded.
Purg xul-ext-webaccounts [0.5-0ubuntu2]
Purg webaccounts-extension-common [0.5-0ubuntu2]
Purg unity-control-center-signon [0.1.7~+14.10.20140814-0ubuntu1]
Purg ubuntu-desktop [1.327]
Purg unity-control-center [14.10.0+14.10.20140922-0ubuntu2]
Purg indicator-datetime [13.10.0+14.10.20141009-0ubuntu1]
Purg systemd-shim [8-4]
```As I've wrote, there are several packages that are to be renewed in order to be able to do what You're proposing and since we are even before toolchain I see nothing more appropriate than a little patience. ;)
Update&#8321;: For sake of testing I've performed &#8222;downgrade&#8220; on one machine installing again UpStart (which removed SystemDSysV and I've reinstalled UReadAhead, FriendlyRecovery which were removed when removing UpStart) and I kind of cornered myself while painting the floor since SystemDSysV is now uninstallable due to 209/215 version dependency conundrum explained earlier. That looks more like present situation in vanilla Vivid install, it works nicely and awaits solution in proposed repositora about the faith of SystemD. Just thought that You should know, not having to go through all that Yourself. Yes, systemD is not fully ready for Vivid but it is well and kicking as is UpStart also. In futire days I think we will see full removal of Upstart, at the time when SystemD penetrated all neccessary packages and when all interconnections are ready. Greeting from Upstart machine that I've painted myself into the corner on. ;)
Update&#8322;: Just to clarify, not to leave impression that anybody else trying aforementioned would really corner h{im,er}self. SystemDSysV could be DL-ed (version -1) and used to get again hold of UpStart free install etc. Or, simply, vivid-proposed could be defeated for a while, apt database updated, and -1 version of SystemDSysV would be applied in all further apt doings until vivid-proposed is enabled again or that package get into regular repos. Just got some (rare) spare time and thought to disperse possible FUD I might have unintentionally started. ;)
*Note: I do have vivid-proposed enabled so all my aforementioned experiences are with that factor involved. Your mileage due to vivid-proposed disabled might vary.
**Note: This is true regardless of vivid-proposed enabled or not.

---

### Post by harry332 on 2014-10-26
> **zika said:**
> In cases 2) (which is as I see and from experience even impossible i.e. end up in 3) since removing upstart installs systemd-sysv automatically) and 3) kernel boot line init= switch is not required to use SystemD. At least that is my experience as I wrote repeatedly. *)
In case 3) You loose more than You've displayed**):```
:~$ sudo apt-get purge systemd-shim -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  indicator-datetime* systemd-shim* ubuntu-desktop* unity-control-center*
  unity-control-center-signon* webaccounts-extension-common*
  xul-ext-webaccounts*
0 upgraded, 0 newly installed, 7 to remove and 10 not upgraded.
Purg xul-ext-webaccounts [0.5-0ubuntu2]
Purg webaccounts-extension-common [0.5-0ubuntu2]
Purg unity-control-center-signon [0.1.7~+14.10.20140814-0ubuntu1]
Purg ubuntu-desktop [1.327]
Purg unity-control-center [14.10.0+14.10.20140922-0ubuntu2]
Purg indicator-datetime [13.10.0+14.10.20141009-0ubuntu1]
Purg systemd-shim [8-4]
```As I've wrote, there are several packages that are to be renewed in order to be able to do what You're proposing and since we are even before toolchain I see nothing more appropriate than a little patience. ;)
Update&#8321;: For sake of testing I've performed &#8222;downgrade&#8220; on one machine installing again UpStart (which removed SystemDSysV and I've reinstalled UReadAhead, FriendlyRecovery which were removed when removing UpStart) and I kind of cornered myself while painting the floor since SystemDSysV is now uninstallable due to 209/215 version dependency conundrum explained earlier. That looks more like present situation in vanilla Vivid install, it works nicely and awaits solution in proposed repositora about the faith of SystemD. Just thought that You should know, not having to go through all that Yourself. Yes, systemD is not fully ready for Vivid but it is well and kicking as is UpStart also. In futire days I think we will see full removal of Upstart, at the time when SystemD penetrated all neccessary packages and when all interconnections are ready. Greeting from Upstart machine that I've painted myself into the corner on. ;)
Update&#8322;: Just to clarify, not to leave impression that anybody else trying aforementioned would really corner h{im,er}self. SystemDSysV could be DL-ed (version -1) and used to get again hold of UpStart free install etc. Or, simply, vivid-proposed could be defeated for a while, apt database updated, and -1 version of SystemDSysV would be applied in all further apt doings until vivid-proposed is enabled again or that package get into regular repos. Just got some (rare) spare time and thought to disperse possible FUD I might have unintentionally started. ;)
*Note: I do have vivid-proposed enabled so all my aforementioned experiences are with that factor involved. Your mileage due to vivid-proposed disabled might vary.
**Note: This is true regardless of vivid-proposed enabled or not.

You were right about the option 2 being incorrect.
I have now made corrections to it.

In your case uninstalling systemd-shim (8-4) removes more packages than in my setup, because I do not have Unity DE installed.

Then, about the init=/lib/systemd/systemd kernel boot line.
My setup will not boot at all without that line, it leads to kernel panic instead.

But as you have systemd-shim (8-4) installed, you do not have systemd (215) at all.
You see systemd-shim (8-4) breaks systemd (>=209).
For systemd (215) you need the newest systemd-shim (8-4build1).

---

### Post by zika on 2014-10-26
> **harry332 said:**
> But as you have systemd-shim (8-4) installed, you do not have systemd (215) at all.
You see systemd-shim (8-4) breaks systemd (>=209).
For systemd (215) you need the newest systemd-shim (8-4build1).As I've emphasized more that once. ;) Not to mention stuff between code-tags.
> **harry332 said:**
> Then, about the init=/bin/systemd kernel boot line.
My setup will not boot at all without that line, it leads to kernel panic instead.I suspect that You have some relicts of UpStart that You did not remove/purge completely.

---

### Post by zika on 2014-10-26
Vivid-proposed got complete:```
The following packages will be upgraded:
   libpam-systemd (208-8ubuntu8 => 215-5ubuntu1)
   libsystemd-daemon0 (208-8ubuntu8 => 215-5ubuntu1)
   libsystemd-journal0 (208-8ubuntu8 => 215-5ubuntu1)
   libsystemd-login0 (208-8ubuntu8 => 215-5ubuntu1)
   libudev1 (208-8ubuntu8 => 215-5ubuntu1)
   systemd (208-8ubuntu8 => 215-5ubuntu1)
   systemd-shim (8-4 => 8-4build1)
   systemd-sysv (208-8ubuntu8 => 215-5ubuntu1)
   udev (208-8ubuntu8 => 215-5ubuntu1)
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15,4 kB/3605 kB of archives.
After this operation, 7268 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
```Left, now, is to figure out```
dpkg: warning: unable to delete old directory '/etc/systemd/system/multi-user.target.wants': Directory not empty
```and```
Created symlink from /etc/systemd/system/getty.target.wants/getty@tty1.service to /lib/systemd/system/getty@.service.
Created symlink from /etc/systemd/system/multi-user.target.wants/remote-fs.target to /lib/systemd/system/remote-fs.target.
```

---

### Post by harry332 on 2014-10-26
> **zika said:**
> As I've emphasized more that once. ;) Not to mention stuff between code-tags.
I suspect that You have some relicts of UpStart that You did not remove/purge completely.

Well I did purge upstart, cdmanager, libcgmanager0 and systemd-shim.
So possible upstart remnants are not the cause.
Have you tried to boot with systemd (215) without the kernel line?
You see the 215 version does not work as well as 208 here.

---

### Post by zika on 2014-10-26
> **harry332 said:**
> Well I did purge upstart, cdmanager, libcgmanager0 and systemd-shim.
So possible upstart remnants are not the cause.
Have you tried to boot with systemd (215) without the kernel line?
You see the 215 version does not work as well as 208 here.As I wrote above, I've just got 251 and reboot is the first time to do as soon as I finish this post. ;)
Update&#8321;: Yeap, live&kicking and writing this after (re)boot without anything added to kernel boot line, clean vanilla.
Update&#8322;:```
:~$ sudo apt-get purge -s systemd-shim
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  indicator-datetime* systemd-shim* ubuntu-desktop* unity-control-center*
  unity-control-center-signon* webaccounts-extension-common*
  xul-ext-webaccounts*
```

---

### Post by zika on 2014-10-26
> **harry332 said:**
> My setup will not boot at all without that line, it leads to kernel panic instead.Do You (by any chance) have multiple kernels installed and (if so) did You update initramfs for all of them?

---

### Post by harry332 on 2014-10-26
> **zika said:**
> Do You (by any chance) have multiple kernels installed and (if so) did You update initramfs for all of them?

ATM I only have the latest Ubuntu kernel installed (one version only). I do not use the mainline kernel PPA ones now.
So you uninstalled systemd-shim completely too; or did you upgrade it to 8-4build1?

---

### Post by Alan F on 2014-10-26
Are you guys aware that SystemD can provide a 'bootchart like', but much smarter than Bootchart, graphical display of the boot process?

Just run, in Terminal ....

      systemd-analyze plot > plot.svg

and a graph of the last boot, named plot.svg, will be written to the Home directory.

---

### Post by zika on 2014-10-26
> **Alan F said:**
> Are you guys aware that SystemD can provide a 'bootchart like', but much smarter than Bootchart, graphical display of the boot process?
Just run, in Terminal ....```
systemd-analyze plot > plot.svg
```and a graph of the last boot, named plot.svg, will be written to the Home directory.Yes, of course, it is a serious tool (SystemD as a whole) and that is why we (at least me) like it seeing being implemented in Ubuntu.

---

### Post by zika on 2014-10-26
> **harry332 said:**
> So you uninstalled systemd-shim completely too; or did you upgrade it to 8-4build1?
[http://ubuntuforums.org/showthread.php?t=2249915&p=13152336#post13152336](http://ubuntuforums.org/showthread.php?t=2249915&p=13152336#post13152336) (and several other posts of mine about systemd-shim)
No, I have not uninstalled it because I would seriously crippled my install by doing that. I did upgrade it```
:~$ dpkg -l|grep systemd-shim
ii  systemd-shim                                          8-4build1                                amd64        shim for systemd
```

---

### Post by rrnbtter on 2014-10-26
Greetings,

> **Alan F said:**
> Are you guys aware that SystemD can provide a 'bootchart like', but much smarter than Bootchart, graphical display of the boot process?

Just run, in Terminal ....

      systemd-analyze plot > plot.svg

and a graph of the last boot, named plot.svg, will be written to the Home directory.

Thanks for the info, this is a real nice feature! I am also enjoying all of the posts in this thread. Quite an interesting web that has been weaved by our Grand Puba (Canonical).  I don't think I could navagate it without the excellent tour guides in this thread.

---

### Post by Cavsfan on 2014-10-27
I have not done anything special during the entire development cycle for Utopic and had custom boot entries to boot with either upstart or systemd.

Here in Vivid I have the same custom grub enteries:
```
menuentry "Vivid Vervet 15.04 Mate (devel branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Mate Systemd (Devel Branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Mate (devel branch) (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro recovery nomodeset
        initrd /initrd.img
}
```

I have not opened up proposed updates. I am patient and I'll wait for them to come to me. :)

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                      208-8ubuntu8                             amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                  208-8ubuntu8                             amd64        systemd utility library
ii  libsystemd-journal0:amd64                 208-8ubuntu8                             amd64        systemd journal utility library
ii  libsystemd-login0:amd64                   208-8ubuntu8                             amd64        systemd login utility library
ii  systemd                                   208-8ubuntu8                             amd64        system and service manager
ii  systemd-shim                              8-4                                      amd64        shim for systemd

```

It looks like I do have the Vivid systemd-shim though:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd-shim
systemd-shim:
  Installed: 8-4
  Candidate: 8-4
  Version table:
 *** 8-4 0
        500 http://us.archive.ubuntu.com/ubuntu/ [COLOR=#ff0000]vivid[/COLOR]/main amd64 Packages
        100 /var/lib/dpkg/status
```

It already looks to be a little faster:
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.446s (kernel) + 15.364s (userspace) = 19.810s

```

---

### Post by zika on 2014-10-27
> **Cavsfan said:**
> It already looks to be a little faster:```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.446s (kernel) + 15.364s (userspace) = 19.810s
```Without refererence (time before upgrade) there is no information in that number... ;)

---

### Post by harry332 on 2014-10-27
I think there is a difference if one has systemd-shim (cgmanager + libcgmanager0) installed or if one has purged those packages.
Shim is a systemd emulator (imitating systemd). It emulates the systemd function that are required to run
 the systemd helpers without using the init service.
Systemd-shim makes it possible to run an application (using systemd-logind) where systemd is not pid 1.
If kernel line init=/lib/systemd/systemd is used, systemd-shim is useless.

---

### Post by Cavsfan on 2014-10-27
> **zika said:**
> Without refererence (time before upgrade) there is no information in that number... ;)

Sorry I could go back and find the reference but I was recalling that from memory as fact. ;)

---

### Post by Cavsfan on 2014-10-27
> **harry332 said:**
> I think there is a difference if one has systemd-shim (cgmanager + libcgmanager0) installed or if one has purged those packages.
Shim is a systemd emulator (imitating systemd). It emulates the systemd function that are required to run
 the systemd helpers without using the init service.
Systemd-shim makes it possible to run an application (using systemd-logind) where systemd is not pid 1.
If kernel line init=/lib/systemd/systemd is used, systemd-shim is useless.

I guess this is over my head. 
I use init=/lib/systemd/systemd in the kernel line so where does that leave me - not using systemd-shim?

---

### Post by fjgaude on 2014-10-27
> **Cavsfan said:**
> I guess this is over my head. 
I use init=/lib/systemd/systemd in the kernel line so where does that leave me - not using systemd-shim?

Here what i get with my setup:

frank@flash:~$ sudo systemd-analyze (14.10)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s

frank@flash:~$ sudo systemd-analyze (15.04)
Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s

At this point 15.04 gets 1.1 vs 14.10's 1.3 using GTKperf.

But will it hold that quickness?

---

### Post by zika on 2014-10-27
> **Cavsfan said:**
> Sorry I could go back and find the reference but I was recalling that from memory as fact. ;)Nothing to be sorry about. I was just trying to get some plausible conclusions. As a matter of fact I even do not have numbers to recall from memory because I have not put them there... ;) I will try to remember to remember them next time.

---

### Post by harry332 on 2014-10-27
> **Cavsfan said:**
> I guess this is over my head. 
I use init=/lib/systemd/systemd in the kernel line so where does that leave me - not using systemd-shim?

The idea to use systemd-shim is to run an application that uses systemd-logind, when systemd is not pid 1.
However, if you set init=/lib/systemd/systemd in the kernel booting line, you force systemd as pid 1.
Then you are not using systemd-shim.

---

### Post by harry332 on 2014-10-27
> **fjgaude said:**
> Here what i get with my setup:

frank@flash:~$ sudo systemd-analyze (14.10)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s

frank@flash:~$ sudo systemd-analyze (15.04)
Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s

At this point 15.04 gets 1.1 vs 14.10's 1.3 using GTKperf.

But will it hold that quickness?

That is what you get when using Intel Haswell processor and a fast SSD. :guitar:

---

### Post by zika on 2014-10-27
> **harry332 said:**
> The idea to use systemd-shim is to run an application that uses systemd-logind, when systemd is not pid 1.
However, if you set init=/lib/systemd/systemd in the kernel booting line, you force systemd as pid 1.
Then you are not using systemd-shim.This is starting to make some sense. Thank You for food for thought.

---

### Post by harry332 on 2014-10-27
> **zika said:**
> This is starting to make some sense. Thank You for food for thought.

Thanks for that.
I have been reading the "fight" in favor and against systemd and systemV (sysvinit) in Debian lately. What a mess!

---

### Post by Cavsfan on 2014-10-27
> **zika said:**
> Nothing to be sorry about. I was just trying to get some plausible conclusions. As a matter of fact I even do not have numbers to recall from memory because I have not put them there... ;) I will try to remember to remember them next time.

Or perhaps you could remember to go find that other thread with Utopic and find my previous posts and compare that to what I posted. :p I'm not that outgoing myself.

> **harry332 said:**
> The idea to use systemd-shim is to run an application that uses systemd-logind, when systemd is not pid 1.
However, if you set init=/lib/systemd/systemd in the kernel booting line, you force systemd as pid 1.
Then you are not using systemd-shim.

I'm just rolling with the punches; not doing anything like purging this or installing that aside from what comes down through the regular updates.
I just got the addition of init=/lib/systemd/systemd in the kernel line from the first couple of posts in the first thread. I do see in conky when systemd is running and when init is running.

Systemd seems to be a little faster. Nothing like booting an SSD which the difference between the two is not really discernible at least by the naked eye.

---

### Post by zika on 2014-10-27
> **Cavsfan said:**
> Or perhaps you could remember to go find that other thread with Utopic and find my previous posts and compare that to what I posted. :p I'm not that outgoing myself.Ups, I might have not been clear enough: I thought that I could not recall numbers for [SIZE=5]**my**[/SIZE] machine because I did not remember them. To add to that I 've changed whole machine lately, so...
It is good to know that there is a possible comparison and I will try to compare &#8222;Your&#8220; results (i.e. results for Your machine) soon.
Update&#8321;: Not to be only writing, difference with/without init= switch in kernel boot line gives 1sec difference i.e. ~4.55% in favor of init= switch present. Will keep writing down numbers (not here, of course) (if I do not forget, yes, a script could be made or even one-liner for /etc/rc.local or something like that) so, one day, a more resolute difference will emerge.

---

### Post by Cavsfan on 2014-10-27
> **harry332 said:**
> The idea to use systemd-shim is to run an application that uses systemd-logind, when systemd is not pid 1.
However, if you set init=/lib/systemd/systemd in the kernel booting line, you force systemd as pid 1.
Then you are not using systemd-shim.

I do see that systemd is pid 1 and init is pid 1 when upstart is used to boot. So, I would have to do what zika did in order to get the full benefit of systemd? Is that what you are saying?
Sorry, fighting thick skull disease from setting in. :)
> **zika said:**
> Ups, I might have not been clear enough: I thought that I could not recall numbers for [SIZE=5]**my**[/SIZE] machine because I did not remember them. To add to that I 've changed whole machine lately, so...
It is good to know that there is a possible comparison and I will try to compare „Your“ results (i.e. results for Your machine) soon.
Update&#8321;: Not to be only writing, difference with/without init= switch in kernel boot line gives 1sec difference i.e. ~4.55% in favor of init= switch present. Will keep writing down numbers (not here, of course) (if I do not forget, yes, a script could be made or even one-liner for /etc/rc.local or something like that) so, one day, a more resolute difference will emerge.

Sorry for any confusion. I thought that is what you meant - that I go get my previous results to compare my newer results with. No big deal though. On this older machine a few seconds here or there really does not make much difference to me. Except that when windows 7 starts up, I go perform some sort of task and come back and then it's through booting up.
Although I've heard from my son that even on windows 8 SSDs boot in a matter of a second or two. SSDs are supposed to have a huge amount of RAM which might explain how they can read ahead so fast.
That would be on either windows or Ubuntu systemd or upstart.

---

### Post by zika on 2014-10-27
> **Cavsfan said:**
> So, I would have to do what zika did in order to get the full benefit of systemd?What did I do? ;)

---

### Post by fjgaude on 2014-10-27
> **harry332 said:**
> That is what you get when using Intel Haswell processor and a fast SSD. :guitar:

Yes, notice my signature. <smile>

---

### Post by Cavsfan on 2014-10-27
> **zika said:**
> What did I do? ;)

You said you removed your ability to boot with upstart and whatever that entailed. You now boot exclusively with systemd. That is what you did and that is what I meant. ;)

---

### Post by Cavsfan on 2014-10-27
> **fjgaude said:**
> Yes, notice my signature. <smile>

Someday.... My son has accumulated 4 SSDs of various sizes for his new full tower system which also sports an Nvidia GeForce GTX 780 Ti that he plans to SLI eventually.

My time is coming maybe next year hopefully to get a new system with an SSD.

When you talk in milliseconds and not seconds - that is a fast booting machine. :)

Can you really tell any difference between systemd and upstart with an SSD? Or do you have to look at the output of systemd-analyze?

---

### Post by ventrical on 2014-10-27
> **Cavsfan said:**
> 

Systemd seems to be a little faster. Nothing like booting an SSD which the difference between the two is not really discernible at least by the naked eye.


I'll get a 250ms boot with the last update of Utopic on my SSD but it gained a second or so since cycle upgrade with xubuntu.  Systemd gave me a double-dutch plymouth screen (meaning that it blinked on , then blinked off .. then blinked to unity-greeter (before I bricked that install) .. taking up a second or so more than usual. Must be me , something I did , or did not do,  or something . So I'll just pick myself up , dust myself off , and do it all over again :)lol

 Regards..

---

### Post by zika on 2014-10-27
> **Cavsfan said:**
> You said you removed your ability to boot with upstart and whatever that entailed. You now boot exclusively with systemd. That is what you did and that is what I meant. ;)Yeap, I simply purged upstart, now I see what You've meant.

---

### Post by harry332 on 2014-10-28
> **Cavsfan said:**
> Someday.... My son has accumulated 4 SSDs of various sizes for his new full tower system which also sports an Nvidia GeForce GTX 780 Ti that he plans to SLI eventually.

My time is coming maybe next year hopefully to get a new system with an SSD.

When you talk in milliseconds and not seconds - that is a fast booting machine. :)

Can you really tell any difference between systemd and upstart with an SSD? Or do you have to look at the output of systemd-analyze?

Well I have an Intel Core i7 4970 (Haswell) and a Samsung 850 Pro SSD.
They are a really fast booting combination.
Also the Asus Sabertooth Z97 has a fast boot function (reading only certain hardware when booting).

Actually, I do not see any difference when booting with upstart + systemd-shim or systemd + systemd-sysv + init=/lib/systemd/systemd. Booting from grub menu to DE is less than 5 sec.
I don't see anything about Plymouth there, only black screen from the start to DE.

---

### Post by harry332 on 2014-10-28
> **Cavsfan said:**
> I do see that systemd is pid 1 and init is pid 1 when upstart is used to boot. So, I would have to do what zika did in order to get the full benefit of systemd? Is that what you are saying?
Sorry, fighting thick skull disease from setting in. :)
...


I set systemd up to be the pid 1 by installing systemd-sysv (and purging upstart, systemd-shim, cgmanager and libcgmanager0),
so I have nothing left from upstart nor sysvinit. I also have init=/lib/systemd/systemd in the kernel boot line.

I am not sure if systemd is really pid I if the kernel boot line is not used and systemd-shim with cgmanager is still installed.
That is a combination where systemd-shim does emulate systemd during booting, but the setup is not actually directly using systemd.
This is what I think Zika is using. He may correct if I am wrong.

So for a full systemd setup, I think there would be two options:
1) using the kernel line init=/lib/systemd/systemd
2) purging systemd-shim and cgmanager + libcgmanager0

I also have noticed that without systemd-shim installed, one must use the kernel booting line, otherwise the setup cannot boot (it will not find /lib/systemd/systemd file).

---

### Post by Cavsfan on 2014-10-28
> **harry332 said:**
> I set systemd up to be the pid 1 by installing systemd-sysv (and purging upstart, systemd-shim, cgmanager and libcgmanager0),
so I have nothing left from upstart nor sysvinit. I also have init=/lib/systemd/systemd in the kernel boot line.

I am not sure if systemd is really pid I if the kernel boot line is not used and systemd-shim with cgmanager is still installed.
That is a combination where systemd-shim does emulate systemd during booting, but the setup is not actually directly using systemd.
This is what I think Zika is using. He may correct if I am wrong.

So for a full systemd setup, I think there would be two options:
1) using the kernel line init=/lib/systemd/systemd
2) purging systemd-shim and cgmanager + libcgmanager0

I also have noticed that without systemd-shim installed, one must use the kernel booting line, otherwise the setup cannot boot (it will not find /lib/systemd/systemd file).

Thanks for the information. I'm not going to do anything extra. I will just wait for the powers to be to do that. I like having the capability to boot upstart or systemd for now.
I still have that bug in systemd boot that EST is 4 hours behind. [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258)
If they switch Vivid over to systemd then I will follow.

Even this shows to be 4 hours behind:
```
cavsfan@cavsfan-MS-7529:~$ sudo hwclock -r
[sudo] password for cavsfan: 
Tue 28 Oct 2014 10:18:33 AM EDT  -0.390897 seconds
```

It is actually 2:18PM here.

---

### Post by mc4man on 2014-10-28
The time here is correct everywhere inc. in system setup & win8, the init doesn't *seem* to matter.
As far as your last command likely hwclock defaults to utc, that shouldn't effect anything (system time
I gather you can switch the hwclock to system time for the session, why or to what (dis)advantage don't know

sudo hwclock -w

---

### Post by Cavsfan on 2014-10-29
> **mc4man said:**
> The time here is correct everywhere inc. in system setup & win8, the init doesn't *seem* to matter.
As far as your last command likely hwclock defaults to utc, that shouldn't effect anything (system time
I gather you can switch the hwclock to system time for the session, why or to what (dis)advantage don't know

sudo hwclock -w

Booting with all the operating systems (7) I have on this PC the time is correct as long as I boot Utopic and Vivid with upstart.
The only thing that works booting systemd is entering **sudo ntpdate ntp.ubuntu.com** in terminal. Or probably if I put that cron script back in there but I'm not going to.

I just now booted with systemd into both and the time was off by 4 hours. Somehow the bug I created [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208)
got marked as a duplicate of the one you opened [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1377698](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1377698)
But that just involved booting with upstart. The problem remains in systemd.

I deleted the line that marked it as a duplicate with an explanation that the difference is systemd-boot. It must have been marked as a dup by some bot because systemd is in the bug description.

Here is what Vivid just displayed upon booting with systemd:

[[IMG]http://en.zimagez.com/miniature/20141029135046.jpg[/IMG]]("http://en.zimagez.com/zimage/20141029135046.php")

Even though it says it detected the time was off and fixed it, the time was still 4 hours behind.
So, the bug remains and I'm sticking with upstart until it is fixed.

---

### Post by zika on 2014-11-01
Just a little recap for those (like me) that (even ocasionally) used &#8222;text&#8220; switch in kernel boot line in order to stop GUI from being started by default. SystemD provides a nice remedy, at the end. Following [https://fedoraproject.org/wiki/SysVinit_to_Systemd_Cheatsheet](https://fedoraproject.org/wiki/SysVinit_to_Systemd_Cheatsheet) I've (once I've found some spare time, weekend, etc.): &#8222;text&#8220;=&#8222;systemd.unit=runlevel3.target&#8220;. Not to mention isolate and other switches for systemctl that wor very nicely. Once You start thinking SysteD way it all fits like a glove. Enjoy.
([COLOR=#333333]systemd.unit=emergency.service for recovery boot)[/COLOR]

---

### Post by Cavsfan on 2014-11-19
I can confirm that the US Eastern Standard Time problem being 4 hours behind is fixed with today's updates in Vivid.
I had been using upstart since this was a major problem for me. But, when I seen the update I booted into Vivid Gnome systemd for the first time since installing it and the time is correct.
It looks like a lot of work went into this:

> systemd (215-6ubuntu1) vivid; urgency=medium

  * Merge with Debian unstable. Remaining Ubuntu changes:
    - Create disk/by-partlabel links for mmcblk partitions.
    - Hack to support system-image read-only /etc, and modify files in
      /etc/writable/ instead.
    - debian/rules: Drop doc dir symlinking. It creates havoc with dpkg
      upgrades, and we already have the automatic per-file symlinking.
    - debian/rules: Add an epoch to libgudev.
    - Don't install 80-networking.rules and the Debian *.agent scripts, we
      never supported them in Ubuntu. Instead, extend systemd's "net" device
      udev rule to trigger ifup@.service on network devices.
    - Keep our much simpler udev maintainer scripts (all platforms must
      support udev, no debconf).
    - Add udev Apport package hook.
    - debian/extra/initramfs.top: Drop $ROOTDELAY, we do that in a more
      sensible way with wait-for-root. Will get applicable to Debian once
      Debian gets wait-for-root in initramfs-tools.
    - debian/extra/initramfs.bottom: If LVM is installed, settle udev,
      otherwise we get missing LV symlinks. Workaround for LP #1185394.
    - Add 40-hyperv-hotadd.rules: Workaround for LP #1233466.
    - Mark graphics devices as PRIMARY_DEVICE_FOR_DISPLAY so that we can wait
      for those in plymouth.
    - Add debian/udev.lvm2.init: Dummy SysV init script to satisfy insserv
      dependencies to "lvm2" which is handled with udev rules in Ubuntu.
    - Add /run/shm -> /dev/shm symlink in debian/tmpfiles.d/debian.conf
      (LP: #1320534, Closes: #674755).
    - Lower Breaks: to lvm2 again. Our lvm2 package has always used udev for
      device setup, and thus is be compatible with systemd, too.
    - Lower Breaks: to plymouth version which has the udev inotify fix in
      Ubuntu.
    - Add HP ProLiant Server Cartridge power control support.
    - Provide shutdown fallback for upstart. (LP: #1370329)
    - Add boot-and-services autopkgtest to check booting with systemd-sysv and
      that the most crucial services behave as expected.
    - debian/ifup@.service: Additionally run for "auto" class. We don't really
      support "allow-hotplug" in Ubuntu at the moment, so we need to deal with
      "auto" devices appearing after "/etc/init.d/networking start" already
      ran.  (LP: #1374521)

    Upgrade fixes, keep until 16.04 LTS release:
    - systemd Conflicts/Replaces/Provides systemd-services.
    - Remove obsolete systemd-logind upstart job.

  * Clean up obsolete /etc/udev/rules.d/README on upgrades. (LP: #1381655)
  * Add Get-RTC-is-in-local-time-setting-from-etc-default-rc.patch: In Ubuntu
    we currently keep the setting whether the RTC is in local or UTC time
    in /etc/default/rcS "UTC=yes|no", instead of /etc/adjtime. (LP: #1377258)
  * Add systemd Apport hook for adding systemd-delta and information about
    failed units.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 19 Nov 2014 08:55:55 +0100

Hopefully this will make it to Trusty soon. I just checked and it has not yet.

---

### Post by Cavsfan on 2014-11-20
I guess I was wrong about Vivid systemd time being fixed. Right now it shows exactly 5 hours ahead.

---

### Post by zika on 2014-12-10
[http://anzwix.com/a/systemd/NEWSPrepareNEWSForNewRelease](http://anzwix.com/a/systemd/NEWSPrepareNEWSForNewRelease)

---

### Post by cariboo on 2014-12-10
Is there a way to keep upstart from re-installing it self automatically, if I forget to check what is being installed, as every time it gets installed, it breaks my system.

---

### Post by zika on 2014-12-10
> **cariboo907 said:**
> Is there a way to keep upstart from re-installing it self automatically, if I forget to check what is being installed, as every time it gets installed, it breaks my system.???
What do You mean by &#8222;re-installing&#8220;? Do You have systemd-sysv installed? If You do that shoud prevent UpStart from getting even near. You've got my attention.
Behaviour like the one You mention {sh,c}ould happen on Debian, but even there that should be resolved.

---

### Post by cariboo on 2014-12-10
I did have systemd-sysv installed, but with the latest updates, upstart was installed again. This is the second time it happened, the first time the system just ran as it should, but this time both monitors shutdown, and when my Benq restarted, there was only a flashing cursor, and upon reboot, at the login  screen, the mouse cursor disappeared after I had logged in.

To get things working again, I started in recovery mode, and installed systemd-sysv again, while I was at it, I removed the nvidia-331 drivers, but I don't think that was a part of the problem.

---

### Post by zika on 2014-12-10
> **cariboo907 said:**
> I did have systemd-sysv installed, but with the latest updates, upstart was installed again. This is the second time it happened, the first time the system just ran as it should, but this time both monitors shutdown, and when my Benq restarted, there was only a flashing cursor, and upon reboot, at the login  screen, the mouse cursor disappeared after I had logged in.
To get things working again, I started in recovery mode, and installed systemd-sysv again, while I was at it, I removed the nvidia-331 drivers, but I don't think that was a part of the problem.The only reason I could think of is that by some sort of glitch You do have some dependency issues unresolved. Try to list what packages do You have from UpStart installed. Maybe some atavism still lurkes on Your machine.
It should be:```
:~$ dpkg -l|grep upstart
ii  libupstart1:amd64                                     1.13.2-0ubuntu5                                          amd64        Upstart Client Library
ii  upstart-bin                                           1.13.2-0ubuntu5                                          amd64        event-based init daemon - essential binaries
```I do not clearly remember if I did cleaning of UpStart manually before it became official.

---

### Post by Cavsfan on 2014-12-10
All of the nvidia-331 drivers just updated to 331.113-0ubuntu2 so they should not be an issue.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia 
ii  nvidia-331                                  331.113-0ubuntu2                           amd64        NVIDIA binary driver - version 331.113
ii  nvidia-331-uvm                              331.113-0ubuntu2                           amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-331                       331.113-0ubuntu2                           amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.7                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver
```

If I installed systemd-sysv, is the boot line **quiet splash init=/lib/systemd/systemd** still good to go?

---

### Post by cariboo on 2014-12-10
I checked and found libupstart1 and removed it, but removing upstart-bin also removes ubuntu-desktop, unity and unity-greeter. Removing ubuntu-desktop, won't hurt anything, but I use unity, so removing it is a no go.

---

### Post by zika on 2014-12-11
> **cariboo907 said:**
> I checked and found libupstart1 and removed it, but removing upstart-bin also removes ubuntu-desktop, unity and unity-greeter. Removing ubuntu-desktop, won't hurt anything, but I use unity, so removing it is a no go.No, as I gave You list, upstart-bin (together wih libupstart1) is here to stay for some time.

---

### Post by zika on 2014-12-11
> **Cavsfan said:**
> All of the nvidia-331 drivers just updated to 331.113-0ubuntu2 so they should not be an issue.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia 
ii  nvidia-331                                  331.113-0ubuntu2                           amd64        NVIDIA binary driver - version 331.113
ii  nvidia-331-uvm                              331.113-0ubuntu2                           amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-331                       331.113-0ubuntu2                           amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.7                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver
```

If I installed systemd-sysv, is the boot line **quiet splash init=/lib/systemd/systemd** still good to go?You do not need init=... anymore.

---

### Post by Cavsfan on 2014-12-11
> **cariboo907 said:**
> I checked and found libupstart1 and removed it, but removing upstart-bin also removes ubuntu-desktop, unity and unity-greeter. Removing ubuntu-desktop, won't hurt anything, but I use unity, so removing it is a no go.

> **zika said:**
> No, as I gave You list, upstart-bin (together wih libupstart1) is here to stay for some time.

Very interesting! I guess I need to know that too.

> **Cavsfan said:**
> All of the nvidia-331 drivers just updated to 331.113-0ubuntu2 so they should not be an issue.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia 
ii  nvidia-331                                  331.113-0ubuntu2                            amd64        NVIDIA binary driver - version 331.113
ii  nvidia-331-uvm                              331.113-0ubuntu2                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-331                       331.113-0ubuntu2                           amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.7                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                             amd64        Tool for configuring the NVIDIA graphics  driver
```

If I installed systemd-sysv, is the boot line **quiet splash init=/lib/systemd/systemd** still good to go?

> **zika said:**
> You do not need init=... anymore.

Thanks!
Still a little hesistant to make the jump. Hopefully soon. :)

---

### Post by zika on 2014-12-14
We've got ourselves 218 today... ;)
```
Get:1 http://archive.ubuntu.com/ubuntu/ vivid-proposed/universe systemd-sysv amd64 218-1ubuntu1 [8520 B]
Get:2 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main udev amd64 218-1ubuntu1 [898 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libudev1 amd64 218-1ubuntu1 [34,7 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libpam-systemd amd64 218-1ubuntu1 [106 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main systemd amd64 218-1ubuntu1 [3062 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd0 amd64 218-1ubuntu1 [71,7 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libgudev-1.0-0 amd64 1:218-1ubuntu1 [14,4 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-daemon0 amd64 218-1ubuntu1 [16,1 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-journal0 amd64 218-1ubuntu1 [57,1 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-login0 amd64 218-1ubuntu1 [27,2 kB]
```Update&#8321;: I'm back in 218, just to disperse doubt... ;)
Update&#8322;: It is just as it is promissed by ling given in #46... ;) Nice...

---

### Post by Cavsfan on 2014-12-14
> **zika said:**
> We've got ourselves 218 today... ;)
```
Get:1 http://archive.ubuntu.com/ubuntu/ vivid-proposed/universe systemd-sysv amd64 218-1ubuntu1 [8520 B]
Get:2 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main udev amd64 218-1ubuntu1 [898 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libudev1 amd64 218-1ubuntu1 [34,7 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libpam-systemd amd64 218-1ubuntu1 [106 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main systemd amd64 218-1ubuntu1 [3062 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd0 amd64 218-1ubuntu1 [71,7 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libgudev-1.0-0 amd64 1:218-1ubuntu1 [14,4 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-daemon0 amd64 218-1ubuntu1 [16,1 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-journal0 amd64 218-1ubuntu1 [57,1 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ vivid-proposed/main libsystemd-login0 amd64 218-1ubuntu1 [27,2 kB]
```Update&#8321;: I'm back in 218, just to disperse doubt... ;)
Update&#8322;: It is just as it is promissed by ling given in #46... ;) Nice...

It's not made it to this side of the planet yet. :p
I just checked -- twice. I guess tomorrow it shall be. ;)

---

### Post by Cavsfan on 2014-12-15
Still not here yet. :shock:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy libsystemd-login0 
libsystemd-login0:
  Installed: 217-3ubuntu1
  Candidate: 217-3ubuntu1
  Version table:
 *** 217-3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

I don't get it. Maybe later on today? I opened up proposed and did not see it in there either.

---

### Post by Mateusz Stachowski on 2014-12-15
> **Cavsfan said:**
> I don't get it. Maybe later on today? I opened up proposed and did not see it in there either.

The 218 is still in proposed.

[http://packages.ubuntu.com/vivid/systemd](http://packages.ubuntu.com/vivid/systemd)

---

### Post by Cavsfan on 2014-12-15
> **Cavsfan said:**
> Still not here yet. :shock:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy libsystemd-login0 
libsystemd-login0:
  Installed: 217-3ubuntu1
  Candidate: 217-3ubuntu1
  Version table:
 *** 217-3ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

I don't get it. Maybe later on today? I opened up proposed and did not see it in there either.

> **Mateusz Stachowski said:**
> The 218 is still in proposed.

[http://packages.ubuntu.com/vivid/systemd](http://packages.ubuntu.com/vivid/systemd)

Thanks but is there any reason that page has 217-3ubuntu1 on it and why when I enabled proposed and did sudo apt-get update && sudo apt-get upgrade I did not see anything with systemd in the name in the list of things to be installed? I didn't install them. I disabled proposed.

---

### Post by zika on 2014-12-15
[http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages.gz)
(search for 218-1)

---

### Post by Elfy on 2014-12-15
> **Cavsfan said:**
> Thanks but is there any reason that page has 217-3ubuntu1 on it and why when I enabled proposed and did sudo apt-get update && sudo apt-get upgrade I did not see anything with systemd in the name in the list of things to be installed? I didn't install them. I disabled proposed.

Perhaps your mirror is behind. 

The 218 version is available here - but I use Main Server.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Cavsfan on 2014-12-15
> **zika said:**
> [http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/main/binary-amd64/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/vivid-proposed/universe/binary-amd64/Packages.gz)
(search for 218-1)

*sheesh* I looked all of those up and then enabled proposed and they are all magically there. :o

> **Elfy said:**
> Perhaps your mirror is behind. 

The 218 version is available here - but I use Main Server.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

I use the main server for the US too. One time ventrical or mc4man some how sensed that a problem I had was caused by a mirror and they were spot on. So, I've used the main servers no matter how slow ever since. 
What is the deal on a developmental system that most of the time the updates are very slow through the terminal method? Not enough dedicated servers until the release point?
Thanks for that link I bookmarked it.

```
The following packages have been kept back:
  cpp-4.9 g++-4.9 gcc-4.9 gcc-4.9-base gnome-backgrounds gnome-shell-extensions lib32gcc1 libasan1 libatomic1 libcilkrts5 libcloog-isl4 libgcc-4.9-dev libgcc1 libgomp1 libitm1 liblsan0 libquadmath0
  libstdc++-4.9-dev libstdc++6 libtsan0 libubsan0
The following packages will be upgraded:
  apport apport-gtk dbus dbus-x11 gir1.2-gudev-1.0 gnome-session-canberra gnome-system-monitor libaacs0 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcanberra0 libcrystalhd3 libdbus-1-3 libgudev-1.0-0 libpam-systemd libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libsystemd0 libtbb2 libudev1 python-wxversion python3-apport
  python3-problem-report syslinux syslinux-common systemd ubuntu-drivers-common udev
32 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 6,799 kB of archives.
After this operation, 1,310 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

So, what do I do now just bite the bullet and take the updates? What could go wrong? :p
Or should I just wait until they hit the regular repos? Is that what you are saying          Elfy, they are in the regular repos where you are?
Thanks!

---

### Post by Cavsfan on 2014-12-19
Made the jump after installing an Alpha 1 ISO yesterday. I don't know why system monitor shows upstart is running when it's not even installed.
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                                 218-2ubuntu3                               amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                             218-2ubuntu3                               amd64        systemd utility library (deprecated)
ii  libsystemd-login0:amd64                              218-2ubuntu3                               amd64        systemd login utility library (deprecated)
ii  libsystemd0:amd64                                    218-2ubuntu3                               amd64        systemd utility library
ii  systemd                                              218-2ubuntu3                               amd64        system and service manager
ii  systemd-shim                                         9-1                                        amd64        shim for systemd
ii  systemd-sysv                                         218-2ubuntu3                               amd64        system and service manager - SysV links
```

This Alpha is greatly improved and lots of things are much different. Still not up to speed been on it less than 24 hours.
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.174s (kernel) + 13.165s (userspace) = 17.339s
```

This is an old machine but that is faster than it's ever been.

---

### Post by fjgaude on 2014-12-20
Same Intel computer, see signature!

After release of 14.10:
frank@flash:~$ sudo systemd-analyze
 Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s

After update for 15.04, Alpha 1:
 Startup finished in 894ms (kernel) + 5.712s (userspace) = 6.606s

---

### Post by rrnbtter on 2014-12-20
Greetings,

> **Cavsfan said:**
> I don't know why system monitor shows upstart is running when it's not even installed.

Ubuntu currently uses both Systemd and Upstart when Systemd is default. Systemd "farms off" still unsupported tasks to Upstart, since Systemd is still in development for Ubuntu (it is not fully implemented.

Run Top in a terminal. If Systemd is pid1 then you are defaulting to Systemd and it doesn't matter if the Upstart and Sysvinit utilitys are present. 

Anyway, welcome to the Systemd club, your feed back has been helpful and appreciated (at least by myself).

---

### Post by Cavsfan on 2014-12-20
> **rrnbtter said:**
> Greetings,

[QUOTE=Cavsfan;13190462]I don't know why system monitor shows upstart is running when it's not even installed.

Ubuntu currently uses both Systemd and Upstart when Systemd is default. Systemd "farms off" still unsupported tasks to Upstart, since Systemd is still in development for Ubuntu (it is not fully implemented.

Run Top in a terminal. If Systemd is pid1 then you are defaulting to Systemd and it doesn't matter if the Upstart and Sysvinit utilitys are present. 

Anyway, welcome to the Systemd club, your feed back has been helpful and appreciated (at least by myself).[/QUOTE]

Thanks for that explanation! :) Yes, I've  got VinDSL's conky running at all times (it's a basic necessity :) ) and it shows the top 10 processes.
The bottom one was init PID 1 always when booting with upstart. Now the bottom process is sytemd PID 1. 
It was when I used the init= in the bootline and now since I installed systemd-sysv and dropped the init= from the bootline it forever will be I reckon. 

Also thanks for that command top! Another tool in the arsenal. I like how that works and yes it is PID 1 there as well of course.

(On a side note gedit is very unstable now. I installed leafpad and it is much better. I wish I could make leafpad the default text editor but I'm not seeing that as an option.)

Thanks

---

### Post by zika on 2014-12-21
> **Cavsfan said:**
> I wish I could make leafpad the default text editor but I'm not seeing that as an option.Edit /usr/share/applications/defaults.list or create [~/.local/share/applications/mimeapps.list ]("https://wiki.archlinux.org/index.php/default_applications")or```
man mimeopen
```

---

### Post by rrnbtter on 2014-12-21
Greetings,

> **Cavsfan said:**
>  I wish I could make leafpad the default text editor but I'm not seeing that as an option.)


Open Nautilus, Right Click on the text file of your choice and choose Properties, Click on the "Open With" tab, choose "Leafpad", Click on "Set as default". Done!

PS, Incedentally, I don't think Gedit has a behavior problem. The problem is with gksudo, discussed elsewhere in this section. It's worth a read since that problem may also effect Leafpad when run as graphic.

---

### Post by Cavsfan on 2014-12-21
> **Cavsfan said:**
> I wish I could make leafpad the default text editor but I'm not seeing that as an option.
> **zika said:**
> Edit /usr/share/applications/defaults.list or create [~/.local/share/applications/mimeapps.list ]("https://wiki.archlinux.org/index.php/default_applications")or```
man mimeopen
```

Thanks zika but rrnbtter's method was much easier.

> **rrnbtter said:**
> Greetings,

[QUOTE=Cavsfan;13191084]I wish I could make leafpad the default text editor but I'm not seeing that as an option.

Open Nautilus, Right Click on the text file of your choice and choose Properties, Click on the "Open With" tab, choose "Leafpad", Click on "Set as default". Done!

PS, Incedentally, I don't think Gedit has a behavior problem. The problem is with gksudo, discussed elsewhere in this section. It's worth a read since that problem may also effect Leafpad when run as graphic.[/QUOTE]

No it really is gedit. I just open it up without sudo and it will not display the line numbers even if it's set to do so. Also the mouse is invisible when hovering over the text. It's kind of hard to manage or even use.
This is has just been since I installed the alpha1 iso.

---

### Post by zika on 2014-12-21
> **Cavsfan said:**
> Thanks zika but rrnbtter's method was much easier.suum cuique
> **Cavsfan said:**
> No it really is gedit. I just open it up without sudo and it will not display the line numbers even if it's set to do so. Also the mouse is invisible when hovering over the text. It's kind of hard to manage or even use.
This is has just been since I installed the alpha1 iso.Gedit with sudo? Again? [img]http://www.sherv.net/cm/emoticons/no/animated-no-smiley-emoticon.gif[/img]

---

### Post by Cavsfan on 2014-12-21
> **Cavsfan said:**
> Thanks zika but rrnbtter's method was much easier.

> **zika said:**
> suum cuique

quicquid

Actually I was trying to use pkexec but it's just as bad or worse than sudo. ;)
```
cavsfan@cavsfan-MS-7529:~$ pkx gedit /etc/fstab

(gedit:12152): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:12152): GLib-GObject-WARNING **: The property GtkToolButton:stock-id is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:12152): GLib-GObject-WARNING **: The property GtkWidget:margin-right is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:12152): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:12152): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

However using leafpad did not give any errors at all (this time):
```
cavsfan@cavsfan-MS-7529:~$ pkx leafpad /etc/fstab
cavsfan@cavsfan-MS-7529:~$ 
```

But, at this time many things are finicky and change constantly on 15.04. At least for me they are.

---

### Post by rrnbtter on 2014-12-21
Greetings,
@cavsfan; I still wouldn't put it on Gedit. Mine is working fine but I have been getting graphics rendering problems all over the map. I even had a Drop Menu problem in Firefox for a few days. I am still getting it at various times on different programs even running the 3.19RC1 kernel. I think this will get fixed in a few days. Mean time good to hear you have Leafpad working. Regarding the sudo thing, many of us are using sudo -H in place of gksudo.

---

### Post by Cavsfan on 2014-12-21
> **rrnbtter said:**
> Greetings,
@cavsfan; I still wouldn't put it on Gedit. Mine is working fine but I have been getting graphics rendering problems all over the map. I even had a Drop Menu problem in Firefox for a few days. I am still getting it at various times on different programs even running the 3.19RC1 kernel. I think this will get fixed in a few days. Mean time good to hear you have Leafpad working. Regarding the sudo thing, many of us are using sudo -H in place of gksudo.

My gedit got 100% worse when I installed the alpha Vivid ISO on the 18th. It's hardly manageable. I know that gksu is going away but they should find a suitable replacement before hand.
Pkexec does not (to me that is) look like it will be the replacement. I know it is still really early in the cycle and everything is very volatile at the moment it seems. 
Leafpad seems to be fairing the best. Here's what I just got with sudo -H: (no better than gksu or pkexec)
```
avsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/fstab
[sudo] password for cavsfan: 

(gedit:5345): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkToolButton:stock-id is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkWidget:margin-right is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

Like you say I guess we'll just have to be patient and wait...

---

### Post by mc4man on 2014-12-21
> **Cavsfan said:**
> My gedit got 100% worse when I installed the alpha Vivid ISO on the 18th. It's hardly manageable. I know that gksu is going away but they should find a suitable replacement before hand.
Pkexec does not (to me that is) look like it will be the replacement. I know it is still really early in the cycle and everything is very volatile at the moment it seems. 
Leafpad seems to be fairing the best. Here's what I just got with sudo -H: (no better than gksu or pkexec)
```
avsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/fstab
[sudo] password for cavsfan: 

(gedit:5345): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkToolButton:stock-id is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkWidget:margin-right is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

Like you say I guess we'll just have to be patient and wait...
The glib warning should go when a newer gedit is supplied, as far as the gtk warnings from a root gedit they have been & continue to be of no concern. Probably could be removed but Gnome dev's don't support root gui's so likely  they won't.  In that regard they then become meaningless.

---

### Post by muktupavels on 2014-12-21
@cavsfan: just forget about these warnings... how many time you have posted these here?

First three warnings are just "spam". GTK+ has deprecated many properties, these are only few. It will be removed only in GTK+ 4.x until then it is only warning.

You should not worry about last two warnings. Don't know why, but running with sudo gedit fails to find org.gnome.SessionManager service. That means if you edit file and will try logout then gedit will not able to inform SessionManager that you have unsaved work. But at least logout in indicator-applet (if using flashback session and probably in unity) does not care if you have some unsaved work and will logout you anyway if you confirm action. (If you use logout button on panel or user menu applet then then logout dialog will inform you about unsaved document in gedit if not run with sudo). Otherwise gedit should work just fine.

Yes, gedit has problems now, but it might be because it is not updated to 3.14.x, it is still on 3.10.4 version...

---

### Post by mc4man on 2014-12-21
line numbers are returned in gedit 3.14 (w/ newer libgtksourceview..) 
also those gtk warnings are gone in root or non root gedit but some new ones may appear, if use isn't affected then nothing to be concerned about
(- appears gedit will need some work to look right in an ubuntu session

---

### Post by Cavsfan on 2014-12-22
> **mc4man said:**
> [QUOTE=Cavsfan;13191643]My gedit got 100% worse when I installed the alpha Vivid ISO on the 18th. It's hardly manageable. I know that gksu is going away but they should find a suitable replacement before hand.
Pkexec does not (to me that is) look like it will be the replacement. I know it is still really early in the cycle and everything is very volatile at the moment it seems. 
Leafpad seems to be fairing the best. Here's what I just got with sudo -H: (no better than gksu or pkexec)
```
avsfan@cavsfan-MS-7529:~$ sudo -H gedit /etc/fstab
[sudo] password for cavsfan: 

(gedit:5345): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkToolButton:stock-id is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): GLib-GObject-WARNING **: The property GtkWidget:margin-right is deprecated and shouldn't be used anymore. It will be removed in a future version.

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:5345): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

Like you say I guess we'll just have to be patient and wait...

The glib warning should go when a newer gedit is supplied, as far as the gtk warnings from a root gedit they have been & continue to be of no concern. Probably could be removed but Gnome dev's don't support root gui's so likely  they won't.  In that regard they then become meaningless.[/QUOTE]

Thanks for that information! :) I won't worry about it. Gedit is bad for me right now. I'll wait on the next gedit to come down the pipes. 

> **albertsmuktupavels said:**
> @cavsfan: just forget about these warnings... _how many time you have posted these here?_
First three warnings are just "spam". GTK+ has deprecated many properties, these are only few. It will be removed only in GTK+ 4.x until then it is only warning.

You should not worry about last two warnings. Don't know why, but running with sudo gedit fails to find org.gnome.SessionManager service. That means if you edit file and will try logout then gedit will not able to inform SessionManager that you have unsaved work. But at least logout in indicator-applet (if using flashback session and probably in unity) does not care if you have some unsaved work and will logout you anyway if you confirm action. (If you use logout button on panel or user menu applet then then logout dialog will inform you about unsaved document in gedit if not run with sudo). Otherwise gedit should work just fine.

Yes, gedit has problems now, but it might be because it is not updated to 3.14.x, it is still on 3.10.4 version...

Excuse me? I can see they are warnings and I was not worried about them breaking my system. 
I really am not even close to being the first or only one that posts **gksudo gedit** error messages by any stretch of your imagination.
Plus seeing "_is deprecated and shouldn't be used anymore. It will be removed in a future version._" is a tad *disconcerting*.
I'm not sure I've seen that exact message before.
> **mc4man said:**
> line numbers are returned in gedit 3.14 (w/ newer libgtksourceview..) 
also those gtk warnings are gone in root or non root gedit but some new ones may appear, if use isn't affected then nothing to be concerned about
(- appears gedit will need some work to look right in an ubuntu session

Thanks! I'll just stop worrying about those warnings and let it go.

Sorry, I guess you can blame me for straying off of the thread topic of [SIZE=5]systemd[/SIZE].

---

### Post by Cavsfan on 2014-12-23
So... how is running only systemd working for everyone? 
The only changes I've noticed is at boot time I no longer see those messages with the green button (or whatever) beside them like when network manager was started up, etc.

---

### Post by harry332 on 2014-12-25
> **Cavsfan said:**
> So... how is running only systemd working for everyone? 
The only changes I've noticed is at boot time I no longer see those messages with the green button (or whatever) beside them like when network manager was started up, etc.

Systemd only is running fine here (with Gnome-shell DE and GDM).
But I would like to know how many of you actually have a Systemd-only setup.
Meaning - you have purged at least these:
 - systemd-shim
 - cgmanager + libcgmanager0
 - upstart
And you have systemd-sysv installed.

---

### Post by zika on 2014-12-25
> **harry332 said:**
> Systemd only is running fine here (with Gnome-shell DE and GDM).
But I would like to know how many of you actually have a Systemd-only setup.
Meaning - you have purged at least these:
- systemd-shim
- cgmanager + libcgmanager0
- upstart
And you have systemd-sysv installed.Beware:```
:~$ sudo apt-get purge -s systemd-shim Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-control-center gnome-control-center-data libcolord-gtk1
  libgoa-backend-1.0-1 libopts25 ntp
Suggested packages:
  ntp-doc
The following packages will be REMOVED:
  indicator-datetime* systemd-shim* ubuntu-desktop* unity-control-center* unity-control-center-signon* webaccounts-extension-common* xul-ext-webaccounts*
The following NEW packages will be installed:
  gnome-control-center gnome-control-center-data libcolord-gtk1
  libgoa-backend-1.0-1 libopts25 ntp
0 upgraded, 6 newly installed, 7 to remove and 0 not upgraded.
``````
:~$ sudo apt-get purge -s cgmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-control-center gnome-control-center-data libcolord-gtk1 libgoa-backend-1.0-1 libopts25 ntp
Suggested packages:
  ntp-doc
The following packages will be REMOVED:
  cgmanager* indicator-datetime* systemd-shim* ubuntu-desktop* unity-control-center* unity-control-center-signon* webaccounts-extension-common* xul-ext-webaccounts*
The following NEW packages will be installed:
  gnome-control-center gnome-control-center-data libcolord-gtk1 libgoa-backend-1.0-1 libopts25 ntp
0 upgraded, 6 newly installed, 8 to remove and 0 not upgraded.
``````
:~$ sudo apt-get purge -s upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'upstart' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``````
:~$ dpkg -l|grep sysv
ii  systemd-sysv                                         218-2ubuntu3                               amd64        system and service manager - SysV links
ii  sysv-rc                                              2.88dsf-53.2ubuntu3                        all          System-V-like runlevel change mechanism
ii  sysvinit-utils                                       2.88dsf-53.2ubuntu3                        amd64        System-V-like utilities
```

---

### Post by harry332 on 2014-12-25
Like I wrote, I have Gnome-shell DE with GDM.
I do not have Unity DE nor LightDM installed.
Removing systemd-shim and cgmanager will change unity-control-center to gnome-control-center.
Also the meta package ubuntu-desktop is removed.
This is only to say that Ubuntu does not yet fully support SystemD.

---

### Post by zika on 2014-12-25
> **harry332 said:**
> Like I wrote, I have Gnome-shell DE with GDM.
I do not have Unity DE nor LightDM installed.
Removing systemd-shim and cgmanager will change unity-control-center to gnome-control-center.
Also the meta package ubuntu-desktop is removed.
This is only to say that Ubuntu does not yet fully support SystemD.Like I wrote: just beware... ;)
I try to have things to coexist, most of the time I do succeed... ;)

---

### Post by rrnbtter on 2014-12-25
Greetings,

```
dpkg -l|grep sysv
ii  sysv-rc                                             2.88dsf-53.2ubuntu3                        all          System-V-like runlevel change mechanism
ii  sysvinit-utils                                      2.88dsf-53.2ubuntu3                        i386         System-V-like utilities
ii  upstart                                             1.13.2-0ubuntu5                            i386         event-based init daemon - sysv compat

```

The sysvinit-utils are running regardless of the boot condition. Installing systemd-sysv only eliminates the need for systemd-shim and the systemd boot line in /default/grub. This means that systemd is still dependent on upstart and the sysvinit-utils. In short don't go to far with this process unless you have a fully updated ISO available for reinstallation. This is a development section and Systemd is in a state of development. 
Currently I don't see the point of installing systemd-sysv in Unity desktop. Be careful people and be patient (if you are new at this)! Else, go for it!

---

### Post by zika on 2014-12-25
> **rrnbtter said:**
> Currently I don't see the point of installing systemd-sysv in Unity desktop.Would You care to elaborate on this?

---

### Post by rrnbtter on 2014-12-25
Greetings,
> **zika said:**
> Would You care to elaborate on this?

I say that "Currently I don't see the point of installing systemd-sysv in Unity desktop." because it removes the opportunity to remove the line in /etc/default/grub "init=/lib/systemd/systemd" that lets me get back to booting with upstart. Installing systemd-sysv will overwrite /sbin/init with a link to systemd. But sysvinit-utils is installed regardless of wrether systemd-sysv is installed or not. That is because Systemd is designed to be a drop-in for upstart and sysvinit and it needs the utils for backward compatibility.  It is my understanding that when Systemd is final and a user issues a upstart command the systemd will apply the command and also give the user a suggested Systemd replacement command (to help in transition). 

So if you look at your code from "dpkg -l|grep sysv" it shows that with systemd-sysv installed the sysvinit-utils is designated ii which means that it is necessary and also installed. 

In my same code without systemd-sysv installed you get the same result.  
The reason I said "for Unity Desktop" is because I don't test the other desktops and don't know what the result would be. 
Installing Systemd-sysv causes a direct boot into systemd where without it the  "init=/lib/systemd/systemd" directs a boot into systemd with systemd-shim. But the result is the same. One method results in a permenant systemd boot and the other a temporary (or optional) systemd boot. 
At this point I think Systemd is reliable but there could be a need (breakage) that may invoke the need to go back to upstart. So why at this point install systemd-sysv. 

At least that is my understanding of the situation.

---

### Post by harry332 on 2014-12-26
> **rrnbtter said:**
> Greetings,

I say that "Currently I don't see the point of installing systemd-sysv in Unity desktop." because it removes the opportunity to remove the line in /etc/default/grub "init=/lib/systemd/systemd" that lets me get back to booting with upstart.
...
Installing Systemd-sysv causes a direct boot into systemd where without it the  "init=/lib/systemd/systemd" directs a boot into systemd with systemd-shim.


Rrnbtter, could you please explain this clearly.
See I have a bit different setup than others do. I only have Gnome-shell DE installed.
I have purged upstart, systemd-shim and cgmanager.
I do use the kernel line init=/lib/systemd/systemd.
And if I remove it, my setup will not boot, but end into a kernel panic.

Sysvinit-utils must be installed with systemd-sysv, if one tries to remove it, systemd-sysv is removed and upstart and systemd-shim plus others are installed instead.

---

### Post by zika on 2014-12-26
> **harry332 said:**
> And if I remove it, my setup will not boot, but end into a kernel panic.Sorry for interfering, which version of kernel?
First though is about improper initramfs/initrd...

---

### Post by rrnbtter on 2014-12-26
Greetings,
> **harry332 said:**
> Rrnbtter, could you please explain this clearly.
See I have a bit different setup than others do. I only have Gnome-shell DE installed.
I have purged upstart, systemd-shim and cgmanager.
I do use the kernel line init=/lib/systemd/systemd.
And if I remove it, my setup will not boot, but end into a kernel panic.

Sysvinit-utils must be installed with systemd-sysv, if one tries to remove it, systemd-sysv is removed and upstart and systemd-shim plus others are installed instead.

As I have already stated, I am not prepared to discuss non Unity desktops. Also, I'm not trying to put myself out there as an expert. 
The point is that right now systemd in Ubuntu is intended to be used with the former utilities in place for the convenience of users that may not transition so easily. It is ok to install systemd-sysv and remove the boot line and boot directly into systemd if desired. 
However some are trying to take it further than Ubuntu currently intends it to be taken. In fact systemd is not ready for default and needs the backward compatibility to function itself. Therefore forcing a removal of upstart and sysvinit-utils will bork the system (in most cases). 

My cautionary note is that in this forum we try not to lead beginners off the cliff even though we have a right to go there ourselves.  Heck, there are users here that intentionally bork their system just for the experience or learning opportunity. I have already performed a full reinstall over this systemd thing and I wouldn't discourage others from doing the same thing. After all this is a testing section. I'm just saying that if you don't have the guts for it, be very carefull with removing stuff randomly. Ubuntu will get this all ready for primetime eventually.

---

### Post by rrnbtter on 2014-12-26
Greetings,
In simple form. Install "top", and run it in a terminal. If systemd is pid1 then you are running systemd. It doesn't matter if you get there with the bootline and systemd-shim or install systemd-sysv and remove the boot line. You only need systemd to be pid1. To continue to remove things after that is accomplished is called "testing".

---

### Post by harry332 on 2014-12-26
> **rrnbtter said:**
> Greetings,

As I have already stated, I am not prepared to discuss non Unity desktops. Also, I'm not trying to put myself out there as an expert. 
...
Therefore forcing a removal of upstart and sysvinit-utils will bork the system (in most cases). 
...


Well it is impossible to remove both upstart and sysvinit-utils. This way also systemd-sysv is removed and the setup is unbootable.
You see package systemd depends on sysv-rc, which in turn depends on sysvinit-utils.
To have a systemd boot, upstart and systemd-shim plus cgmanager can be removed.
Note, that I have nowhere stated that any beginner should try this.
I did this and my setup boots and functions well, right now without any bugs.
But my setup needs to have the kernel boot line.

---

### Post by harry332 on 2014-12-26
> **zika said:**
> Sorry for interfering, which version of kernel?
First though is about improper initramfs/initrd...

I have the official vivid kernel, I do not use any PPA's at the moment.
There is nothing wrong with my initramfs. It works well, on each boot.

---

### Post by zika on 2014-12-26
> **harry332 said:**
> ...And if I remove it, my setup will not boot, but end into a kernel panic...> **harry332 said:**
> There is nothing wrong with my initramfs. It works well, on each boot.I must have read it wrong...

---

### Post by Cavsfan on 2014-12-26
> **Cavsfan said:**
> So... how is running only systemd working for everyone? 
The only changes I've noticed is at boot time I no longer see those messages with the green button (or whatever) beside them like when network manager was started up, etc.

> **harry332 said:**
> Systemd only is running fine here (with Gnome-shell DE and GDM).
But I would like to know how many of you actually have a Systemd-only setup.
Meaning - you have purged at least these:
 - systemd-shim
 - cgmanager + libcgmanager0
 - upstart
And you have systemd-sysv installed.

I tried to purge systemd-shim and did not like what it would do...

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get remove systemd-shim
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  indicator-datetime systemd-shim ubuntu-desktop unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 6,131 kB disk space will be freed.
Do you want to continue? [Y/n] 

```

That is a no-go for me.

It does seem a little more stable now. I've been in it for hours at a time with no major catastrophes; except gedit is a mess until the next version comes through in updates I will continue to use leafpad.

---

### Post by Cavsfan on 2014-12-26
> **rrnbtter said:**
> Greetings,
In simple form. Install "top", and run it in a terminal. If systemd is pid1 then you are running systemd. It doesn't matter if you get there with the bootline and systemd-shim or install systemd-sysv and remove the boot line. You only need systemd to be pid1. To continue to remove things after that is accomplished is called "testing".

+1 

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l|grep sysv
ii  systemd-sysv                                         218-2ubuntu3                               amd64        system and service manager - SysV links
ii  sysv-rc                                              2.88dsf-53.2ubuntu3                        all          System-V-like runlevel change mechanism
ii  sysvinit-utils                                       2.88dsf-53.2ubuntu3                        amd64        System-V-like utilities
rc  upstart                                              1.13.2-0ubuntu5                            amd64        event-based init daemon - sysv compat

```

I've removed the bootline and PID 1 is systemd, upstart is not installed, so how can I not be running systemd?

---

### Post by rrnbtter on 2014-12-26
Greetings,

> **Cavsfan said:**
> 
I've removed the bootline and PID 1 is systemd, upstart is not installed, so how can I not be running systemd?

You (are) running systemd.  You removed Upstart but the upstart scripts are built into sysvinit-utils (for this conversion). Hence, sysvinti-utils was a dependency of Upstart. You don't need the Upstart manager because Systemd is doing that job. But you still need the util scripts for backward compatibility and what ever is yet unscripted in Systemd. This will probably work in 14.10 but there is a limit to how far back you can go with this. 

I am running systemd but I'm not going to purge anything at the moment. I'm running Systemd, Xmir, and Unity7 desktop and it is the best system I have ever owned and my computer is five years old. I'm not going to mess up a good thing by being impulsive and purging something that might be needed.

---

### Post by zika on 2014-12-26
@rrnbtter & others: This might come as a bit of dissapointment (to You) but I did a little test:
On the same install I've left upstart, then installed systemd-sysv and, finally, returned upstart. The boot was all the time completely the same. No additions or removals on kernel command line. Hence words: [COLOR=#000000][FONT=Ubuntu Mono]event-based init daemon - sysv compat

[/FONT][/COLOR]

---

### Post by rrnbtter on 2014-12-26
Greetings,
"[COLOR=#000000][FONT=Ubuntu Mono]event-based init daemon - sysv compat"
No, I'm not disappointed. That sounds right to me, although I don't think I could have got there [the exact terminoligy] with out you. So, thanks for the clarification.  
[/FONT][/COLOR]

---

### Post by zika on 2014-12-26
> **rrnbtter said:**
> Greetings,
"[COLOR=#000000][FONT=Ubuntu Mono]event-based init daemon - sysv compat"
No, I'm not disappointed. That sounds right to me, although I don't think I could have got there [the exact terminoligy] with out you. So, thanks for the clarification.  
[/FONT][/COLOR]**I am** disapointed: I did not know that user did put init= in kernel line and there is a difference... ;) I just saw that now checking grub file... I'll explore deeper when I get another chunk of free_time&will to test that on my machine.  Sorry for misinformation. UpStart still shows its head when installed... ;)

---

### Post by rrnbtter on 2014-12-26
Greetings,
"UpStart still shows its head when installed." 
No question about that. My point in my posts is that as long as it isn't pid1 why bother to remove it or anything else. Sysvinit-utils has the scripts for compatibility. [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Cavsfan on 2014-12-26
> **rrnbtter said:**
> Greetings,
"[COLOR=#000000][FONT=Ubuntu Mono]event-based init daemon - sysv compat"
No, I'm not disappointed. That sounds right to me, although I don't think I could have got there [the exact terminoligy] with out you. So, thanks for the clarification.  
[/FONT][/COLOR]

> **zika said:**
> **I am** disapointed: I did not know that user did put init= in kernel line and there is a difference... ;) I just saw that now checking grub file... I'll explore deeper when I get another chunk of free_time&will to test that on my machine.  Sorry for misinformation. UpStart still shows its head when installed... ;)

I hope you're not referring to me. I have no "init=" line on  my boot line any more since installing systemd-sysv. You said I didn't need it so I took it off.
Remember I have custom grub from my signature. Cool grub picture of my choice, font colors for top, bottom and menu as well as highlighted line.

Here is my boot line which works perfectly fine and boots with systemd:
```
menuentry "Vivid Vervet 15.04 (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
```

Here is a picture of my grub menu on Vivid. ;)

[[IMG]http://en.zimagez.com/miniature/20141226135835.jpg[/IMG]]("http://en.zimagez.com/zimage/20141226135835.php") 

These font colors: 		
```
		echo " set color_normal=light-green/black"
		echo " set menu_color_normal=yellow/black"
		echo " set menu_color_highlight=white/black"
```

---

### Post by zika on 2014-12-26
> **rrnbtter said:**
> No question about that. My point in my posts is that as long as it isn't pid1 why bother to remove it or anything else. Sysvinit-utils has the scripts for compatibility.I must admit that I did not understand what You pointed to here.
1. UpStart removed => SystemD is pid1
2. UpStart present   => /sbin/init is pid1
> **Cavsfan said:**
> I hope you're not referring to me.By no means, no. I even do not see where You could have found Yourself in that post of mine.

---

### Post by Cavsfan on 2014-12-26
> **rrnbtter said:**
> Greetings,
"UpStart still shows its head when installed." 
No question about that. My point in my posts is that as long as it isn't pid1 why bother to remove it or anything else. Sysvinit-utils has the scripts for compatibility. [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

I can verify that. I reinstalled and upstart was the default unless you use the "init=" addition to the boot line.
But after systemd-sysv is installed systemd boots and one should not use the "init=" line any more as zika stated earlier in this thread answering my question.

---

### Post by Cavsfan on 2014-12-26
> **Cavsfan said:**
> I hope you're not referring to me.

> **zika said:**
> By no means, no. I even do not see where You could have found Yourself in that post of mine.

Just a misunderstanding, you mentioned "the user". I just misunderstood. My apologies. :)

---

### Post by harry332 on 2014-12-27
> **Cavsfan said:**
> I can verify that. I reinstalled and upstart was the default unless you use the "init=" addition to the boot line.
But after systemd-sysv is installed systemd boots and one should not use the "init=" line any more as zika stated earlier in this thread answering my question.

Why are you saying one should not use the "init=" line any more?
What is wrong using it, even if systemd-sysv is installed?
It may very well be that most users do not have to use it, though.

Systemd does not work fully OK in every single setup right now.
For example, my setup needs that line. But I have removed more packages related to upstart than any other you fellows here.
Still, my initramfs is working fine. The problem is that my setup does not find the /lib/systemd/systemd file if I remove the kernel line.
Some month ago I had issues with booting and I made a bug report about it.
Martin Pitt also suspected my intramfs file back then, but could not find any errors in it.
At that time, the real issue was the gdm package from Gnome3 Staging PPA. I do not use that PPA (or any other) any more.
My setup has booted well ever since.

---

### Post by harry332 on 2014-12-27
> **zika said:**
> I must have read it wrong...

I do not know about that. You tell me.
My setup does not find /lib/systemd/systemd file if I remove that kernel line.
How does initramfs help with that then?

---

### Post by zika on 2014-12-27
> **harry332 said:**
> I do not know about that. You tell me.I just did... ;) ([SIZE=1]I know about Your setup only as much as I can deduce from Your writting. [COLOR=#696969]Hint: kernel panic[/COLOR]. Hence my shot in the dark or wild guess, call it as You wish.[/SIZE])
[SIZE=1]
Back to the topic of this thread:[/SIZE]
After some time in front of KB and after some reading and, of course, testing, I came to conclusion that Gnome (even before 3.14 but now especially) assumes SystemD.
After weeks of using SystemD going back to UpStart was a bit of a struggle. All the tools I welcomed at introduction of SystemD I really missed. Back to SystemD (even not complete as pointed here) and happy... ;)

---

### Post by Cavsfan on 2014-12-28
> **harry332 said:**
> Why are you saying one should not use the "init=" line any more?
What is wrong using it, even if systemd-sysv is installed?
It may very well be that most users do not have to use it, though.

Systemd does not work fully OK in every single setup right now.
For example, my setup needs that line. But I have removed more packages related to upstart than any other you fellows here.
Still, my initramfs is working fine. The problem is that my setup does not find the /lib/systemd/systemd file if I remove the kernel line.
Some month ago I had issues with booting and I made a bug report about it.
Martin Pitt also suspected my intramfs file back then, but could not find any errors in it.
At that time, the real issue was the gdm package from Gnome3 Staging PPA. I do not use that PPA (or any other) any more.
My setup has booted well ever since.

> **harry332 said:**
> I do not know about that. You tell me.
My setup does not find /lib/systemd/systemd file if I remove that kernel line.
How does initramfs help with that then?

All I know is when I installed the Alpha1 ISO on 12/18 or 19th when it  booted, at the top it displayed "starting version 218" but PID 1 was init  so it was booting with upstart.
But something in systemd was starting up I don't know what.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd
systemd:
  Installed: 218-2ubuntu3
  Candidate: 218-2ubuntu3
```

I then installed systemd-sysv and removed the init= part from my bootline as you can see in post [_#101_]("http://ubuntuforums.org/showthread.php?t=2249915&page=11&p=13194824#post13194824").
Which is the same boot line I use for Precise, Trusty and Mint 17 Rebecca as well. But PID 1 shows systemd and systemd-analyze works and I recall it doesn't if you are running upstart.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.187s (kernel) + 13.832s (userspace) = 18.020s. 
```

That's my 17 cents (adjusted for inflation). :p

---

### Post by harry332 on 2014-12-29
> **Cavsfan said:**
> All I know is when I installed the Alpha1 ISO on 12/18 or 19th when it  booted, at the top it displayed "starting version 218" but PID 1 was init  so it was booting with upstart.
But something in systemd was starting up I don't know what.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd
systemd:
  Installed: 218-2ubuntu3
  Candidate: 218-2ubuntu3
```

I then installed systemd-sysv and removed the init= part from my bootline as you can see in post [_#101_]("http://ubuntuforums.org/showthread.php?t=2249915&page=11&p=13194824#post13194824").
Which is the same boot line I use for Precise, Trusty and Mint 17 Rebecca as well. But PID 1 shows systemd and systemd-analyze works and I recall it doesn't if you are running upstart.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.187s (kernel) + 13.832s (userspace) = 18.020s. 
```

That's my 17 cents (adjusted for inflation). :p

That is also what should happen, so it is OK.
Installing systemd-sysv will overwrite /sbin/init with a link to systemd.
After that PID 1 is systemd.

However, at least on some cases the setup cannot find the new booting link /lib/systemd/systemd.
That is why those setups need to have the kernel "init=" line.
In your case (like in most cases) that is not necessary though.

Lastly, why doesn't it work on all cases.
Well, no one has been able to tell me that.

---

### Post by Cavsfan on 2014-12-29
The answer to that question is above my pay grade. :p

 My system is over 5 years old too. I have an Intel Quad core 2.83Ghz.

I did also notice that systemd-fsck does some sort of quick disk check or something at bootup. 

That's about all I know. I don't see a whole lot of difference between systemd and upstart so far at least.

Received an update to anacron that seems to be at least partly for systemd just a while ago.
```
anacron (2.3-23) unstable; urgency=medium

  * Team upload.
  * Add IgnoreSIGPIPE=false to anacron.service (Closes: #771393)
  * Add anacron-resume.service file to make sure anacron also runs at resume
    when running under systemd (Closes: #744753)

 -- Ivo De Decker <ivodd@debian.org>  Sun, 28 Dec 2014 20:14:44 +0100
```

---

### Post by zika on 2014-12-29
> **Cavsfan said:**
> I did also notice that systemd-fsck does some sort of quick disk check or something at bootup.Only if Your passno for that partition in /etc/fstab iz not equal to 0.

---

### Post by Cavsfan on 2014-12-29
> **Cavsfan said:**
> 
I did also notice that systemd-fsck does some sort of quick disk check or something at bootup. 

> **zika said:**
> Only if Your passno for that partition in /etc/fstab iz not equal to 0.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=bef4bb7d-6065-45ff-ab83-aac86a26c859 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=e14dc02e-6ea8-4c95-b4d0-9dc04d32294d none            swap    sw              0       0
```

Orly? Is that a 1 I see there? You tell me. It's the same on every Linux partition and I haven't edited fstabs in quite a long time.

On a side note: I thought we'd have breakage by now but, none I've seen yet as long as proposed is not enabled. That will getcha into trublez...

---

### Post by Cavsfan on 2014-12-29
I see from here that that 1 (the 6th item in that line in fstab) does cause it to check the disk. But, it goes by so fast that's it's not worth changing or worrying about.

[http://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](http://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)

&#1085;&#1080;&#1112;&#1077; &#1073;&#1080;&#1090;&#1085;&#1086;

---

### Post by zika on 2014-12-30
> **Cavsfan said:**
> &#1085;&#1080;&#1112;&#1077; &#1073;&#1080;&#1090;&#1085;&#1086;&#1055;&#1072;, &#1080; &#1085;&#1080;&#1112;&#1077;... ;)

To translate, for the sake of others:> **Cavsfan said:**
> It does not matterWell, it does not indeed... ;)

---

### Post by MAFoElffen on 2015-01-04
Is this just something not there yet?
```

mafoelffen@vivid01:~$ systemctl list-units --type service --all | grep not-found
&#9679; auditd.service                                                                            not-found inactive dead    auditd.service
&#9679; console-screen.service                                                                    not-found inactive dead    console-screen.service
&#9679; display-manager.service                                                                   not-found inactive dead    display-manager.service
&#9679; kbd.service                                                                               not-found inactive dead    kbd.service
&#9679; lvm2-activation.service                                                                   not-found inactive dead    lvm2-activation.service
&#9679; mdadm-raid.service                                                                        not-found inactive dead    mdadm-raid.service
&#9679; multipath-tools-boot.service                                                              not-found inactive dead    multipath-tools-boot.service
&#9679; systemd-sysusers.service                                                                  not-found inactive dead    systemd-sysusers.service
&#9679; systemd-udev-hwdb-update.service                                                          not-found inactive dead    systemd-udev-hwdb-update.service

```

---

### Post by Cavsfan on 2015-01-05
> **MAFoElffen said:**
> Is this just something not there yet?
```

mafoelffen@vivid01:~$ systemctl list-units --type service --all | grep not-found
&#9679; auditd.service                                                                            not-found inactive dead    auditd.service
&#9679; console-screen.service                                                                    not-found inactive dead    console-screen.service
&#9679; display-manager.service                                                                   not-found inactive dead    display-manager.service
&#9679; kbd.service                                                                               not-found inactive dead    kbd.service
&#9679; lvm2-activation.service                                                                   not-found inactive dead    lvm2-activation.service
&#9679; mdadm-raid.service                                                                        not-found inactive dead    mdadm-raid.service
&#9679; multipath-tools-boot.service                                                              not-found inactive dead    multipath-tools-boot.service
&#9679; systemd-sysusers.service                                                                  not-found inactive dead    systemd-sysusers.service
&#9679; systemd-udev-hwdb-update.service                                                          not-found inactive dead    systemd-udev-hwdb-update.service

```

I've got the same and am running systemd exclusively so I don't think so. But, then I'm far from being an expert. :)

```
cavsfan@cavsfan-MS-7529:~$ systemctl list-units --type service --all | grep not-found
&#9679; auditd.service                        not-found inactive dead    auditd.service
&#9679; avahi.service                         not-found inactive dead    avahi.service
&#9679; console-screen.service                not-found inactive dead    console-screen.service
&#9679; festival.service                      not-found inactive dead    festival.service
&#9679; kbd.service                           not-found inactive dead    kbd.service
&#9679; mdadm-raid.service                    not-found inactive dead    mdadm-raid.service
&#9679; multipath-tools-boot.service          not-found inactive dead    multipath-tools-boot.service
&#9679; systemd-sysusers.service              not-found inactive dead    systemd-sysusers.service
&#9679; systemd-udev-hwdb-update.service      not-found inactive dead    systemd-udev-hwdb-update.service

```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                                 218-3ubuntu1                                amd64        system and service manager - PAM  module
ii  libsystemd-daemon0:amd64                             218-3ubuntu1                                amd64        systemd utility library  (deprecated)
ii  libsystemd-login0:amd64                              218-3ubuntu1                                amd64        systemd login utility library  (deprecated)
ii  libsystemd0:amd64                                    218-3ubuntu1                                amd64        systemd utility library
ii  systemd                                              218-3ubuntu1                                amd64        system and service manager
ii  systemd-shim                                         9-1                                         amd64        shim for systemd
ii  systemd-sysv                                         218-3ubuntu1                                amd64        system and service manager -  SysV links

```

---

### Post by MAFoElffen on 2015-01-05
Okay... so I'm playing with sstemd spawned containers...

Running instances of jobs runs, finsishes and terminates fine from CLI and scripts, no problems there.

If I use systemd-nspawn and boot it, it runs and is fine. (See top of attached, note: container is a debian-tree template)

If I try to start as a systemd service..
```

mafoelffen@vivid01:~$ sudo systemctl start systemd-nspawn@debain.service
Job for systemd-nspawn@debain.service failed. See "systemctl status systemd-nspawn@debain.service" and "journalctl -xe" for details.
mafoelffen@vivid01:~$ sudo systemctl status systemd-nspawn@debian.service
&#9679; systemd-nspawn@debian.service - Container debian
   Loaded: loaded (/lib/systemd/system/systemd-nspawn@.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-nspawn(1)

```.
But the journal -xe does not give any hints on the why it's failing... not sure on that one...

EDIT-- Nevermind. Not sure what happened. Recalled the same commands from the command buffer (no change or edits to) and all of a sudden it is all working fine!?! (second attachment)

---

### Post by zika on 2015-01-06
[http://ubuntuforums.org/showthread.php?t=2259716](http://ubuntuforums.org/showthread.php?t=2259716)

---

### Post by zika on 2015-01-06
> **MAFoElffen said:**
> Okay... so I'm playing with sstemd spawned containers...

Running instances of jobs runs, finsishes and terminates fine from CLI and scripts, no problems there.

If I use systemd-nspawn and boot it, it runs and is fine. (See top of attached, note: container is a debian-tree template)

If I try to start as a systemd service..
```

mafoelffen@vivid01:~$ sudo systemctl start systemd-nspawn@debain.service
Job for systemd-nspawn@debain.service failed. See "systemctl status systemd-nspawn@debain.service" and "journalctl -xe" for details.
mafoelffen@vivid01:~$ sudo systemctl status systemd-nspawn@debian.service
&#9679; systemd-nspawn@debian.service - Container debian
   Loaded: loaded (/lib/systemd/system/systemd-nspawn@.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-nspawn(1)

```.
But the journal -xe does not give any hints on the why it's failing... not sure on that one...

EDIT-- Nevermind. Not sure what happened. Recalled the same commands from the command buffer (no change or edits to) and all of a sudden it is all working fine!?! (second attachment)Yo've made me interested, as soon as I do get some spare time I'll look into that. Nice. Thank You for the push.

---

### Post by MAFoElffen on 2015-01-06
I got a chance (funded) to go back to school to document my skills. The school I'm currently going to doesn't give credit for past experience. I initially laughed when they told me I had to take "Intro to Linux" for one of my degrees (UNIX since '88, Solaris support since 2005, Debian branched Linux support since 2008...). While others were learning the basic's and how to do basic installs, I got to drill down into through the system, configs and such. There is so much there in that I really like. systemd opens up a whole lot more that just faster boots. 

I didn't think I would learn much and they let me take it as Independent Study. It was all commandline rhel, CentOS and Fedora. I was not surprized by the commandline, but I got my teeth into systemd and I took an interest into systemd. I saw possibilities there and was hoping Ubuntu would get more into it. Been following Lennart Poettering's (Red Hat Server) Blog on "systemd for Administrators Series." 

But if you are interested, this is probably the most comprehensive collection of resources that I've found to learn about and play with systemd and it's related utilties:
[http://www.freedesktop.org/wiki/Software/systemd/](http://www.freedesktop.org/wiki/Software/systemd/) (Mostly links to other resources)

I think my first favorite feature was implementing journalctl logging... and being able to read human friendly versions of syslogs... Next is t see things differently by redistributing and reorganizing things as services and such. Definitely gave me a different perspective of what might be possible..

---

### Post by zika on 2015-01-07
Much obliged for a nice resource...
I've seen it before but now I've bookmarked it.
I do like SystemD very much, as I've already wrote not once.
It is nice to go back to school. I'm too old for that but I do make my desk(top) a nice place to pretend I'm in school again... ;)

---

### Post by ivo-welch on 2015-03-02
I looked at the alpha 2 weeks ago, and it did not have systemd as its default boot system.  is there a plan to switch to systemd by default in 15.04?

my other systems are arch, and it would be nice to rely on the same configurations...

---

### Post by coffeecat on 2015-03-02
*Thread moved to **Ubuntu Development Version**.*

---

### Post by dino99 on 2015-03-02
> **ivo-welch said:**
> I looked at the alpha 2 weeks ago, and it did not have systemd as its default boot system.  is there a plan to switch to systemd by default in 15.04?

my other systems are arch, and it would be nice to rely on the same configurations...

15.04 will continue to set upstart as its default. But users have the choice to test/use systemd by installing systemd-sysv . If installed, then the 'advanced' grub boot menu let you choose upstart/systemd, systemd in that case is the default setting.
Myself am using systemd-sysv as the default boot setting, and i've found it better than upstart.

---

### Post by grahammechanical on 2015-03-02
New installs of vivid get that Advanced option systemd option and even my long standing install of vivid has been upgraded to an Advanced option to launch under systemd. Every new kernel installed on vivid gets that advanced option. No user interaction on my part.

If, at the last Ubuntu Online summit it was not decided to make systemd the default for 15.04 then it will not be the default. I heard two promises about systemd. 1) Ubuntu will switch to systemd; 2) The switch will be transparent to the user. I do not know of any promises about time scale. It would be irresponsible for Canonical to switch to systemd without first testing all use cases of Ubuntu and that must include the server edition.

The switch to making systemd the default with upstart as an advanced option may come during the development period of 15.10 or even 16.04. But I cannot see it happening for 15.04. The 19th February was Vivid feature freeze.

Regards.

---

### Post by sammiev on 2015-03-02
I haven't tried ubuntu-gnome on upstart for a while now as I had to switch to systemd because of an loading problem with upstart. Systemd has been work very well so far.

---

### Post by ivo-welch on 2015-03-02
good.  so, am I guessing right that grub then sets an environment variable that induces the loader to invoke systemd instead of /sbin/init (which presumably is upstart)?  and, once running, the standard systemd hierarchies apply.  good.

I was a bit concerned that running a beta version together with a non-common config could screw things up.  but if this is reasonably solid, then systemd, here I come!  ( ;-).  I am using the gnome flavor, which seems to like systemd. )

and, the time will come, perhaps even before I am dead, when the distribution default will switch from BIOS to EFI !  then I will have a modern boot chain.

/iaw

---

### Post by dino99 on 2015-03-03
[COLOR="#FF0000"]Ready to switch on Vivid[/COLOR]

As per [https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration](https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration) we aimed for switching the system (not session) init from upstart to systemd this cycle. 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654)

---

### Post by ventrical on 2015-03-03
> **9d9 said:**
> [COLOR=#FF0000]Ready to switch on Vivid[/COLOR]

As per [https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration](https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration) we aimed for switching the system (not session) init from upstart to systemd this cycle. 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654)

But they have left open that it is really for wider testing and if there is too much breakage they will switch back before release .. and still much more approval has to come down the pipe from others .. so it's not written in stone just yet.

Regards..

---

### Post by ventrical on 2015-03-03
> **grahammechanical said:**
> New installs of vivid get that Advanced option systemd option and even my long standing install of vivid has been upgraded to an Advanced option to launch under systemd. Every new kernel installed on vivid gets that advanced option. No user interaction on my part.

If, at the last Ubuntu Online summit it was not decided to make systemd the default for 15.04 then it will not be the default. I heard two promises about systemd. 1) Ubuntu will switch to systemd; 2) The switch will be transparent to the user. I do not know of any promises about time scale. It would be irresponsible for Canonical to switch to systemd without first testing all use cases of Ubuntu and that must include the server edition.

The switch to making systemd the default with upstart as an advanced option may come during the development period of 15.10 or even 16.04. But I cannot see it happening for 15.04. The 19th February was Vivid feature freeze.

Regards.

They have it on the front stove top as a confirm for the remainder of this cycle. It's not exactly cooked yet and they are leaving some leeway open to switch-back before final release. I think they should leave it be and just leave systemd in advanced options for now.

---

### Post by sudodus on 2015-03-03
I'm getting systemd in a dist-upgrade right now with Lubuntu Vivid. I tried it some time ago in an iso file with the new Ubuntu interface (but I don't know where to look for differences, except that boot options must sometimes be entered twice).

---

### Post by dino99 on 2015-03-03
> **sudodus said:**
> I'm getting systemd in a dist-upgrade right now with Lubuntu Vivid. I tried it some time ago in an iso file with the new Ubuntu interface (but I don't know where to look for differences, except that boot options must sometimes be entered twice).

boot options was needed, but not now (aka: init=/etc/systemd/systemd) since latest used systemd-sysv

---

### Post by Cavsfan on 2015-03-03
> **sudodus said:**
> I'm getting systemd in a dist-upgrade right now with Lubuntu Vivid. I tried it some time ago in an iso file with the new Ubuntu interface (but I don't know where to look for differences, except that boot options must sometimes be entered twice).

> **9d9 said:**
> boot options was needed, but not now (aka: init=/etc/systemd/systemd) since latest used systemd-sysv

Right and no need for a boot option entry to get upstart either once you've installed systemd-sysv. Advanced options in grub should do that.

If you want to see that just enter **sudo grub-mkconfig > <text file name>** then look in what every you named it between where 10_linux starts and ends.

FWIW [http://ubuntuforums.org/showthread.php?t=2076205&page=27&p=13208995#post13208995](http://ubuntuforums.org/showthread.php?t=2076205&page=27&p=13208995#post13208995)

---

### Post by Elfy on 2015-03-04
Reading what I see - looks like they just need to catch up with the Lubuntu lead and they'll be switching over.

---

### Post by rrnbtter on 2015-03-04
Greetings,
I personally appreciate the way Ubuntu is handling this conversion. Since quite a few applications are still not systemd compatible,  Ubuntu is wrapping the upstart scripts into sysvinit and systemd just farms the job out to sysvinit to resolve the incompatability when it occurs. This should keep some popular but not well maintained apps from being deprecated. Because quite a few of those apps are not maintained at all I personally don't think this process will change when systemd goes default (at least for a couple of years). But the OP question is kind of like the one about wrether or not Ubuntu will go over 700meg limit on their install disk.

---

### Post by raptir on 2015-03-04
> **rrnbtter said:**
> Greetings,
I personally appreciate the way Ubuntu is handling this conversion. Since quite a few applications are still not systemd compatible,  Ubuntu is wrapping the upstart scripts into sysvinit and systemd just farms the job out to sysvinit to resolve the incompatability when it occurs. This should keep some popular but not well maintained apps from being deprecated. Because quite a few of those apps are not maintained at all I personally don't think this process will change when systemd goes default (at least for a couple of years). But the OP question is kind of like the one about wrether or not Ubuntu will go over 700meg limit on their install disk.

Even Fedora, which has spearheaded the conversion to systemd, provides sysvinit compatibility four years after they made the switch. I doubt it will be fully removed any time soon.

---

### Post by Elfy on 2015-03-05
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html)

thanks for that - now there'll be no umming and aahing :)

---

### Post by bapoumba on 2015-03-05
> **Elfy said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html)

thanks for that - now there'll be no umming and aahing :)

Umm, aah.

---

### Post by Elfy on 2015-03-05
bad bad admins :p

---

### Post by zika on 2015-03-05
It must be said: Ubuntu developers & others contributing to our delight have gone a great path from the time I've started using and learning Ubuntu-way of living. This SystemD transition proves to be the most comfortable journey and quite a success.. Congratulation to everybody that participated in this move. Not to forget that whole Vivid U+1 trip was the best so far... ;) Ubuntu has matured as a respectable young man... ;)

---

### Post by zika on 2015-03-05
> **Elfy said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html)thanks for that - now there'll be no umming and aahing :)> **bapoumba said:**
> Umm, aah.> **Elfy said:**
> bad bad admins :p[img]http://clipart.coolclips.com/AGifm/tf05192/CoolClips_wb022569.gif[/img][img]http://clipart.coolclips.com/AGifm/tf05192/CoolClips_wb022507.gif[/img]

---

### Post by bapoumba on 2015-03-05
Sorry everyone, I could not resist :)

---

### Post by zika on 2015-03-05
> **bapoumba said:**
> Sorry everyone, I could not resist :)[img]http://dir.coolclips.com/People/Body_Parts/Hands/Hands_Working/business_CoolClips_busi0940.jpg[/img]

---

### Post by sudodus on 2015-03-05
> **bapoumba said:**
> Sorry everyone, I could not resist :)

After all, you *are* Bap umm b aah :-D

---

### Post by bapoumba on 2015-03-05
> **sudodus said:**
> After all, you *are* Bap umm b aah :-D
aah, umm :D

---

### Post by sammiev on 2015-03-05
Been really no big issues running systemd here, not expecting any next Monday.

---

### Post by Elfy on 2015-03-05
> **sammiev said:**
> Been really no big issues running systemd here, not expecting any next Monday.

Same, been using it more or less all the time for almost 2 cycles. Was a bit off and on last one to be sure here.

---

### Post by ventrical on 2015-03-05
> **bapoumba said:**
> aah, umm :D

Any relation to Poumba from the Lion King? :)lol

---

### Post by sammiev on 2015-03-05
> **ventrical said:**
> Any relation to Poumba from the Lion King? :)lol

LOL

sammiev <--- zips mouth now

---

### Post by Cavsfan on 2015-03-05
You guys crack me up!  :lol: :lol: :lol:  I'm indeed also glad to see this happening. 
I too have been running systemd exclusively. Thanks zika for pointing out to install systemd-sysv. Although I guess that won't be necessary soon.

BTW I just installed Vivid Mate beta1 today. Had a couple rough patches like something called tilda keep getting in my way until I removed it from startup applications.

But it's looking pretty sweet! :)

---

### Post by sudodus on 2015-03-05
testing systemd now before and after upgrading to 3.19

---

### Post by sammiev on 2015-03-05
There are other OS that have been using systemd for a while with no upstart and no problems.

I have been using one for a while, expect to see the same results here. ;)

---

### Post by zika on 2015-03-07
```
[    9.354657] systemd[1]: Started Various fixups to make systemd work better on Debian.
```;)

---

### Post by lee295012-gmail on 2015-03-07
hope they can fix being able to turn the pc off.

---

### Post by bapoumba on 2015-03-07
> **ventrical said:**
> Any relation to Poumba from the Lion King? :)lol

> **sammiev said:**
> LOL

sammiev <--- zips mouth now
Nope, no relation. It is somewhere on the forums. My eldest son said that word showing an apple when he was starting to speak. In French, it sounds a little close. We laughed so much the word stayed in the family, then I chose it as username when I installed ubuntu from one of the first images that got out before it even had a name. I wanted a different userame for that distro. Kept it and started using it about everywhere ubuntu related :)

---

### Post by sudodus on 2015-03-07
That's a very nice history behind your username :-)

---

### Post by VinDSL on 2015-03-07
> **sammiev said:**
> Been really no big issues running systemd here, not expecting any next Monday.
Only prob I've had with systemd is...

About half the time, or more, my rig won't shutdown properly.

It goes through the entire shutdown process, but it doesn't switch off the power supply when it's finished.  I need to manually push n' hold the power button for 5 seconds, to kill the power supply.

I've had no such problem(s) when selecting upstart at boot.  It shuts down properly every time.

---

### Post by bapoumba on 2015-03-07
Thanks sudodus :)
All the threads about usernames are old and closed.. I'd better stop drifting the thread away, or Elfy will show me his big eyes ^^

---

### Post by lee295012-gmail on 2015-03-07
> **VinDSL said:**
> Only prob I've had with systemd is...

About half the time, or more, my rig won't shutdown properly.

It goes through the entire shutdown process, but it doesn't switch off the power supply when it's finished.  I need to manually push n' hold the power button for 5 seconds, to kill the power supply.

I've had no such problem(s) when selecting upstart at boot.  It shuts down properly every time.

bug report here about systemd and shutting the pc down.
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1427672](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1427672)

---

### Post by Cavsfan on 2015-03-07
> **VinDSL said:**
> Only prob I've had with systemd is...

About half the time, or more, my rig won't shutdown properly.

It goes through the entire shutdown process, but it doesn't switch off  the power supply when it's finished.  I need to manually push n' hold  the power button for 5 seconds, to kill the power supply.

I've had no such problem(s) when selecting upstart at boot.  It shuts down properly every time.

> **lee295012-gmail said:**
> bug report here about systemd and shutting the pc down.
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1427672](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1427672)

Wish I knew about the shutting down problem but I always restart at the end of the day and boot into Windows so my wife can get on for 20 minutes or so in the morning.
I always set it to sleep and leave it on at night. I shut it down only to replace something or to clean it.

The wife knows windows only. Guess I need to teach her some Linux/Ubuntu eh?
But, after she gets off, I'm rebooting and in Ubuntu all day.

Nice find on the bug lee295012-gmail! I'm sure they'll have that fixed shortly. I'd add my name but I can't.

---

### Post by VinDSL on 2015-03-07
Just saw this on the news feeds...

[INDENT]**[SIZE=4]Grab your pitchforks: Ubuntu to switch to systemd on Monday[/SIZE]**[/INDENT]
> [SIZE=3]The Ubuntu Project is set to move forward with a plan to make a controversial system management tool a key part of Ubuntu Linux.

On [COLOR="#FF0000"]Monday, March 9[/COLOR], the Ubuntu maintainers will reconfigure code base for the forthcoming version of the OS so that it uses the much-debated systemd suite of tools to handle core initialization tasks and manage system daemons.

That means that when Ubuntu 15.04 ships (presumably in April), all new Ubuntu installs will be running systemd by default.[/SIZE]

SOURCE:  [http://www.theregister.co.uk/2015/03/07/ubuntu_to_switch_to_systemd/](http://www.theregister.co.uk/2015/03/07/ubuntu_to_switch_to_systemd/)

---

### Post by sammiev on 2015-03-07
> **VinDSL said:**
> Just saw this on the news feeds...

[INDENT]**[SIZE=4]Grab your pitchforks: Ubuntu to switch to systemd on Monday[/SIZE]**[/INDENT]


SOURCE:  [http://www.theregister.co.uk/2015/03/07/ubuntu_to_switch_to_systemd/](http://www.theregister.co.uk/2015/03/07/ubuntu_to_switch_to_systemd/)

Posted already a few pages back.

---

### Post by VinDSL on 2015-03-07
> **sammiev said:**
> Posted already a few pages back.

Interesting!

The article only came out  [s] 3 hours [/s] ago...

Alrighty, then...  :oops:

**EDIT**

Correction...

```
Current Date/Time: Sat Mar  7 23:57:01 UTC 2015
```

11 hours ago  :)

---

### Post by VinDSL on 2015-03-07
@Cavsfan 

Thx for the bugs link!

I'll check it out, right now...  ;)

---

### Post by VinDSL on 2015-03-07
> **lee295012-gmail said:**
> hope they can fix being able to turn the pc off.

Running this, from a terminal, works a treat (for now)...

```
sudo shutdown -h now
```

---

### Post by zika on 2015-03-08
Or, for those who hate to type: REISUO. Hate to say, but PowerOff works here (on SystemD, UpStart do have an issue as _ventrical_ mentioned below). SystemD-way (to stay on-topic ;)) should work also:```
sudo poweroff
```and &#8222;-f&#8220; should force it (exclude init in that process) if it somehow fails... Nice set of options...

---

### Post by VinDSL on 2015-03-08
Only thing I don't like about 'poweroff -f' is it **halts** the system - as in *BOOM*.  It's like tossing a stun grenade into your PC. 

Better have all your data saved and programs closed before you invoke 'poweroff -f', you know?

IMO 'shutdown now' is a gentler workaround...  ;)

---

### Post by ventrical on 2015-03-08
> **lee295012-gmail said:**
> hope they can fix being able to turn the pc off.

Power off works great here from GUI on systemD. It's upstart that has the problem. Especially with gnome-shell. With kernel 4.n.n-n it runs like a swiss watch on systemD.

Regards..

---

### Post by zika on 2015-03-08
> **VinDSL said:**
> Only thing I don't like about 'poweroff -f' is it **halts** the system - as in *BOOM*.  It's like tossing a stun grenade into your PC. 
Better have all your data saved and programs closed before you invoke 'poweroff -f', you know?
IMO 'shutdown now' is a gentler workaround...  ;)That is precisely why I've recommended (above) REISUO or (plain, without exclusion of init) SystemD command... ;)

---

### Post by zika on 2015-03-08
> **ventrical said:**
> Power off works great here from GUI on systemD. It's upstart that has the problem. Especially with gnome-shell. With kernel 4.n.n-n it runs like a swiss watch on systemD.
Regards..Yeap, You're right, You've reminded me that with UpStart there was a problem with shutdown, recently, once I've checked. 8-)

---

### Post by VinDSL on 2015-03-08
> **ventrical said:**
> Power off works great here from GUI on systemD. It's upstart that has the problem. Especially with gnome-shell. With kernel 4.n.n-n it runs like a swiss watch on systemD.

Shutdown seems to be working for me, at the moment, after last night's incremental upgrades.  YaY!

I'm getting a couple of annoying 'apport' error dialog popups while booting into the desktop, but it doesn't have anything to do with 'systemd' - I get the same popups with 'upstart'.  

Seems like 'apport' is always lagging behind.  I'm tempted to just disable it.  I've done this in the past, when my 'apport aggravation level' peaks.  :p

Otherwise, yes, I've been extremely pleased with Linux 3.9/4.0 so far.  Worked a treat on this ancient iron...

---

### Post by enricobe on 2015-03-08
How can i set systemd as default on boot? Thank you :)

---

### Post by Cavsfan on 2015-03-08
> **enricobe said:**
> How can i set systemd as default on boot? Thank you :)

Just install systemd-sysv. **sudo apt-get install systemd-sysv** It will switch you over to systemd as default immediately.  
A sudo update-grub will automagically be performed and upon rebooting you will will be using systemd.

---

### Post by enricobe on 2015-03-08
> **Cavsfan said:**
> Just install systemd-sysv. **sudo apt-get install systemd-sysv** It will switch you over to systemd as default immediately.  
A sudo update-grub will automagically be performed and upon rebooting you will will be using systemd.
Thank you!

---

### Post by Cavsfan on 2015-03-08
> **Cavsfan said:**
> Just install systemd-sysv. **sudo apt-get install systemd-sysv** It will switch you over to systemd as default immediately.  
A sudo update-grub will automagically be performed and upon rebooting you will will be using systemd.

> **enricobe said:**
> Thank you!

You are welcome. 

I guess that will be moot with any ISO downloaded and installed starting tomorrow March 9th as systemd will be the default and an option to boot with upstart will be available in advanced options.

But I'm keeping my install until final release. :)

---

### Post by harry332 on 2015-03-09
So here it is, the switch to systemd:

ubuntu-meta (1.332) vivid; urgency=medium

  * Refreshed dependencies
  * Added systemd-sysv to standard (LP: #1427654)

---

### Post by enricobe on 2015-03-09
I've tried systemd from Advanced Options, then i've choose to switch because it's much faster. My PC boots in about half the time.

---

### Post by VinDSL on 2015-03-09
> **harry332 said:**
> So here it is, the switch to systemd:

ubuntu-meta (1.332) vivid; urgency=medium

  * Refreshed dependencies
  * Added systemd-sysv to standard (LP: #1427654)

Get the pitchforks and lanterns ready...  :)

---

### Post by VinDSL on 2015-03-09
Well, here goes nothin'.  Wish me luck...   ):P


[[img]http://vindsl.com/images/vindsl-desktop-9-mar-2015-1(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-9-mar-2015-1.png")

---

### Post by Alan F on 2015-03-09
If you have previously added the line "init=/lib/systemd/systemd" manually to /etc/default/grub to enable systemd then you will need to remove it manually.

---

### Post by Cavsfan on 2015-03-09
> **harry332 said:**
> So here it is, the switch to systemd:

ubuntu-meta (1.332) vivid; urgency=medium

  * Refreshed dependencies
  * Added systemd-sysv to standard (LP: #1427654)

I was just going to post exactly that. I checked apt-get changelog ubuntu-standard and it showed that. :biggrin:

So, indeed it is official.

I also like how in the terminal it shows the deletion of the old packages that were replaced in the update. This has been going on for a little while.

```
Processing triggers for man-db (2.7.0.2-5) ...
Setting up lib32gcc1 (1:5-20150307-1ubuntu3) ...
Setting up libncursesw5:amd64 (5.9+20140712-2ubuntu2) ...
Setting up init (1.22ubuntu4) ...
Setting up libboost-date-time1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Setting up libboost-system1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Setting up libboost-filesystem1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Setting up libboost-iostreams1.55.0:amd64 (1.55.0+dfsg-3ubuntu2) ...
Setting up libpython-stdlib:amd64 (2.7.8-4) ...
Setting up python (2.7.8-4) ...
Setting up init-system-helpers (1.22ubuntu4) ...
Setting up ubuntu-minimal (1.332) ...
Setting up ubuntu-standard (1.332) ...
Processing triggers for libc-bin (2.19-15ubuntu2) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del initscripts 2.88dsf-53.2ubuntu10 [28.0 kB]
Del sysvinit-utils 2.88dsf-53.2ubuntu10 [41.1 kB]
Del gcc-5-base 5-20150307-1ubuntu1 [14.5 kB]
Del libgcc1 1:5-20150307-1ubuntu1 [39.1 kB]
Del lib32gcc1 1:5-20150307-1ubuntu1 [46.5 kB]
Del init 1.22ubuntu3 [3,834 B]
Del ubuntu-standard 1.331 [2,926 B]
Del nvidia-prime 0.7 [11.7 kB]
Del ubuntu-minimal 1.331 [2,876 B]
Del sysv-rc 2.88dsf-53.2ubuntu10 [36.9 kB]

```

---

### Post by fjgaude on 2015-03-09
Oh wow, all seems good! Shutdown, systemd, work correctly after updating 15.4 this morning.

Startup finished in 958ms (kernel) + 1.142s (userspace) = 2.101s

That userspace sure goes by fast.

GtkPerf = 1.36 sec, not bad for my box.

Toward the Fun!

---

### Post by fjgaude on 2015-03-09
It switched this morning, in the update!

Everything with my setup, Unity, works fine with the auto-booting of systemd.

---

### Post by v3.xx on 2015-03-09
> **fjgaude said:**
> It switched this morning, in the update!

Everything with my setup works fine with the auto-booting of systemd.

Just did the update on Mate, all seems ok.

---

### Post by sgage on 2015-03-09
> **v3.xx said:**
> Just did the update on Mate, all seems ok.

Everything's fine here with Ubuntu Gnome...

---

### Post by merc82 on 2015-03-09
Since the update this morning, that removed upstart and installed systemd-sysv, my /var/log/pm-suspend log is no longer updated. Is this expected? I don't see a replacement log I can use to monitor power management.

---

### Post by philinux on 2015-03-10
Quote by Martin Pitt.

> The plan is to use systemd for a few weeks and if "there are too many or too big regressions", Vivid will be reverted to boot with upstart by default.

---

### Post by harry332 on 2015-03-10
Has anyone noticed that after ubuntu-meta has been upgraded to move towards systemd and systemd-sysv is installed (and upstart removed), we still have the package systemd-shim installed (with cgmanager).

Note, that systemd-shim was created: "for people wanting to use sysvinit or upstart as PID 1, there is a package  (systemd-shim) that works as an emulation layer between systemd  components like systemd-logind and an alternate init system: GNOME/XFCE  talks to systemd-logind, which talks to systemd-shim (instead of  systemd)."

---

### Post by grahammechanical on 2015-03-13
So, today's update made the switch to systemd as the default with upstart as an Advanced option. Now Ubuntu takes an extra 80 seconds to load to the login screen.

I also got kernel 3.19.0-9 which will not build the Nvidia driver module for my adapter so I am reverting to kernel 3.19.0-7 which does give me Nvidia driver but systemd is causing a "failed to start Load kernel Modules" Linux error message as well as a loading time so long that I am tempted to push the power button.

Not impressed with systemd.

---

### Post by harry332 on 2015-03-14
Yes, seems there are definitely something wrong in your setup.
First, tell us do you have systemd-sysv installed?
If so, how can upstart be any option anymore, as it should be removed by now?

---

### Post by dino99 on 2015-03-14
> **harry332 said:**
> Has anyone noticed that after ubuntu-meta has been upgraded to move towards systemd and systemd-sysv is installed (and upstart removed), we still have the package systemd-shim installed (with cgmanager).

Note, that systemd-shim was created: "for people wanting to use sysvinit or upstart as PID 1, there is a package  (systemd-shim) that works as an emulation layer between systemd  components like systemd-logind and an alternate init system: GNOME/XFCE  talks to systemd-logind, which talks to systemd-shim (instead of  systemd)."

indicator-datetime is still depending on systemd-shim (which should not be needed now as systemd-sysv is installed by default)

---

### Post by ventrical on 2015-03-14
> **harry332 said:**
> Yes, seems there are definitely something wrong in your setup.
First, tell us do you have systemd-sysv installed?
If so, how can upstart be any option anymore, as it should be removed by now?

If you look in Grub you will see (upstart) as the alternate now.

---

### Post by zika on 2015-03-14
Just to report that &#8222;text&#8220; boot-line kernel switch now works for SystemD. Good news... ;)
(You'll remember that replacement for that switch was &#8222;systemd.unit=runlevel3.target&#8220; in the very same place, &#8222;systemd.unit=runlevel5.target&#8220; gets us to GUI...)

---

### Post by harry332 on 2015-03-14
If you have systemd-shim installed, your setup is capable of using sysvinit.

---

### Post by harry332 on 2015-03-14
Well no, I do not have alternative upstart mentioned in grub.
But then agian, I have removed systemd-shim, cgmanager and libcgmanager from my setup, which has only Gnome DE with gdm.

---

### Post by grahammechanical on 2015-03-14
> **harry332 said:**
> Yes, seems there are definitely something wrong in your setup.
First, tell us do you have systemd-sysv installed?
If so, how can upstart be any option anymore, as it should be removed by now?

I take what comes down the pipe. We were told that the switch to systemd would be transparent to the user. I am testing this as a user who should not need to install anything. Some of you got in early on systemd. Well, that was your choice. Me? I decided to take it as it comes.

First, I got a systemd option in Advanced options. Which meant that upstart was still default. Now I get an upstart option in Advanced options. Which means that systemd is default. And all I did was a daily update. Which is how it should be. The same arrangement will be there if we put in an install of a daily image released since the 9th.

Systemd is failing to load certain kernel modules and the repeated attempts to load these modules is causing longer loading times. But this is not a problem that needs fixing by me because vivid vervet is still the development version. The devs have until release day to fix these problems otherwise the switch over will take place with 15.10. When the transition from upstart to systemd is completely satifactory I expect upstart code to be removed along with the Advanced option to load with upstart. This should happen without me doing anything but daily update. Whether this happens by 15.04 release date or 15.10 released date is not something I am worrying about.

What is important as far as I am concerned is that one way or another I can use vivid vervet as a daily driver.

---

### Post by ventrical on 2015-03-14
> **harry332 said:**
> Well no, I do not have alternative upstart mentioned in grub.
But then agian, I have removed systemd-shim, cgmanager and libcgmanager from my setup, which has only Gnome DE with gdm.

If you are working with development version 15.04 and updated today (yesterday) you will now see (upstart) as an Advanced Option in GruB (as mentioned by Grahammechanical) and systemD is now the default generic boot.

Regards..

---

### Post by ventrical on 2015-03-14
> **grahammechanical said:**
> I take what comes down the pipe. We were told that the switch to systemd would be transparent to the user. I am testing this as a user who should not need to install anything. Some of you got in early on systemd. Well, that was your choice. Me? I decided to take it as it comes.


I have several different installs of different flavours of Ubuntu dev on different machines that are allowing the developmental upgrade process take place without adding ppas, tweaks etc... and those installs are now generically booting into systemD and displaying (upstart) as an Advanced boot option. This was the whole plan from the start and now we are in the two week global testing period  for bare metal non-interfected installs to roll along with the development process. Basically what we signed up for :)  I do have some installs where I used another members suggest with shims, tweaks etc.. but the bulk on my installs are rolling with the process.  There have been few showstopper bugs and it has been a great experience so far with the exception that nVidia driver will not compile. Iv'e been through this (as have you) so I won't preach to the choir..etc.. :)

Regards..

---

### Post by ventrical on 2015-03-14
> **VinDSL said:**
> Shutdown seems to be working for me, at the moment, after last night's incremental upgrades.  YaY!

I'm getting a couple of annoying 'apport' error dialog popups while booting into the desktop, but it doesn't have anything to do with 'systemd' - I get the same popups with 'upstart'.  

Seems like 'apport' is always lagging behind.  I'm tempted to just disable it.  I've done this in the past, when my 'apport aggravation level' peaks.  :p

Otherwise, yes, I've been extremely pleased with Linux 3.9/4.0 so far.  Worked a treat on this ancient iron...

+1  Upstart now working properly as Advanced Option. I am getting no apport or any other errors. From both system D and (upstart) it is smooth sailing experience on Gnome-shell :)  it is using the:

```

 *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

```

processor with 45nm litography, coolwerks etc.. and awesome graphics on nVidia.

Nice work all around. I thought upstart was borked for good. Thanks for leaving this message :)

Regards..

---

### Post by VinDSL on 2015-03-15
> **ventrical said:**
> +1  Upstart now working properly as Advanced Option. I am getting no apport or any other errors. From both system D and (upstart) it is smooth sailing experience on Gnome-shell :)

No 'apport' errors in 'systemd' or 'upstart', after today's upgrades.  YaY!

Everything is working fine here, including Unity & GS...


[[img]http://vindsl.com/images/vindsl-desktop-14-mar-2015(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-14-mar-2015.png")

---

### Post by harry332 on 2015-03-15
> **ventrical said:**
> If you are working with development version 15.04 and updated today (yesterday) you will now see (upstart) as an Advanced Option in GruB (as mentioned by Grahammechanical) and systemD is now the default generic boot.

Regards..

My point was this: how could upstart be an advanced option or any option as I do not have upstart, upstart-bin, cgmanager, libjson0 nor systemd-shim installed anymore?
There is no upstart in my setup anymore.

And yes I do have dev. 15.04 fully updated (main server) as of today.
But, there is no upstart option in my grub.

---

### Post by dino99 on 2015-03-15
> **harry332 said:**
> My point was this: how could upstart be an advanced option or any option as I do not have upstart, upstart-bin, cgmanager, libjson0 nor systemd-shim installed anymore?
There is no upstart in my setup anymore.

And yes I do have dev. 15.04 fully updated (main server) as of today.
But, there is no upstart option in my grub.

upstart-bin is a needed dependency of unity-greeter  Bug lp:1432317

---

### Post by ventrical on 2015-03-15
Awwwwk!  Another  awesome pic from Vin :)

---

### Post by ventrical on 2015-03-15
> **harry332 said:**
> My point was this: how could upstart be an advanced option or any option as I do not have upstart, upstart-bin, cgmanager, libjson0 nor systemd-shim installed anymore?
There is no upstart in my setup anymore.

And yes I do have dev. 15.04 fully updated (main server) as of today.
But, there is no upstart option in my grub.


I understand your point but, if you were to do a test and install of a flavour of ubuntu daily live current you will get the upstart advanced option in Grub. Obviously you have a customized system?

Regards..

---

### Post by Mateusz Stachowski on 2015-03-15
You don't have those packages because you removed them. In normal upgrades and new installs they are still there to provide that Upstart boot option.

Just look at this list of packages that come with the pending image of Vivid (the current is to old 6th March). You will find there: upstart-bin, systemd-shim, libjson0 and cgmanager but not upstart and there is also systemd-sysv.

[http://cdimage.ubuntu.com/daily-live/pending/vivid-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/pending/vivid-desktop-amd64.manifest)

---

### Post by craig10x on 2015-03-15
I noticed they haven't put up any new daily build images for over a week now...wonder if it has to do with the switch over to systemd?

---

### Post by fjgaude on 2015-03-15
Well, systemd is here for sure but I am a little concerned about how it takes so long to go through the apps:

frank@flash:~$ sudo systemd-analyze (14.10)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s
frank@flash:~$ sudo systemd-analyze (15.04)
Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s
frank@flash:~$ sudo systemd-analyze (15.04 12/27/14)
Startup finished in 890ms (kernel) + 5.808s (userspace) = 6.699s
frank@flash:~$ sudo systemd-analyze (15.04 3/3/15)
Startup finished in 930ms (kernel) + 15.265s (userspace) = 16.196s
frank@flash:~$ sudo systemd-analyze (15.04 3/9/15)
Startup finished in 938ms (kernel) + 2.501s (userspace) = 3.440s
frank@flash:~$ sudo systemd-analyze (15.04 3/12/15)
Startup finished in 1.161s (kernel) + 15.857s (userspace) = 17.018s
frank@flash:~$ sudo systemd-analyze (15.04 3/15/15)
Startup finished in 1.102s (kernel) + 18.914s (userspace) = 20.017s

You can see how things have gotten long as the release has developed. I guess I could live with the 20 seconds. <smile>

---

### Post by zika on 2015-03-15
> **fjgaude said:**
> Well, systemd is here for sure but I am a little concerned about how it takes so long to go through the apps:

frank@flash:~$ sudo systemd-analyze (14.10)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s
frank@flash:~$ sudo systemd-analyze (15.04)
Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s
frank@flash:~$ sudo systemd-analyze (15.04 12/27/14)
Startup finished in 890ms (kernel) + 5.808s (userspace) = 6.699s
frank@flash:~$ sudo systemd-analyze (15.04 3/3/15)
Startup finished in 930ms (kernel) + 15.265s (userspace) = 16.196s
frank@flash:~$ sudo systemd-analyze (15.04 3/9/15)
Startup finished in 938ms (kernel) + 2.501s (userspace) = 3.440s
frank@flash:~$ sudo systemd-analyze (15.04 3/12/15)
Startup finished in 1.161s (kernel) + 15.857s (userspace) = 17.018s
frank@flash:~$ sudo systemd-analyze (15.04 3/15/15)
Startup finished in 1.102s (kernel) + 18.914s (userspace) = 20.017s

You can see how things have gotten long as the release has developed. I guess I could live with the 20 seconds. <smile>Thank You for nice data-set that I've been sorry not to have compiled myself for quite some time. Memory (mine at least) is unstable but data are solid...

---

### Post by rrnbtter on 2015-03-15
Greetings,
> **craig10x said:**
> I noticed they haven't put up any new daily build images for over a week now...wonder if it has to do with the switch over to systemd?

[http://www.cdimage.ubuntu.com/daily-live/20150315/](http://www.cdimage.ubuntu.com/daily-live/20150315/)

Seems to me that with the hoard of updates I'm getting there would have to be images unless there is a loader/boot issue.

---

### Post by Elfy on 2015-03-15
some thread merging occurred a short time ago

---

### Post by craig10x on 2015-03-15
@rrnbtter: Well, how do you like that... when i checked this morning, the latest one listed was from march 6th...looks like they updated it today (march 15) :)
edit: wait a second...isn't that link for 15.04 gnome version?  that one is up to date... 15.04 with unity is still coming up March 6th...
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Cavsfan on 2015-03-15
> **craig10x said:**
> @rrnbtter: Well, how do you like that... when i checked this morning, the latest one listed was from march 6th...looks like they updated it today (march 15) :)
edit: wait a second...isn't that link for 15.04 gnome version?  that one is up to date... 15.04 with unity is still coming up March 6th...
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

No, that is vanilla Ubuntu images built today.

[http://cdimage.ubuntu.com/daily-live/]("http://cdimage.ubuntu.com/daily-live/")

Edit: Oh, my bad. I didn't mean to butt in.

---

### Post by craig10x on 2015-03-15
oh, that's ok Cavsfan ;)
i just wanted confirmation on whether his link was the ubuntu w/unity version daily build for today...when i do a yahoo search i get the March 6th page...
Wanted to check it out on live session tomorrow and wanted to make sure i was downloading the correct iso...

---

### Post by rrnbtter on 2015-03-15
Greetings, 
@craig10x, I've been using that link everyday since Vivid went live last year. I just update the day on my zsync macro every day.
They have one for Unity8 also.

---

### Post by craig10x on 2015-03-15
Thanks...it is the right one...in fact, i am on the live session right now...man, 15.04 is getting like super-zippy...what the heck did they do...this is great ;)
I can't figure why when i yahoo ubuntu 15.04 daily build it keeps bring me to the march 6th uploads...very strange, indeed...

---

### Post by rrnbtter on 2015-03-15
Greetings,
@craig10x, 
Could be that you are getting a link from a cache-ing server somewhere. If you research back to the starting Vivid posts, users were having trouble finding the Vivid images back then. This link got posted from somewhere I don't remember where but I have been using it for the whole run. I keep my image updated just in case I get a crash. I've only needed it for one install though. I have used quite a few of the Unity8 images.

---

### Post by Cavsfan on 2015-03-16
> **craig10x said:**
> Thanks...it is the right one...in fact, i am on the live session right now...man, 15.04 is getting like super-zippy...what the heck did they do...this is great ;)
I can't figure why when i yahoo ubuntu 15.04 daily build it keeps bring me to the march 6th uploads...very strange, indeed...

Actually you are right. On that link [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

It says beside the current link "06-Mar-2015 10:36    -   Latest images to have passed any automatic testing; try this first".
But it does also provide links to today's ISO (March 16) and yesterdays too. Then the March 6th one. 

But the link (sticky) at the top of the Ubuntu Development Version section of the forum does still point to the March 6th ISO [http://ubuntuforums.org/showthread.php?t=2249680](http://ubuntuforums.org/showthread.php?t=2249680)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

That provides ISOs from March 6th but the metalink is kept up to date it looks like.

Hmmm pondering... ;)

---

### Post by Elfy on 2015-03-16
> **Cavsfan said:**
> ...

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

That provides ISOs from March 6th but the metalink is kept up to date it looks like.

Hmmm pondering... ;)

something not right with that - I'll ping someone

---

### Post by Elfy on 2015-03-16
so - images get to 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

when they have passed automated testing

They've not - so they're aren't there.

That does not stop the daily on the tracker incrementing daily.

The upshot is that [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and what's currently on the tracker will be the same when automated testing passes.

Hope that makes sense.

If in doubt - use the tracker :)

EDIT - that said the tracker is all over the place for Ubuntu anyway :D

---

### Post by Cavsfan on 2015-03-16
Thanks for that information Elfy! We were all curious what was going on there.

I just installed the daily Vivid Mate ISO and it did not come with an option to boot with upstart.  

It came with only the 3.19.0-9-generic kernel and only systemd so I'm not even going to attempt upstart as I don't know how to and don't care any way.

I think the last time I booted with upstart a bunch of problems started. Not saying upstart caused it but saying I don't need it any more, not with systemd.

From /boot/grub/grub.cfg:

```
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e86090dc-3f6f-42c7-ba9e-b29329e88757' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e86090dc-3f6f-42c7-ba9e-b29329e88757
    else
      search --no-floppy --fs-uuid --set=root e86090dc-3f6f-42c7-ba9e-b29329e88757
    fi
    linux    /boot/vmlinuz-3.19.0-9-generic root=UUID=e86090dc-3f6f-42c7-ba9e-b29329e88757 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-9-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e86090dc-3f6f-42c7-ba9e-b29329e88757' {
    menuentry 'Ubuntu, with Linux 3.19.0-9-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-9-generic-advanced-e86090dc-3f6f-42c7-ba9e-b29329e88757' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e86090dc-3f6f-42c7-ba9e-b29329e88757
        else
          search --no-floppy --fs-uuid --set=root e86090dc-3f6f-42c7-ba9e-b29329e88757
        fi
        echo    'Loading Linux 3.19.0-9-generic ...'
        linux    /boot/vmlinuz-3.19.0-9-generic root=UUID=e86090dc-3f6f-42c7-ba9e-b29329e88757 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-9-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-9-generic-recovery-e86090dc-3f6f-42c7-ba9e-b29329e88757' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e86090dc-3f6f-42c7-ba9e-b29329e88757
        else
          search --no-floppy --fs-uuid --set=root e86090dc-3f6f-42c7-ba9e-b29329e88757
        fi
        echo    'Loading Linux 3.19.0-9-generic ...'
        linux    /boot/vmlinuz-3.19.0-9-generic root=UUID=e86090dc-3f6f-42c7-ba9e-b29329e88757 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-9-generic
    }
}

### END /etc/grub.d/10_linux ###

```

This is all that came pre-installed:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                        219-4ubuntu5                               amd64        system and service manager - PAM module
ii  libsystemd0:amd64                           219-4ubuntu5                               amd64        systemd utility library
ii  systemd                                     219-4ubuntu5                               amd64        system and service manager
ii  systemd-sysv                                219-4ubuntu5                               amd64        system and service manager - SysV links

```

---

### Post by craig10x on 2015-03-16
Oh, so it is because they haven't passed automated testing yet...that was confusing! ;)
The live session ran fine...only problem i had was it didn't kick out the dvd automatically when i hit restart to end the live session...in fact, the dvd booted back into the live session again...
Had to remove the dvd with the live session on there (when the disc wasn't running of course)....

---

### Post by aljosa2 on 2015-03-16
> **Elfy said:**
> so - images get to 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

when they have passed automated testing

They've not - so they're aren't there.

infact, there's a good reason: with 20150316/16-Mar-2015 08:31 no mouse, no touchpad, so i just wasted 1,5 euro for dvd :(

---

### Post by Elfy on 2015-03-16
> **craig10x said:**
> Oh, so it is because they haven't passed automated testing yet...that was confusing! ;)
The live session ran fine...only problem i had was it didn't kick out the dvd automatically when i hit restart to end the live session...in fact, the dvd booted back into the live session again...
Had to remove the dvd with the live session on there (when the disc wasn't running of course)....

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1432285](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1432285)

at least - possibly a dupe

---

### Post by Elfy on 2015-03-16
> **aljosa2 said:**
> infact, there's a good reason: with 20150316/16-Mar-2015 08:31 no mouse, no touchpad, so i just wasted 1,5 euro for dvd :(

wouldn't know I'm afraid I only ever boot Ubuntu images to double check issues I might be seeing on Xubuntu

---

### Post by Cavsfan on 2015-03-16
> **aljosa2 said:**
> infact, there's a good reason: with  20150316/16-Mar-2015 08:31 no mouse, no touchpad, so i just wasted 1,5  euro for dvd :sad:

Sorry, get some DVD-RWs. I have all my systems on those and just re-use them as needed.

> **craig10x said:**
> Oh, so it is because they haven't passed automated testing yet...that was confusing! ;)
The live session ran fine...only problem i had was it didn't kick out the dvd automatically when i hit restart to end the live session...in fact, the dvd booted back into the live session again...
Had to remove the dvd with the live session on there (when the disc wasn't running of course)....

> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1432285](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1432285)

at least - possibly a dupe

That explains it. When I installed Mate from today's ISO and it asked to reboot, it did not ask me to remove the DVD like it did when I installed the beta.
If I didn't hit eject before it got past the bios screen it would have went into a live session which I did not want.

When it paused after installing the beta, nothing appeared on the screen, but I ejected the DVD then pressed enter and it restarted. At least at that time it was trying.

I me tooed that bug.

---

### Post by craig10x on 2015-03-17
Yep, that's the bug alright...i let it re-boot to the live session, and simply waited for when the disc wasn't actually spinning (you know, when you run live session, it isn't always running)...i knew that would be my opportunity to easily remove it by hitting the computer's eject button, and then i just did a hard shut down and started up back into my installed system again ;)
First time i ever encountered an ubuntu iso that didn't automatically kick the dvd out when i restarted to end the live session...

---

### Post by Ian_Worrall on 2015-03-17
Have to say I'm liking systemd, as since moving to Vivid, upstart was waiting a full 30 seconds to start USB so I could log in.
Systemd is MUCH quicker off the mark for me, but I do seem to get a lot of USB errors on startup (probably doesn't recognize the mobo's USB3 controller I guess).

---

### Post by rrnbtter on 2015-03-17
Greetings,

> **Ian_Worrall said:**
> Have to say I'm liking systemd, as since moving to Vivid, upstart was waiting a full 30 seconds to start USB so I could log in.
Systemd is MUCH quicker off the mark for me, but I do seem to get a lot of USB errors on startup (probably doesn't recognize the mobo's USB3 controller I guess).

I've been a fan of systemd from the start when it first showed in Ubuntu, but it is still a dumb system manager. It doesn't hurt to look at what it is loading at startup and perhaps shutdown some overhead. "systemd-analyze blame" yielded for me a Modem-Manager and I haven't used my modem in the entire five years I've owned this computer. It is just something for Network-Manager to handle (ping) and it takes about 1.3sec to load at startup. Then google the rest of the list and see what turns up. So I don't see systemd as a reason for myself to be any less responsible for the load my system is taking on. 
One interesting result is that unloading "apport" doesn't get rid of apport. Probably that module is still handled by sysv so I had to turn it off in "/etc/default/apport".
This is just an example but the point is that it is at this point a mixed bag of system managers. There has to be some complications until the conversion is complete. But Hey! thats testing!

---

### Post by Cavsfan on 2015-03-23
Are the new ISOs coming (after March 16th) with upstart as an option with systemd the default?

Just curious.

---

### Post by grahammechanical on 2015-03-23
I recently put in a vivid daily from the 20th of Kubuntu and vivid daily from 21st of Lubuntu and Ubuntu Mate neither had upstart as an Advanced option.

---

### Post by Elfy on 2015-03-23
> **Cavsfan said:**
> Are the new ISOs coming (after March 16th) with upstart as an option with systemd the default?

Just curious.

To get image to boot with upstart you'd need to add the init= line to the image boot line.

---

### Post by dino99 on 2015-03-23
There is still some change/work on the table coming soon
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1422681](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1422681)

---

### Post by Cavsfan on 2015-03-23
> **grahammechanical said:**
> I recently put in a vivid daily from the 20th of Kubuntu and vivid daily from 21st of Lubuntu and Ubuntu Mate neither had upstart as an Advanced option.

That is what I thought. That is exactly what I have.

> **Elfy said:**
> To get image to boot with upstart you'd need to add the init= line to the image boot line.

I haven't tried that but upstart is not even installed. So there is no /sbin/upstart to add to the boot line any more.
 
> **9d9 said:**
> There is still some change/work on the table coming soon
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1422681](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1422681)

I was just really trying to confirm that the new ISOs are also like mine from March 16th: only systemd with no option for upstart.

I'm still curious as to whether there will both options at final release. I'm leaving this Ubuntu Mate install totally default and letting the chips fall where they may.
I've added nothing at all to it.

---

### Post by zika on 2015-03-23
It looks like Vivid Daily differs from the (my) Vivid install that is rolling from the very beginning of U+1:
```
    1 root      20   0   29232   3808   2484 S   0,0  0,0   0:00.84 upstart 
``````
:~$ dpkg -l|grep upstart
ii  libupstart1:amd64                                     1.13.2-0ubuntu9                            amd64        Upstart Client Library
rc  upstart                                               1.13.2-0ubuntu9                            amd64        event-based init daemon - sysv compat
ii  upstart-bin                                           1.13.2-0ubuntu9                            amd64        event-based init daemon - essential binaries
``````
:~$ sudo apt-get purge -s upstart-bin libupstart1 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libupstart1* ubuntu-desktop* unity* unity-greeter* unity-tweak-tool* upstart-bin*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg libupstart1 [1.13.2-0ubuntu9]
Purg ubuntu-desktop [1.334]
Purg unity-tweak-tool [0.0.6ubuntu2]
Purg unity [7.3.1+15.04.20150227-0ubuntu1]
Purg unity-greeter [15.04.3-0ubuntu1]
Purg upstart-bin [1.13.2-0ubuntu9]
``````
:~$ cat /boot/grub/grub.cfg |grep upstart    
    menuentry 'Ubuntu, with Linux 4.0.0-999-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.0.0-999-generic-init-upstart-...' {
        linux    /boot/vmlinuz-4.0.0-999-generic root=UUID=... ro  ... init=/sbin/upstart
    menuentry 'Ubuntu, with Linux 4.0.0-996-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.0.0-996-generic-init-upstart-...' {
        linux    /boot/vmlinuz-4.0.0-996-generic root=UUID=... ro  ... init=/sbin/upstart
    menuentry 'Ubuntu, with Linux 3.19.0-9-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-9-generic-init-upstart-...' {
        linux    /boot/vmlinuz-3.19.0-9-generic root=UUID=... ro  ... init=/sbin/upstart
    menuentry 'Ubuntu, with Linux 3.19.0-pf1 (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-pf1-init-upstart-...' {
        linux    /boot/vmlinuz-3.19.0-pf1 root=UUID=... ro  ... init=/sbin/upstart
    menuentry 'Ubuntu, with Linux 3.19-2.dmz.1-liquorix-amd64 (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19-2.dmz.1-liquorix-amd64-init-upstart-...' {
        linux    /boot/vmlinuz-3.19-2.dmz.1-liquorix-amd64 root=UUID=... ro  ... init=/sbin/upstart
```This visit to UpStart was nice... ;)

---

### Post by Cavsfan on 2015-03-23
I was referring to the new ISOs that are coming out now. There is absolutely no Upstart on them. ;)

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep upstart
cavsfan@cavsfan-MS-7529:~$ 
```

---

### Post by zika on 2015-03-23
> **Cavsfan said:**
> I was referring to the new ISOs that are coming out now. There is absolutely no Upstart on them. ;)```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep upstart
cavsfan@cavsfan-MS-7529:~$ 
```So was I, deducting from previous posts. And they should look like that if intention is to make SystemD default. If there were options people would lurk into those territories.
And, yet, here:```
:~$sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  upstart-bin
The following packages will be upgraded:
  command-not-found command-not-found-data init init-system-helpers
  libupstart1 python-commandnotfound python3-commandnotfound
7 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 883 kB of archives.
After this operation, 233 kB disk space will be freed.
Do you want to continue? [Y/n]
``````
:~$ sudo aptitude full-upgrade 
The following NEW packages will be installed:
  upstart{a} 
The following packages will be upgraded:
  upstart-bin 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 401 kB of archives. After unpacking 263 kB will be used.
The following packages have unmet dependencies:
 systemd-sysv : Conflicts: upstart but 1.13.2-0ubuntu10 is to be installed.
                Conflicts: upstart:i386 but it is not going to be installed.
The following actions will resolve these dependencies:
     Remove the following packages:
1)     init                        
2)     systemd-sysv                
3)     ubuntu-minimal              
4)     ubuntu-standard             
Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```Regards from (for a moment) UpStart renegade... ;) It looks nice and responsive as it was never before. DRM-NEXT kernel kind of helps... ;)
Update: So, now, they learned to coexist (not to say cohabitate):```
Building dependency tree       Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  upstart
The following packages will be upgraded:
  cpp-4.9 g++-4.9 gcc-4.9 gcc-4.9-base gir1.2-gudev-1.0 libasan1 libatomic1
  libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386 libcilkrts5
  libgcc-4.9-dev libgfortran3 libgomp1 libgudev-1.0-0 libitm1 liblsan0
  libpam-systemd libquadmath0 libstdc++-4.9-dev libstdc++6 libsystemd0
  libtsan0 libubsan0 libudev1 multiarch-support systemd systemd-sysv udev
  upstart-bin
33 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 51,1 MB of archives.
After this operation, 261 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```To clarify: no package was killed or harmed during this process and I did not intervene in any of these cohabitating efforts. Notice the difference from post of mine above...```
:~$ dpkg -l|grep upstart
ii  libupstart1:amd64                                     1.13.2-0ubuntu10                           amd64        Upstart Client Library
ii  upstart                                               1.13.2-0ubuntu10                           amd64        event-based init daemon - essential binaries
ii  upstart-bin                                           1.13.2-0ubuntu10                           all          event-based init daemon - transitional dummy package
```
Hearing about freeze I can only say:
1. This was a great and calm U+1
2. I'll wait eagerly end of April to see where we will go in U+2... ;)

---

### Post by grahammechanical on 2015-03-23
As an aside, I found these two new installs of Lubuntu and Ubuntu Mate to be very fast at loading. Now, if that proves to be true of Ubuntu 15.04 and the others come release day then a lot of people will be amazed.

What the user experience is like come release day is what is important. My experience with a development release that started out as trusty and then became utopic and is now vivid is not so important in the great scheme of things.

---

### Post by Cavsfan on 2015-03-23
> **grahammechanical said:**
> As an aside, I found these two new installs of Lubuntu and Ubuntu Mate to be very fast at loading. Now, if that proves to be true of Ubuntu 15.04 and the others come release day then a lot of people will be amazed.

What the user experience is like come release day is what is important. My experience with a development release that started out as trusty and then became utopic and is now vivid is not so important in the great scheme of things.

Just curious as to whether the new installs came with systemd as the default and upstart as an option or not.

Also since I have said that I didn't have any way to boot upstart from my March 16th ISO install I got some updates just a little while ago.

```
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils conky-all gir1.2-gudev-1.0 init init-system-helpers libapt-inst1.5 libapt-pkg4.12 libgudev-1.0-0 libpam-systemd libsystemd0 libudev1 systemd systemd-sysv udev
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,974 kB of archives.
After this operation, 100 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Systemd and init's changelogs had some interesting info about upstart which I won't waste time or space mentioning here.

But I decided to try to install upstart and it worked and gave me back both options.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcgmanager0 libjson0
Suggested packages:
  graphviz upstart-monitor
The following NEW packages will be installed:
  libcgmanager0 libjson0 upstart
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 436 kB of archives.
After this operation, 1,962 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

Although booting into upstart had a message that appeared before login screen appeared which was too fast for me to see.
There was no sound and there was no option to restart or shutdown, only logout. Also upstart is PID 1 now instead of init.
In Mate the restart logout, etc button is grayed out also.

So I had to press Alt+Prtscreen and press the letters reisub (BUSIER backwards) so as to not require pressing the reset button.
That did work and I booted into upstart twice and it's obviously broken for the time being.

But, at least I have both options back now.

I'm so confused now I don't even know if this is the right place to post this. :?

---

### Post by Elfy on 2015-03-23
it's all good fun :)

---

### Post by Cavsfan on 2015-03-24
I purged libcgmanager0 libjson0 and upstart. Back to systemd only.

I'll let the powers that be decide which way it goes. I'm not forcing anything.

---

### Post by fjgaude on 2015-03-24
Well, for me, **systemd** seems and measures about 10 seconds slower on bootup... I guess it is going to stay that way. Must have something to do with the testing of each app during the process.

---

### Post by sammiev on 2015-03-24
I'm booting about 3 seconds faster on systemd on my SSD on a Intel system.

---

### Post by fjgaude on 2015-03-26
Well, I can't say for sure, but here's my log:

frank@flash:~$ sudo systemd-analyze (14.10)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s
frank@flash:~$ sudo systemd-analyze (15.04)
Startup finished in 888ms (kernel) + 4.550s (userspace) = 5.438s
frank@flash:~$ sudo systemd-analyze (15.04 12/27/14)
Startup finished in 890ms (kernel) + 5.808s (userspace) = 6.699s
frank@flash:~$ sudo systemd-analyze (15.04 3/3/15)
Startup finished in 930ms (kernel) + 15.265s (userspace) = 16.196s
frank@flash:~$ sudo systemd-analyze (15.04 3/9/15)
Startup finished in 938ms (kernel) + 2.501s (userspace) = 3.440s
frank@flash:~$ sudo systemd-analyze (15.04 3/12/15)
Startup finished in 1.161s (kernel) + 15.857s (userspace) = 17.018s
frank@flash:~$ sudo systemd-analyze (15.04 3/15/15)
Startup finished in 1.102s (kernel) + 18.914s (userspace) = 20.017s
frank@flash:~$ sudo systemd-analyze (15.04 3/16/15)
Startup finished in 1.189s (kernel) + 15.825s (userspace) = 17.015s
frank@flash:~$ sudo systemd-analyze (15.04 3/26/15)
Startup finished in 948ms (kernel) + 20.069s (userspace) = 21.017s

You can see from where I come. <smile>

---

### Post by machak on 2015-03-26
in my case (checked by using  systemd-analyze blame ), [COLOR=#2E1A05]NetworkManager-wait-online.service was taking about 9 sec...

[/COLOR]

---

### Post by Elfy on 2015-03-26
> **machak said:**
> in my case (checked by using  systemd-analyze blame ), [COLOR=#2E1A05]NetworkManager-wait-online.service was taking about 9 sec...

[/COLOR]

similar

---

### Post by grahammechanical on 2015-03-26
I have just loaded my long standing Ubuntu vivid and run systemd-analyze inmmediately the desktop loaded and I got.
> 
Bootup is not yet finished. Please try again later.


The second attempt a few seconds later gave

> Startup finished in 10.817s (kernel) + 3min 3.234s (userspace) = 3min 14.052s


It does take a very long time to load. I think that new installs are much better.

---

### Post by cariboo on 2015-03-26
On my system, which was installed back in October, the systemd-analyze results look like this:

```
systemd-analyze
Startup finished in 2.426s (kernel) + 9.026s (userspace) = 11.453s
```

---

### Post by Elfy on 2015-03-26
```
systemd-analyze 
Startup finished in 1.384s (kernel) + 10.761s (userspace) = 12.145s
```

```
systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @10.758s
&#9492;&#9472;multi-user.target @10.758s
  &#9492;&#9472;libvirt-bin.service @10.622s +135ms
    &#9492;&#9472;network-online.target @10.621s
      &#9492;&#9472;network.target @3.154s
        &#9492;&#9472;NetworkManager.service @2.934s +219ms
          &#9492;&#9472;basic.target @2.930s
            &#9492;&#9472;sockets.target @2.930s
              &#9492;&#9472;avahi-daemon.socket @2.930s
                &#9492;&#9472;sysinit.target @2.929s
                  &#9492;&#9472;networking.service @2.827s +101ms
                    &#9492;&#9472;local-fs.target @2.826s
                      &#9492;&#9472;run-cgmanager-fs.mount @2.948s
                        &#9492;&#9472;local-fs-pre.target @2.280s
                          &#9492;&#9472;systemd-remount-fs.service @462ms +7ms
                            &#9492;&#9472;systemd-fsck-root.service @202ms +260ms
                              &#9492;&#9472;system.slice @184ms
                                &#9492;&#9472;-.slice @183ms
```
If I remove kvm - then it blames NetworkManager-wait-online.service

---

### Post by fjgaude on 2015-03-26
Startup finished in 943ms (kernel) + 15.070s (userspace) = 16.014s
frank@flash:~$ sudo systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @15.069s
&#9492;&#9472;multi-user.target @15.069s
  &#9492;&#9472;kerneloops.service @15.059s +9ms
    &#9492;&#9472;network-online.target @15.058s
      &#9492;&#9472;network.target @6.930s
        &#9492;&#9472;NetworkManager.service @6.790s +139ms
          &#9492;&#9472;basic.target @6.779s
            &#9492;&#9472;sockets.target @6.776s
              &#9492;&#9472;dbus.socket @6.776s
                &#9492;&#9472;sysinit.target @6.776s
                  &#9492;&#9472;networking.service @6.701s +74ms
                    &#9492;&#9472;local-fs.target @6.700s
                      &#9492;&#9472;run-user-1000-gvfs.mount @7.369s
                        &#9492;&#9472;run-user-1000.mount @7.045s
                          &#9492;&#9472;local-fs-pre.target @6.653s
                            &#9492;&#9472;systemd-remount-fs.service @164ms +1ms
                              &#9492;&#9472;systemd-fsck-root.service @87ms +77ms
                                &#9492;&#9472;systemd-fsckd.socket @86ms
                                  &#9492;&#9472;-.slice @79ms

I can't say what is going on here. Will have to do some research.

---

### Post by ventrical on 2015-03-27
This is an f/p

```

ventrical@ventrical-MS-7798:~$ systemd-analyze
Startup finished in 1.162s (kernel) + 1min 31.195s (userspace) = 1min 32.357s
ventrical@ventrical-MS-7798:~$ 



```

because  it is fully booted in less that 4 seconds total on my high speed system.(non -suspend). On my Quad Core is is 3/4 of 1 second.. with ssds.

edit:

After update :

```

ventrical@ventrical-MS-7798:~$ systemd-analyze
Bootup is not yet finished. Please try again later.
ventrical@ventrical-MS-7798:~$ systemd-analyze
Startup finished in 1.091s (kernel) + 1min 34.983s (userspace) = 1min 36.074s
ventrical@ventrical-MS-7798:~$ 


```

but it appeared much slower.



regards..

---

### Post by ventrical on 2015-03-27
> **Elfy said:**
>  ```
systemd-analyze 
Startup finished in 1.384s (kernel) + 10.761s (userspace) = 12.145s
```




I used xubuntu and :

```

ventrical@ventrical-P5QL-PRO:~$ sudo systemd-analyze
[sudo] password for ventrical: 
Startup finished in 1.673s (kernel) + 10.677s (userspace) = 12.350s
ventrical@ventrical-P5QL-PRO:~$ uname -a
Linux ventrical-P5QL-PRO 3.19.0-9-generic #9-Ubuntu SMP Wed Mar 11 17:50:03 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-P5QL-PRO:~$ 


```

so there seems to be varied time with  different flavours.

---

### Post by PJs Ronin on 2015-03-27
About a month ago my Vivid install (I take the dist-upgrade path from a Trusty install) was really fast to boot.   Today, it's as slow as a wet week and I'm having the same NetworkManager delay as:> **machak said:**
> in my case (checked by using  systemd-analyze blame ), [COLOR=#2E1A05]NetworkManager-wait-online.service was taking about 9 sec...[/COLOR]

I'ma hoping this is just a temp speedhump.

---

### Post by fjgaude on 2015-03-27
Well, trying upstart versus systemd from the grub option menu I get back my quick bootup speed of about 6 seconds total.

I guess because of using so many apps, like VirtualBox, Xara, etc., time is taken to recognize them as okay.

So be it... as long as I can still use upstart.

---

### Post by Cavsfan on 2015-03-28
Guess I just have an old machine purchased around March or April of 2009 with a sataII drive and an IDE interface. :p

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze 
Startup finished in 6.897s (kernel) + 17.151s (userspace) = 24.049s
```

This is on Vivid Mate. Still all in all not too shabby. ;)

I tried installing upstart but that did not go well at all so I purged it.

---

### Post by VMC on 2015-03-29
> **Cavsfan said:**
> Guess I just have an old machine purchased around March or April of 2009 with a sataII drive and an IDE interface. :p

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze 
Startup finished in 6.897s (kernel) + 17.151s (userspace) = 24.049s
```

This is on Vivid Mate. Still all in all not too shabby. ;)

I tried installing upstart but that did not go well at all so I purged it.

Also purshased system 2009:
```
Startup finished in 2.907s (kernel) + 12.287s (userspace) = 15.195s
```

First time using Vivid (Xubuntu). Have been on Trusty since beginning of time.

---

### Post by Chanath on 2015-03-30
Does dist-upgrade would move to Systemd in Vivid?
Would it stay with Upstart in Trusty or would it too move to Systemd automatically?

---

### Post by trinitonadam on 2015-03-31
```
A start job is running for udev...
```

```
triniton@triniton:~$ systemd-analyze
Startup finished in 2.123s (kernel) + 1min 3.761s (userspace) = **1min 5.885s**
triniton@triniton:~$ uname -a
Linux triniton 3.19.0-10-generic #10-Ubuntu SMP Mon Mar 23 16:25:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by v3.xx on 2015-03-31
> Startup finished in 4.263s (kernel) + 14.951s (userspace) = 19.215s
That is what I get on a virtual machine (3.19.0-9-generic) and judging from other post, this seems to be a normal response.  If a norm exists ..

---

### Post by Cavsfan on 2015-03-31
> **Chanath said:**
> Does dist-upgrade would move to Systemd in Vivid?
Would it stay with Upstart in Trusty or would it too move to Systemd automatically?

In Vivid if you want systemd as default just install systemd-sysv. But they made the switch to systemd on March 9th.

[http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday](http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday)

Just open System monitor and check if systemd is PID 1. 

My ISO was from March 16th and it came with systemd and no option for upstart unless I wanted to install it.

IMO I wouldn't mess with Trusty as you'd have to install a ppa.

---

### Post by Cavsfan on 2015-03-31
So, I guess the final outcome is still up in the air? I misplaced this post in the wrong thread but not going to type it again. :p

[http://ubuntuforums.org/showthread.php?t=2270510&p=13251126#post13251126](http://ubuntuforums.org/showthread.php?t=2270510&p=13251126#post13251126)

---

### Post by Elfy on 2015-03-31
> **Cavsfan said:**
> So, I guess the final outcome is still up in the air? I misplaced this post in the wrong thread but not going to type it again. :p

[http://ubuntuforums.org/showthread.php?t=2270510&p=13251126#post13251126](http://ubuntuforums.org/showthread.php?t=2270510&p=13251126#post13251126)

I would be inclined towards assuming that systemd will be default. I've certainly seen no discussions lately pointing to any other outcome.

Anyone who between the 23rd October last and now has fiddled about with systemd and upstart will I suspect need to carry on fiddling about :)

What *they* will care about will be those installing or upgrading after 23rd April not people who've been testing since that started.

---

### Post by Cavsfan on 2015-03-31
> **Elfy said:**
> I would be inclined towards assuming that systemd will be default. I've certainly seen no discussions lately pointing to any other outcome.

Anyone who between the 23rd October last and now has fiddled about with systemd and upstart will I suspect need to carry on fiddling about :)

What *they* will care about will be those installing or upgrading after 23rd April not people who've been testing since that started.

Lol! Yeah that was my question whether it will come with both on the final release. 

I figured systemd will be default unless something big happens but I don't see that and I guess they would have to have upstart as a backup.

But we will just have to wait and see I guess. :)

I care because it will definitely impact my wiki if they offer both.

---

### Post by Chanath on 2015-03-31
> **Cavsfan said:**
> In Vivid if you want systemd as default just install systemd-sysv. But they made the switch to systemd on March 9th.

[http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday](http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday)

Just open System monitor and check if systemd is PID 1. 

My ISO was from March 16th and it came with systemd and no option for upstart unless I wanted to install it.

IMO I wouldn't mess with Trusty as you'd have to install a ppa.

OK, I won't mess with Trusty.
I see Systemd in Vivid; ```
systemd-analyze
Startup finished in 6.556s (kernel) + 32.738s (userspace) = 39.295s

```

and,
```
systemd-analyze blame
         15.749s systemd-udev-settle.service
          6.715s NetworkManager-wait-online.service
          6.374s dev-disk-by\x2duuid-e4f96153\x2df744\x2d44bf\x2d8594\x2d5fc3121
          5.783s plymouth-quit-wait.service

```

Maybe, I should get rid of the plymouth service? 
I see in System Monitor Upstart too. I don't know where is PID 1, though.

---

### Post by Cavsfan on 2015-03-31
> **Cavsfan said:**
> In Vivid if you want systemd as default just install systemd-sysv. But they made the switch to systemd on March 9th.

[http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday](http://linux.slashdot.org/story/15/03/06/1448247/ubuntu-to-officially-switch-to-systemd-next-monday)

Just open System monitor and check if systemd is PID 1. 

My ISO was from March 16th and it came with systemd and no option for upstart unless I wanted to install it.

IMO I wouldn't mess with Trusty as you'd have to install a ppa.

> **Chanath said:**
> OK, I won't mess with Trusty.
I see Systemd in Vivid; ```
systemd-analyze
Startup finished in 6.556s (kernel) + 32.738s (userspace) = 39.295s

```

and,
```
systemd-analyze blame
         15.749s systemd-udev-settle.service
          6.715s NetworkManager-wait-online.service
          6.374s dev-disk-by\x2duuid-e4f96153\x2df744\x2d44bf\x2d8594\x2d5fc3121
          5.783s plymouth-quit-wait.service

```

Maybe, I should get rid of the plymouth service? 
I see in System Monitor Upstart too. I don't know where is PID 1, though.

Plymouth should be OK. 

I thought ID in system monitor meant PID but apparently not. 

But you can still see it running. Sort it by Process Name perhaps.

[ATTACH=CONFIG]260998[/ATTACH]

I don't have upstart installed but it didn't come installed on the ISO so I didn't worry about it. I installed and it had major problems so I immediately uninstalled it.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy upstart
upstart:
  Installed: (none)
  Candidate: 1.13.2-0ubuntu10
  Version table:
     1.13.2-0ubuntu10 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages

```

---

### Post by Elfy on 2015-03-31
>  I figured systemd will be default unless something big happens but I don't see that and I guess they would have to have upstart as a backup.It IS already the backup. Not sure why you'd think not.

---

### Post by Cavsfan on 2015-03-31
> I figured systemd will be default unless something big happens but I  don't see that and I guess they would have to have upstart as a backup.

> **Elfy said:**
> It IS already the backup. Not sure why you'd think not.

Because I installed my Vivid Mate ISO on March 16th and I do not have upstart as an option.

All I can boot is systemd unless I installed upstart. I tried that and could not logout, restart or shutdown without cntl+alt+F1 to tty and login there and sudo reboot.
So, I immediately uninstalled upstart and the other 2 packages that came with it.

That is why.

---

### Post by cariboo on 2015-03-31
To see PID 1, open a terminal and run top.

---

### Post by Elfy on 2015-04-01
> **Cavsfan said:**
> Because I installed my Vivid Mate ISO on March 16th and I do not have upstart as an option....

Ever thought that might be a bug in Mate :)

In at least the 2 I've tried this morning - upstart is an option in the advanced grub stanza.

---

### Post by Cavsfan on 2015-04-01
> **cariboo907 said:**
> To see PID 1, open a terminal and run top.

Thanks I should have thought of top. I've used it before

> **Elfy said:**
> Ever thought that might be a bug in Mate :)

In at least the 2 I've tried this morning - upstart is an option in the advanced grub stanza.

I figured it was an anomaly. I also figured that systemd will be the default and upstart will be the option.

That will be fairly easy to put in the wiki. :)

---

### Post by Elfy on 2015-04-01
> **Cavsfan said:**
> ...


I figured it was an anomaly. I also figured that systemd will be the default and upstart will be the option.

That will be fairly easy to put in the wiki. :)

sort of talking to flexiondotorg about it

Edit - looking it seems the reason it doesn't is quite simple, it's not on the manifest, doesn't get installed

---

### Post by fjgaude on 2015-04-01
> **Elfy said:**
> It IS already the backup. Not sure why you'd think not.

That's the way it is with my Unity and Intel system. For me, systemd is simply way too slow, at 21 sec to boot versus upstart at less than 6 sec. I sure hope upstart is kept as the backup in grub menu.

---

### Post by Cavsfan on 2015-04-01
> **Elfy said:**
> [QUOTE=Cavsfan;13256721]

...

I figured it was an anomaly. I also figured that systemd will be the default and upstart will be the option.

That will be fairly easy to put in the wiki. :smile:

sort of talking to flexiondotorg about it

Edit - looking it seems the reason it doesn't is quite simple, it's not on the manifest, doesn't get installed[/QUOTE]

> **fjgaude said:**
> [QUOTE=Elfy;13256300]It IS already the backup. Not sure why you'd think not.

That's the way it is with my Unity and Intel system. For me, systemd is simply way too slow, at 21 sec to boot versus upstart at less than 6 sec. I sure hope upstart is kept as the backup in grub menu.[/QUOTE]

Just did a quick check of all the manifests and Upstart is on the April 1 vanilla Ubuntu Vivid ISO and the Xbuntu ISO only?

You have cat to be kitten me. :P I know this is April fools day but...

---

### Post by Elfy on 2015-04-01
> Just did a quick check of all the manifests and Upstart is on the April 1 vanilla Ubuntu Vivid ISO and the Xbuntu ISO only?

As I've said before - I only really look outside when checking something. 2 extra's ontop of what I actually care about is close enough :p

Not often I look at Lubuntu, Gnome or Kubuntu. 

(Myth and Edu aren't doing anything till 16.04 afaik)

Really just an assumption on my part that others would want to give people the chance to boot upstart simply.

---

### Post by Cavsfan on 2015-04-01
Good enough for me. :P

I wiped my vivid install and will pull the daily ISO and see what happens. Although we already know upstart won't be on there.

You can install upstart but when I did it was more of a pain than it was worth.

---

### Post by Cavsfan on 2015-04-08
With USB drive turned off. I didn't even see the bios screen. :p
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.246s (kernel) + 21.445s (userspace) = 25.691s

```

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze blame
          8.404s NetworkManager-wait-online.service
          5.866s systemd-udev-settle.service
          4.516s ModemManager.service
          4.165s NetworkManager.service
          3.728s dev-sda5.device
          3.421s accounts-daemon.service
          3.106s systemd-logind.service
          3.057s irqbalance.service
          3.057s apport.service
          3.053s grub-common.service
          3.053s loadcpufreq.service
          3.051s lm-sensors.service
          3.050s avahi-daemon.service
          3.047s rsyslog.service
          3.038s lightdm.service
          1.826s systemd-fsck-root.service
          1.362s apparmor.service
          1.167s systemd-udevd.service
          1.137s systemd-tmpfiles-setup-dev.service
          1.000s systemd-modules-load.service
           592ms plymouth-start.service
           561ms systemd-journald.service
           467ms dbus.service
           404ms systemd-tmpfiles-setup.service
           398ms resolvconf.service
           373ms systemd-setup-dgram-qlen.service
           372ms sys-kernel-debug.mount
           336ms upower.service
           331ms dev-mqueue.mount
           328ms dev-hugepages.mount
           306ms dev-disk-by\x2duuid-73666b59\x2db03d\x2d4554\x2d8899\x2d0aa4e2cd4b1a.swap
           300ms speech-dispatcher.service
           282ms systemd-udev-trigger.service
           281ms ondemand.service
           273ms console-setup.service
           227ms systemd-sysctl.service
           200ms polkitd.service
           178ms kmod-static-nodes.service
           171ms ufw.service
           162ms systemd-user-sessions.service
           159ms networking.service
           146ms systemd-vconsole-setup.service
           137ms systemd-journal-flush.service
           132ms pppd-dns.service
           108ms systemd-random-seed.service
           101ms systemd-update-utmp.service
            85ms udisks2.service
            81ms plymouth-read-write.service
            45ms systemd-remount-fs.service
            38ms user@120.service
            32ms udev-finish.service
            23ms kerneloops.service
            15ms rc-local.service
            12ms user@1000.service
            10ms ntp.service
             9ms dns-clean.service
             5ms cpufrequtils.service
             5ms alsa-restore.service
             4ms ifup-wait-all-auto.service
             3ms rtkit-daemon.service
             3ms ureadahead-stop.service
             3ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount
             1ms plymouth-quit-wait.service

```

I will say that Vivid goes into suspend mode in under 2 seconds. While Trusty and Mint go into suspend in about 4-5 seconds. FWIW.

---

### Post by ventrical on 2015-04-08
> **Cavsfan said:**
> Good enough for me. :P

I wiped my vivid install and will pull the daily ISO and see what happens. Although we already know upstart won't be on there.

You can install upstart but when I did it was more of a pain than it was worth.

Ayy??

Just did a daily current and Upstart is certainly  installed on the hard install as alternate option.

Regards..

---

### Post by ventrical on 2015-04-08
> **fjgaude said:**
> That's the way it is with my Unity and Intel system. For me, systemd is simply way too slow, at 21 sec to boot versus upstart at less than 6 sec. I sure hope upstart is kept as the backup in grub menu.

I have been experimenting with my OC box which is a legacy LGA775 socket and will only overclock single cores and systemD has significantly increased the startup time at high overclocks with the exception of a thermal-fault-limit error  which is an f/p and ignored.

 I do not see much of a difference on my newer hardware. My fastest MSi box will boot in 3 seconds with systemD or upstart .. it doesn't seem to discriminate, but it may improve older systems and SATA I and SATA II version boxes bootup time.

Regards..

---

### Post by fjgaude on 2015-04-08
```

```frank@flash:~$ sudo systemd-analyze blame
          8.266s NetworkManager-wait-online.service
          7.144s systemd-udev-settle.service
           402ms dev-disk-by\x2duuid-a8d5f6b2\x2d1f67\x2d4f71\x2d84f9\x2d437fa4a
           280ms vboxdrv.service
           198ms NetworkManager.service
           163ms ModemManager.service
           138ms plymouth-quit-wait.service
           118ms accounts-daemon.service
           114ms binfmt-support.service
            99ms avahi-daemon.service
            95ms systemd-logind.service
            94ms rsyslog.service
            92ms grub-common.service
            89ms lm-sensors.service
            89ms speech-dispatcher.service
            88ms irqbalance.service
            88ms apport.service
            86ms bluetooth.service
            85ms thermald.service
            83ms pppd-dns.service
            83ms systemd-user-sessions.service
            83ms ifup-wait-all-auto.service
            82ms rtkit-daemon.service

frank@flash:~$ sudo systemd-analyze
Startup finished in 1.107s (kernel) + 15.908s (userspace) = 17.015s
```

```

I can use from the grub menu either upstart or systemd as the default. I don't see why systemd takes longer to boot. I guess in the long run it doesn't make that much difference, considering we don't boot very often.

My main system: Ubuntu Unity Linux on Z87 Haswell motherboard, ASRock Model Z87E-ITX with Intel i5-4670K CPU 3.4GHz (800MHz-4.0GHz overclock), HD4600 video, Titan CU30 cooler, 16G DDR3 G.Skill 2400MHz, Plextor M5S 256G and M5P 128G SSDs, WD VelociRaptor WD5000BHTZ 500G HDD, 300W SFX psu, latest UEFI BIOS 2.50. Suspend and Resume without issue. Booting fast, 5 to 20 seconds, from either Plextor SSD or VelociRaptor HDD in Lian Li PC-Q30X case. ASUS Monitor, 27" WQHD, 2560 x 1440 pixels.

Thanks for all the info, Ventrical!

---

### Post by ventrical on 2015-04-08
[s]A lot of info from systemd-analyze is not accurate .. ie;[/s]

```

ventrical@ventrical-MS-7798:~$ sudo systemd-analyze blame
    1min 30.143s powerd.service
         28.433s NetworkManager-wait-online.service
           929ms click-system-hooks.service
           464ms dev-disk-by\x2duuid-4da84d6c\x2dae00\x2d472b\x2da337\x2da0c029d
           452ms nmbd.service
           426ms samba-ad-dc.service
           397ms systemd-udev-settle.service
           305ms NetworkManager.service
           296ms ModemManager.service
           281ms ufw.service
           245ms lxc-net.service
           242ms accounts-daemon.service
           239ms lightdm.service
           211ms apparmor.service
           207ms user@1000.service
           199ms rsyslog.service
           197ms systemd-logind.service
           185ms lm-sensors.service
           182ms plymouth-read-write.service
           181ms grub-common.service
           179ms avahi-daemon.service
           160ms thermald.service
           158ms irqbalance.service
           153ms ondemand.service
           149ms smbd.service
           130ms networking.service
            86ms console-setup.service
            84ms systemd-journald.service
            74ms kerneloops.service
            70ms systemd-fsck-root.service
            59ms udisks2.service
            57ms alsa-restore.service
            57ms systemd-udevd.service
            57ms ifup-wait-all-auto.service
            56ms colord.service
            55ms console-kit-log-system-start.service
            50ms pppd-dns.service
            48ms speech-dispatcher.service
            47ms lxc.service
            47ms systemd-user-sessions.service
            47ms apport.service
            47ms systemd-udev-trigger.service
            46ms dbus.service
            43ms dns-clean.service
            42ms systemd-tmpfiles-setup-dev.service
            41ms plymouth-start.service
            35ms polkitd.service
            35ms plymouth-quit-wait.service
            27ms systemd-tmpfiles-setup.service
            20ms sys-kernel-debug.mount
            20ms resolvconf.service
            19ms pulseaudio.service
            19ms systemd-modules-load.service
            18ms dev-hugepages.mount
            18ms ofono.service
            16ms dev-mqueue.mount
            16ms ifup@eth0.service
            15ms systemd-backlight@backlight:acpi_video0.service
            15ms systemd-sysctl.service
            13ms upower.service
            12ms dev-disk-by\x2duuid-3387bf26\x2d1c95\x2d44f3\x2db194\x2d9b6f353
            11ms systemd-update-utmp.service
            11ms ntp.service
            11ms systemd-vconsole-setup.service
            10ms systemd-journal-flush.service
             9ms rtkit-daemon.service
             8ms kmod-static-nodes.service
             7ms ifup@lxcbr0.service
             7ms udev-finish.service
             6ms systemd-remount-fs.service
             6ms systemd-random-seed.service
             5ms ureadahead-stop.service
             5ms lvm2.service
             4ms systemd-update-utmp-runlevel.service
             4ms rc-local.service
             2ms sys-fs-fuse-connections.mount
ventrical@ventrical-MS-7798:~$ sudo systemd-analyze
Startup finished in 1.156s (kernel) + 1min 30.977s (userspace) = 1min 32.134s
ventrical@ventrical-MS-7798:~$ 

```

 but I tell you my pc boots in about 3 seconds & 3/4 of a second to load from unity-greeter and all programs are on demand with only fractions of a second to load program like Libre Office so I would not take the info from systemd-analyze as bare metal standard.

Regards..

---

### Post by Cavsfan on 2015-04-08
> **ventrical said:**
> Ayy??

Just did a daily current and Upstart is certainly  installed on the hard install as alternate option.

Regards..

I just checked the manifests and upstart is not listed except on Ubuntu and Xubuntu.
Just like a week or so ago.

[LIST=1]
[*]Ubuntu - Upstart 
[*]Kubuntu - no Upstart 
[*]Xubuntu - Upstart 
[*]Lubuntu - no Upstart 
[*]Ubuntu GNOME - no Upstart 
[*]Ubuntu Mate - no Upstart 
[/LIST]

regards

---

### Post by Mateusz Stachowski on 2015-04-08
> **ventrical said:**
> A lot of info from systemd-analyze is not accurate .. ie;

```

ventrical@ventrical-MS-7798:~$ sudo systemd-analyze blame
    1min 30.143s powerd.service
         28.433s NetworkManager-wait-online.service
           929ms click-system-hooks.service
           464ms dev-disk-by\x2duuid-4da84d6c\x2dae00\x2d472b\x2da337\x2da0c029d
           452ms nmbd.service
           426ms samba-ad-dc.service
           397ms systemd-udev-settle.service
           305ms NetworkManager.service
           296ms ModemManager.service
           281ms ufw.service
           245ms lxc-net.service
           242ms accounts-daemon.service
           239ms lightdm.service
           211ms apparmor.service
           207ms user@1000.service
           199ms rsyslog.service
           197ms systemd-logind.service
           185ms lm-sensors.service
           182ms plymouth-read-write.service
           181ms grub-common.service
           179ms avahi-daemon.service
           160ms thermald.service
           158ms irqbalance.service
           153ms ondemand.service
           149ms smbd.service
           130ms networking.service
            86ms console-setup.service
            84ms systemd-journald.service
            74ms kerneloops.service
            70ms systemd-fsck-root.service
            59ms udisks2.service
            57ms alsa-restore.service
            57ms systemd-udevd.service
            57ms ifup-wait-all-auto.service
            56ms colord.service
            55ms console-kit-log-system-start.service
            50ms pppd-dns.service
            48ms speech-dispatcher.service
            47ms lxc.service
            47ms systemd-user-sessions.service
            47ms apport.service
            47ms systemd-udev-trigger.service
            46ms dbus.service
            43ms dns-clean.service
            42ms systemd-tmpfiles-setup-dev.service
            41ms plymouth-start.service
            35ms polkitd.service
            35ms plymouth-quit-wait.service
            27ms systemd-tmpfiles-setup.service
            20ms sys-kernel-debug.mount
            20ms resolvconf.service
            19ms pulseaudio.service
            19ms systemd-modules-load.service
            18ms dev-hugepages.mount
            18ms ofono.service
            16ms dev-mqueue.mount
            16ms ifup@eth0.service
            15ms systemd-backlight@backlight:acpi_video0.service
            15ms systemd-sysctl.service
            13ms upower.service
            12ms dev-disk-by\x2duuid-3387bf26\x2d1c95\x2d44f3\x2db194\x2d9b6f353
            11ms systemd-update-utmp.service
            11ms ntp.service
            11ms systemd-vconsole-setup.service
            10ms systemd-journal-flush.service
             9ms rtkit-daemon.service
             8ms kmod-static-nodes.service
             7ms ifup@lxcbr0.service
             7ms udev-finish.service
             6ms systemd-remount-fs.service
             6ms systemd-random-seed.service
             5ms ureadahead-stop.service
             5ms lvm2.service
             4ms systemd-update-utmp-runlevel.service
             4ms rc-local.service
             2ms sys-fs-fuse-connections.mount
ventrical@ventrical-MS-7798:~$ sudo systemd-analyze
Startup finished in 1.156s (kernel) + 1min 30.977s (userspace) = 1min 32.134s
ventrical@ventrical-MS-7798:~$ 

```

 but I tell you my pc boots in about 3 seconds & 3/4 of a second to load from unity-greeter and all programs are on demand with only fractions of a second to load program like Libre Office so I would not take the info from systemd-analyze as bare metal standard.

Regards..

Just because you see desktop much sooner and can run programs doesn't mean that the init (in this case systemd) finished starting all the services.

For example I had a ready to use Unity booted with systemd after about 40 or 50 seconds but I didn't have the most important thing internet connection active. When checking out systemd-analyze it would show me 2 min 30 sec for boot. Then the blame showed that ifup-wait-all-auto.service took that 2 minutes. Those two minutes are the maximum set for this service. Even after that time I didn't have internet so I went back to Upstart. Systemd didn't have any benefits for me in boot up time so nothing lost here.

I'm not sure if the devs fixed the problems with ifup-wait-all-auto.service because I see it mentioned in the changelogs of systemd and ifupdown all the time. There was several changes made to this service in the past weeks. The last one in ifupdown on 4th April.

[https://lists.ubuntu.com/archives/vivid-changes/2015-April/007830.html](https://lists.ubuntu.com/archives/vivid-changes/2015-April/007830.html)

---

### Post by ventrical on 2015-04-08
> **Mateusz Stachowski said:**
> Just because you see desktop much sooner and can run programs doesn't mean that the init (in this case systemd) finished starting all the services.

For example I had a ready to use Unity booted with systemd after about 40 or 50 seconds but I didn't have the most important thing internet connection active. When checking out systemd-analyze it would show me 2 min 30 sec for boot. Then the blame showed that ifup-wait-all-auto.service took that 2 minutes. Those two minutes are the maximum set for this service. Even after that time I didn't have internet so I went back to Upstart. Systemd didn't have any benefits for me in boot up time so nothing lost here.

I'm not sure if the devs fixed the problems with ifup-wait-all-auto.service because I see it mentioned in the changelogs of systemd and ifupdown all the time. There was several changes made to this service in the past weeks. The last one in ifupdown on 4th April.

[https://lists.ubuntu.com/archives/vivid-changes/2015-April/007830.html](https://lists.ubuntu.com/archives/vivid-changes/2015-April/007830.html)

Yes .. thanks for pointing this out. I stand corrected.

---

### Post by ventrical on 2015-04-08
> **Cavsfan said:**
> I just checked the manifests and upstart is not listed except on Ubuntu and Xubuntu.
Just like a week or so ago.

[LIST=1]
[*]Ubuntu - Upstart 
[*]Kubuntu - no Upstart 
[*]Xubuntu - Upstart 
[*]Lubuntu - no Upstart 
[*]Ubuntu GNOME - no Upstart 
[*]Ubuntu Mate - no Upstart 
[/LIST]

regards

From your original post I assumed you were speaking of all the ubuntus.

Regards..

---

### Post by Cavsfan on 2015-04-09
> **Cavsfan said:**
> I just checked the manifests and upstart is not listed except on Ubuntu and Xubuntu.
Just like a week or so ago.

[LIST=1]
[*]Ubuntu - Upstart 
[*]Kubuntu - no Upstart 
[*]Xubuntu - Upstart 
[*]Lubuntu - no Upstart 
[*]Ubuntu GNOME - no Upstart 
[*]Ubuntu Mate - no Upstart 
[/LIST]

regards

> **ventrical said:**
> From your original post I assumed you were speaking of all the ubuntus.

Regards..

Indeed I was. That's why I listed them. But now I notice the Ubuntu ISO is still dated 26-Mar-2015.
The rest are either 8-Apr-2015 or 9-Apr-2015.

I don't understand why they're not all providing both Systemd and Upstart. Not that I'm worried or anything.
But all I have it Systemd.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Apr 2 08:24

```


regards

---

### Post by QDR06VV9 on 2015-04-09
> **Cavsfan said:**
> Indeed I was. That's why I listed them. But now I notice the Ubuntu ISO is still dated 26-Mar-2015.
The rest are either 8-Apr-2015 or 9-Apr-2015.

I don't understand why they're not all providing both Systemd and Upstart. Not that I'm worried or anything.
But all I have it Systemd.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Apr 2 08:24

```


regards
Hi there Cavsfan. I just checked from [here]("http://cdimage.ubuntu.com/ubuntu-mate/releases/15.04/beta-1/ubuntu-mate-15.04-beta1-desktop-powerpc.manifest")
And it shows me ubuntu-mate 2/26/15
```
upstart    1.13.2-0ubuntu7
system-tools-backends    2.10.2-2
systemd    219-3ubuntu1
systemd-shim    9-1
sysv-rc    2.88dsf-53.2ubuntu9
sysvinit-utils    2.88dsf-53.2ubuntu9
```
But I have seen those in the manifests since the first beta release:D

---

### Post by Cavsfan on 2015-04-09
> **Cavsfan said:**
> Indeed I was. That's why I listed them. But now I notice the Ubuntu ISO is still dated 26-Mar-2015.
The rest are either 8-Apr-2015 or 9-Apr-2015.

I don't understand why they're not all providing both Systemd and Upstart. Not that I'm worried or anything.
But all I have it Systemd.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Apr 2 08:24

```


regards

> **runrickus said:**
> Hi there Cavsfan. I just checked from [here]("http://cdimage.ubuntu.com/ubuntu-mate/releases/15.04/beta-1/ubuntu-mate-15.04-beta1-desktop-powerpc.manifest")
And it shows me ubuntu-mate 2/26/15
```
upstart    1.13.2-0ubuntu7
system-tools-backends    2.10.2-2
systemd    219-3ubuntu1
systemd-shim    9-1
sysv-rc    2.88dsf-53.2ubuntu9
sysvinit-utils    2.88dsf-53.2ubuntu9
```
But I have seen those in the manifests since the first beta release:D

Thanks! I guess the manifests are not correct then. But I'm not going to re-install until after the 26th though. Systemd runs fine for me. :)

But that manifest says it's from the powerpc ISO. I only looked at the 64 bit amd desktop ISOs.

I'm just getting a problem fixed that I created from not thinking about what Kansasnoob said about the 14.04.2 installs in a previous post in this thread. 

The mistake I made was not in re-installing 14.04, it was in formatting my original 14.04 DVD and downloading the 14.04.2 one.

Since my install had upgraded to 14.04.2 and had the 3.13 kernel I didn't give it a thought. 

But when I installed 14.04.2 from ISO it didn't come with the 3.13 kernel but the 3.16 kernel which makes it only good until 2016. :shock:

So, for 2 or more hours I searched high and low for the 14.04.1 ISO and finally found it. :D Trust me _that ISO is hard to find_! I kept seeing 14.04.1 ISOs only to lead to a download of a 14.04.2 ISO.

Could NOT find anything other than the Ubuntu ISO so I installed Flashback with Compiz (gotta have the eye candy of course) :lol:

I installed it and got the 3.13 kernel back and it's good until 2019! :KS

I kind of had to learn that the hard way. I didn't even realize the kernels changed until today when a new kernel came through in updates. That's when panic set in. :oops:

But everything is once again hunky dorey here in Cavfan land lol.

[SIZE=3]So, a big warning to ya'll out there if you've got Trusty installed from early on you are good but if you do a clean install with the 14.04.2 ISO it's only good until 2016 and not 2019 as expected.[/SIZE]

I guess I better make a thread about this in general help instead of getting off topic here. But it is not something you want to go through to keep your LTS.

---

### Post by cariboo on 2015-04-09
I was doing a little reading about systemd when I found a command that creates a chart similar to bootchart:

```
systemd-analyze plot > plot.xml
```

which creates an xml file that can be opened in a web browser.

---

### Post by zika on 2015-04-10
> **Cavsfan said:**
> [SIZE=3]So, a big warning to ya'll out there if you've got Trusty installed from early on you are good but if you do a clean install with the 14.04.2 ISO it's only good until 2016 and not 2019 as expected.[/SIZE]This conclusion (apart from the size of letters ;)) would be true only if repositories were different... ;) It looks just like a branch(ing) (with obvious reasons) regarding kernel which is easy to change/remedy if someone finds a need to do that... ;)

---

### Post by Cavsfan on 2015-04-11
> **runrickus said:**
> Hi there Cavsfan. I just checked from [here]("http://cdimage.ubuntu.com/ubuntu-mate/releases/15.04/beta-1/ubuntu-mate-15.04-beta1-desktop-powerpc.manifest")
And it shows me ubuntu-mate 2/26/15
```
upstart    1.13.2-0ubuntu7
system-tools-backends    2.10.2-2
systemd    219-3ubuntu1
systemd-shim    9-1
sysv-rc    2.88dsf-53.2ubuntu9
sysvinit-utils    2.88dsf-53.2ubuntu9
```
But I have seen those in the manifests since the first beta release:D

Hey runrickus!
I just noticed that was from the beta1. But on the beta2 [here]("http://cdimage.ubuntu.com/ubuntu-mate/releases/vivid/beta-2/ubuntu-mate-15.04-beta2-desktop-i386.manifest") it is not listed. :D

Nor is it listed on today's Mate ISO either [here]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/vivid-desktop-amd64.manifest").

> **cariboo907 said:**
> I was doing a little reading about systemd when I found a command that creates a chart similar to bootchart:

```
systemd-analyze plot > plot.xml
```

which creates an xml file that can be opened in a web browser.

That does provide a pretty informative output. 

It would seem fairly accurate on my old system but I still can't tell the difference between 15.05 booting and 14.04 booting very much at least.

They are pretty fast though. Windows 7 is quite another story.

 I could go make a sammich or get a cup of coffee and maybe when I got back it would be done booting up. :lol:

---

### Post by fjgaude on 2015-04-11
Sure gives us a lot of the load information, but what does it mean? My bootup with systemd is 15 seconds slower than upstart from the grub menu.

---

### Post by QDR06VV9 on 2015-04-11
> **Cavsfan said:**
> Hey runrickus!
I just noticed that was from the beta1. But on the beta2 [here]("http://cdimage.ubuntu.com/ubuntu-mate/releases/vivid/beta-2/ubuntu-mate-15.04-beta2-desktop-i386.manifest") it is not listed. :D

Nor is it listed on today's Mate ISO either [here]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/vivid-desktop-amd64.manifest").

It now seems harder to tell what packages is coming or going:rolleyes:  
Hope Upstart will be in Synaptic or software-manager at time of release![-o<
Thanks for the Heads-up Cavsfan;)

---

### Post by Cavsfan on 2015-04-11
> **fjgaude said:**
> Sure gives us a lot of the load information, but what does it mean? My bootup with systemd is 15 seconds slower than upstart from the grub menu.

I am not sure why systemd would boot so slow - my system boots normally and I don't have the option for upstart.

> **runrickus said:**
> It now seems harder to tell what packages is coming or going:rolleyes:  
Hope Upstart will be in Synaptic or software-manager at time of release![-o<
Thanks for the Heads-up Cavsfan;)

You're welcome. ;) I'm fairly sure the final release will include both as that has been stated more than once. 

But for some odd reason it only comes on 2 flavors while we're testing it, which seems to me a little ironic.

---

### Post by fjgaude on 2015-04-11
I have the option for upstart but systemd is the default. Hmmm... maybe I'll wait to see what the release version is like, with a fresh install. Thanks!

---

### Post by craig10x on 2015-04-16
Off topic...but i was just wondering...i know that thursday will be 15.04 RC and final release will be next thursday.  I usually like to upgrade about a day or two before final release (to avoid the busy servers) but was thinking of doing it over this weekend...I was just wondering, at this point, are you getting many daily updates on your software updater in 15.04 development? Or is it pretty quiet at this point?

---

### Post by fjgaude on 2015-04-16
Yes, I'm getting daily updates of 20 to 40 files... I'd wait three days after release to update if I were you. <smile>

---

### Post by craig10x on 2015-04-16
Thanks...i know in the past when i did it about 2 days before release, there wasn't much coming up on the updater, but i wasn't sure how it was about a week before final release...

---

### Post by Elfy on 2015-04-16
This IS the dev support channel, we do that whole running the dev version for ages.

If you want the easy way, install the day before and hope nothing was actually going wrong in the days before.

If you don't want to do that please post an ' is it there yet thread' elsewhere that I can merge with the rest - thanks.

The answer to your particular question is really no different now than it was 5 or 6 years ago.

---

### Post by craig10x on 2015-04-17
No problem, Elfy...in the past, i was sometimes active as a development tester, but now i just kind of jump in at the very end of it, just to avoid the busy server rush on the final release ;)
And i was just wondering if the updates had slowed down at this point, since it's only 1 week to final now...I know it's been pretty reliable because i have tested development on live sessions along the way every once in a while, including recently (when beta 2 came out)...

---

### Post by Elfy on 2015-04-17
bunches of updates today ;)

---

### Post by fjgaude on 2015-04-17
Yes, 61 files updated today.

---

### Post by craig10x on 2015-04-17
Probably a lot of last minute bug fixes since final release is so close now...
Oh, what the heck... i will probably do the upgrade this weekend...after all, what's a few bunches :mrgreen:

Oh, then of course, i'd be able to both report on how the "in place" upgrade went at the end of development cycle AND even make an observation about how systemd is working on my newly installed 15.04 ;)

---

### Post by Cavsfan on 2015-04-17
The final release ISO will never change after the 23th. 

So, if you wait 2 days or whatever after the 23th the ISO will be the same there just may be some updates afterwards.

Utopic was released on October 23rd 2014 and the ISOs are still dated that day.

[http://releases.ubuntu.com/14.10/](http://releases.ubuntu.com/14.10/)

---

### Post by Cavsfan on 2015-04-17
I still do not understand why Upstart is not on the manifests of any of the ISOs except 2 still. :-k

---

### Post by craig10x on 2015-04-17
@Cavsfan:  I did the upgrade...went 100% smooth as they usually do for me...all apps, settings, data retained...just 2 items got knocked off the unity launcher (screenshot and calculator) so just had to pin those back on the launcher...will do some checking later, but everything seems fine...as far as the boot up with systemd, it seemed about the same as before (using 14.10 without systemd of course), didn't notice much difference...

---

### Post by fjgaude on 2015-04-17
Well, well! Here's poor situation with systemd:

```

frank@flash:~$ sudo systemd-analyze (14.10 9/25/14)
Startup finished in 886ms (kernel) + 5.013s (userspace) = 5.899s
frank@flash:~$ sudo systemd-analyze (15.04 12/27/14)
Startup finished in 890ms (kernel) + 5.808s (userspace) = 6.699s
frank@flash:~$ sudo systemd-analyze (15.04 4/11/15)
Startup finished in 946ms (kernel) + 16.069s (userspace) = 17.015s
```

I'll do a clean install of 15.04 after it is released and see if **systemd** is competitive with **upstart**.

---

### Post by Cavsfan on 2015-04-17
> **craig10x said:**
> @Cavsfan:  I did the upgrade...went 100% smooth as they usually do for me...all apps, settings, data retained...just 2 items got knocked off the unity launcher (screenshot and calculator) so just had to pin those back on the launcher...will do some checking later, but everything seems fine...as far as the boot up with systemd, it seemed about the same as before (using 14.10 without systemd of course), didn't notice much difference...

Did you get systemd and upstart as a backup. I haven't been able to use upstart for over a month. 
I tried installing it but it was bad - every logout, restart and shutdown button was greyed out so I un-installed it. Luckily I had Cairo Dock to logout with.

> **fjgaude said:**
> I'll do a clean install of 15.04 after it is released and see if **systemd** is competitive with **upstart**.

Indeed me too I'll wait.

---

### Post by craig10x on 2015-04-17
Both are installed (according to package manager)...i assume systemd is default (don't know how you check that)...

---

### Post by fjgaude on 2015-04-17
Yes, it's the default. When you boot, use the grub menu Advanced option and then you see both systemd and upstart.

---

### Post by Cavsfan on 2015-04-17
So, you just did an upgrade from Utopic and got both systemd and upstart?
This is taken from my /boot/grub/grub.cfg file upon booting there is no upstart option. There would be an init= on the upstart boot line and there is none.

```
### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  51cdc344-58c1-4f4d-842a-e89abdf53c2a
    else
      search --no-floppy --fs-uuid --set=root 51cdc344-58c1-4f4d-842a-e89abdf53c2a
    fi
    linux    /boot/vmlinuz-3.19.0-14-generic root=UUID=51cdc344-58c1-4f4d-842a-e89abdf53c2a ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-14-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
    menuentry 'Ubuntu, with Linux 3.19.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-14-generic-advanced-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  51cdc344-58c1-4f4d-842a-e89abdf53c2a
        else
          search --no-floppy --fs-uuid --set=root 51cdc344-58c1-4f4d-842a-e89abdf53c2a
        fi
        echo    'Loading Linux 3.19.0-14-generic ...'
        linux    /boot/vmlinuz-3.19.0-14-generic root=UUID=51cdc344-58c1-4f4d-842a-e89abdf53c2a ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-14-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-14-generic-recovery-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  51cdc344-58c1-4f4d-842a-e89abdf53c2a
        else
          search --no-floppy --fs-uuid --set=root 51cdc344-58c1-4f4d-842a-e89abdf53c2a
        fi
        echo    'Loading Linux 3.19.0-14-generic ...'
        linux    /boot/vmlinuz-3.19.0-14-generic root=UUID=51cdc344-58c1-4f4d-842a-e89abdf53c2a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-14-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-13-generic-advanced-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  51cdc344-58c1-4f4d-842a-e89abdf53c2a
        else
          search --no-floppy --fs-uuid --set=root 51cdc344-58c1-4f4d-842a-e89abdf53c2a
        fi
        echo    'Loading Linux 3.19.0-13-generic ...'
        linux    /boot/vmlinuz-3.19.0-13-generic root=UUID=51cdc344-58c1-4f4d-842a-e89abdf53c2a ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-13-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-13-generic-recovery-51cdc344-58c1-4f4d-842a-e89abdf53c2a' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  51cdc344-58c1-4f4d-842a-e89abdf53c2a
        else
          search --no-floppy --fs-uuid --set=root 51cdc344-58c1-4f4d-842a-e89abdf53c2a
        fi
        echo    'Loading Linux 3.19.0-13-generic ...'
        linux    /boot/vmlinuz-3.19.0-13-generic root=UUID=51cdc344-58c1-4f4d-842a-e89abdf53c2a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-13-generic
    }
}

### END /etc/grub.d/10_linux ###
```

I guess I could install it again but I'm not going to because I'm not going to do anything special.
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy upstart
upstart:
  Installed: (none)
  Candidate: 1.13.2-0ubuntu13
  Version table:
     1.13.2-0ubuntu13 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages

```

I will wait until final release on the 23rd. Right now the beta2 ISOs for Ubuntu and Xubuntu are the only 2 that offer upstart as an option.
I do not get why that is.

---

### Post by craig10x on 2015-04-18
By the way, only release critical fixes should be coming in on the updates now (as of the 16th and until final release on the 23rd)...
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Final-Freeze](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Final-Freeze)
I must say, it is running very stable and very zippy...should be a nice release :D
systemd seems to be ok...but i don't really notice much difference...i do see something on the screen as i am shutting down (before it goes to the shut down background) but it goes by so fast, i can't get to read it...anybody else getting that?  (not a big deal but was just curious)...it does shut down fast, though...boot up seems about the same time...maybe a few seconds slower during the initial process...

edit: was able to read what appears on the screen as i am shutting down, it says "light display manager" and underneath that "acpi"...was wondering if anyone else gets that?
oh, and interestingly enough, i got some updates in the afternoon, and since then, the boot up seems more normal as fara s the amount of time it takes and shut down is very fast...

---

### Post by QDR06VV9 on 2015-04-18
> **craig10x said:**
> Both are installed (according to package manager)...i assume systemd is default _[COLOR=#ff0000](don't know how you check that)..[/COLOR]_.

This is an example on mine craig10x
```
me@me-Aspire-M3300:~$ pidof systemd && echo "systemd" || echo "other"
other
me@me-Aspire-M3300:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit
```
The one(1) indicates i am using upstart and also below the 1 it shows "sysvinit"
Regards;)

---

### Post by craig10x on 2015-04-18
Thanks runrickus ;)
Oh, and a friend that uses another linux distro that also uses systemd told me that what i see on the screen as i am shutting down is apparently normal for systemd (where it mentions about light dm and acpi)...

---

### Post by Cavsfan on 2015-04-18
```
cavsfan@cavsfan-MS-7529:~$ pidof systemd && echo "systemd" || echo "other"
1151
systemd
cavsfan@cavsfan-MS-7529:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1151
sysvinit

```

Fairly odd... Although top shows systemd PID to be 1 as well as my conky top 10 processes.

I asked you craig10x and fjgaude if you did an upgrade from utopic to vivid and got upstart along with systemd. I don't believe either of you responded.
Just curious how you got both unless you installed from a Ubuntu or Xubuntu ISO.

---

### Post by QDR06VV9 on 2015-04-18
> **Cavsfan said:**
> ```
cavsfan@cavsfan-MS-7529:~$ pidof systemd && echo "systemd" || echo "other"
1151
systemd
cavsfan@cavsfan-MS-7529:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1151
sysvinit

```

Fairly odd... Although top shows systemd PID to be 1 as well as my conky top 10 processes.

I asked you craig10x and fjgaude if you did an upgrade from utopic to vivid and got upstart along with systemd. I don't believe either of you responded.
Just curious how you got both unless you installed from a Ubuntu or Xubuntu ISO.
Sorry Cavsfan I know you asked others, but I had to install it and then that makes it run as default.):P
Just uninstall it to go back to systemd.
Also see here [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

### Post by Cavsfan on 2015-04-18
Thanks for the reply. I'm not doing anything out of the ordinary as many people with little knowledge of all this would do.

I'll wait until final release and download it, hopefully finding a torrent which is much faster than an ISO will be just after release. I'm using Vivid Mate and I believe there are torrents available.

There probably will be on this site: [https://ubuntu-mate.org/vivid/](https://ubuntu-mate.org/vivid/)

I shall expect that it comes with both.

---

### Post by Cavsfan on 2015-04-23
I just installed the final release ISO Vivid Mate 15.04 and it _did not_ come with upstart.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy upstart
upstart:
  Installed: (none)
  Candidate: 1.13.2-0ubuntu13
  Version table:
     1.13.2-0ubuntu13 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages

```

Guess I'd have to install it if I wanted it.

---

### Post by zika on 2015-04-23
Nice conundrum to (re)solve:```
:~$ sudo apt-get purge -s upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntu-desktop* unity* unity-greeter* unity-tweak-tool* upstart*
  upstart-bin*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg ubuntu-desktop [1.334]
Purg unity-tweak-tool [0.0.6ubuntu2]
Purg unity [7.3.2+15.04.20150420-0ubuntu1]
Purg unity-greeter [15.04.4-0ubuntu1]
Purg upstart-bin [1.13.2-0ubuntu13]
Purg upstart [1.13.2-0ubuntu13]
```... ;)

---

### Post by Cavsfan on 2015-04-23
> **zika said:**
> Nice conundrum to (re)solve:```
:~$ sudo apt-get purge -s upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntu-desktop* unity* unity-greeter* unity-tweak-tool* upstart*
  upstart-bin*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg ubuntu-desktop [1.334]
Purg unity-tweak-tool [0.0.6ubuntu2]
Purg unity [7.3.2+15.04.20150420-0ubuntu1]
Purg unity-greeter [15.04.4-0ubuntu1]
Purg upstart-bin [1.13.2-0ubuntu13]
Purg upstart [1.13.2-0ubuntu13]
```... ;)

I installed it and once again it has no ability to logoff, restart, suspend or shutdown. I even booted twice to be sure there is a problem and yes there is.

Here's all I get:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge upstart
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  upstart*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,741 kB disk space will be freed.
Do you want to continue? [Y/n] 
```

But, on Mate at least it's worthless. Systemd is working well. ;)

---

### Post by QDR06VV9 on 2015-04-23
Well that sucks! I am running Mate also, Upstart is Still my 1st choice(although not for long) as that choice will be taken away from me soon.
```
me@me-Aspire-M3300:~$ pidof systemd && echo "systemd" || echo "other"
other
me@me-Aspire-M3300:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit

``` 
Must be lucky I have not had a single hiccup yet.
```
System:    Host: me-Aspire-M3300 Kernel: 4.0.0-040000-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.04 vivid
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 1400/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 4000.8GB (38.2% used)
Info:      Processes: 208 Uptime: 3:55 Memory: 999.0/5967.1MB
           Client: Shell (bash) inxi: 2.2.16 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
Linux me-Aspire-M3300 4.0.0-040000-lowlatency #201504121935 SMP PREEMPT Sun Apr 12 23:45:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Cavsfan on 2015-04-23
> **runrickus said:**
> Well that sucks! I am running Mate also, Still my 1st choice(although not for long) as that choice will be taken away from me soon.
```
me@me-Aspire-M3300:~$ pidof systemd && echo "systemd" || echo "other"
other
me@me-Aspire-M3300:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit

``` 
Must be lucky I have not had a single hiccup yet.
```
System:    Host: me-Aspire-M3300 Kernel: 4.0.0-040000-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.04 vivid
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 1400/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 4000.8GB (38.2% used)
Info:      Processes: 208 Uptime: 3:55 Memory: 999.0/5967.1MB
           Client: Shell (bash) inxi: 2.2.16 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
Linux me-Aspire-M3300 4.0.0-040000-lowlatency #201504121935 SMP PREEMPT Sun Apr 12 23:45:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Why will it be taken away? Because you like me just jump from one developmental version to the next? We can still test the next Mate version of Wascally Wabbit. :P

I have 2 LTSs installed which are good until 2019. 

While I've got upstart installed:
```
cavsfan@cavsfan-MS-7529:~$ pidof systemd && echo "systemd" || echo "other"
1088
systemd
cavsfan@cavsfan-MS-7529:~$ pidof /sbin/init && echo "sysvinit" || echo "other"
1088
sysvinit
```

Which is odd because top says it is PID 1.

---

### Post by QDR06VV9 on 2015-04-23
> **Cavsfan said:**
> Why will it be taken away? Because you like me just jump from one developmental version to the next? We can still test the next Mate version of Wascally Wabbit. :P


Yep just like you I jump from cycle to cycle.
But I too run Three 14.04 LTS Os's
Plus I'm sure you have seen this already
> As stated on the mailing list few months ago ([https://lists.ubuntu.com/archives/ub...er/015154.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html")),  
Ubuntu never offered a choice of init system, and won't start doing   that. systemd is mandatory to be the supported ubuntu path. That's the   reason 
why ubuntu-standard won't depend on systemd|upstart.
 Note that for some kernel reasons, the Touch image is still using upstart, but that will change in the future.
Plus This link to confirm [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html)

I wish I could get you to try [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia]("https://launchpad.net/%7Emamarley/+archive/ubuntu/nvidia")
Try it You'll Like it:p

---

### Post by Cavsfan on 2015-04-24
> **runrickus said:**
> Yep just like you I jump from cycle to cycle.
But I too run Three 14.04 LTS Os's
Plus I'm sure you have seen this already

> As stated on the mailing list few months ago ([https://lists.ubuntu.com/archives/ub...er/015154.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html")),  
Ubuntu never offered a choice of init system, and won't start doing    that. systemd is mandatory to be the supported ubuntu path. That's the    reason 
why ubuntu-standard won't depend on systemd|upstart.
 Note that for some kernel reasons, the Touch image is still using upstart, but that will change in the future.

Plus This link to confirm [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html)

I wish I could get you to try [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia]("https://launchpad.net/%7Emamarley/+archive/ubuntu/nvidia")
Try it You'll Like it:p

I had not seen that. All I ever heard was that upstart would be available until about 16.04 or 16.10 or something like that when they cut the cord but I guess on most of the flavors the cord was just cut.
Systemd works great here. Upstart is not worth messing with and I don't care to invest the time that it would take to get it working properly. I'll just use systemd.

I believe it's only available on vanilla Ubuntu and Xubuntu but I haven't, nor do I care to at this point peruse the manifests of all the flavors again. :P

My nVidia card is pretty old now and it won't hold up to the new driver versions any more.

I remember back on Lucid Lynx I was able to install the most latest driver directly from nVidia's website but not any more. 

I also haven't been able to update the driver on my windows 7 install in a few years either. Every time I did I would have to roll it back.

Here's what I have on all my systems I believe it is all of them anyway.
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l |grep nvidia
ii  nvidia-304-updates                          304.125-0ubuntu2                           amd64        NVIDIA legacy binary driver - version 304.125
ii  nvidia-libopencl1-304-updates               304.125-0ubuntu2                           amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304-updates               304.125-0ubuntu2                           amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                             346.59-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver
```

I'll probably hold out a while on jumping into the next developmental version though. Will have to wait and see.

---

### Post by Mateusz Stachowski on 2015-04-25
In blueprints created for Vivid (15.04) there is this:

[https://blueprints.launchpad.net/ubuntu/+spec/core-1403-systemd-transition](https://blueprints.launchpad.net/ubuntu/+spec/core-1403-systemd-transition)

> * Target for 16.04 LTS is to support upstart as a helper init for compatibility with locally-installed jobs

and this

[https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration](https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration)

> automatic fallback to upstart in grub (additional boot flag/checkpoint): TODO

Besides that in the  [Bug #1427654]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654") "FFE: switch system init to systemd [not touch] in 15.04" you can read:

> As per [https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration](https://blueprints.launchpad.net/ubuntu/+spec/core-1411-systemd-migration) we aimed for switching the system (not session) init from upstart to systemd this cycle.

[https://blueprints.launchpad.net/ubuntu/+spec/core-1403-session-init-systemd-migration](https://blueprints.launchpad.net/ubuntu/+spec/core-1403-session-init-systemd-migration)

Also there is the **init **package which is essential and depends on systemd-sysv or upstart-sysv.

[http://packages.ubuntu.com/vivid/init](http://packages.ubuntu.com/vivid/init)

---

### Post by Cavsfan on 2015-05-08
Admins, could you create a thread for the w cycle? 

All I had in Vivid was systemd and now I have both and I see what you all were saying about the slowness in systemd.

---

### Post by slickymaster on 2015-05-08
> **Cavsfan said:**
> Admins, could you create a thread for the w cycle? 

All I had in Vivid was systemd and now I have both and I see what you all were saying about the slowness in systemd.
Here you go: [http://ubuntuforums.org/showthread.php?t=2277355](http://ubuntuforums.org/showthread.php?t=2277355)

And being so, I'm closing this one.

---

