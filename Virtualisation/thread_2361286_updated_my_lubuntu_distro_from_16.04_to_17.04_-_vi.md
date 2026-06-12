---
title: "updated my lubuntu distro from 16.04 to 17.04 - virtual box issues"
date: 2017-05-14
forum: Virtualisation
---

### Post by dave241 on 2017-05-14
-SOLVED-
I rebooted and reinstalled
first time i tried to reinstall it didnt do anything
reboot and another reinstall fixed it

I am trying to use my virtual box for my kali image and after upgrading my linux distro it seems to be broken  here is my error

```
sudo /sbin/vboxconfig
[sudo] password for dave: 
Created symlink /etc/systemd/system/multi-user.target.wants/vboxdrv.service &#8594; /lib/systemd/system/vboxdrv.service.
Created symlink /etc/systemd/system/multi-user.target.wants/vboxballoonctrl-service.service &#8594; /lib/systemd/system/vboxballoonctrl-service.service.
Created symlink /etc/systemd/system/multi-user.target.wants/vboxautostart-service.service &#8594; /lib/systemd/system/vboxautostart-service.service.
Created symlink /etc/systemd/system/multi-user.target.wants/vboxweb-service.service &#8594; /lib/systemd/system/vboxweb-service.service.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-install.log to find out what went wrong.
```

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.


pastebin wont let me paste it "too large" I think this is the important part of the log.

```
1 make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 CONFIG_MODULE_SIG= -C /lib/modules/4.4.0-31-generic/build -j2 modules
2 make[1]: warning: -jN forced in submake: disabling jobserver mode.
3 test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
4 echo >&2;                            \
5 echo >&2 "  ERROR: Kernel configuration is invalid.";        \
6 echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
7 echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
8 echo >&2 ;                            \
9 /bin/false)

```
Now I believe line 7 says how to fix the problem. I am just unsure how it wants me to do it.

---

### Post by wildmanne39 on 2017-05-14
*Thread moved to **Virtualisation**.*

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by ajgreeny on 2017-05-15
And now, please tell us what the solution really was; did the suggestion in line #7 put it right?

---

