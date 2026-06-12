---
title: "faxgetty crash"
date: 2010-02-15
forum: Server Platforms
---

### Post by nuzzosono on 2010-02-15
Hi everybody, I did a quick search but I didn't find any clue to solve my problem.
 
I have set up a small server to work like an Hylafax server.
 
The machine is an old pentium with the latest version on ubuntu running (9.10 karmic koala)
 
I installed hylafax via official repository (apy-get hylafax-server etc)
 
The problem is that the component faxgetty crash very frequent, I asked to the hylafax forum but they told me that probably in an os problem.
 
This is the log that I found in the moment of the crash:
 
```
 
Feb 15 17:48:00 faxserver FaxGetty[14137]: MODEM PHILIPS BU PC ADD ON CARDS#012P
CA22EV (33600) 33.6 FAX MODEM 336/
Feb 15 18:08:44 faxserver FaxGetty[14137]: ANSWER: FAX CONNECTION DEVICE '/dev/
ttyS0'
Feb 15 18:09:01 faxserver kernel: [553607.496064] faxgetty[14137]: segfault at a
40 ip 0805c073 sp bfe941f0 error 4 in faxgetty[8048000+72000]

```
[SIZE=2][/SIZE] 
any idea?
 
Where can I start from?
 
Thanks in advance.

---

### Post by nuzzosono on 2010-02-25
up! Please!!

---

### Post by valentijnsessink on 2010-06-30
Same problem here, with almost the same message: faxgetty[3988]: segfault at a3d ip 0805c083 sp bf923ad0 error 4 in faxgetty[8048000+72000]

Did you find out what goes wrong?

---

