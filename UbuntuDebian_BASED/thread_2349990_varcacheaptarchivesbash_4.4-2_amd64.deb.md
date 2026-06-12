---
title: "/var/cache/apt/archives/bash_4.4-2_amd64.deb"
date: 2017-01-20
forum: Ubuntu/Debian BASED
---

### Post by xracerx on 2017-01-20
```
     are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 79819 files and directories currently installed.)
Preparing to unpack .../archives/bash_4.4-2_amd64.deb ...
bash.preinst: cannot run dpkg-query: Invalid argument..........................................................................................................................................................]
dpkg: error processing archive /var/cache/apt/archives/bash_4.4-2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.4-2_amd64.deb
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
update-kali-menu: error: can't open /usr/share/applications/byobu.desktop: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Problem executing scripts DPkg::Post-Invoke '[ ! -x /usr/share/kali-menu/update-kali-menu ] || /usr/share/kali-menu/update-kali-menu wait_dpkg'
E: Sub-process returned an error code
root@ECOPSGN102:/mnt/c/Users/denny.oo/Desktop# cat /etc/release
cat: /etc/release: No such file or directory
root@ECOPSGN102:/mnt/c/Users/denny.oo/Desktop# cat lsb/release
cat: lsb/release: No such file or directory
root@ECOPSGN102:/mnt/c/Users/denny.oo/Desktop# uname -a
Linux ECOPSGN102 3.4.0+ #1 PREEMPT Thu Aug 1 17:06:05 CST 2013 x86_64 GNU/Linux
root@ECOPSGN102:/mnt/c/Users/denny.oo/Desktop#

```

Hi,

I have already tried all of these but it does not work:

```
[FONT=Calibri]sudo dpkg --configure -a
[/FONT]
  [FONT=Calibri]sudo apt-get -f upgrade[/FONT]
  [FONT=Consolas]sudo apt-get install -f
[/FONT]

```

---

### Post by Habitual on 2017-01-20
```
/usr/share/kali-menu/update-kali-menu
``` is interesting.

```
cat /etc/lsb-release
``` output please.

---

### Post by ajgreeny on 2017-01-20
In future please give us more information than you did here; what were you trying to do?
You show a chunk of terminal output but not the command which produced it which is a bit confusing.

Where is this bash package from?
What version of Ubuntu are you running?
Is it actually Ubuntu or some other Ubuntu-derived distro?

---

### Post by xracerx on 2017-01-21
> root@ECOPSGN102:/mnt/c/Users/alvin.oo/Desktop$ cat /etc/lsb-release
DISTRIB_ID=Kali
DISTRIB_RELEASE=kali-rolling
DISTRIB_CODENAME=kali-rolling
DISTRIB_DESCRIPTION="Kali GNU/Linux Rolling"

Attached is the output.

---

### Post by howefield on 2017-01-21
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

