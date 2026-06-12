---
title: "Empathy"
date: 2013-01-01
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-01-01
i am testing today's build(2013-01-01) and empathy refuses to work
it's happening from 3 builds ago,i am testing everyday's builds
is there anything wrong with telepathy?

---

### Post by jokerdino on 2013-01-02
I get this when I run from the terminal:

```

$ empathy
empathy: error while loading shared libraries: libtelepathy-logger.so.2: cannot open shared object file: No such file or directory

```

You probably might want to keep an eye on [https://answers.launchpad.net/ubuntu/+question/218002](https://answers.launchpad.net/ubuntu/+question/218002) as well.

---

### Post by rrnbtter on 2013-01-02
Greetings,

> **kuvanito said:**
> 
is there anything wrong with telepathy?

Gajim works fine. I have Empathy removed.

---

### Post by mc4man on 2013-01-02
wait for an empathy update
or
downgrade to previous
or
tmp symlink - amd64 install
```
sudo ln -s  /usr/lib/x86_64-linux-gnu/libtelepathy-logger.so.3.2.0 /usr/lib/x86_64-linux-gnu/libtelepathy-logger.so.2

```
If using symlink & it has issues  then remove the link, downgrade or wait

edit: a simple re-build of empathy seems like it would do

---

### Post by kuvanito on 2013-01-02
> **mc4man said:**
> wait for an empathy update
I will.Thank You...

---

### Post by zika on 2013-01-03
There is some trouble with Empathy:

```
(Reading database ... 217937 files and directories currently installed.)
Unpacking libtelepathy-logger3:amd64 (from .../libtelepathy-logger3_0.6.0-2~git1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libtelepathy-logger.so.3.2.0', which is also in package libtelepathy-logger2:amd64 0.6.0-1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on libtelepathy-logger3 (>= 0.2.10); however:
  Package libtelepathy-logger3:amd64 is not installed.

dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-yahoo:
 account-plugin-yahoo depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.

dpkg: error processing account-plugin-yahoo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-jabber:
 account-plugin-jabber depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.

dpkg: error processing account-plugin-jabber (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-telepathylogger-0.2:
 gir1.2-telepathylogger-0.2 depends on libtelepathy-logger3 (>= 0.2.10); however:
  Package libtelepathy-logger3:amd64 is not installed.

dpkg: error processing gir1.2-telepathylogger-0.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of telepathy-logger:
 telepathy-logger depends on libtelepathy-logger3 (= 0.6.0-2~git1); however:
  Package libtelepathy-logger3:amd64 is not installed.

dpkg: error processing telepathy-logger (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto-empathy:
 nautilus-sendto-empathy depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.

dpkg: error processing nautilus-sendto-empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mcp-account-manager-uoa:
 mcp-account-manager-uoa depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.

dpkg: error processing mcp-account-manager-uoa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-aim:
 account-plugin-aim depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.
 account-plugin-aim depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing account-plugin-aim (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-salut:
 account-plugin-salut depends on empathy (= 3.6.2-0ubuntu2); however:
  Package empathy is not configured yet.
 account-plugin-salut depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing account-plugin-salut (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gir1.2-telepathylogger-0.2; however:
  Package gir1.2-telepathylogger-0.2 is not configured yet.

dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 empathy
 account-plugin-yahoo
 account-plugin-jabber
 gir1.2-telepathylogger-0.2
 telepathy-logger
 nautilus-sendto-empathy
 mcp-account-manager-uoa
 account-plugin-aim
 account-plugin-salut
 gnome-shell

``````
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libtelepathy-logger3
The following NEW packages will be installed:
  libtelepathy-logger3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0 B/75.5 kB of archives.
After this operation, 230 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 217937 files and directories currently installed.)
Unpacking libtelepathy-logger3:amd64 (from .../libtelepathy-logger3_0.6.0-2~git1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libtelepathy-logger.so.3.2.0', which is also in package libtelepathy-logger2:amd64 0.6.0-1
Errors were encountered while processing:
 /var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Proposed is turned-off...

---

### Post by mc4man on 2013-01-03
> empathy (3.6.2-0ubuntu2) raring; urgency=low

  * No-change rebuild for new telepathy-logger version (LP: #1095428)
 -- Jeremy Bicha <jbicha@ubuntu.com>   Thu, 03 Jan 2013 11:50:12 -0500

There will be some additional updates inc. a new package  - libtelepathy-logger3

If you experience any issue with libtelepathy-logger3 failing to install due to same file in libtelepathy-logger2 then you can force an overwrite with dpkg or if using synaptic & all the other packages installed then probably safe to remove libtelepathy-logger2 (ck. 1st.), ect.

Edit: Ex. of forced in a **amd64** install
```
sudo dpkg -i --force overwrite '/var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb'

```
(unfortunately the previous upload of libtelepathy-logger had the new .3 .so but kept the same package name libtelepathy-logger2

---

### Post by zika on 2013-01-03
> **mc4man said:**
> There will be some additional updates inc. a new package  - libtelepathy-logger3

If you experience any issue with libtelepathy-logger3 failing to install due to same file in libtelepathy-logger2 then you can force an overwrite with dpkg or if using synaptic & all the other packages installed then probably safe to remove libtelepathy-logger2 (ck. 1st.), ect.

Edit: Ex. of forced in a **amd64** install
```
sudo dpkg -i --force overwrite '/var/cache/apt/archives/libtelepathy-logger3_0.6.0-2~git1_amd64.deb'

```(unfortunately the previous upload of libtelepathy-logger had the new .3 .so but kept the same package name libtelepathy-logger2Thank You, that seemed to work...
(I've tried purging libtelepathy-logger2 as soon as error appeared but...)

---

### Post by kuvanito on 2013-01-04
yesterday's updates brought success!
all is well now
empathy works and ubuntu 13.04 ROCKS!
thread marked as SOLVED!

---

