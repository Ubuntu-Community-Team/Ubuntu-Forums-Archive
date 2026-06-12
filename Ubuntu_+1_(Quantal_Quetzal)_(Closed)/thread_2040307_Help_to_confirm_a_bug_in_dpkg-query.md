---
title: "Help to confirm a bug in dpkg-query"
date: 2012-08-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-10
Hey, can anyone help to confirm this? I have tested with dpkg-query, which is not SUID, but I can see some danger considering sudo'd dpkg... See below:

This works as expected:
```

[18:27:51] ahsl@AL-DESK01:[~]: dpkg-query -W -f='\nPackage:${Package}\nDepends:${Depends}\nProvides:${Provides}\n${Description}\n\n' apt

```
> 
Package:apt
Depends:ubuntu-keyring, libapt-pkg4.12 (>= 0.9.7.1ubuntu1), libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.6), gnupg
Provides:
commandline package manager
 This package provides commandline tools for searching and
 managing as well as querying information about packages
 as a low-level access to all features of the libapt-pkg library.
 .
 These include:
  * apt-get for retrieval of packages and information about them
    from authenticated sources and for installation, upgrade and
    removal of packages together with their dependencies
  * apt-cache for querying available information about installed
    as well as installable packages
  * apt-cdrom to use removable media as a source for packages
  * apt-config as an interface to the configuration settings
  * apt-key as an interface to manage authentication keys

Then I made a mistake and used double quotation marks instead of single quotation marks. See what happens:
```

[18:28:12] ahsl@AL-DESK01:[~]: sudo dpkg-query -W -f="${provides}" apt

```
> 
dpkg-query: error in show format: H&#65533;C0
*** glibc detected *** dpkg-query: free(): invalid pointer: 0x00007f9596bedc84 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7e506)[0x7f9596bf0506]
dpkg-query[0x4091a3]
dpkg-query[0x404473]
dpkg-query[0x402779]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f9596b9376d]
dpkg-query[0x4027ed]
======= Memory map: ========
00400000-0041f000 r-xp 00000000 08:01 2904021                            /usr/bin/dpkg-query
0061e000-0061f000 r--p 0001e000 08:01 2904021                            /usr/bin/dpkg-query
0061f000-00620000 rw-p 0001f000 08:01 2904021                            /usr/bin/dpkg-query
00620000-00734000 rw-p 00000000 00:00 0 
01526000-01547000 rw-p 00000000 00:00 0                                  [heap]
7f9596691000-7f95966a6000 r-xp 00000000 08:01 524420                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f95966a6000-7f95968a5000 ---p 00015000 08:01 524420                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f95968a5000-7f95968a6000 r--p 00014000 08:01 524420                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f95968a6000-7f95968a7000 rw-p 00015000 08:01 524420                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f95968a7000-7f9596b72000 r--p 00000000 08:01 2889281                    /usr/lib/locale/locale-archive
7f9596b72000-7f9596d24000 r-xp 00000000 08:01 525233                     /lib/x86_64-linux-gnu/libc-2.15.so
7f9596d24000-7f9596f24000 ---p 001b2000 08:01 525233                     /lib/x86_64-linux-gnu/libc-2.15.so
7f9596f24000-7f9596f28000 r--p 001b2000 08:01 525233                     /lib/x86_64-linux-gnu/libc-2.15.so
7f9596f28000-7f9596f2a000 rw-p 001b6000 08:01 525233                     /lib/x86_64-linux-gnu/libc-2.15.so
7f9596f2a000-7f9596f2f000 rw-p 00000000 00:00 0 
7f9596f2f000-7f9596f51000 r-xp 00000000 08:01 525223                     /lib/x86_64-linux-gnu/ld-2.15.so
7f959712e000-7f9597131000 rw-p 00000000 00:00 0 
7f959714e000-7f9597151000 rw-p 00000000 00:00 0 
7f9597151000-7f9597152000 r--p 00022000 08:01 525223                     /lib/x86_64-linux-gnu/ld-2.15.so
7f9597152000-7f9597154000 rw-p 00023000 08:01 525223                     /lib/x86_64-linux-gnu/ld-2.15.so
7fff3731f000-7fff37340000 rw-p 00000000 00:00 0                          [stack]
7fff373ff000-7fff37400000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

