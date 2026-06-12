---
title: "Gutsy Upgrade (Daru1): What Still Doesn't work"
date: 2007-10-26
forum: System76 Support
---

### Post by MarkID on 2007-10-26
I upgraded to Gutsy one week ago, and still have some issues.

First and major is WiFi.  On startup my WiFi is automatically detected and logged into without using a passphrase or keyring.  This worries me form a security point of view.  I am given no opportunity to chooose a different network to log into.   Also, when I come out of suspend and hibernate the WiFi is completely hosed.  Nothing is detected and there is no way to connect.  I have to do a complete restart to connect.

When I first upgraded, the Darter would just hang on start.  It only works by choosing a different kernel (2.6.20-16 rather than 2.6.22-14).  What am I losing by not using the most up to date kernel?

I need a fix for these problems.  Thanks.

---

### Post by thomasaaron on 2007-10-26
**To fix the hang:**

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u
sudo reboot

**Regarding the keyring:** 
I believe you can set one up by going into:
System > Administration > Keyring Manager

**Regarding the wireless problem after resuming:**
Run your System 76 Driver
That should fix it.

---

### Post by perce on 2007-10-26
> **thomasaaron said:**
> 

**Regarding the wireless problem after resuming:**
Run your System 76 Driver
That should fix it.

Not completely: I made a clean install and quite often NetworkManager hangs at resume, I have to kill and restart it.

---

### Post by MarkID on 2007-10-26
> **perce said:**
> Not completely: I made a clean install and quite often NetworkManager hangs at resume, I have to kill and restart it.

Yep, same here.  Running the latest driver, 2.1.1, and I still lose wirelss on resume.  I must do complete restart to get it back (which kind of defeats the purpose of suspend/hibernate).

---

### Post by thomasaaron on 2007-10-26
There was a bug report / fix on that one under Feisty.
1. Did you run the "Restore" function on the System 76 driver, or only the Install function?

2. If you ran the restore function and it still hangs, file a bug report here:
[https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by perce on 2007-10-26
> 
2. If you ran the restore function and it still hangs, file a bug report here:
[https://launchpad.net/system76](https://launchpad.net/system76)

I ran restore after installing, so I filed the bug report. I also ran restore again in case something had gone wrong the first time.

---

### Post by MarkID on 2007-10-26
> **thomasaaron said:**
> There was a bug report / fix on that one under Feisty.
1. Did you run the "Restore" function on the System 76 driver, or only the Install function?

2. If you ran the restore function and it still hangs, file a bug report here:
[https://launchpad.net/system76](https://launchpad.net/system76)

Ran Restore.  Still NM/Wifi problems.  Bug filed.

---

### Post by perce on 2007-10-28
I've probably found a fix: tested a couple of times and it worked:

[https://bugs.launchpad.net/system76/+bug/157550/comments/2](https://bugs.launchpad.net/system76/+bug/157550/comments/2)

This was taken from somewhere in the forum, and I sort of remember we already did that just after I bought the laptop in May,

---

### Post by MarkID on 2007-10-28
> **perce said:**
> I've probably found a fix: tested a couple of times and it worked:

[https://bugs.launchpad.net/system76/+bug/157550/comments/2](https://bugs.launchpad.net/system76/+bug/157550/comments/2)

This was taken from somewhere in the forum, and I sort of remember we already did that just after I bought the laptop in May,

Thanks.  I'm an "intermediate" Linux user.  Can someone post an easy to follow "operation" to follow to implement this fix.  Thanks.

---

### Post by AusIV4 on 2007-10-28
> **MarkID said:**
> Thanks.  I'm an "intermediate" Linux user.  Can someone post an easy to follow "operation" to follow to implement this fix.  Thanks.

```
$ sudo pico /etc/acpi/suspend.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```
ctrl+x, y to save

```
$ sudo pico /etc/acpi/resume.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```
ctrl+x, y to save

Now, those are the instructions according to the bug report, however I believe the last step should read 


```
$ sudo pico /etc/acpi/resume.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start
```
ctrl+x, y to save

Because suspend.d should stop the process, and resume.d should start it again, and the original instructions have it stopping twice (and never starting).

Try it both ways, one of them should work.

---

### Post by perce on 2007-10-28
> **AusIV4 said:**
>  

Now, those are the instructions according to the bug report, however I believe the last step should read 



You're right, in the bug report I made a mistake with cut and paste.

---

### Post by MarkID on 2007-10-30
> **AusIV4 said:**
> ```
$ sudo pico /etc/acpi/suspend.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```
ctrl+x, y to save

```
$ sudo pico /etc/acpi/resume.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```
ctrl+x, y to save

Now, those are the instructions according to the bug report, however I believe the last step should read 


```
$ sudo pico /etc/acpi/resume.d/99-networkmanager
```
Paste:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start
```
ctrl+x, y to save

Because suspend.d should stop the process, and resume.d should start it again, and the original instructions have it stopping twice (and never starting).

Try it both ways, one of them should work.

OK.  I tried this (in the correct form) but all it seems to do is to keep the NM icon open after resume, but there's still no connection and still no way to get a connection.  This is sorely distressing.

---

