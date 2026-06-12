---
title: "dpkg errors"
date: 2014-10-10
forum: Ubuntu/Debian BASED
---

### Post by ArthankTheTurtle on 2014-10-10
Hi . I am new to this forum and this is my first post ... Today I had the worst day of my life : 
      -- first , after i formated a partition , the old UUID remained and created errors . I didn;t know back then what to do , since apt-get lines did not work . ( didn't know is because of dpkg ) .
                               I fixed that deleting the UUID from the file . 
      -- now as i tried to update kali and upgrade grub , i encountered the following error lines :  ( i know this might have been already posted in one form or another , but the solutions i found on the forum this far neede dpkg)
this is what i get while trying to fix the apt-get install by apt-get -f install 
Cod : 
   
[TABLE]
[TR]
[TD]```
root@TheWhiteTurtle:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 136 not upgraded.
10 not fully installed or removed.
Need to get 5076 kB of archives.
After this operation, 114 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.kali.org/kali-security/](http://security.kali.org/kali-security/) kali/updates/main libc6 i386 2.13-38+deb7u4 [3820 kB]
Get:2 [http://security.kali.org/kali-security/](http://security.kali.org/kali-security/) kali/updates/main libc6-i686 i386 2.13-38+deb7u4 [1256 kB]                                                     
Fetched 5076 kB in 31s (162 kB/s)                                                                                                                              
Reading changelogs... Done
debconf: Perl may be unconfigured (Can't locate loadable object for  module re in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2  /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5  /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at  /usr/share/perl/5.14/Text/Wrap.pm line 50
Compilation failed in require at /usr/share/perl/5.14/Text/Wrap.pm line 50.
BEGIN failed--compilation aborted at /usr/share/perl/5.14/Text/Wrap.pm line 50.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 10.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 337302 files and directories currently installed.)
Preparing to replace libc6:i386 2.13-38+deb7u3 (using .../libc6_2.13-38+deb7u4_i386.deb) ...
Can't locate loadable object for module re in @INC (@INC contains:  /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2  /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14  /usr/local/lib/site_perl .) at /usr/share/perl/5.14/Text/Wrap.pm line 50
Compilation failed in require at /usr/share/perl/5.14/Text/Wrap.pm line 50.
BEGIN failed--compilation aborted at /usr/share/perl/5.14/Text/Wrap.pm line 50.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 10.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/libc6_2.13-38+deb7u4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-38+deb7u4_i386.deb
Can't locate File/FcntlLock.pm in @INC (@INC contains: /etc/perl  /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5  /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14  /usr/local/lib/site_perl .) at /usr/share/kali-menu/update-kali-menu  line 9.
BEGIN failed--compilation aborted at /usr/share/kali-menu/update-kali-menu line 9.
E: Problem executing scripts DPkg:: Post-Invoke '/usr/share/kali-menu/update-kali-menu wait_dpkg'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
[/TD]
[/TR]
[/TABLE]





I really don't know . Not even if I wrote in the right topic . I am kinda lost . Please help me . 

~Artie~

---

### Post by coffeecat on 2014-10-10
Kali - not Ubuntu.

*Thread moved to **Other Operating Systems and Projects**.*

---

