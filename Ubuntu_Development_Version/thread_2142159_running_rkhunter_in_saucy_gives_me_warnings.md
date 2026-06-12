---
title: "running rkhunter in saucy gives me warnings"
date: 2013-05-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-05-04
Just doing some test with rkhunter (root kit hunter) and I get the following:

```

[19:20:16] Info: SCAN_MODE_DEV set to 'THOROUGH'
[19:20:16]   Checking /dev for suspicious file types         [ Warning ]
[19:20:16] Warning: Suspicious file types found in /dev:
[19:20:16]          /dev/.udev/rules.d/root.rules: ASCII text
[19:20:18]   Checking for hidden files and directories       [ Warning ]
[19:20:18] Warning: Hidden directory found: '/dev/.udev'
[19:20:18] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[19:20:32]


```

I assume these are f/ps

---

### Post by cariboo on 2013-05-04
Did you run:

```
rkhunter --propupd
```

before running your scan? This command should be run after doing a lot of updates, in order to get the rkhunter database up-to-date.

---

### Post by nazaroo2 on 2013-08-17
ignore this post: wrong thread *(eyes crossing)

---

### Post by ventrical on 2013-08-17
> **nazaroo2 said:**
> ignore this post: wrong thread *(eyes crossing)

Thanks for the bump! :) lol

---

### Post by ventrical on 2013-08-17
> **cariboo907 said:**
> Did you run:

```
rkhunter --propupd
```

before running your scan? This command should be run after doing a lot of updates, in order to get the rkhunter database up-to-date.

Just seen this now.

Thanks..

---

### Post by QDR06VV9 on 2013-08-20
> **ventrical said:**
> Just seen this now.

Thanks..

Seems that a few things have changed since I last used it.

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---

### Post by ventrical on 2013-08-20
> **runrickus said:**
> Seems that a few things have changed since I last used it.

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

But .. Oy ... look at the last edit date of the wiki...

RKhunter  (last edited 2011-10-28 04:57:06 by

:) 

lol

---

### Post by cariboo on 2013-08-20
The last rkhunter update was in May 2012, and from the looks of the changelog, there weren't huge changes, so the wiki page is still valid, and has some very good information that I haven't been able to find in the rkhunter documentation.

---

### Post by QDR06VV9 on 2013-08-21
> **cariboo907 said:**
> The last rkhunter update was in May 2012, and from the looks of the changelog, there weren't huge changes, so the wiki page is _still valid, and has some very good information that I haven't been able to find in the rkhunter documentation._

I Learned more from that link also:P

---

### Post by ventrical on 2013-08-21
> **cariboo907 said:**
> The last rkhunter update was in May 2012, and from the looks of the changelog, there weren't huge changes, so the wiki page is still valid, and has some very good information that I haven't been able to find in the rkhunter documentation.


 I'm not disputing those points. I was just making note of being current as in Aug 2013.

Regards..

---

### Post by QDR06VV9 on 2013-08-22
> **ventrical said:**
> I'm not disputing those points. I was just making note of being current as in Aug 2013.

Regards..

