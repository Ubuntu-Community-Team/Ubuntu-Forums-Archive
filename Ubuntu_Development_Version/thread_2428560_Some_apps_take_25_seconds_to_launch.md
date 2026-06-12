---
title: "Some apps take 25 seconds to launch"
date: 2019-10-05
forum: Ubuntu Development Version
---

### Post by makitso on 2019-10-05
Installed filezilla via apt on 19.10.  However, when you launch the app it takes 25 seconds before it becomes available.  I see this on one other app -- gftp, both are timing out.  FWIW, app works correctly if installed via SNAP.

[FONT=Helvetica]09:07:51 write(12, “\1\0\0\0\0\0\0\0”, 8) = 8[/FONT]
[FONT=Helvetica]09:07:51 write(13, “\1\0\0\0\0\0\0\0”, 8) = 8[/FONT]
[FONT=Helvetica]09:07:51 poll([{fd=12, events=POLLIN}], 1, 25000) = 1 ([{fd=12, revents=POLLIN}])[/FONT]
[FONT=Helvetica]09:07:51 read(12, “\1\0\0\0\0\0\0\0”, 16) = 8[/FONT]
**[FONT=Helvetica]09:07:51 poll([{fd=12, events=POLLIN}], 1, 25000) = 0 (Timeout)[/FONT]**
[FONT=Helvetica]09:08:16 write(12, “\1\0\0\0\0\0\0\0”, 8) = 8[/FONT]
[FONT=Helvetica]09:08:16 futex(0x55cff178e3d0, FUTEX_WAKE_PRIVATE, 2147483647) = 0[/FONT]
[FONT=Helvetica]09:08:16 close(12) = 0[/FONT]
[FONT=Helvetica]09:08:16 write(13, “\1\0\0\0\0\0\0\0”, 8) = 8[/FONT]
[FONT=Helvetica]09:08:16 futex(0x7ff9b1658f58, FUTEX_WAKE_PRIVATE, 2147483647) = 0[/FONT]
[FONT=Helvetica]09:08:16 futex(0x7ff9b1658f58, FUTEX_WAKE_PRIVATE, 2147483647) = 0[/FONT]
[FONT=Helvetica]09:08:16 statfs("/home/rob", {f_type=EXT2_SUPER_MAGIC, f_bsize=4096, f_blocks=2563397, f_bfree=1131896, f_bavail=996754, f_files=655360, f_ffree=443159, f_fsid={val=[1484858622, 1130548194]}, f_namelen=255, f_frsize=4096, f_flags=ST_VALID|ST_RELATIME}) = 0[/FONT]
[FONT=Helvetica]09:08:16 futex(0x7ff9b1658f58, FUTEX_WAKE_PRIVATE, 2147483647) = 0[/FONT]
[FONT=Helvetica]09:08:16 futex(0x7ff9b1658f58, FUTEX_WAKE_PRIVATE, 2147483647) = 0[/FONT]
[FONT=Helvetica]09:08:16 inotify_init1(IN_CLOEXEC) = 12[/FONT]
[FONT=Helvetica]09:08:16 fcntl(12, F_GETFL) = 0 (flags O_RDONLY)[/FONT]

---

### Post by rbmorse on 2019-10-05
I had the same problem with a couple of apps I use.  The issue turned out to be a support library they wanted was missing.  Installing it  from repository fixed things right up. 

Open a terminal and try launching the problem application from there.  The error messages may help you identify the problem.  In my case it was appmenu-gtk2-module, but your applications may be looking for something else.

---

### Post by makitso on 2019-10-05
Your suggestion fixed the issue with Ubuntu but it still exists in Ubuntu budgie.

---

### Post by rbmorse on 2019-10-05
Is there any error message when you try to launch the application from a terminal?

---

### Post by makitso on 2019-10-06
Yes, but I get this but it the app does this on 19.04 as well, and its just a warning

Failed to load module "canberra-gtk-module"

---

### Post by dino99 on 2019-10-06
My system has both installed: libcanberra-gtk-module & libcanberra-gtk3-module
Chromium is the only app  loading/opening slow here.

---

### Post by rbmorse on 2019-10-06
Isn't Chromium a SNAP?   If so, it's going to load slow.  Nature of the beast.  I've learned to accept it.

---

### Post by cruzer001 on 2019-10-06
> **rbmorse said:**
> Isn't Chromium a SNAP?   If so, it's going to load slow.  Nature of the beast.  I've learned to accept it.
Got to watch the software center, lots of snap packages.
No need to accept it.  Chromium is in our repositories as a .deb package, runs just as fast as FF on my box.

---

### Post by PaulW2U on 2019-10-06
> **cruzer001 said:**
> Chromium is in our repositories as a .deb package
Did you realise that you posted in the development forum? For Ubuntu 19.10, and _eventually_ all supported releases, Chromium will be a snap.

Testing for the transitioning from deb to snap started some time ago.

[Call for testing: chromium-browser deb to snap transition ]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/")

---

### Post by rbmorse on 2019-10-06
Yabut,I kinda like the idea of having the browser and the mail clients, in particular, extra-sandboxed.  They're not _that_ slow to load.

---

### Post by cruzer001 on 2019-10-06
> **PaulW2U said:**
> Did you realise that you posted in the development forum?
Oops

---

### Post by corradoventu on 2019-10-08
I have the problem with the application 'virtual moon atlas' [https://www.ap-i.net/mantis/view.php?id=2204](https://www.ap-i.net/mantis/view.php?id=2204) it take about 30 seconds to launch in Ubuntu 19.10 wile start in about 3 seconds in 19.04.
It start in few seconds in 19.10 only if started with 'sudo'

---

### Post by makitso on 2019-10-09
The latest apt update fixed this problem for me.  Just to be sure I spun up a VM and tried and it is fixed.

---

### Post by corradoventu on 2019-10-09
Also for me the problem has been fixed by last update.

---

