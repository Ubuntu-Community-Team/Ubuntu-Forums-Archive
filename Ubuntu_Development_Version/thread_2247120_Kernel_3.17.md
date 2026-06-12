---
title: "Kernel 3.17"
date: 2014-10-05
forum: Ubuntu Development Version
---

### Post by Doug S on 2014-10-05
[Kernel 3.17 is released.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-utopic/")

---

### Post by sammiev on 2014-10-05
Thanks Doug,

Been using it for a few hours now and so far no issues.

Edit: Seems to freeze on boot every 2nd boot.

---

### Post by jerrylamos on 2014-10-06
crash.  Created launchpad bug 1378035

DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
Linux Aspire1 3.17.0-031700-generic #201410051635 SMP Sun Oct 5 20:36:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

utopic was updated to 3.16.0-20 then installed kernel 3.17

Acer Aspire 1 with external monitor at 1360x768 built in 1024x600 monitor off.

crash occurred on boot-up of kernel 3.17,
Desktop displayed but unresponsive, couldn't wake hidden launcher.
After few tens of seconds screen flashed to wallpaper, flashed again to desktop.
Seems to be recovered O.K.

---

### Post by jerrylamos on 2014-10-06
Kernel 17 with google-chrome external monitor "video" on full screen stops.  On part screen, more like a jerky slideshow.  Do note full screen video on this netbook is more like a slide show with either google-chrome or chromium.  It's like using a software driver such as vesa.

Firefox does do full screen video fairly usable, a little jerky, with no measurements I'd say Kernel 17 might be a little better than 3.16.0-20.

---

### Post by a_user2 on 2014-10-08
with kernel 3.17.0 my iMon IR remote isn't working anymore. no errors in syslog. actually according to log messages the device has been successfully detected and initialized. i see the very same messages as on 3.16.x kernels (mainline or ubuntu official) but on 3.17.0 neither irw not irrecord or what ever shows reactions.

strange is that the ir reciever is part of an chieftec case wich also has knobs on the front. the knobs are working fine.

---

### Post by jerrylamos on 2014-10-09
3.17 booted a few times yesterday Oct 8 O.K. except for compiz crashes previously filed with launchpad.
Hung early in boot today.
3.16.0-21 booted O.K., do note when the launcher is partway up, showing just the right side of the icons, hesitates for some seconds before finishing boot.  Nothing new in /var/crash.
Usual complaints in .cache/upstart/unity7.log see following
```

[5660:5660:1009/133755:ERROR:webgraphicscontext3d_command_buffer_impl.cc(243)] Failed to initialize command buffer.
[11:24:1009/133755:ERROR:command_buffer_proxy_impl.cc(153)] Could not send GpuCommandBufferMsg_Initialize.
[11:24:1009/133755:ERROR:webgraphicscontext3d_command_buffer_impl.cc(223)] CommandBufferProxy::Initialize failed.
[11:24:1009/133755:ERROR:webgraphicscontext3d_command_buffer_impl.cc(243)] Failed to initialize command buffer.
[5660:5721:1009/133803:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
compiz (core) - Warn: unhandled ConfigureNotify on 0x40c4cc!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Previous 2 lines repeated five more times.
[5660:5702:1009/135959:ERROR:channel.cc(316)] RawChannel read error (connection broken)
```
Removed 3.17 will try again later.

---

### Post by zika on 2014-10-09
> **jerrylamos said:**
> .cache/**upstart**/unity7.logUtopic?

---

### Post by jerrylamos on 2014-10-09
> **zika said:**
> Utopic?
14.10 Unity Unicorn whatever the right code name is, the one with compiz.

I'm usually running a development level, usually unity though I'm no fan.  Find more bugs with that combo, particularly compiz.

I do try 14.10 lubuntu, mate, debian, this is ubuntu 14.10 gnome 3.12.  I even tried ubuntu next which wanted to turn this desktop wide screen into a "smart" phone with a narrow display up the left side.  I'll try again sometime.  next even asked me to swipe from the right side of the screen.  mouse swipes didn't work.

Will try 3.17 on ubuntu gnome 3.12 14.10 latest beta next.

---

### Post by jerrylamos on 2014-10-09
3.17 onto ubuntu gnome 3.16.0-21 did not boot.
3.17 started then hung.  No kernel panic, just a few of the usual text lines then just sat there doing nothing.
Same thing I get on 3.16.0-21 unity plus 3.17, hangs in boot.  Can't do Ctrl-Alt-F1 or F2, nobody home.

Try again in a few days.

---