### Post by yaztromo on 2010-09-01
[https://bugs.launchpad.net/ubuntu/+source/hylafax/+bug/600219](https://bugs.launchpad.net/ubuntu/+source/hylafax/+bug/600219)

---

### Post by hhubris on 2010-11-02
> **yaztromo said:**
> [https://bugs.launchpad.net/ubuntu/+source/hylafax/+bug/600219](https://bugs.launchpad.net/ubuntu/+source/hylafax/+bug/600219)

It seems there was a fix committed, I'm assuming to the original Debian packages.

What is the quickest way I will be able to get this fix applied to a 10.04.1 LTS installation?

Thank you in advance for any help.

---

### Post by cphuntington97 on 2011-04-18
Did we ever find a solution to this? Also running 10.04.2 LTS. Would greatly appreciate a patch.

In the mean time, could anyone provide a script that watches the logs for faxgetty to crash and restarts hylafax or faxgetty when this happens? I am not much of a wizard.

---

### Post by yaztromo on 2011-04-18
Since the Hylafax bug in 10.04 I just run the Hardy 8.04 packages

[http://packages.ubuntu.com/hardy/hylafax-server](http://packages.ubuntu.com/hardy/hylafax-server)

They work fine on Karmic and I don't get any crashes.

---

### Post by jringoot on 2011-10-07
[FONT="Lucida Sans Unicode"]Thanks for the tip yaztromo, but installing the previous version of hylafax is not so straightforward, see below:

[/FONT][FONT="Courier New"]root@cal-04:~/config# uname -a
Linux cal-04 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
root@cal-04:~/config# dpkg -i /root/config/hylafax-server_4.4.3-1_i386.deb 
(Reading database ... 219533 files and directories currently installed.)
Preparing to replace hylafax-server 2:4.4.3-1 (using .../hylafax-server_4.4.3-1_i386.deb) ...
Unpacking replacement hylafax-server ...
dpkg: dependency problems prevent configuration of hylafax-server:
 hylafax-server depends on hylafax-client (= 2:4.4.3-1); however:
  Version of hylafax-client on system is 2:6.0.3-5.1ubuntu1.
 hylafax-server depends on metamail; however:
  Package metamail is not installed.
 hylafax-server depends on sharutils; however:
  Package sharutils is not installed.
dpkg: error processing hylafax-server (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 hylafax-server
root@cal-04:~/config# 
root@cal-04:~/config# apt-get install metamail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package metamail is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package metamail has no installation candidate
root@cal-04:~/config# 
[/FONT]

---

### Post by yaztromo on 2011-10-13
Your first dependency problem could be solved by also installing the hardy client deb for hylafax too from packages.ubuntu.com.

Also for metamail try getting the hardy package for that as well. It is a long time since I rolled back hylafax so I might have to had to manually install metamail too.

So....

- Grab the hardy packages for metamail and hylafax-client from packages.ubuntu.com
- Put all the packages into one dpkg -i command like dpkg -i metamail-blah.deb hylafax-client-blah.deb hylafax-server-blah.deb

Maybe that will work.

---

### Post by jringoot on 2011-10-14
I installed these, last friday 2011/10/07:

hylafax-client_6.0.5-5ubuntu2_i386.deb
root@cal-04:~/config# dpkg -I hylafax-client_6.0.5-5ubuntu2_i386.deb 
 new debian package, version 2.0.
 size 335084 bytes: control archive= 2689 bytes.
      95 bytes,     4 lines      conffiles            
     835 bytes,    20 lines      control              
    2452 bytes,    36 lines      md5sums              
    1867 bytes,    69 lines   *  postinst             #!/bin/sh
     351 bytes,    16 lines   *  postrm               #!/bin/sh
      32 bytes,     1 lines      shlibs               
 Package: hylafax-client
 Source: hylafax
 Version: 2:6.0.5-5ubuntu2
 Architecture: i386
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 Installed-Size: 896
 Pre-Depends: libpaper-utils
 Depends: libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libtiff4, zlib1g (>= 1:1.1.4), enscript | libgnomeprint-data, ucf, gsfonts, ghostscript
 Recommends: netpbm, transfig
 Suggests: mgetty-viewfax
 Conflicts: mgetty-fax
 Section: comm
 Priority: extra
 Homepage: [http://www.hylafax.org](http://www.hylafax.org)
 Description: Flexible client/server fax software - client utilities
  The HylaFAX client software communicates with a HylaFAX server via TCP/IP.
  .
  HylaFAX support the sending and receiving of facsimiles, the polled
  retrieval of facsimiles and the send of alphanumeric pages.
 Original-Maintainer: Giuseppe Sacco <eppesuig@debian.org>

hylafax-server_6.0.5-5ubuntu2_i386.deb
root@cal-04:~/config# dpkg -I hylafax-server_6.0.5-5ubuntu2_i386.deb 
 new debian package, version 2.0.
 size 1110372 bytes: control archive= 15298 bytes.
    9329 bytes,   201 lines      conffiles            
    1192 bytes,    21 lines      control              
   12046 bytes,   181 lines      md5sums              
    9359 bytes,   304 lines   *  postinst             #!/bin/sh
    1181 bytes,    40 lines   *  postrm               #!/bin/sh
     192 bytes,    11 lines   *  prerm                #!/bin/sh
   10626 bytes,    74 lines      templates            
 Package: hylafax-server
 Source: hylafax
 Version: 2:6.0.5-5ubuntu2
 Architecture: i386
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 Installed-Size: 3968
 Depends: hylafax-client (= 2:6.0.5-5ubuntu2), libc6 (>= 2.11), libgcc1 (>= 1:4.1.1), libpam0g (>= 0.99.7.1), libstdc++6 (>= 4.1.1), libtiff4, zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, libtiff-tools (>= 3.6.1-3), bsd-mailx | mailx, psmisc, sed (>= 4.1.2), ghostscript, adduser, lsb-base (>= 3.0-6), exim4-daemon-light | mail-transport-agent
 Suggests: mgetty, psrip
 Conflicts: capi4hylafax (<< 1:01.02.03-4), mgetty-fax
 Section: comm
 Priority: extra
 Homepage: [http://www.hylafax.org](http://www.hylafax.org)
 Description: Flexible client/server fax software - server daemons
  This package support the sending and receiving of facsimiles, the polled
  retrieval of facsimiles and the send of alphanumeric pages.
  .
  The host running the server must have either a Class 1, Class 2, or a
  Class 2.0 fax modem attached to one of its serial ports. End-user
  applications to manage the transmission of documents via facsimile are
  provided separately by the hylafax-client package.
 Original-Maintainer: Giuseppe Sacco <eppesuig@debian.org>
root@cal-04:~/config# 


they appear stable, working since last week friday without error.
Received 26 faxes since then.

---

### Post by freechelmi on 2012-05-28
> **jringoot said:**
> I installed these, last friday 2011/10/07:

hylafax-client_6.0.5-5ubuntu2_i386.deb

Hi , are you sure this version includes the patch for the faxgetty error ?

---

### Post by yaztromo on 2012-05-28
The bug free package for hardy wasn't built until this year and has the ending "-5" not "-2". So I imagine he's running a version with the bug still present.

You can get the latest one at [http://eppesuigoccas.homedns.org/~giuseppe/debian/hylafax/lucid-i386/bug%23600219-no-optimization/](http://eppesuigoccas.homedns.org/~giuseppe/debian/hylafax/lucid-i386/bug%23600219-no-optimization/)

AFAIK it is not in the repositories yet.

---

### Post by freechelmi on 2012-05-28
> **yaztromo said:**
> The bug free package for hardy wasn't built until this year and has the ending "-5" not "-2". So I imagine he's running a version with the bug still present.

You can get the latest one at [http://eppesuigoccas.homedns.org/~giuseppe/debian/hylafax/lucid-i386/bug%23600219-no-optimization/](http://eppesuigoccas.homedns.org/~giuseppe/debian/hylafax/lucid-i386/bug%23600219-no-optimization/)

AFAIK it is not in the repositories yet.

I'm running lucid, did you mean lucid as well ?

I've install the debs from 

[https://launchpad.net/~a.bono/+archive/hylafax/+build/2795868](https://launchpad.net/~a.bono/+archive/hylafax/+build/2795868)

And cross fingers.


Why this recompiled did not end in Ubuntu Updates for Lucid ?

---

