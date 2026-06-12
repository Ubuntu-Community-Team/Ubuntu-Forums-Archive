---
title: "Hangs at: &quot;Setting up console font and keymap...&quot;"
date: 2008-11-18
forum: Server Platforms
---

### Post by Sivar on 2008-11-18
Hello all,

I run or have access to about 4 Ubuntu servers. None have X Windows, all are remotely accessed with SSH.

On every one of these servers I've tried to upgrade to 8.10 Intrepid, the upgrade hangs on:
```
Setting up console font and keymap...
``` during the do-release-upgrade process, or during an "aptitude full-upgrade"
This happened on release day and has happened today. 
I searched Google for this problem. A few had answered their own post with things like "Turned out to be a bunch of garbage in the TTY" (whatever that means) and a few said that it works for them after a reboot (what is this, Windows?), and one guy said to change the keymap in Gnome, which is of course not an option, nor would I know why it should be changed at all.

This is what currently happens:
```
user@server:~# sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following partially installed packages will be configured:
  console-setup ubuntu-minimal
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up console-setup (1.25ubuntu3) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
 * Setting up console font and keymap...

```

I am not sure what is tripping the rc.d error, but I don't remember seeing it on any of the other Ubuntu servers which refuse to update themselves.

How do I get rid of this error?

Best regards,
Frustrated Admin

---

### Post by Sivar on 2008-11-19
Has no one else seen this? I have several times, so I figured it must be common, but maybe not.

---

### Post by vertigo23 on 2009-02-20
I'm seeing this on one of my 8.04 servers.  Annoying as all get-out.

---

### Post by vertigo23 on 2009-02-20
Ah, what someone told you about "garbage in the TTY" is probably accurate.  Log onto the system locally with a keyboard and monitor, and check the consoles (alt-F1 to F6 - those are the TTYs) to see if any of them are hung up with e.g. a bunch of kernel warnings.

---

### Post by FRuMMaGe on 2009-12-17
[Possible workaround]("http://ubuntuforums.org/showthread.php?p=8516423#post8516423")

---

