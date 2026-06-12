---
title: "kernel driver not installed"
date: 2019-03-24
forum: Virtualisation
---

### Post by edstevens on 2019-03-24
While this deals with a specific product (Oracle VirtualBox) the problem, and solution, appears to be more generically Ubuntu related.

When I purchased my laptop, running Ubuntu 16.04 LTS, a couple of years ago one of the first things I did was install Oracle VirtualBox.  Have upgraded it several times since, and have never had a problem with it from Day One.  Then a few days ago (have not used it in a few weeks) I needed to do some work with one of the VMs created under Vbox.  The Vbox control console opened just fine, but when I tried to start any one of the VMs, I got this:

[IMG]https://community.oracle.com/servlet/JiveServlet/showImage/2-15099489-708523/pastedImage_0.png[/IMG]

So, following the instructions there:
 [INDENT][FONT=courier new]ed@ed-Gazelle-00:~$ sudo /sbin/vboxconfig[/FONT]
[FONT=courier new][sudo] password for ed: [/FONT]
[FONT=courier new]vboxdrv.sh: Building VirtualBox kernel modules.[/FONT]
[FONT=courier new]vboxdrv.sh: failed: Look at /var/log/vbox-install.log to find out what went wrong.[/FONT]
 
[FONT=courier new]There were problems setting up VirtualBox.  To re-start the set-up process, run[/FONT]
[FONT=courier new]  /sbin/vboxconfig[/FONT]
[FONT=courier new]as root.[/FONT]
[/INDENT]
contents of the log file:
 [INDENT][FONT=courier new]make  KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0  CONFIG_MODULE_SIG= -C /lib/modules/4.4.0-47-generic/build -j4 modules[/FONT]
[FONT=courier new]make[1]: warning: -jN forced in submake: disabling jobserver mode.[/FONT]
[FONT=courier new]test -e include/generated/autoconf.h -a -e include/config/auto.conf || (                \[/FONT]
[FONT=courier new]echo >&2;                                                       \[/FONT]
[FONT=courier new]echo >&2 "  ERROR: Kernel configuration is invalid.";           \[/FONT]
[FONT=courier new]echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\[/FONT]
[FONT=courier new]echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";      \[/FONT]
[FONT=courier new]echo >&2 ;                                                      \[/FONT]
[FONT=courier new]/bin/false)[/FONT]
[FONT=courier new]mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*[/FONT]
[FONT=courier new]make -f ./scripts/Makefile.build obj=/tmp/vbox.0[/FONT]
[FONT=courier new]@                                                                             [/FONT]
[/INDENT]
The  man page for make says nothing about 'oldconfig' or 'prepare', and  doing a little googling about it what I find sounds like it can be  pretty dangerous to your system if you don't take a lot of precautions.
 
Advice?

---

### Post by edstevens on 2019-03-25
Ok, I fixed it (for the time being) by rebooting and reverting back to the previous kernel - 4.4.0.142.  And having done that I come back here an see that several others have reported the same issue.  Seems that the 143 update broke Vbox, and according to [https://ubuntuforums.org/showthread.php?t=2415046](https://ubuntuforums.org/showthread.php?t=2415046) the VBox team is aware and has a fix in at test build.  I'll continue to revert to the 142 update until such time as Vbox rolls out the fix in a GA release.

---

