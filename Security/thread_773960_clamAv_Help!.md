---
title: "clamAv Help!"
date: 2008-04-29
forum: Security
---

### Post by devsen on 2008-04-29
I installed clamav but when I try to run a scan I get the following error -

clamscan: error while loading shared libraries: libclamav.so.4: cannot open shared object file: No such file or directory

Not sure which config file I need to update?

Thanks for any help - Dev, Suffolk, England

---

### Post by Monicker on 2008-04-29
> **devsen said:**
> I installed clamav but when I try to run a scan I get the following error -

clamscan: error while loading shared libraries: libclamav.so.4: cannot open shared object file: No such file or directory

Not sure which config file I need to update?

Thanks for any help - Dev, Suffolk, England


Did you install using the Ubuntu package management, or from source?  I've never seen that error with clamav when using Synaptic or apt-get, which is what you normally should be using to install software in Ubuntu.

---

### Post by cagey cretin on 2008-09-01
I just updated from 6.06 LTS to 8.04. I wanted to compile clamav-0.93.3, but the compiler in 6.04 was spitting out errors about a bug that clamav didn't like. Couldn't upgrade the compiler so I upgraded the OS. So now I am trying to compile clamav (as opposed to the synaptic), and it compiles fine, then when I try to scan an item it spits out:

_"clamscan: error while loading shared libraries: libclamav.so.4: cannot open shared object file: No such file or directory"_

So I run:

[U]# find / -name /usr/local/lib/libclamav.so.4
/usr/local/lib/libclamav.so.4[/U]

Fine. It's there but it isn't. I do a make uninstall and then run:

_apt-get install clamav_

and it installs. I try to scan the file and I get:

_bash: /usr/local/bin/clamscan: No such file or directory_

I just installed it, so I know it's *somewhere*. So:

[U]# whereis clamscan
clamscan: /usr/bin/clamscan /usr/share/man/man1/clamscan.1.gz[/U]

Huh? Why does it think it's in one place then another? So I then run:

[U]# /usr/bin/clamscan ./file.txt
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
..file.txt: OK[/U]

Weird. Just weird. And kind of irritating. 

I want the most up to date version, not so much worried about this machine, but I put files on windows machines and I want to be clean. 

Why am I getting errors when I run the version built from source? I dunno. I tried searching the net with that text string and came up with one hit: this thread.

So, I kept diggin. 

I  use synaptic to remove clamav, clamav-freshclam, and then I delete the /etc/clamav directory. 

According to this webpage:

[http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html](http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html)

*Some people may get an error that references libclamav.so.4. You should be able to run sudo ldconfig to fix the problem.*_sudo ldconfig_* to fix the problem.*

So, I do it. Then I go back to the source directory and try again to compile. then I run clamscan again, and it works. 

This fixed the library call error for me (I hope it does for you, too). Still though. weird. Really weird...

---

