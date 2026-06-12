---
title: "Was my hardy ubuntu netbook hacked?"
date: 2010-05-30
forum: Security
---

### Post by 2nubu on 2010-05-30
Hi,

Earlier, I was editing my eBay selling item. And some things went awry, which sometimes happen with my Dell Mini 10v keyboard and mouse making my cursor fly everywhere.

Anyhow, when I finished editing my eBay selling item and finalized it, I noticed my three pics were missing. And then as I tried to go back to change it-- My menu bar moved to the bottom. And all sorts of weird things were happening.

So I ran Rkhunter and this is what I get:

[PHP][ Rootkit Hunter version 1.3.0 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/en                                      [ No update ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zhutf                                   [ No update ]
solemole@solemole:~$ sudo rkhunter -c
[ Rootkit Hunter version 1.3.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
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
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
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
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
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
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
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
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
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
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]
    Checking for Apache backdoor                             [ Not found ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]
\


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ Warning ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ Warning ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ Warning ]
    Checking version of PHP                                  [ Warning ]


System checks summary
=====================

File properties checks...
    Files checked: 119
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 4
    Suspect applications: 3

The system checks took: 40 minutes and 48 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)[/PHP]What worries me (though I know nothing about ubuntu security) is the warning about "passwd file changes" ... does that mean someone changed my system password?

P.S. If you can help me out on this one, also... how reliable is Google Chrome for Linux security-wise? ... I mean, it offers to save passwords for websites, but it never has a master password for the list.

Anyways, I hope someone could answer the questions to my problems, particularly the rkhunter and chrome ones. My earlier experience with eBay *could* be just haywire typing.

Thanks,
nuub

---

### Post by BoneKracker on 2010-05-30
No. "passwd file changes" means there was a change made to the file /etc/passwd.  That file is basically a list of users.  Most of these users are system accounts (accounts used by the system so it can drop root privileges).  That would be normal to see after you added a new user or after you installed a new daemon.

---

### Post by HermanAB on 2010-05-30
Howdy,

The only sure fire way to get your Ubuntu machine hacked, is by running VNC on it.  So if you don't use VNC, then you'll be OK.

---

### Post by BoneKracker on 2010-05-30
> **HermanAB said:**
> Howdy,

The only sure fire way to get your Ubuntu machine hacked, is by running VNC on it.  So if you don't use VNC, then you'll be OK.

Or run samba without a firewall.  That'll get you hacked in fairly short order too.  Anything running on well-known Windows ports will attract script-kiddies like flies to road-kill.

---

### Post by Chayak on 2010-05-30
That's about the big three though SSH with weak passwords is the number one reason *nix machines get rooted most of the time.

It's really easy to raise the security bar of your system above the script kiddie level.

---

### Post by 2nubu on 2010-05-30
> **BoneKracker said:**
> No. "passwd file changes" means there was a change made to the file /etc/passwd.  That file is basically a list of users.  Most of these users are system accounts (accounts used by the system so it can drop root privileges).  That would be normal to see after you added a new user or after you installed a new daemon.

Thanks everyone...

But I'm the only one using my netbook; so I don't know what/how any other "users" could be added.... and also, pardon my ignorance, what is a daemon?

---

### Post by BoneKracker on 2010-05-30
> **2nubu said:**
> Thanks everyone...

But I'm the only one using my netbook; so I don't know what/how any other "users" could be added.... and also, pardon my ignorance, what is a daemon?

Look at the file:```

sudo less /etc/passwd
```
All of those are users on your system.  How many of them are you?

A daemon is a program that runs in the background.  For example, the part of gnu/linux that handles sound is a daemon.  The part that provides the graphical user interface is a daemon.  Simplistically, any program that's "always" running is a daemon.  Often, for security reasons, the system is set up so that such programs can run as a user having less privileges than "root" (which has all privileges).  That's why you see lots of "system users" (users that aren't people), and most of them seem like their named for part of the system or for some server-type of program.

As an example, you may have and account for "sshd".  "sshd" is not a real person, but when the system starts up sshd, most of it is being run as though it were started by the user "sshd".  The user "sshd" has limited privileges.  For example, you can see in the /etc/passwd file that it probably has a home directory that says something like "/var/empty" (a directory intentionally left empty).  While your user has "/bin/bash" for a shell, the sshd user has something like "/sbin/nologin" or "/bin/false" (fake shells).  That way, if somebody who connects to the system by way of ssh manages to hack the server to try to make it execute commands for them, they really can't do anything or access any files.

So, when you install a new program, sometimes a new "system user" gets added to /etc/passwd.  Like lets say you installed  FTP server software called "vsftpd".  A new user might get added called "vsftpd".  Then, the next time you ran rkhunter, it would alert you to the fact that changes had been made to the file.  That's when you say to yourself, "Hmmm... did I do something that would change that file?", and maybe you remember installing new software.  Maybe you take a look at the file to what changes have been made.

Also, if it seems funny that a file named "passwd" actually has no passwords in it, here's why: it used to have passwords in it, but now they are kept in a separate encrypted file called "shadow", which is also in /etc.

---

### Post by 2nubu on 2010-05-30
Thanks... That's very interesting.

I've been using Windows since Win95... So all this Linux/Ubuntu stuff is a lot to take in... especially with someone like me who needs (OCDlike) to secure and set preference to any OS he's using.

I don't know if I'll ever get a handle on Ubuntu. So please bear with me, peeps.

Thanks again, everyone.

cheers,
2nubu

---

### Post by BoneKracker on 2010-05-30
Sure you will.  Just don't try to swallow it all at once.

Learn to use the basic system and the software you absolutely needed to install.

Then, learn how to use the command line, because this will give you a better understanding of how the system works, enable to explore its inner workings, and make it easier to learn and do the more advanced things.

Somebody pointed out an excellent tutorial the other day I had forgotten about. It's worth going through when you have the time (even if some of it is a little bit old).
[http://rute.2038bug.com/](http://rute.2038bug.com/)

---

