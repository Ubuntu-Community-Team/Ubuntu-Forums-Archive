---
title: "apt-get upgrade - Problems with Perl?"
date: 2006-08-23
forum: Server Platforms
---

### Post by ronzo on 2006-08-23
I cannot do an apt-get upgrade on my ubuntu-server. I always get the following message and don't know what to do:

```
root@server1:/# apt-get upgrade Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libkrb53
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/380kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate Debconf/FrontEnd/Noninteractive.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/ConfModule.pm line 13.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/ConfModule.pm line 13.
Compilation failed in require at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/AutoSelect.pm line 8.
Compilation failed in require at (eval 1) line 8.
BEGIN failed--compilation aborted at (eval 1) line 8.
) -- aborting
(Reading database ...
dpkg: serious warning: files list file for package `debconf' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.1_i386.deb (--unpack):
 unable to open files list file for package `libpam0g': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Anyone able to help me?

---

### Post by Crucinator on 2006-08-23
Try reinstalling FrontEnd in Synaptic.  I had a similar problem [here]("http://www.ubuntuforums.org/showthread.php?t=232984").

---

### Post by ronzo on 2006-08-23
I have a server installation here. So there's no synaptic installed.

---

### Post by ronzo on 2006-08-23
A few reboots ago I got error messages concerning the root partition and was forced to do a filesystem check manually. I did that and was not experiencing problems again.

Could the behaviour of apt-get be related to a filesystem problem? Can I be sure that my filesystem (and all the files on it) is ok after a manual fsck? (the file "/usr/sbin/dpkg-preconfigure" was definitely missing on my server so I copied it from another machine with almost the same configuration.) / is an independent ext3-Partition on my server ...

---

