---
title: "all shells crash"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-03-30
Updating just gave me a new version of the kernel, and now every shell I try crashes: gnome-shell, compiz, gnome-panel have crashed.  Firefox works, but that's all I have on my desktop now.  Bug reporting seems to be working.

---

### Post by Gregory Lee on 2012-03-31
I'm still down for the count, here.  I see 7 crash files from Mar 30 and 31 in my /var/crash, and there have been other crashes with no crash file, when the desktop was unresponsive after booting up.  I haven't tried all the shells, yet, but Unity 2d and 3d crash, and also Gnome 3 and Gnome Classic.  I sent several bug reports -- the last two were [https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/970194](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/970194) and [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/970232](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/970232).

From the fact that no one else here seems to have this exact problem, I'm guessing that it has to do with fglrx and my GPU, Radeon HP 6550D.  I wonder if the fglrx kernel module needed to be recompiled with the new 3.2.0-21 kernel version -- I didn't notice a new version of the module among my updates.  I guess the module is here:
```
# ls -l /lib/modules/3.2.0-21-generic/updates/dkms/
total 7612
-rw-r--r-- 1 root root 4632848 Mar 30 08:17 fglrx_updates.ko
-rw-r--r-- 1 root root 3154616 Mar 30 08:17 wl.ko

```
Also, I see that the earliest dated file in /var/crash is this,
-rw-r----- 1 greg greg 3902169 Mar 30 08:34 _usr_bin_compiz.1000.crash
which is just 17 minutes after the file date of the fglrx module.

---

### Post by dcstar on 2012-03-31
> **Gregory Lee said:**
> Updating just gave me a new version of the kernel, and now every shell I try crashes: gnome-shell, compiz, gnome-panel have crashed.  Firefox works, but that's all I have on my desktop now.  Bug reporting seems to be working.

I also had multiple issues after updating yesterday, I put in a couple of bug reports thinking it was just individual items but now I suspect that something in that batch of updates is badly borked.

Give it a few days and this sort of thing is usually resolved when someone finally figures out what went wrong.

---

### Post by ventrical on 2012-03-31
Unity Greeter has also crashed. can log in after updating omnibus and 3.2.0-21 but no Unity Launcher, menubar .. etc..


[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/970476](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/970476)

---

### Post by Gregory Lee on 2012-04-02
Lots of updates today (Monday, April 2), so ever hopeful, I tried rebooting into Unity 2d, again.  No go.  This time, it was a SIGSEGV from nautilus ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/972046](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/972046)
).

I got email from bug reports I sent Friday and Saturday.  My bugs were marked invalid, because I have the ubuntu3 version of coreutils instead of the ubuntu2 version.  Double-talk.  Why should I bother to send the bug reports, I wonder?

---

### Post by cariboo on 2012-04-03
Your link doesn't work, do you have the bug marked as private?

---

### Post by Gregory Lee on 2012-04-03
Yes, sorry, I forget to change it to non-private.  Now, I've done that.

---

### Post by cariboo on 2012-04-03
You are going to need to add more information. I'm about to leave for work, but I'd suggest using gdb to try and add the correct info.

Have a look [here]("https://wiki.ubuntu.com/Backtrace") on how to do it.

---

### Post by dcstar on 2012-04-03
Things are a lot more stable on both my test systems after the updates of the last 24 hours.

---

### Post by Gregory Lee on 2012-04-03
> **dcstar said:**
> Things are a lot more stable on both my test systems after the updates of the last 24 hours.
That's great.  No change here, though, after all updates.  Thanks to cariboo907 for the suggestion to use gdb to hunt bugs myself.

I'm getting consistent crashes every time I try to log in, but the crash is reported differently depending on which shell I attempt:

[LIST]
[*]With Gnome (3) it's "gnome-shell crashed with SIGSEGV in g_object_newv()" ([bug here]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/858109"))
[*]With Unity 3D, it's "compiz crashed with SIGSEGV in g_object_newv()" ([bug here]("https://bugs.launchpad.net/ubuntu/+source/nux/+bug/972659"))
[*]With Unity 2D, it's "unity-2d-shell crashed with SIGSEGV" ([bug here]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/972679"))
[/LIST]
Actually, that last one is not entirely consistent, since last time I tried Unity 2D, it was nautilus that crashed.

---

### Post by nanog on 2012-04-04
This happened to me while traveling. The only way to get a funtional system was to drop to vt and mv failsafe xorg to xorg.conf. all shells and light dm are down on my system. It seems like a drm xorg  problem based on it happennig with any kernel and the errors in dmesg. Mannually starting compiz triggers drm errors.

---

### Post by Gregory Lee on 2012-04-04
Well, that doesn't sound quite the same as my crashes.  After getting a new kernel this morning, 3.2.0-22, I tried again to log in to Unity 3D, but it just crashed again ([https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/970541](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/970541)).

When I started this thread and called it "all shells crash", I hadn't actually tried all the shells -- only Gnome 3, Gnome Classic, Unity 3D, and Unity 2D.  I just got around to trying KDE, and it seems to be okay.  So I guess I'll just use KDE for a while.  I was really getting tired of all the crash, crash, crash.

---

### Post by cariboo on 2012-04-04
This is just a suggestion, but have you removed the ~/.config directory in /home/$USERNAME? Be aware that any customization you have done will be lost.

---

### Post by Gregory Lee on 2012-04-04
> **cariboo907 said:**
> This is just a suggestion, but have you removed the ~/.config directory in /home/$USERNAME? Be aware that any customization you have done will be lost.
No, I haven't done that.  Why should I do that?  Is there some reason to suspect that something there might cause Gnome and Unity shells to crash, but leave KDE unaffected?

---

### Post by cariboo on 2012-04-04
You're running a testing release, there could be some corruption or strange settings in that directory. I haven't run any KDE variant for several years, so I'm not familiar where all the configuration files go in the home directory.

---

### Post by nanog on 2012-04-09
Gnome and kde are completely different. Different de and graphics bindings (esp compiz). my problem seems to have disappeared after upgrade so it could have been a real bug or simply a corrupt deb (happens all the time). moral of the story is reboot before you travel...

---

