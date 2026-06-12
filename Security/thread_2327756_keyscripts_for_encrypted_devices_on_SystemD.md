---
title: "keyscripts for encrypted devices on SystemD"
date: 2016-06-14
forum: Security
---

### Post by xen3 on 2016-06-14
The goal for this post was to enable a "keyscript" for opening a LUKS container. The "keyscript" parameter is a valid parameter in /etc/crypttab, but SystemD doesn't support it.

Using a keyscript, one can derive keys that are more dynamic, such as based on the presence of network hosts, etcetera.

In this way, you can, for instance, create a "dynamic" key (that you need to statically set ;-)) that you need to create based on parameters that are relevant to your location (such as obtaining it from some server in your network) in this way ensuring that your volumes can only get mounted for instance from within your own network.

That does not protect you against getting hacked, but if you have something that you only want to prevent against being opened outside of your own location (such as law enforcement) then they need to potentially take your entire network with them (which is also a liability) or do the unlocking at your location.

In my case this particular volume can only get unlocked by knowing the MAC address of this computer's ethernet NIC and hence it becomes a tad difficult to do it unless you are running the thing from this computer.

In my case, my MAC address is augmented with parameters only available on a network host :p.

These parameters might just as well reside within an encrypted container which means that at that point, you would be using a different computer to store your encryption key, such that you do not need to enter it each time you boot the computer. This different computer then keeps running, but the key becomes unavailable (and protected) the moment it is turned off (such as taken away). This way you could create a very strong password that you do not need to type all the time (potentially losing your memory of it, which is a risk) but which key (an additional key to the same volume) is loaded from or derived from a different computer that is also strongly protected. However, as long as that other computer is running, anyone with access to your physical computer or your physical location, will have access to the key. The moment that other computer is turned off, it may become very difficult to reproduce it.

In my case it is not that important, but I wanted to have a little bit of a protection for my /var filesystem. It also has a password, but this way, I do not need to type it each time I boot; and my root filesystem is not protected. I protect /var because it contains logs, and without further modification, it can contain logs of anything you do and access, including sudo commands. Of course, you may also have a history of that in your /root/.bash_history. I had not the time anymore to check how I could ever prune those logs, so I created this solution for myself instead.

So the purpose was to enable keyscripts but this is what I did to enable SysV cryptdisks:

- remove /lib/systemd/systemd-cryptsetup
- remove /lib/systemd/system/cryptdisks.service
- create it anew with a valid service file (see below)
- reload daemons: systemctl daemon-reload
- enable service: systemctl enable cryptdisks.service

At this point you cannot test because /etc/init.d/cryptdisks gets hijacked by /lib/lsb/init-functions.d/40-systemd, so if you want to test it, you need to patch it by disabling the check:

```
[FONT=monospace][COLOR=#000000]patch -d /lib/lsb/init-functions.d << "EOF"           [/COLOR]
--- 40-systemd.orig     2016-06-17 15:54:34.079516646 +0200  
+++ 40-systemd  2016-06-17 12:16:16.005467513 +0200
@@ -16,3 +16,3 @@
     # Redirect SysV init scripts when executed by the user
-    if [ $PPID -ne 1 ] && [ -z "${init:-}" ] && [ -z "${_SYSTEMCTL_SKIP_REDIRECT:-}" ]; then
+    if [ $PPID -ne 1 ] && false && [ -z "${init:-}" ] && [ -z "${_SYSTEMCTL_SKIP_REDIRECT:-}" ]; then
         case $(readlink -f "$0") in  
EOF[/FONT]
```[FONT=monospace]
[/FONT]
So now you can test your "keyscripted" (in /etc/crypttab) encryption opening by issuing:

/etc/init.d/cryptdisks start

Not sure if this is the proper way. But it works for me for now (so many troubles....).

---

### Post by xen3 on 2016-06-17
This is the service file I am using for /lib/systemd/system/cryptdisks.service

```
[Unit]
Description=CryptDisks
After=lvm2.service
Before=local-fs-pre.target
DefaultDependencies=no

[Service]
ExecStart=/etc/init.d/cryptdisks start

[Install]
WantedBy=sysinit.target
```

This means that in addition to the above, I have enabled the lvm2.service.

---

