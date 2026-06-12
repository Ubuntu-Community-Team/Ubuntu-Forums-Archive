---
title: "Ubuntu, Linux, cygwin, and ssh are awesome"
date: 2009-01-18
forum: Testimonials &amp; Experiences
---

### Post by thanatos6 on 2009-01-18
just wanted to say ubuntu is awesome. i was playing a game on my windows machine during some no-restartable synchronization between a few of my servers. The system locked up, couldn't even open the task manager. I logged in with my laptop running ubuntu 8.10 amd64 via ssh (the windows computer is running cygwin + ssh) i was able to safely kill the game's process remotely, and thus saving me 6 hours of headache.:guitar:

---

### Post by stalkingwolf on 2009-01-18
nice

---

### Post by solwic on 2009-01-18
Very cool.  :)

---

### Post by _me_ubu_ on 2009-01-25
I am compiling Linux source code. I am getting this error. Can anyone help please?

$ make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTLD  scripts/kconfig/mconf
/usr/lib/gcc/i686-pc-cygwin/3.4.4/../../../../i686-pc-cygwin/bin/ld: warning: auto-importing has been activated without --ena
ble-auto-import specified on the command line.
This should work unless it involves constant data structures referencing symbols from auto-imported DLLs.scripts/kconfig/mcon
f.o:mconf.c:(.text+0x2f5): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x9e1): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0xb71): more undefined references to `_libintl_gettext' follow
scripts/kconfig/mconf.o:mconf.c:(.text+0x128f): undefined reference to `_libintl_textdomain'
scripts/kconfig/mconf.o:mconf.c:(.text+0x14b4): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x1507): undefined reference to `_libintl_gettext'
scripts/kconfig/zconf.tab.o:zconf.tab.c:(.text+0x55f8): more undefined references to `_libintl_gettext' follow
Info: resolving _stdscr by linking to __imp__stdscr (auto-import)
Info: resolving _COLS by linking to __imp__COLS (auto-import)
Info: resolving _LINES by linking to __imp__LINES (auto-import)
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/mconf] Error 1
make: *** [menuconfig] Error 2

---

### Post by _me_ubu_ on 2009-01-25
$ make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTLD  scripts/kconfig/mconf
/usr/lib/gcc/i686-pc-cygwin/3.4.4/../../../../i686-pc-cygwin/bin/ld: warning: auto-importing has been activated without --ena
ble-auto-import specified on the command line.
This should work unless it involves constant data structures referencing symbols from auto-imported DLLs.scripts/kconfig/mcon
f.o:mconf.c:(.text+0x2f5): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x9e1): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0xa89): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0xb26): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0xb51): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0xb71): more undefined references to `_libintl_gettext' follow
scripts/kconfig/mconf.o:mconf.c:(.text+0x128f): undefined reference to `_libintl_bindtextdomain'
scripts/kconfig/mconf.o:mconf.c:(.text+0x129b): undefined reference to `_libintl_textdomain'
scripts/kconfig/mconf.o:mconf.c:(.text+0x14b4): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x1507): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x1522): undefined reference to `_libintl_gettext'
scripts/kconfig/mconf.o:mconf.c:(.text+0x154f): undefined reference to `_libintl_gettext'
scripts/kconfig/zconf.tab.o:zconf.tab.c:(.text+0x54f6): undefined reference to `_libintl_gettext'
scripts/kconfig/zconf.tab.o:zconf.tab.c:(.text+0x55f8): more undefined references to `_libintl_gettext' follow
Info: resolving _stdscr by linking to __imp__stdscr (auto-import)
Info: resolving _COLS by linking to __imp__COLS (auto-import)
Info: resolving _LINES by linking to __imp__LINES (auto-import)
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/mconf] Error 1
make: *** [menuconfig] Error 2

---

### Post by solwic on 2009-01-25
> **_me_ubu_ said:**
> $ make menuconfig....

....

 

Wrong thread/section for that, home-skillet.

---