I knew where you going with that!! LOL
Ventrical have you tried eset for linux?
from [http://www.eset.com/us/business/products/file-linux/]("http://www.eset.com/us/business/products/file-linux/")
or [http://www.eset.com/us/home/products/nod32-for-linux/]("http://www.eset.com/us/home/products/nod32-for-linux/")
I found it very useful but for my needs I did not keep it.(priceing)
The eset icon will not show up under unity(but you can access from dash)but it will running GS!
Regards

---

### Post by ventrical on 2013-08-22
> **runrickus said:**
> I knew where you going with that!! LOL
Ventrical have you tried eset for linux?
from [http://www.eset.com/us/business/products/file-linux/](http://www.eset.com/us/business/products/file-linux/)
or [http://www.eset.com/us/home/products/nod32-for-linux/](http://www.eset.com/us/home/products/nod32-for-linux/)
I found it very useful but for my needs I did not keep it.(priceing)
The eset icon will not show up under unity(but you can access from dash)but it will running GS!
Regards


I know some of the people  whom earlier worked for the percursor of eset (nod32/thunderbtyte..etc..)  circa1992 so , thanks but no thanks. :) lol

  I did get CAV for linux (Ubuntu) working just swell for the Precise kernels series but no luck yet with Saucy. It has a real time guard (on access)  and passed the EICAR test with flying colours. I had tried it ealrier ..about a year ago but there were lots of bugs .. now  a lot of those bugs are ironed out but it will not compile a redirfs file in the kernel (3.11.x.x).  I am not looking for a security system. I am just beta testing whats out there, whats in here .. etc.. 

regards..

---

### Post by QDR06VV9 on 2013-08-22
> **ventrical said:**
> I know some of the people  whom earlier worked for the percursor of eset (nod32/thunderbtyte..etc..)  circa1992 so , > thanks but no thanks. :) lol

  I did get CAV for linux (Ubuntu) working just swell for the Precise kernels series but no luck yet with Saucy. It has a real time guard (on access)  and passed the EICAR test with flying colours. I had tried it ealrier ..about a year ago but there were lots of bugs .. now  a lot of those bugs are ironed out but it will not compile a redirfs file in the kernel (3.11.x.x).  I am not looking for a security system. I am just beta testing whats out there, whats in here .. etc.. 

regards..

Yes I know you beta test, I was inerested in what you thought of Eset?
```
thanks but no thanks. :) lol
```
And I Agree!!:D

---

### Post by ventrical on 2013-08-22
rkhunter appears to be working well...

```

root@ventrical-asus-aiproactive-extreme:~# rkhunter --propupd
[ Rootkit Hunter version 1.4.0 ]
File updated: searched for 167 files, found 133
root@ventrical-asus-aiproactive-extreme:~# rkhunter --check
[ Rootkit Hunter version 1.4.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pkill                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/fsck                                               [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/route                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ping                                                [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/kmod                                                [ OK ]
    /bin/dash                                                [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Jynx Rootkit                                             [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

[Press <ENTER> to continue]


  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ Warning ]
    Checking for group file changes                          [ Warning ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 133
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 50 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

root@ventrical-asus-aiproactive-extreme:~# 

```

... and I'll check that log file..

edit

Here is the info I get on that warning..

```

[14:43:21] Info: SCAN_MODE_DEV set to 'THOROUGH'
[14:43:21]   Checking /dev for suspicious file types         [ Warning ]
[14:43:21] Warning: Suspicious file types found in /dev:
[14:43:21]          /dev/.udev/rules.d/root.rules: ASCII text
[14:43:21]   Checking for hidden files and directories       [ Warning ]
[14:43:21] Warning: Hidden directory found: '/dev/.udev'
[14:43:21] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[14:43:31]
[14:43:31] Info: Test 'apps' disabled at users request.
[14:43:31]
[14:43:31] System checks summary
[14:43:31] =====================
[14:43:31]
[14:43:31] File properties checks...
[14:43:31] Files checked: 133
[14:43:31] Suspect files: 1
[14:43:31]
[14:43:31] Rootkit checks...
[14:43:31] Rootkits checked : 292
[14:43:31] Possible rootkits: 0
[14:43:32]
[14:43:32] Applications checks...
[14:43:32] All checks skipped
[14:43:32]
[14:43:32] The system checks took: 1 minute and 50 seconds
[14:43:32]
[14:43:32] Info: End date is Thu Aug 22 14:43:32 EDT 2013


```

but I think they are whitelist f/ps.

---

### Post by QDR06VV9 on 2013-08-22
[/QUOTE] but I think they are whitelist f/ps.[/QUOTE]

These 2 lines are Identical to mine..
```
 Checking for passwd file changes                         [ Warning ]
           Checking for group file changes                          [ Warning ]
```

---

### Post by ventrical on 2013-08-23
This thread covers a lot of those spurious warnings:

[http://ubuntuforums.org/showthread.php?t=1931897](http://ubuntuforums.org/showthread.php?t=1931897)

Regards..

---

### Post by QDR06VV9 on 2013-08-23
> **ventrical said:**
> This thread covers a lot of those spurious warnings:

[http://ubuntuforums.org/showthread.php?t=1931897](http://ubuntuforums.org/showthread.php?t=1931897)

Regards..

Thanks for your research I learn ALOT from you and VinDSL!
You Both are Keepers.:popcorn:

---

### Post by ventrical on 2013-08-23
> **runrickus said:**
> Thanks for your research I learn ALOT from you and VinDSL!
You Both are Keepers.:popcorn:

And thanks for your contribs!!  :)  If VinDSL or I are Ubuntu RockStars it is because of contributors like you :) lol

 Gee .. haven't see VinDSL. Hope he made it back ok after all the ruckus :) lol

---

### Post by QDR06VV9 on 2013-08-24
> **ventrical said:**
> And thanks for your contribs!!  :)  If VinDSL or I are Ubuntu RockStars it is because of contributors like you :) lol

 Gee .. haven't see VinDSL. Hope he made it back ok after all the ruckus :) lol

