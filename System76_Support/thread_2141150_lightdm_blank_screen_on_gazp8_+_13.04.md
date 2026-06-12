---
title: "lightdm blank screen on gazp8 + 13.04"
date: 2013-05-01
forum: System76 Support
---

### Post by M4rduk on 2013-05-01
Has anyone else seen the following issue?

Clean install of Ubuntu 13.04 64-bit on a gazp8, with System76 driver version 3.2.7 installed immediately after the first reboot.
 
Periodically, on first boot, lightdm will display a black screen and only the mouse cursor is visible. The cursor can be moved, and lightdm is fully fonctional. If I type in my password and hit Enter, I will be logged in. If I hit down and press enter, I will be logged in with the Guest account. I can work my way around this easily enough, but it confuses my kids.

Once a first login has been successful, the problem does not seem to appear again. This happens once every 10 bootups, I would say.

Looking around the log files in /var/log/lightdm, I do not see anything that stands out error-wise. I have reinstalled 3 times so far from clean media with correct checksums. The only thing I constantly do is install the System76 driver. I follow the documentation and select "Restore System", but not "Install Drivers".

Running 'service lightdm restart' fixes the issue.

I will keep a close eye on the timestamps in /var/log/lightdm the next time this occurs. I was just curious to know if any other system76 users are seeing this behaviour, with a gazp8 or other model.

Thanks!

---

### Post by M4rduk on 2013-05-02
Happened again today, immediately after doing a Software Update that pulled down the following packages :

Start-Date: 2013-05-02  18:52:44
Commandline: aptdaemon role='role-commit-packages' sender=':1.183'
Upgrade: linux-image-extra-3.8.0-19-generic:amd64 (3.8.0-19.29, 3.8.0-19.30), linux-headers-3.8.0-19:amd64 (3.8.0-19.29, 3.8.0-19.30), linux-image-3.8.0-19-generic:amd64 (3.8.0-19.29, 3.8.0-19.30), linux-headers-3.8.0-19-generic:amd64 (3.8.0-19.29, 3.8.0-19.30), linux-libc-dev:amd64 (3.8.0-19.29, 3.8.0-19.30)
End-Date: 2013-05-02  18:53:19

Nothing abnormal in /var/log/lightdm/lightdm.log, x-0-greeter.log or x-0.log.

I also changed my wallpaper right after the update, before rebooting. Since lightdm will display your wallpaper when you select your username, I'm wondering if the issue can be related to a wallpaper change. Will investigate further.

---

### Post by Carborundum on 2013-05-03
I haven't seen this on my gazp7, but I've probably rebooted it fewer than ten times since installing 13.04 so I may have been lucky so far. I am using a custom wallpaper. I will report back if this starts happening.

---

### Post by M4rduk on 2013-05-03
> **Carborundum said:**
> I haven't seen this on my gazp7, but I've probably rebooted it fewer than ten times since installing 13.04 so I may have been lucky so far. I am using a custom wallpaper. I will report back if this starts happening.

Thanks!

---

### Post by M4rduk on 2013-05-05
Happened again this morning, no system updates or wallpaper changes had been executed prior to shutdown yesterday. So the issue is definitely not related to these two actions.

No problems detected in /var/log/lightdm/*.

---

### Post by M4rduk on 2013-05-05
Just found this, which seems to be the same issue, although I definitely get a mouse cursor and can login if I just type my password.

[http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html](http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489)

I will try adding a short sleep statement as described in the article and report back here in a few days.

---

### Post by shaun.husain on 2013-05-06
Hi M4rduk,

You're not alone, and I appreciate you're figuring this out ahead of me.  I ran into the same problem after upgrading to 13.04 from 12.10 on a gazp8.  Tried the switch to gdm but without success (it changed over fine but after logging in the login screen wasn't "removed" and I couldn't see my desktop).  Ultimately the **sleep 2** line within my **/etc/init.d/lightdm.conf** just before the **exec lightdm** call is what has fixed it for now.  I'll report back if I get any more issues or info on any better resolution.  I would be interested in understanding how to further debug lightdm as well. I'm a fairly well versed programmer but haven't messed much in the linux source itself.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

it appears there's a --debug argument that can be passed that gives verbose logging, perhaps that will help to narrow down the issue.

-Shaun

---

### Post by M4rduk on 2013-05-07
Hi, so far using a one second delay has solved it for me. I would go against using the debug option, as this will incur frequent writes to hard disk. That means more wear and tear on your hard drive / SSD drive and more battery drainage. From what I've seen, the race condition does not result in any noticeable errors even when running -debug.

If anyone from System76 reads this, can you check into this? The latest driver states "fixed a LightDM race condition", that doesn't seem to work for 13.04.

Thanks!

---

### Post by isantop on 2013-05-07
It looks like we'll need to apply the fix for 13.04 as well. That was for 12.10.

---

### Post by M4rduk on 2013-05-07
> **isantop said:**
> It looks like we'll need to apply the fix for 13.04 as well. That was for 12.10.

Was the fix for 12.10 adding a small sleep delay to lightdm?

---

### Post by isantop on 2013-05-07
Yes.

---