```

[18:28:48] ahsl@AL-DESK01:[~]: uname -a

```
> 
Linux AL-DESK01 3.5.0-7-generic #7-Ubuntu SMP Tue Jul 31 07:22:20 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

[18:29:43] ahsl@AL-DESK01:[~]: dpkg-query --version

```
> 
Debian dpkg-query package management program query tool version 1.16.7 (amd64).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.


Regards,
Effenberg

---

### Post by ventrical on 2012-08-10
```

dale@dale-desktop:~/Desktop$ dpkg-query -W -f='\nPackage:${Package}\nDepends:${Depends}\nProvides:${Provides}\n${Description}\n\n' apt

Package:apt
Depends:ubuntu-keyring, libapt-pkg4.12 (>= 0.9.7.1ubuntu1), libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.6), gnupg
Provides:
commandline package manager
 This package provides commandline tools for searching and
 managing as well as querying information about packages
 as a low-level access to all features of the libapt-pkg library.
 .
 These include:
  * apt-get for retrieval of packages and information about them
    from authenticated sources and for installation, upgrade and
    removal of packages together with their dependencies
  * apt-cache for querying available information about installed
    as well as installable packages
  * apt-cdrom to use removable media as a source for packages
  * apt-config as an interface to the configuration settings
  * apt-key as an interface to manage authentication keys

dale@dale-desktop:~/Desktop$ sudo dpkg-query -W -f="${provides}" apt
[sudo] password for dale: 
dpkg-query: error in show format: (null)
dale@dale-desktop:~/Desktop$ uname -a
Linux dale-desktop 3.5.0-8-generic #8-Ubuntu SMP Sat Aug 4 04:43:06 UTC 2012 i686 i686 i686 GNU/Linux
dale@dale-desktop:~/Desktop$ dpkg-query --version
Debian dpkg-query package management program query tool version 1.16.7 (i386).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.
dale@dale-desktop:~/Desktop$ 

