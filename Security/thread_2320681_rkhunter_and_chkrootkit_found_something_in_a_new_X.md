---
title: "rkhunter and chkrootkit found something in a new Xubuntu installation, please help!!!"
date: 2016-04-16
forum: Security
---

### Post by dona-25 on 2016-04-16
Hi!

I am new to Ubuntu and Linux, I just installed Xubuntu 14.04 in my Desktop PC alongside with Windows Vista. I installed ClamTk, rkhunter and chkrootkit for security. 
After I installed and configured Xubuntu, I have only watched a few regular YouTube videos without using FlashPlayer. Then, I ran a scan with rkhunter and chkrootkit just for curiosity. 
For my dismay, both scans found something???

Please help! I don't understand the results, are them false positives or there is something wrong or infected in my new Xubuntu installation?


```
sudo rkhunter --chec**k**
[sudo] password for: 
[ Rootkit Hunter version 1.4.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                          [ None found ]
    Checking LD_LIBRARY_PATH variable                   [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                          [ OK ]
    /usr/sbin/chroot                                            [ OK ]
    /usr/sbin/cron                                               [ OK ]
    /usr/sbin/groupadd                                         [ OK ]
    /usr/sbin/groupdel                                          [ OK ]
    /usr/sbin/groupmod                                        [ OK ]
    /usr/sbin/grpck                                              [ OK ]
    /usr/sbin/nologin                                            [ OK ]
    /usr/sbin/pwck                                              [ OK ]
    /usr/sbin/rsyslogd                                          [ OK ]
    /usr/sbin/tcpd                                               [ OK ]
    /usr/sbin/useradd                                           [ OK ]
    /usr/sbin/userdel                                            [ OK ]
    /usr/sbin/usermod                                          [ OK ]
    /usr/sbin/vipw                                               [ OK ]
    /usr/bin/awk                                                 [ OK ]
    /usr/bin/basename                                         [ OK ]
    /usr/bin/chattr                                              [ OK ]
    /usr/bin/cut                                                  [ OK ]
    /usr/bin/diff                                                  [ OK ]
    /usr/bin/dirname                                            [ OK ]
    /usr/bin/dpkg                                                [ OK ]
    /usr/bin/dpkg-query                                       [ OK ]
    /usr/bin/du                                                   [ OK ]
    /usr/bin/env                                                 [ OK ]
    /usr/bin/file                                                  [ OK ]
    /usr/bin/find                                                 [ OK ]
    /usr/bin/GET                                                 [ OK ]
    /usr/bin/groups                                             [ OK ]
    /usr/bin/head                                                [ OK ]
    /usr/bin/id                                                    [ OK ]
    /usr/bin/killall                                                [ OK ]
    /usr/bin/last                                                  [ OK ]
    /usr/bin/lastlog                                              [ OK ]
    /usr/bin/ldd                                                   [ OK ]
    /usr/bin/less                                                  [ OK ]
    /usr/bin/locate                                               [ OK ]
    /usr/bin/logger                                               [ OK ]
    /usr/bin/lsattr                                                [ OK ]
    /usr/bin/md5sum                                            [ OK ]
    /usr/bin/mlocate                                            [ OK ]
    /usr/bin/newgrp                                             [ OK ]
    /usr/bin/passwd                                            [ OK ]
    /usr/bin/perl                                                 [ OK ]
    /usr/bin/pgrep                                              [ OK ]
    /usr/bin/pkill                                                 [ OK ]
    /usr/bin/pstree                                             [ OK ]
    /usr/bin/rkhunter                                           [ OK ]
    /usr/bin/runcon                                             [ OK ]
    /usr/bin/sha1sum                                          [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                                 [ OK ]
    /usr/bin/sort                                                 [ OK ]
    /usr/bin/stat                                                [ OK ]
    /usr/bin/strace                                             [ OK ]
    /usr/bin/strings                                             [ OK ]
    /usr/bin/sudo                                               [ OK ]
    /usr/bin/tail                                                 [ OK ]
    /usr/bin/test                                                [ OK ]
    /usr/bin/top                                                 [ OK ]
    /usr/bin/touch                                              [ OK ]
    /usr/bin/tr                                                   [ OK ]
    /usr/bin/uniq                                                [ OK ]
    /usr/bin/users                                              [ OK ]
    /usr/bin/vmstat                                            [ OK ]
    /usr/bin/w                                                   [ OK ]
    /usr/bin/watch                                             [ OK ]
    /usr/bin/wc                                                 [ OK ]
    /usr/bin/wget                                              [ OK ]
    /usr/bin/whatis                                            [ OK ]
    /usr/bin/whereis                                           [ OK ]
    /usr/bin/which                                             [ OK ]
    /usr/bin/who                                               [ OK ]
    /usr/bin/whoami                                           [ OK ]
    **/usr/bin/unhide.rb                                      [ Warning ]**
    /usr/bin/mawk                                             [ OK ]
    /usr/bin/lwp-request                                    [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/fsck                                                  [ OK ]
    /sbin/ifconfig                                              [ OK ]
    /sbin/ifdown                                               [ OK ]
    /sbin/ifup                                                   [ OK ]
    /sbin/init                                                    [ OK ]
    /sbin/insmod                                               [ OK ]
    /sbin/ip                                                      [ OK ]
    /sbin/lsmod                                                 [ OK ]
    /sbin/modinfo                                              [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                                [ OK ]
    /sbin/route                                                 [ OK ]
    /sbin/runlevel                                              [ OK ]
    /sbin/sulogin                                               [ OK ]
    /sbin/sysctl                                                [ OK ]
    /bin/bash                                                   [ OK ]
    /bin/cat                                                     [ OK ]
    /bin/chmod                                                 [ OK ]
    /bin/chown                                                 [ OK ]
    /bin/cp                                                      [ OK ]
    /bin/date                                                   [ OK ]
    /bin/df                                                       [ OK ]
    /bin/dmesg                                                 [ OK ]
    /bin/echo                                                   [ OK ]
    /bin/ed                                                      [ OK ]
    /bin/egrep                                                  [ OK ]
    /bin/fgrep                                                  [ OK ]
    /bin/fuser                                                  [ OK ]
    /bin/grep                                                   [ OK ]
    /bin/ip                                                      [ OK ]
    /bin/kill                                                     [ OK ]
    /bin/less                                                   [ OK ]
    /bin/login                                                  [ OK ]
    /bin/ls                                                      [ OK ]
    /bin/lsmod                                                [ OK ]
    /bin/mktemp                                             [ OK ]
    /bin/more                                                 [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                    [ OK ]
    /bin/netstat                                              [ OK ]
    /bin/ping                                                  [ OK ]
    /bin/ps                                                    [ OK ]
    /bin/pwd                                                  [ OK ]
    /bin/readlink                                             [ OK ]
    /bin/sed                                                  [ OK ]
    /bin/sh                                                    [ OK ]
    /bin/su                                                    [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                              [ OK ]
    /bin/which                                               [ OK ]
    /bin/kmod                                                [ OK ]
    /bin/dash                                                 [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                              [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                             [ Not found ]
    Adore Rootkit                                             [ Not found ]
    aPa Kit                                                     [ Not found ]
    Apache Worm                                            [ Not found ]
    Ambient (ark) Rootkit                                  [ Not found ]
    Balaur Rootkit                                            [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                                 [ Not found ]
    CiNIK Worm (Slapper.B variant)                     [ Not found ]
    Danny-Boy's Abuse Kit                                 [ Not found ]
    Devil RootKit                                              [ Not found ]
    Dica-Kit Rootkit                                          [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                        [ Not found ]
    Enye LKM                                                  [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                                 [ Not found ]
    ****`it Rootkit                                           [ Not found ]
    GasKit Rootkit                                            [ Not found ]
    Heroin LKM                                                [ Not found ]
    HjC Kit                                                      [ Not found ]
    ignoKit Rootkit                                            [ Not found ]
    IntoXonia-NG Rootkit                                   [ Not found ]
    Irix Rootkit                                                [ Not found ]
    Jynx Rootkit                                               [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                              [ Not found ]
    Knark Rootkit                                             [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                 [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                         [ Not found ]
    MRK Rootkit                                               [ Not found ]
    Ni0 Rootkit                                                [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                   [ Not found ]
    Oz Rootkit                                                 [ Not found ]
    Phalanx Rootkit                                           [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                  [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                     [ Not found ]
    RSHA's Rootkit                                            [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                 [ Not found ]
    Shutdown Rootkit                                        [ Not found ]
    SHV4 Rootkit                                              [ Not found ]
    SHV5 Rootkit                                              [ Not found ]
    Sin Rootkit                                                 [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                           [ Not found ]
    'Spanish' Rootkit                                          [ Not found ]
    **Suckit Rootkit                                                      [ Not found ]**
    Superkit Rootkit                                          [ Not found ]
    TBD (Telnet BackDoor)                                 [ Not found ]
    TeLeKiT Rootkit                                           [ Not found ]
    T0rn Rootkit                                               [ Not found ]
    trNkit Rootkit                                              [ Not found ]
    Trojanit Kit                                                 [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                                [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                              [ Not found ]
    Volc Rootkit                                               [ Not found ]
    Xzibit Rootkit                                              [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                                  [ Not found ]

[Press <ENTER> to continue]


  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories   [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files     [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                     [ None found ]
    Checking for sniffer log files                              [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                            [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]
    Checking for hidden ports                                 [ Skipped ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                    [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware            [ None found ]

  Performing group and account checks
    Checking for passwd file                                    [ Found ]
    Checking for root equivalent (UID 0) accounts       [ None found ]
    Checking for passwordless accounts                    [ None found ]
    [B]Checking for passwd file changes                          [ Warning ]
     Checking for group file changes                             [ Warning ][/B]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                       [ Not found ]
    Checking for running syslog daemon                     [ Found ]
    Checking for syslog configuration file                    [ Found ]
    Checking if syslog remote logging is allowed           [ Not allowed ]

  Performing filesystem checks
    [B]Checking /dev for suspicious file types                 [ Warning ]
    Checking for hidden files and directories                [ Warning ][/B]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 135
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 292
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 47 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```



 ```
sudo chkrootkit
[sudo] password for: 
ROOTDIR is `/'
Checking `amd'...                                                       not found
Checking `basename'...                                               not infected
Checking `biff'...                                                        not found
Checking `chfn'...                                                       not infected
Checking `chsh'...                                                       not infected
Checking `cron'...                                                       not infected
Checking `crontab'...                                                   not infected
Checking `date'...                                                       not infected
Checking `du'...                                                          not infected
Checking `dirname'...                                                   not infected
Checking `echo'...                                                       not infected
Checking `egrep'...                                                      not infected
Checking `env'...                                                         not infected
Checking `find'...                                                         not infected
Checking `fingerd'...                                                     not found
Checking `gpm'...                                                         not found
Checking `grep'...                                                         not infected
Checking `hdparm'...                                                     not infected
Checking `su'...                                                           not infected
Checking `ifconfig'...                                                     not infected
Checking `inetd'...                                                        not infected
Checking `inetdconf'...                                                  not found
Checking `identd'...                                                       not found
Checking `init'...                                                           not infected
Checking `killall'...                                                         not infected
Checking `ldsopreload'...                                                not infected
Checking `login'...                                                         not infected
Checking `ls'...                                                             not infected
Checking `lsof'...                                                          not infected
Checking `mail'...                                                          not found
Checking `mingetty'...                                                   not found
Checking `netstat'...                                                     not infected
Checking `named'...                                                      not found
Checking `passwd'...                                                     not infected
Checking `pidof'...                                                        not infected
Checking `pop2'...                                                        not found
Checking `pop3'...                                                        not found
Checking `ps'...                                                           not infected
Checking `pstree'...                                                      not infected
Checking `rpcinfo'...                                                     not found
Checking `rlogind'...                                                      not found
Checking `rshd'...                                                         not found
Checking `slogin'...                                                       not infected
Checking `sendmail'...                                                    not infected
Checking `sshd'...                                                         not found
Checking `syslogd'...                                                     not tested
Checking `tar'...                                                           not infected
Checking `tcpd'...                                                         not infected
Checking `tcpdump'...                                                    not infected
Checking `top'...                                                           not infected
Checking `telnetd'...                                                      not found
Checking `timed'...                                                        not found
Checking `traceroute'...                                                  not found
Checking `vdir'...                                                           not infected
Checking `w'...                                                             not infected
Checking `write'...                                                         not infected
Checking `aliens'...                                                        no suspect files
Searching for sniffer's logs, it may take a while...                nothing found
Searching for rootkit HiDrootkit's default files...                   nothing found
Searching for rootkit t0rn's default files...                          nothing found
Searching for t0rn's v8 defaults...                                    nothing found
Searching for rootkit Lion's default files...                          nothing found
Searching for rootkit RSHA's default files...                        nothing found
Searching for rootkit RH-Sharpe's default files...                 nothing found
Searching for Ambient's rootkit (ark) default files and dirs...  nothing found
Searching for suspicious files and dirs, it may take a while... nothing found
Searching for LPD Worm files and dirs...                             nothing found
Searching for Ramen Worm files and dirs...                         nothing found
Searching for Maniac files and dirs...                                 nothing found
Searching for RK17 files and dirs...                                    nothing found
Searching for Ducoci rootkit...                                          nothing found
Searching for Adore Worm...                                            nothing found
Searching for ShitC Worm...                                             nothing found
Searching for Omega Worm...                                           nothing found
Searching for Sadmind/IIS Worm...                                    nothing found
Searching for MonKit...                                                    nothing found
Searching for Showtee...                                                 nothing found
Searching for OpticKit...                                                  nothing found
Searching for T.R.K...                                                     nothing found
Searching for Mithra...                                                    nothing found
Searching for LOC rootkit...                                             nothing found
Searching for Romanian rootkit...                                      nothing found
**Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED**
Searching for Volc rootkit...                                            nothing found
Searching for Gold2 rootkit...                                           nothing found
Searching for TC2 Worm default files and dirs...                  nothing found
Searching for Anonoying rootkit default files and dirs...         nothing found
Searching for ZK rootkit default files and dirs...                   nothing found
Searching for ShKit rootkit default files and dirs...                nothing found
Searching for AjaKit rootkit default files and dirs...               nothing found
Searching for zaRwT rootkit default files and dirs...              nothing found
Searching for Madalin rootkit default files...                        nothing found
Searching for Fu rootkit default files...                               nothing found
Searching for ESRK rootkit default files...                           nothing found
Searching for rootedoor...                                               nothing found
Searching for ENYELKM rootkit default files...                      nothing found
Searching for common ssh-scanners default files...              nothing found
Searching for suspect PHP files...                                     nothing found
Searching for anomalies in shell history files...                     nothing found
Checking `asp'...                                                           not infected
Checking `bindshell'...                                                     not infected
Checking `lkm'...                                                            chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                                      not found
Checking `sniffer'...                                                        lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient[1160])
Checking `w55808'...                                                     not infected
Checking `wted'...                                                        chkwtmp: nothing deleted
Checking `scalper'...                                                      not infected
Checking `slapper'...                                                      not infected
Checking `z2'...                                                            user root deleted or never logged from lastlog!
user jbl deleted or never logged from lastlog!
user jbl deleted or never logged from lastlog!
Checking `chkutmp'...                                                   The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1607 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                             not infected
```


Above are the scan results, but in case of **rkhunter** it says: **Suckit Rootkit    [ Not found ]  **and in case of **chkrootkit** it says: [B]Searching for Suckit rootkit...    Warning: /sbin/init INFECTED

rkhunter[/B] have other warnnings that I don't understand too.

I will verry much appreciate any help to understand what is the meanning of these two scan results, and if there is something to worry about. :confused:


Thank you! :)

---

### Post by TheFu on 2016-04-16
Unix security doesn't start with scanners.  That is the Windows philosophy.  For scanners to be effective, they require constant, continuous, feeding, updates, care.  Not good for lazying Unix-types like me.  With F/LOSS tools, it is always best to read up on how old the package is and how often it gets updated.  AV scanners on Unix tend to only be useful if you have Windows PCs on the network. Makes your Linux machine a better neighbor, but doesn't add any real security to it.

Check my signature for Linux/Ubuntu Security links.

---

### Post by dona-25 on 2016-04-17
TheFu, thank you for your comments. I am a** newbie to Linux**, what I need is help to understand the meaning of the results of the scans performed with **rkhunter** and **chkrootkit**.:confused:

I have researched a little bit on the web, and I have found that it is _highly probable_ that:  **Searching for Suckit rootkit...            Warning: /sbin/init INFECTED  **is a FALSE POSITIVE there is a known bug in chkrootkit, please look at this link: [B][https://bugs.launchpad.net/cyborg/+bug/454566](https://bugs.launchpad.net/cyborg/+bug/454566)

[/B]I am going to uninstall chkrootkit from my PC to avoid scary *False Positive*s that I don't know how to handle[B].
[/B]
Please someone explain me what rkhunter found means:[B]

/usr/bin/unhide.rb                                                                                  [ Warning ]
[/B]
** Checking for passwd file changes                                            [ Warning ]**
[B]Checking for group file changes                                                [ Warning ]
 [/B]
**Checking /dev for suspicious file types                            [ Warning ]**[B]
Checking for hidden files and directories          [ Warning ]


[/B]By the way, I installed Xubuntu 12.04 first, then immediately after I upgraded to Xubuntu 14.04. 

Please, for any possible Fix, I will need Step By Step guide. 

Thanks! [B]:)


[/B]

---

### Post by TheFu on 2016-04-17
That is another false positive.

---

### Post by Habitual on 2016-04-18
You are likely to have to investigate each of these Warnings as an exercise on how to tell rkhunter what it can exclude in it's running.
On a default install there are many Warnings and it is alarming, but you have to "tell" rkhunter on what is allowable.

Until you run 
```
rkhunter --propupd 
```
which tells rkhunter everything on the system is "OK" "as is"

So, here's my standard rkhunter (1.4.3) conf file that I use to tell rkhunter everything is OK.
I am including only 1 sample directive for each type. The rest is up to you to populate.

```
ALLOWDEVFILE=/dev/.udev/rules.d/root.rules
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENFILE=/dev/.initramfs
SCRIPTWHITELIST=/usr/sbin/adduser

APP_WHITELIST="openssl:0.9.8g gpg:1.4.9 [sshd:5.1p1]("http://ubuntuforums.org/sshd/5.1p1.html") php 5.2.6"


```

After editing some directives in /etc/rkhunter.conf, to update the entire she-bang
to update the rkhunter environment based on the new edits, run
```
rkhunter --propupd
```

then
```
rkhunter --update && rkhunter -c -sk
``` and view the log if there are Additional Warnings
Make adjustment in /etc/rkhunter.conf > 
Rinse,
Lather,
Repeat.

Consult the comment-rich file in /etc/rkhunter.conf
Hope that helps.

chkrootkit? Never touch the stuff.

---

### Post by dona-25 on 2016-04-18
TheFu, Habitual, thank you for your comments. I have done some research on the web about what rkhunter scan found on my Xubuntu installation, and this is what I understand:[B]

Checking for passwd file changes    [ Warning ][/B]
[B]Checking for group file changes         [ Warning ]


[/B]The warnings above are because I have set **two users** for my Xubuntu system. One as an Administrator, and the second as a regular User.

 
Habitual, I have done:

sudo rkhunter --update
sudo rkhunter --propupd

After that, I don't have below warnings anymore: [B]

Checking for passwd file changes    [ Warning ][/B]
[B]Checking for group file changes         [ Warning ]
[/B]

But, I still have these warnings:

[B]/usr/bin/unhide.rb                                                                                   [ Warning ]

[/B]**Checking /dev for suspicious file types                                [ Warning ]**[B]
Checking for hidden files and directories           [ Warning ][/B]

For the above, I don't understand what these results mean. Is there something to worry about? Please, I need a detailed explanation. 

Thanks!

---

### Post by Habitual on 2016-04-19
> **dona-25 said:**
> 
Habitual, I have done:

sudo rkhunter --update
sudo rkhunter --propupd

After that, I don't have below warnings anymore: [B]

Checking for passwd file changes    [ Warning ][/B]
[B]Checking for group file changes         [ Warning ]
[/B]

But, I still have these warnings:

[B]/usr/bin/unhide.rb                                                                                   [ Warning ]

[/B]**Checking /dev for suspicious file types                                [ Warning ]**[B]
Checking for hidden files and directories           [ Warning ][/B]

For the above, I don't understand what these results mean. Is there something to worry about? Please, I need a detailed explanation. 

Thanks!
Great!
Now you have to edit /etc/rkhunter.conf as root and use the examples I showed you.
For each Warning, there will need to be a directive in /etc/rkhunter.conf in the manner 
I gave as an example. "1 sample directive for each type" above.

After editing, you'll need to re-run
```
sudo rkhunter --propupd && sudo rkhunter -c -sk
```
and Process any additional Warnings you may have missed.

Again, /etc/rkhunter.conf is amply commented.

---

### Post by dona-25 on 2016-04-21
Habitual, thank you for your comments. Finally after much searching here and there on the web, I have found the answers about what these warnings below mean:

[B]/usr/bin/unhide.rb                                                                                   [ Warning ]

[/B]**Checking /dev for suspicious file types                                [ Warning ]**[B]
Checking for hidden files and directories           [ Warning ]

[/B]Please look at this link:[B] [https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/219840](https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/219840)



[/B]SOLUTIONS:

[B][B]/usr/bin/unhide.rb                                                                                   [ Warning ] 

[/B][/B]rkhunter simply informs you the *unhide.rb* executable located in */usr/bin/ *is a ruby script. It is perfectly normal in that case and you can white-list it in: */etc/rkhunter.conf.local*  which is rkhunter configuration file adding without the **#** symbol this entry bellow:[B]

SCRIPTWHITELIST=/usr/bin/unhide.rb

[/B]For these warnings below, they are False Positives because rkhunter is not configured by default to not complain about them:[B][B]

Checking /dev for suspicious file types                                [ Warning ][/B][B]
Checking for hidden files and directories           [ Warning ]

[/B][/B]The solution is in  */etc/rkhunter.conf.local  *configuration file, remove the**[B] # **[/B]symbol or add these entries below if they do not exist: [B]

ALLOWHIDDENDIR=/dev/.udev
ALLOWDEVFILE=/dev/.initramfs

[/B]I hope for all the Linux newbies like me, it will make their life easier knowing what this warnings mean, and how to fix them.


Have a nice day!!! [B]:popcorn:

[/B]

---

### Post by Habitual on 2016-04-21
Glad it worked out!

---

### Post by TheFu on 2016-04-21
And if I were going to create a virus/bad program, /usr/bin/unhide.rb is where I'd place it, since a few people will have added it as a file to be ignored.  Provided the output is ... 
```
Scanning for hidden processes...
No hidden processes found!

```
nobody will probably notice it isn't actually doing anything desired.  That's the problem with whitelists that don't do other checking too.

---

