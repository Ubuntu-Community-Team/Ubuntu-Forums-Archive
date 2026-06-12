---
title: "synaptic installs but will not run"
date: 2016-08-19
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-19
As the title suggests.

I have proposed enabled.

---

### Post by P-I H on 2016-08-19
I had that problem too. I was able to run Synaptic according to the attached picture.
Perhaps it's related to my problem
[https://ubuntuforums.org/showthread.php?t=2334279](https://ubuntuforums.org/showthread.php?t=2334279)

---

### Post by ventrical on 2016-08-19
ahhh .. yeah .. I remember that happened in other dev versions also .. 

thnxs

---

### Post by cariboo on 2016-08-19
It seems the desktop file is broken, as synaptic runs if you use the following command:

```
sudo -H synaptic
```

running synaptic-pkexec gives me  the following error message:

```
synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: Xxx,,, (cariboo)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.
```

---

### Post by mc4man on 2016-08-20
It would be policy-kit or dbus/policykit that's broken with the -proposed systemd

---

### Post by QIII on 2016-08-20
Just sudo worked for me in the terminal without the need for su or -H.

I dragged the icon from the Dash onto the desktop and changed the command in Properties to "synaptic" from "synaptic-pkexec", which gave me non-admin access.

Installing gksu let me change the command to "gksudo synaptic" and gave me admin rights.

I'd say that confirms it is PolicyKit.

---

### Post by ventrical on 2016-08-20
I filed this but I think it is the wrong package.

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615191](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615191)

---

### Post by Smask on 2016-08-20
I had some issues with policykit several months ago. I can't remember what I did to fix it other than cleaning up the system with an axe (loads of old cruft from several dist-upgrades.) Cleaning cruft with an axe = "Let's see if I can uninstall this package without removing half of the system". Some of the cruft have its origin from I usually have proposed enabled. (that's why I'm running on a kernel that's listed as "Local or Obsolete at the moment. Why did they remove 4.6 from the repos?)

Nowadays I start synaptic using synaptic-pkexec.

---

### Post by ventrical on 2016-08-20
Mine was fresh install.

 But I know what you mean :)

+1

---

### Post by ventrical on 2016-08-20
> **ventrical said:**
> I filed this but I think it is the wrong package.

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615191](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615191)

Confirmed.

Changed from systemd to synaptic.

Thanks Martin.

Regards..

---

### Post by P-I H on 2016-08-20
I changed back to the initial value in /etc/X11/Xsession.d/00upstart according to the document in
[https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html)

```
As an alternative, unless you removed upstart, you temporarily switch
back to the upstart jobs by editing /etc/X11/Xsession.d/00upstart and
replacing the line

    if [ "${1#*.target}" != "$1" ]; then

with

    if false && [ "${1#*.target}" != "$1" ]; then

(i. e. effectively disable the "if").



```

After a reboot 
- Synaptic will not start
- Not able to install packets with Ubuntu Software
- Not able to make changes in User Account using System Settings

---

### Post by ventrical on 2016-08-20
> **P-I H said:**
> I changed back to the initial value in /etc/X11/Xsession.d/00upstart according to the document in
[https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-July/039465.html)

```
As an alternative, unless you removed upstart, you temporarily switch
back to the upstart jobs by editing /etc/X11/Xsession.d/00upstart and
replacing the line

    if [ "${1#*.target}" != "$1" ]; then

with

    if false && [ "${1#*.target}" != "$1" ]; then

(i. e. effectively disable the "if").



```

After a reboot 
- Synaptic will not start
- Not able to install packets with Ubuntu Software
- Not able to make changes in User Account using System Settings

I filed this bug and it is getting consideration thanks to mac4man.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1615191](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1615191)

---

