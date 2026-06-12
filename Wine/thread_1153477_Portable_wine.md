---
title: "Portable wine"
date: 2009-05-08
forum: Wine
---

### Post by Nathan_M on 2009-05-08
Hi,
I have a USB stick, and I want a portable version of wine to run on it, so that I can run a few Windows apps on a couple of different computers. I've downloaded the wine source, done make configure and make, and now I have a wine executable, which can run basic programs. I notice none of the other wine related commands are available, such as winecfg. What can I do to get this working as a fully-working version of wine? Also, what files is it safe for me to delete now that I have wine working (to save space on the USB stick)? Presumably, all *.c and *.h files, but what else?

---

### Post by asdfoo on 2009-05-08
> **Nathan_M said:**
> Hi,
I have a USB stick, and I want a portable version of wine to run on it, so that I can run a few Windows apps on a couple of different computers. I've downloaded the wine source, done make configure and make, and now I have a wine executable, which can run basic programs. I notice none of the other wine related commands are available, such as winecfg. What can I do to get this working as a fully-working version of wine? Also, what files is it safe for me to delete now that I have wine working (to save space on the USB stick)? Presumably, all *.c and *.h files, but what else?

This is a fully working version of Wine, it runs from the build directory.  You will however need to specify where your Wine prefix will be when you run programs, by setting the environment variable WINEPREFIX, it defaults to ~/.wine

You can delete all *.rc files and Makefiles too.

---

### Post by Nathan_M on 2009-05-08
> **asdfoo said:**
> This is a fully working version of Wine, it runs from the build directory.  You will however need to specify where your Wine prefix will be when you run programs, by setting the environment variable WINEPREFIX, it defaults to ~/.wine

You can delete all *.rc files and Makefiles too.

Thanks. I'm gonna set up a few little bash scripts to handle the WINEPREFIX stuff, and things like that. There are quite a few housekeeping tasks that I've worked out. But having a winecfg command would make things much easier... I just can't work out why it isn't there.

---

### Post by Nathan_M on 2009-05-08
> **Nathan_M said:**
> Thanks. I'm gonna set up a few little bash scripts to handle the WINEPREFIX stuff, and things like that. There are quite a few housekeeping tasks that I've worked out. But having a winecfg command would make things much easier... I just can't work out why it isn't there.

I've found it.

$ ./wine-1.1.20/wine ./wine-1.1.20/programs/winecfg/winecfg.exe.so

---

### Post by asdfoo on 2009-05-08
> **Nathan_M said:**
> I've found it.

$ ./wine-1.1.20/wine ./wine-1.1.20/programs/winecfg/winecfg.exe.so

just do ./wine-1.1.20/wine winecfg

---

