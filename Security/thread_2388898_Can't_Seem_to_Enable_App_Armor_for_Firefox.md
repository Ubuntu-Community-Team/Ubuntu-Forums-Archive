---
title: "Can't Seem to Enable App Armor for Firefox"
date: 2018-04-09
forum: Security
---

### Post by open4epl on 2018-04-09
How do I get Firefox profile in App Armor?

Here's info from Term.:
```
apparmor module is loaded.
33 profiles are loaded.
33 profiles are in enforce mode.
   /sbin/dhclient
   /snap/core/4206/usr/lib/snapd/snap-confine
   /snap/core/4206/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /snap/core/4206/usr/lib/snapd/snap-confine//snap_update_ns
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/lib/snapd/snap-confine//snap_update_ns
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ippusbxd
   /usr/sbin/tcpdump
   snap.core.hook.configure
   snap.ufw.doc
   snap.ufw.init
   snap.ufw.ipset
   snap.ufw.shell
   snap.ufw.srv
   snap.ufw.ufw
   webbrowser-app
   webbrowser-app//oxide_helper
0 profiles are in complain mode.
8 processes have profiles defined.
8 processes are in enforce mode.
   /sbin/dhclient (1704) 
   /usr/sbin/cups-browsed (1172) 
   /usr/sbin/cupsd (1054) 
   /usr/sbin/cupsd (1178) 
   /usr/sbin/cupsd (1179) 
   /usr/sbin/cupsd (1180) 
   /usr/sbin/cupsd (1181) 
   /usr/sbin/cupsd (1182) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---

### Post by &amp;KyT$0P# on 2018-04-09
Please post the output of
```
ls -la /etc/apparmor.d
```

---

### Post by deadflowr on 2018-04-09
Since the profile in the disable folder is a link you need to unlink it.

```
sudo unlink /etc/apparmor.d/disable/usr.bin.firefox
```
beware of possible complications like this:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1627239]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1627239")

and to reverse it
```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
```

Hope it helps

---

### Post by open4epl on 2018-04-09
> **halogen2 said:**
> Please post the output of
```
ls -la /etc/apparmor.d
```


```
total 184
drwxr-xr-x   8 root root  4096 Apr  9 13:21 .
drwxr-xr-x 136 root root 12288 Apr  9 03:15 ..
drwxr-xr-x   4 root root  4096 Apr  8 13:03 abstractions
drwxr-xr-x   2 root root  4096 Apr  9 13:21 cache
drwxr-xr-x   2 root root  4096 Apr  9 00:58 disable
drwxr-xr-x   2 root root  4096 Apr  5  2016 force-complain
-rw-r--r--   1 root root   732 Mar 31  2017 lightdm-guest-session
drwxr-xr-x   2 root root  4096 Apr  8 13:03 local
-rw-r--r--   1 root root  3310 Apr 12  2016 sbin.dhclient
-rw-r--r--   1 root root 26638 Apr  9 13:21 snap.core.4206.usr.lib.snapd.snap-confine
drwxr-xr-x   5 root root  4096 Apr  8 13:03 tunables
-rw-r--r--   1 root root  5995 Nov 30 15:31 usr.bin.evince
-rw-r--r--   1 root root  8467 Feb  8 12:49 usr.bin.firefox
-rw-r--r--   1 root root 38551 Dec 20  2016 usr.bin.webbrowser-app
-rw-r--r--   1 root root 23155 Nov 30 14:48 usr.lib.snapd.snap-confine.real
-rw-r--r--   1 root root   469 Feb 13  2016 usr.sbin.cups-browsed
-rw-r--r--   1 root root  5119 Feb 19 12:51 usr.sbin.cupsd
-rw-r--r--   1 root root   546 Sep 18  2015 usr.sbin.ippusbxd
-rw-r--r--   1 root root  1527 Jan  5  2016 usr.sbin.rsyslogd
-rw-r--r--   1 root root  1469 Sep  8  2017 usr.sbin.tcpdump
```

> **deadflowr said:**
> Since the profile in the disable folder is a link you need to unlink it.

```
sudo unlink /etc/apparmor.d/disable/usr.bin.firefox
```
beware of possible complications like this:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1627239](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1627239)

and to reverse it
```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
```

Hope it helps


Here's the results:

```
eddie@eddie-HP-Notebook:~$ sudo unlink /etc/apparmor.d/disable/usr.bin.firefox
[sudo] password for eddie: 
unlink: cannot unlink '/etc/apparmor.d/disable/usr.bin.firefox': No such file or directory
eddie@eddie-HP-Notebook:~$ sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
eddie@eddie-HP-Notebook:~$ sudo unlink /etc/apparmor.d/disable/usr.bin.firefox
eddie@eddie-HP-Notebook:~$ sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
eddie@eddie-HP-Notebook:~$
```

---

### Post by deadflowr on 2018-04-09
fwiw, the bug report I linked provides somewhat of a workaround in [comment #3.]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1627239/comments/3")

Note that the command is supposed to be one line but launchpad wastes space in the comments section so it looks like different lines.
Should be
```
 echo "/dev/shm/org.chromium.* rw," | sudo tee -a /etc/apparmor.d/local/usr.bin.firefox
```
and not how it looks in launchpad
```
 echo "/dev/shm/org.chromium.* rw," | sudo tee -a /etc/apparmor.d/local/
usr.bin.firefox
```
just in case you try it and you realize it went bonkers or failed because you only ran the first part.

---

### Post by open4epl on 2018-04-09
Should I try the above 2 commands you just posted?

---

### Post by deadflowr on 2018-04-09
> **open4epl said:**
> Should I try the above 2 commands you just posted?

Just the first one.
Read my post again.
I tried to explain why I posted them.

Also, I would recommend reading through the bug report I posted, as it might glean you more insight.

---

### Post by open4epl on 2018-04-09
I see. It came out the same way for me. How do I fix it?

---

### Post by deadflowr on 2018-04-09
> **open4epl said:**
> I see. It came out the same way for me. How do I fix it?

You mean when you pasted it into the terminal?

---

### Post by open4epl on 2018-04-09
Yeah, when I pasted it in the terminal, it came out the same way it did for you.

---

### Post by deadflowr on 2018-04-09
> **open4epl said:**
> Yeah, when I pasted it in the terminal, it came out the same way it did for you.

That's fine.
terminal's use a wraparound feature.
So as long as you pasted the first command, then the text will wrap around to the next line, as if it was not broken.

If you tried to run the second command I posted, it would have ended short and asked for a password (sudo) and then told you the password failed, because the second line of that command (usr.bin/firefox) would have become the password field input. And then it would also fail after you entered the correct password since that command is incomplete (since t would be missing that usr.bin.firefox part).

---

### Post by &amp;KyT$0P# on 2018-04-09
@open4epl Have you tried this to enable AppArmor for Firefox? -
```
cd;sudo aa-enforce usr.bin.firefox
```

---

