---
title: "Rkhunter warning"
date: 2010-03-26
forum: Security
---

### Post by dinw3 on 2010-03-26
[PHP][ Rootkit Hunter version 1.3.4 ]

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
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
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
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
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
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]
[/PHP]


can someone explain that ?

---

### Post by dinw3 on 2010-03-26
[PHP]  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]


[/PHP]

---

### Post by yeleek on 2010-03-26
What does the actual log say? /var/log/rkhunter.log

You'll need sudo to read it ie.

sudo less /var/log/rkhunter.log

This will allow you to see specifically what it was complaining about.

---

### Post by cariboo on 2010-03-26
This comes up so often, it should be in Recurring Discussions.

Unhide and unhide-linux26 are installed as dependencies of rkhunter, the warning about /dev is perfectly normal too, the same for hidden files and directories.

---

### Post by dinw3 on 2010-03-26
How can i be so sure about that ?

---

### Post by doas777 on 2010-03-26
> **dinw3 said:**
> How can i be so sure about that ?


well short answer, anyone who runs rkhunter on a stock freshly installed ubuntu box will get those exact same messages, if it helps.

the long, honest answer is that you can never be sure that a computer is clean and safe. period. there is just no way to affirmatively tell. you cannot ever prove anything. all you can do is fail to disprove it for long enough to feel like you are stating fact not supposition.

---

### Post by bodhi.zazen on 2010-03-26
> **dinw3 said:**
> How can i be so sure about that ?

Google the results from rkhunter and investigate the situation.

Boot a live CD, install rkhunter, run rkhunter, google the results, repeat until you are sure.

---

### Post by dinw3 on 2010-03-27
doas777 and bodhi.zazen : I am very disappointed to know that there is no specific answer to these warnings . :icon_frown: how do i know that my system is not under malicious programs .It is better to move to window as it offers a good malware protection tools . Ubunta should work hard to solve this problem , this is very disappointing matter !

---

### Post by dinw3 on 2010-03-27
[PHP]Checking application versions...

    Checking version of Exim MTA                             [ Warning ]
    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]

[/PHP]

I notice these warning today .

---

### Post by unspawn on 2010-03-27
> **dinw3 said:**
> I notice these warning today .
As yeleek already suggested you should check your rkhunter.log for details. (The README that comes with RKH, which the majority of users of course never reads until it's too late, can also offer you guidance.) Searching this forum or the rkhunter-users mailing list archives will show you how to white-list version numbers (hint: APP_WHITELIST).


[!] RKH can, out of the box, give a lot of alerts. The majority of the alerts and their white-listing counterparts are documented in the rkhunter-users mailing list archives. If you think all of this warning stuff is a nuisance and you do not want to be bothered with configuring it or correlating log results then you're free to contribute to make it "better". Else maybe you mistook it for some "fire and forget" tool? Like a lot of things GNU/Linux it takes an effort to make it work right. It shouldn't be any other way. You could move to using a combination of a log reporter like Logwatch, an integrity checker like Samhain, Osiris, Integrit, Aide (or even tripwire) and a malware slash rootkit evidence checker like OSSEC-HIDS or Chkrootkit.

---

### Post by OpSecShellshock on 2010-03-27
> **dinw3 said:**
> doas777 and bodhi.zazen : I am very disappointed to know that there is no specific answer to these warnings . :icon_frown: how do i know that my system is not under malicious programs .It is better to move to window as it offers a good malware protection tools . Ubunta should work hard to solve this problem , this is very disappointing matter !

I believe you're misunderstanding the nature of the tools available for both Ubuntu and Windows. In both cases, the tools cannot possibly prove that you're not running malware. All they can really do is tell you if they think you are, based on the most current information they have available. If a malware scan on any OS comes back clean, it does not mean that you definitely don't have malicious software. All it means is that the scanning engine couldn't find anything on your system that matches its database of known issues. RKHunter is just comparing what it expects system files to look like against what they actually look like. This means that if you update system files but don't update RKHunter (or if there isn't an update available yet), you're going to get warnings on whatever was updated.

A rootkit isn't just some file that can be found according to its name and deleted to solve the problem. It's a bottom-up full system compromise. The absolute best you can do with software geared toward finding them is locate things that you might want to look into further and then manually determine whether it's legitimate or suspicious. Usually it's legitimate. As I often say, there is no substitute for personal discretion. If an AV software vendor tries to leave you under the impression that there is, well, that's advertising for you.

---

### Post by bodhi.zazen on 2010-03-28
> **dinw3 said:**
> doas777 and bodhi.zazen : I am very disappointed to know that there is no specific answer to these warnings . :icon_frown: how do i know that my system is not under malicious programs .It is better to move to window as it offers a good malware protection tools . Ubunta should work hard to solve this problem , this is very disappointing matter !

You are misunderstanding how to use these tools. You have been given answers, but you choose to ignore or disbelieve the answers you have been given. You are making three "mistakes":

