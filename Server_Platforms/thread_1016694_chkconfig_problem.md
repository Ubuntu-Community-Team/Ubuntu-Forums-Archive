---
title: "chkconfig problem"
date: 2008-12-20
forum: Server Platforms
---

### Post by chranmat on 2008-12-20
Hi,

When I try to stop bind9 from starting with the system using chkconfig I get the following errors:

root@host:/# chkconfig bind9 off
insserv: warning: script 'S10udev' missing LSB tags and overrides
insserv: warning: script 'S08loopback' missing LSB tags and overrides
insserv: warning: script 'S37udev-finish' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
insserv: warning: script 'loopback' missing LSB tags and overrides
insserv: script vmware-core: service VMware already provided!
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: script vmware: service VMware already provided!
insserv: There is a loop between service networking and mountall
insserv:  loop involving service mountall at depth 9
insserv:  loop involving service checkfs at depth 8
insserv: There is a loop between service networking and mountall
insserv: There is a loop between service udev and hwclockfirst
insserv:  loop involving service hwclockfirst at depth 6
insserv:  loop involving service mountdevsubfs at depth 5
insserv: There is a loop between service hwclock and mountdevsubfs
insserv:  loop involving service udev at depth 8
insserv:  loop involving service umountnfs at depth 2
insserv:  loop involving service networking at depth 1
insserv:  loop involving service hwclock at depth 15
insserv:  loop involving service mountnfs at depth 12
insserv:  loop involving service checkroot at depth 15
insserv:  loop involving service $network at depth 21
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1
root@host:/#

Someone who know what to do?

Regards,
Christian

---

### Post by bluefrog on 2008-12-20
update-rc.d bind9 remove

---

### Post by martien on 2008-12-20
Does Ubuntu support chkconfig at all? Isn't it for red hat based systems?

---

### Post by hictio on 2008-12-20
> **martien said:**
> Does Ubuntu support chkconfig at all? Isn't it for red hat based systems?

Yeap, 'chkconfig' does work on RH systems.

> 
Users of Red Hat and Mandriva will be used to configuring which services run by using the chkconfig command, for example, chkconfig sshd on. In Ubuntu, chkconfig is not available, however there is an alternative, sysv-rc-conf (which is not installed by default).


From: [Switching To Ubuntu From Linux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux), specifically [Services, Chkconfig and Initscripts](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux#Services,%20Chkconfig%20and%20Initscripts), read it, there is a workaround using a function on the root's .bashrc file, and you could also install 'sysv-rc-conf' with:

```

sudo aptitude install sysv-rc-conf (ENTER)

```

---

### Post by ibutho on 2008-12-20
> **martien said:**
> Does Ubuntu support chkconfig at all? Isn't it for red hat based systems?

Its supported to some extent, but from my personal experience (using Ubuntu 7.10 and 8.04) it currently does not work as well as the versions in Red Hat/Fedora and Mandriva.

---

### Post by cariboo on 2008-12-20
As bluefrog said the prefered debian way is to use update-rc.d. To stop bind9 from starting in a terminal type:

```
sudo update-rc.d -f bind9 remove
```

Just type update-rc.d in a terminal for options.

Jim

---

### Post by chranmat on 2008-12-21
I installed chkconfig with api-get. From what I understad it should be supported then?

> **martien said:**
> Does Ubuntu support chkconfig at all? Isn't it for red hat based systems?

---

### Post by chranmat on 2008-12-21
sysv-rc-conf looks great. Also the article SwitchingToUbuntuFromLinux are very helpful for me as new in Ubuntu.

> **hictio said:**
> Yeap, 'chkconfig' does work on RH systems.



From: [Switching To Ubuntu From Linux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux), specifically [Services, Chkconfig and Initscripts](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux#Services,%20Chkconfig%20and%20Initscripts), read it, there is a workaround using a function on the root's .bashrc file, and you could also install 'sysv-rc-conf' with:

```

sudo aptitude install sysv-rc-conf (ENTER)

```

---

### Post by swajime on 2009-09-19
> **cariboo907 said:**
> As bluefrog said the prefered debian way is to use update-rc.d. To stop bind9 from starting in a terminal type:

```
sudo update-rc.d -f bind9 remove
```

Just type update-rc.d in a terminal for options.

Jim

The manpage of update-rc.d states [INDENT]"Please note that this program was designed for use in package maintainer scripts and accordingly, has only the very limited functionality required by such scripts.  **System administrators are [COLOR="Red"]_not_[/COLOR] encouraged to use update-rc.d to manage runlevels.**  They should edit the links directly or use runlevel editors such as sysv-rc-conf and bum instead."[/INDENT]
It would be nice if someone could explain what we need to do to get chkconfig to work properly.
-- 
John

---