```

Whoops .. you are using 64bit ! :)

---

### Post by effenberg0x0 on 2012-08-10
Ok, thanks, hopefully this is exclusive to x86_64 and kernel 3.5.0-7. Let's see if someone else sees this.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-10
See the same crasher in 64 bit. *earliest kernel here is the -generic #3, same deal.
You'd likely get a /var/crash, whether worth pursuing ...?

Edit - worth pursuing as in "" should produce no results anyway

---

### Post by effenberg0x0 on 2012-08-10
> **mc4man said:**
> See the same crasher in 64 bit. *earliest kernel here is the -generic #3, same deal.
You'd likely get a /var/crash, whether worth pursuing ...?

Weird, I got nothing on /var/crash/*dpkg-query*, and no crash/report dialog, anything. I have checked apport service and default/apport, its OK :\ Do you get something in /var/crash?

Regards,
Effenberg

---

### Post by cariboo on 2012-08-10
I got crash output, when I ran your command, it's about 40K in size, so I've  attached it

---

### Post by mc4man on 2012-08-10
Get 2 crash reports in /var/crash, one root, one user.
Bit of an 'oddity'
Did a reboot & ran this twice
dpkg-query -W -f="$[Depends]" apt
returned nothing as expected both times

Then ran it with sudo & got the crash, repeated  without sudo & also now got the crash ??
screen is reports (did a test build of naut 3.4.2 to see how it's going to work out if brought back

---

### Post by effenberg0x0 on 2012-08-10
> **mc4man said:**
> Get 2 crash reports in /var/crash, one root, one user.
Bit of an 'oddity'
Did a reboot & ran this twice
dpkg-query -W -f="$[Depends]" apt
returned nothing as expected both times

Then ran it with sudo & got the crash, repeated  without sudo & also now got the crash ??
screen is reports (did a test build of naut 3.4.2 to see how it's going to work out if brought back

I've looked at my /var/crash with more attention. Apport is crashing every time.. this is probably why I get nothing... I'll try to just gdb it and get a bt.

---

### Post by mc4man on 2012-08-10
from here - 
> Program received signal SIGABRT, Aborted.
0x00007ffff7a53405 in __GI_raise (sig=<optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
64	../nptl/sysdeps/unix/sysv/linux/raise.c: No such file or directory.
(gdb) bt
#0  0x00007ffff7a53405 in __GI_raise (sig=<optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
#1  0x00007ffff7a56b6b in __GI_abort () at abort.c:91
#2  0x00007ffff7a90d0e in __libc_message (do_abort=2, fmt=0x7ffff7b98fd0 "*** glibc detected *** %s: %s: 0x%s ***\n")
    at ../sysdeps/unix/sysv/linux/libc_fatal.c:201
#3  0x00007ffff7a9b506 in malloc_printerr (action=3, str=0x7ffff7b95f81 "free(): invalid pointer", ptr=<optimized out>)
    at malloc.c:5007
#4  0x00000000004091a3 in dpkg_error_destroy (err=err@entry=0x7fffffffe0e0) at ../../../lib/dpkg/error.c:91
#5  0x0000000000404473 in showpackages (argv=0x7fffffffe250) at ../../src/querycmd.c:521
#6  0x0000000000402779 in main (argc=<optimized out>, argv=0x7fffffffe250) at ../../src/querycmd.c:865


As far as apport - it doesn't crash here but I Never get any gtk popups anymore, that dies out after a few days running an install
(something in the home dir., a new user gets them for a bit

So here usually bookmark /var/crash & clean out every day even though there's a daily cron job that removes week old reports - 
sudo rm /var/crash/*.*

---

### Post by effenberg0x0 on 2012-08-10
Got something. I reported it at [COLOR="Red"]_**[#1035512]("https://bugs.launchpad.net/ubuntu/+bug/1035512")**_[/COLOR]
> 
Reading symbols from /usr/bin/dpkg-query...Reading symbols from /usr/lib/debug/usr/bin/dpkg-query...done.
done.
[New LWP 23389]
warning: Can't read pathname for load map: Input/output error.
Core was generated by `dpkg-query -W -f= apt'.
Program terminated with signal 6, Aborted.
#0  0x00007faec01e8405 in __GI_raise (sig=<optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
64	../nptl/sysdeps/unix/sysv/linux/raise.c: No such file or directory.
(gdb) bt
#0  0x00007faec01e8405 in __GI_raise (sig=<optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
#1  0x00007faec01ebb6b in __GI_abort () at abort.c:91
#2  0x00007faec0225d0e in __libc_message (do_abort=2, 
    fmt=0x7faec032dfd0 "*** glibc detected *** %s: %s: 0x%s ***\n") at ../sysdeps/unix/sysv/linux/libc_fatal.c:201
#3  0x00007faec0230506 in malloc_printerr (action=3, str=0x7faec032af81 "free(): invalid pointer", 
    ptr=<optimized out>) at malloc.c:5007
#4  0x00000000004091a3 in dpkg_error_destroy (err=err@entry=0x7fff3695e690) at ../../../lib/dpkg/error.c:91
#5  0x0000000000404473 in showpackages (argv=0x7fff3695e800) at ../../src/querycmd.c:521
#6  0x0000000000402779 in main (argc=<optimized out>, argv=0x7fff3695e800) at ../../src/querycmd.c:865
(gdb) 


Regards,
Effenberg

---

### Post by mc4man on 2012-08-10
have you tried running apport-cli <some option> to see if it works?
(like apport-cli --window  > press enter, click a window

---

### Post by effenberg0x0 on 2012-08-11
I'm marking this one solved (fix committed).

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-11
> **mc4man said:**
> have you tried running apport-cli <some option> to see if it works?
(like apport-cli --window  > press enter, click a window

Hi, I didn't get a chance to test it. After applying all updates from yesterday to now, apport appears be working normally. apport-retrace is still crashing, but judging by some reports and discussions in boards, I think it hasn't been in a usable state for a while.

Regards,
Effenberg

---