I Liked the play (ruckus)!;)
_He is back!_ We or at least me was wondering if you were going to get back!
Allls good..:D

```
> **VinDSL said:**
> Yeah, Vent is back.  He gave the mods/admins a run for their money on Discourse.

Didn't know he had it in him.  He (ahem) vented on 'em...  LoL!  :D
```

---

### Post by ventrical on 2013-08-26
> **runrickus said:**
> I Liked the play (ruckus)!;)
_He is back!_ We or at least me was wondering if you were going to get back!
Allls good..:D




Thats great news ! : )...


 Actually I was not trying to  compete with or aggravate the mods (although they certainly did have their hair up)  ;)   I was actually just trying to brainstorm and problem solve. The thing where I went wrong is that I thought we were invited to do so on Discourse and I believe now that this was not the case. Still, we have to be security concious. I have some more senior clients that I am training in Ubuntu after horror sessions with Vista. Most of them like Pogo online games and there is a problem with the Java permissions and Adobe flash player.  The whole thing is that you have to give the java applets full permissions, and the java and Adobe have to be current so there is a dance with the Software Center that one has to do to get everything running smooth. On Ubuntu with FireFox (so far) it works like a charm, but, with Vista there are holes for all sorts of adware , pop-ups and other malicious distractions to get the end user to download and install even more malware (that I usually end up having to remove.)  Most malware scanners on Windows based machines will not detect a lot of these PUPs once the java apps are given blanket permissions. Also , like on most installs of Vista I have worked with, the downtime to get any reasonable facsimile of a repair done  equals many hours . Then , after a convert or side by side install I have to babysit and instruct because Ubuntu is just too wild for some more senior clientel. Once it is tamed down  though  the efforts are all worth the while.

Still, some newer users are shocked to have an OS that does not need conventional AV software installed. They just don't get it and they feel more secure if they have somthing installed that will emulate or give them some sense of security. Enter Avast AV software  (big thanks to VinDSL for helping me install that correctly) and Comodo AV.. with a real time guard. The problems always are performance and economics. Some retired people can't aford a new system and they are not willing to pay for a Windows 7 upgrade .. so I try to help and instruct them in Ubuntu to restore their desktops  to some semblance of usage while not being too overly difficult to learn. CAV for linux is not a really big performace hog on Ubuntu 12.04 (will not make with Saucy kernels) but I am hoping I can get more senior PC users interested in Ubuntu by having the added securiity of an AV guard.  .... and then there is work....! .. :) lol

---

### Post by grahammechanical on 2013-08-26
> Actually I was not trying to  compete with

What have I missed? What have I missed? Don't tell me. Plausable Deniabilty, and all that. :)

As an aside have you noticed what Canonical is trying to achieve with its Click packaging in the Ubuntu SDK? An app developer will have to include in the packaging a Manifest listing all the authorisations that the app will need. This manifest is then examined and if the app is not going to put the security of Ubuntu at risk it will be allowed in the software centre. And the manifiest will be used to create an apparmor profile. Then if code in the app tries to do anything outside the apparmor profile it will be blocked. They say it will speed up the acceptance of apps into the software centre as it removes the need for a line by line audit of the code.

It seems to be a good thing.

Oh, if Mark can be disruptive and Ubuntu can be distruptive, why not Ventrical. :) Just trying to be amusing.

Regards.

---

### Post by ventrical on 2013-08-26
> **grahammechanical said:**
> What have I missed? What have I missed? Don't tell me. Plausable Deniabilty, and all that. :)

