---
title: "installing FST in Ubuntu Studio"
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by dead_devil_66 on 2009-08-28
Hi to you all!

I installed FST in ubuntu but i got these warning messages after typing "make" in the console:

```

cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
audiomaster.c: In function ‘jack_host_callback’:
audiomaster.c:119: warning: incompatible implicit declaration of built-in function ‘floor’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fst.o fst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fstinfofile.o fstinfofile.c
fstinfofile.c: In function ‘load_fst_info_file’:
fstinfofile.c:36: warning: incompatible implicit declaration of built-in function ‘malloc’
fstinfofile.c:47: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:76: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_info_file_is_valid’:
fstinfofile.c:139: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_info_from_plugin’:
fstinfofile.c:162: warning: incompatible implicit declaration of built-in function ‘malloc’
fstinfofile.c: In function ‘fst_get_info’:
fstinfofile.c:220: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:246: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_free_info’:
fstinfofile.c:258: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:261: warning: incompatible implicit declaration of built-in function ‘free’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o gtk.o gtk.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o jfst.o jfst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vsti.o vsti.c
vsti.c: In function ‘queue_midi’:
vsti.c:79: warning: assignment from incompatible pointer type
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vstwin.o vstwin.c
vstwin.c: In function ‘fst_load’:
vstwin.c:480: warning: assignment from incompatible pointer type
winegcc -mwindows -o fst.exe audiomaster.o fst.o fstinfofile.o gtk.o jfst.o vsti.o vstwin.o     `pkg-config --libs gtk+-2.0` `pkg-config --libs jack` `pkg-config --libs alsa` `pkg-config --libs lash-1.0`  -L/usr/X11R6/lib -lX11   -luuid

```will i have any problem running FST?

Thanks in advance!

---

### Post by Stochastic on 2009-08-28
Those look to be simply warnings from GCC.  In recent versions GCC has become pickier about code.  In most instances you can safely ignore warning lines.  IF however, it stops right after those warnings or you see an ERROR printed out, then things went wrong.

It's good to let the authors of that software know that those warnings are visible upon compile.  They may have advice on how to fix them, or they may need to fix something in their software.  In this case, it's most likely the latter.

---

### Post by dead_devil_66 on 2009-08-28
> **Stochastic said:**
> Those look to be simply warnings from GCC.  In recent versions GCC has become pickier about code.  In most instances you can safely ignore warning lines.  IF however, it stops right after those warnings or you see an ERROR printed out, then things went wrong.

It's good to let the authors of that software know that those warnings are visible upon compile.  They may have advice on how to fix them, or they may need to fix something in their software.  In this case, it's most likely the latter.

well, in that case, i will email them with the compiler output messages.

oh! and btw, i tried to start up 4front bass plugin through FST but it didnt started. Strange thing indeed because that company makes software instruments to linux....

---

### Post by sgx on 2009-08-28
> **dead_devil_66 said:**
> well, in that case, i will email them with the compiler output messages.

oh! and btw, i tried to start up 4front bass plugin through FST but it didnt started. Strange thing indeed because that company makes software instruments to linux....
Did you start with the command

fst /home/you/plugin.dll

?  If so, check the output from the terminal window. It may mention a .dll from windowsxxx it could not find, that you need to put in your 

/home/you/.wine/drive_c/windows/system32 folder, which of course hints
that wine and wineasio should be installed to use fst. Some plugins require being in

/home/you/.wine/drive_c/Program Files/Steinberg/VstPlugIns 

Commands including phrases like 'Program Files' need to have an  *  as a space filler,

Program*Files

Hope this helps someone out there

---

