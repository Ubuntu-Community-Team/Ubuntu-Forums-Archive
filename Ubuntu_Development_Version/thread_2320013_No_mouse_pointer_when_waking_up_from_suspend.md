---
title: "No mouse pointer when waking up from suspend"
date: 2016-04-09
forum: Ubuntu Development Version
---

### Post by sammiev on 2016-04-09
Hi,

Testing Xubuntu 16.04 and noticed today when waking up from suspend that the mouse pointer is invisible.

Can someone else try this please?

It has been about a week since I used suspend, so not sure when this problem started.

Thanks

---

### Post by zika on 2016-04-09
Unclutter active?

---

### Post by sammiev on 2016-04-09
Hi zika,

Empty or full desktop still all the same.

Can get the pointer back with Ctrl + Alt + F1 then Crtl + Alt F7.

I need to look this over a little more. :)

---

### Post by sammiev on 2016-04-09
It seems locking the display on suspend has been a problem for more than two years with Xubuntu.

Unlocking the display on suspend seems to have corrected the problem.

I'm rather new to Xubuntu as my main OS.

---

### Post by PhilGil on 2016-04-16
This is not actually fixed, is it? I have the same problem, which began after an update a couple of weeks ago. It's fine if I log out before I suspend the laptop, but if I suspend while still logged in the mouse cursor will be missing when I resume.

---

### Post by sammiev on 2016-04-17
It's not fixed yet and your correct about it starting after an update some weeks back.

There is just a work around at this time.

---

### Post by PaulW2U on 2016-04-19
> **sammiev said:**
> It's not fixed yet and your correct about it starting after an update some weeks back.
Hi sammiev, yes this is bug [#1568604]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604") which looks like will not be fixed before the final release on Thursday. According to the bug report the bug has been fixed in Debian so hopefully the fix will find its way into Ubuntu soon.

Expect lots of questions in the coming days from those that upgrade to Xenial but don't read the release notes. :(

---

### Post by sammiev on 2016-04-19
> **PaulW2U said:**
> Hi sammiev, yes this is bug [#1568604]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604") which looks like will not be fixed before the final release on Thursday. According to the bug report the bug has been fixed in Debian so hopefully the fix will find its way into Ubuntu soon.

Expect lots of questions in the coming days from those that upgrade to Xenial but don't read the release notes. :(

+1 and Thursday should be fun. :)

---

### Post by vhaarr+launchpad on 2016-04-20
I've been having a similar - but not actually related - issue on a Fujitsu Lifebook laptop. I don't have the laptop here, and I can't remember the exact model.

The solution provided on several threads and blogs is to add these to */etc/default/grub*:
```
i8042.nomux=1 i8042.noloop=1
```
Or similar. But it didn't solve the issue on this laptop.

I fixed it by adding a script to */lib/systemd/system-sleep/* like so:
```
#!/bin/bash
[ "$1" = "post" ] && modprobe psmouse
[ "$1" = "pre" ] && modprobe -r psmouse
exit 0
```
Or, alternatively,
```
#!/bin/bash
if [ "$1" = "post" ]; then
    modprobe -r psmouse
    modprobe psmouse
fi;
exit 0
```

And then chmod +x the script.

I don't remember which of the scripts worked, but one of them did, at least.

I am just adding this information here for future Googlers.

---

### Post by sudodus on 2016-04-20
I found a bug today, that affects systems made from Lubuntu Xenial Alternate, but not systems made from Lubuntu Xenial Desktop.

Maybe it is a duplicate of 'your' bug, maybe not. See this link [cursor invisible after timeout and screen-saving](http://ubuntuforums.org/showthread.php?t=2321069)

---