As an aside have you noticed what Canonical is trying to achieve with its Click packaging in the Ubuntu SDK? An app developer will have to include in the packaging a Manifest listing all the authorisations that the app will need. This manifest is then examined and if the app is not going to put the security of Ubuntu at risk it will be allowed in the software centre. And the manifiest will be used to create an apparmor profile. Then if code in the app tries to do anything outside the apparmor profile it will be blocked. They say it will speed up the acceptance of apps into the software centre as it removes the need for a line by line audit of the code.

It seems to be a good thing.

Oh, if Mark can be disruptive and Ubuntu can be distruptive, why not Ventrical. :) Just trying to be amusing.

Regards.

Thanks a million Graham! :)

Thanks also for that tidbit of info. Bravo I say! Repository maintanence is the crux, the backbone if you will, of Ubuntu security. The keepers of the hive allow Ubuntu and all it's flavours to basically run free without the drudgery (no offence to matt Drudge) :) of all the security software that is essential with  Windows OS flavours. (That's not an inflamatory criticism to evoke controversey, it's a proven fact). As I noted (and with the help of others-Cariboo) I was able to actually get rkhunter to work, apparently. My next step will be to download a rootkit emulator  of some sort (equal to the likes of EICAR) and see if it will detect it.

 .. as for Mark.. I really hope he gets Knighted for all the benevolent work he has done. I don't think that too many people realize the efforts he has put in to relieving burdens and sufferings  that many people go through while struggling to tame commercial Operating Systems. He made it economically feasible for almost anyone, anywhere to have an effervescent experience on the internet without having to pay the high price of a new hardware form factor and I cite Lucid Lynx as this hallmark.

Regards..

---

### Post by cariboo on 2013-08-26
My personal belief is that both rkhunter and chkrootkit are fairly useless applications, because they just aren't setup properly for a normal user to get the most benefit from them. They both depend on the user reading the the documentation before using them the first time, and as we all know no one looks at the documentation until something goes wrong. 

There are very few viruses left out in the wild, as malware seems to be way more profitable for the bad guys. I personally haven't used it, but a few of the moderation team have had good things to say about BitDefender. Instructions for adding their repositories are available [here]("http://download.bitdefender.com/repos/#"). You still need a license key, but I not sure if it is free any more or not.

**Edit:** One thing I forgot to add, is that both utilities don't prevent rootkits, they only tell you about the problem after the fact.

---

### Post by QDR06VV9 on 2013-08-26
> **cariboo907 said:**
> My personal belief is that both rkhunter and chkrootkit are fairly useless applications, because they just aren't setup properly for a normal user to get the most benefit from them. They both depend on the user reading the the documentation before using them the first time, and as we all know no one looks at the documentation until something goes wrong. 

There are very few viruses left out in the wild, as malware seems to be way more profitable for the bad guys. I personally haven't used it, but a few of the moderation team have had good things to say about BitDefender. Instructions for adding their repositories are available [here]("http://download.bitdefender.com/repos/#"). You still need a license key, but I not sure if it is free any more or not.

**Edit:** _One thing I forgot to add, is that both utilities don't prevent rootkits, they only tell you about the problem after the fact._
Thanks cariboo907!
I did try eset for 30 days and it picked up on some malware in real time!
But like you I have no (real) worries about viruses, but malware sounds as if thats something in  near future to be conserned over..   Just be Wise when Browsing the Web!!

---

### Post by SuperFreak on 2013-08-26
[http://www.bitdefender.com/business/antivirus-for-unices.html]("http://www.bitdefender.com/business/antivirus-for-unices.html")

Free Licence available for personal use, but it needs to be renewed every 90 days

---

### Post by cariboo on 2013-08-26
> **runrickus said:**
>   Just be Wise when Browsing the Web!!

Education is always better than relying on third party programs to protect your system, as many millions of Windows users have found. In truth, the only thing we do see fairly often from Ubuntu users, are browser exploits, and these types of problems can be prevented by using browser add ons, such as noscript for FIrefox and NotScripts for chromium (I'm not a chrome user, so I don't know it Notscripts works) and adblock. Creating whitelists may take a bit of time but once setup, you can just enjoy your browsing. :-)

---