First, as with any [HIDS](http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system) , you MUST run in on a fresh install. Running these tools "after the fact" is useless as the malware can be hidden from the HIDS. The whole point of HIDS is that you install it on a known good system.

You need to learn what is "normal" for your system. This is the same in Windows, you will have problem if you blindly install malware scanners or antivirus and start deleting files they detect.

Same applies to Linux and rkhunter.

Second, you need to google and understand the "warnings" you recieve from rkhunter.

Third, you do not trust the advice you have recieved in this thread. Several users have given you an answer, and that answer would be supported by a google search.

So if you are unwilling to use the tool properly, unwilling to research the warnings you recieve, and you do not trust the advice you have been given there really is:

1. Not much point in running rkhunter.

2. Not much we can do to help you further.

Linux is not Windows and Linux does not suffer from viruses and rootkits in to the same degree as other OS and rkhunter is, by it's nature, going to give you a ton of false positives. You need to either:

1. Trust others when they tell you they are false positives.

2. Or, research and confirm for this for yourself.

So if you do not trust the good advice of others, time to fire up google, start running rkhunter on a live CD, and learn for yourself.

---

### Post by doas777 on 2010-03-29
just to add, the rootkit detector tools in windows (RKR is prolly the best) will detect a good number of false positives as well. I remember one day I spent 3 hours trying to trace a rootkit trace RKR found for me, just to realise it was daemon tools hiding it's scsi drivers (somthing I want it to do).

---

### Post by XitNow on 2010-03-30
I have a question.  I am new to Ubuntu from Vista.  Played around with some Unix in college, have a real basic understanding and not much else so I appologize in advance for my inexperience.
 
I had a couple issues with a box, didn't think I really needed to do anything to protect linux.  Re-installed newest version, added stuff to firefox (noscript, adblock etc), intalled firewall, used a hardening tool, then ran rkhunter.
 
It came back with some warning messages, the one that worried me the most was a possible rootkit named Xibit or something like that.  I am assuming that this is not a warning message that you guys are getting right out of the box correct?

---

### Post by ricyaun on 2010-03-31
Now this is the only well informed remark showing experience and forethought.  All the rest are mere rumor and inuendo than reality.  Root kits don't just happen either they are put there.  At present a big thing with root kits are being used for is to destabilize the Linux OS.  As it becomes more popular it is drawing more attention from corporate sources, which there is no direct reference to Microsoft there.  It is way bigger than that. They are primarily located in the BIOS and MBR.  Among other things they can be used to seed the OS for reboot.  They can either tamper with the OS at bootup, or give a "hacker" root user privileges without cracking the password in Linux or the Administrator account in Windows.

---

### Post by ricyaun on 2010-03-31
> **bodhi.zazen said:**
> You are misunderstanding how to use these tools. You have been given answers, but you choose to ignore or disbelieve the answers you have been given. You are making three "mistakes":

First, as with any [HIDS](http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system) , you MUST run in on a fresh install. Running these tools "after the fact" is useless as the malware can be hidden from the HIDS. The whole point of HIDS is that you install it on a known good system.

You need to learn what is "normal" for your system. This is the same in Windows, you will have problem if you blindly install malware scanners or antivirus and start deleting files they detect.

Same applies to Linux and rkhunter.

Second, you need to google and understand the "warnings" you recieve from rkhunter.

Third, you do not trust the advice you have recieved in this thread. Several users have given you an answer, and that answer would be supported by a google search.

So if you are unwilling to use the tool properly, unwilling to research the warnings you recieve, and you do not trust the advice you have been given there really is:

1. Not much point in running rkhunter.

2. Not much we can do to help you further.

Linux is not Windows and Linux does not suffer from viruses and rootkits in to the same degree as other OS and rkhunter is, by it's nature, going to give you a ton of false positives. You need to either:

1. Trust others when they tell you they are false positives.

2. Or, research and confirm for this for yourself.

So if you do not trust the good advice of others, time to fire up google, start running rkhunter on a live CD, and learn for yourself.

My above remark was in relation to bodhi's remarks.  I am new to this and forgot to include the quote.

---

### Post by ricyaun on 2010-03-31
So bodhi.zazhen knows I was agreeing and comoplimenting his superior understanding of the issue at hand.

---

### Post by doas777 on 2010-04-01
> **XitNow said:**
> I have a question.  I am new to Ubuntu from Vista.  Played around with some Unix in college, have a real basic understanding and not much else so I appologize in advance for my inexperience.
 
I had a couple issues with a box, didn't think I really needed to do anything to protect linux.  Re-installed newest version, added stuff to firefox (noscript, adblock etc), intalled firewall, used a hardening tool, then ran rkhunter.
 
It came back with some warning messages, the one that worried me the most was a possible rootkit named Xibit or something like that.  I am assuming that this is not a warning message that you guys are getting right out of the box correct?

no, that is not one i would ignore. please post the full log if you can, and I'll look at it. just fyi, a rootkit cannot be cleaned via any conventional means, so if you can confirm infection, it's time to rebuild.

---

