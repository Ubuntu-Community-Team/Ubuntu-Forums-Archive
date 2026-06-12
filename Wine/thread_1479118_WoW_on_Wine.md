---
title: "WoW on Wine"
date: 2010-05-10
forum: Wine
---

### Post by DJ_Max on 2010-05-10
I've been trying to get WoW to play, I got it fully installed with latest updates, but when ever I try and launch the game, I can't make it past the intro without it crashing.

```
Internal symbol error: unable to access memory location 0x8) [/tmp/wine-1.1.44/dlls/ntdll/loader.c:2612] in ntdll (0x00000000)
```

I tried with Wine installed from the repositories, and I also installed it from the source (1.1.44)

DRI is enabled, using OpenGL for graphics on an Intel card.

---

### Post by hikaricore on 2010-05-10
> **DJ_Max said:**
> using OpenGL for graphics on an Intel card.

You may need to get a real video card to play Wow on your system.
Intel often doesn't cut it on the opengl/linux side of things.

---

### Post by DJ_Max on 2010-05-10
> **hikaricore said:**
> You may need to get a real video card to play Wow on your system.
Intel often doesn't cut it on the opengl/linux side of things.
How could that be related to my GPU?

---

### Post by hikaricore on 2010-05-11
Wow/Intel is usually video related, it's a safe bet to start there in most cases.
Didn't really read your error however.  I suggest purging wine and reinstalling the latest ppa version.
If you installed from source you'll need to to a make uninstall, installing wine over another copy of wine with source/packages is a surefire way to fack things up.

After you reinstall wine launch wow directly without using the launcher and post the full error report here, not just one line from the end.

---

### Post by DJ_Max on 2010-05-12
I didn't install over anything.... I have the latest version and I didn't use the launcher

Here's the crash report
[http://docs.google.com/Doc?docid=0AcmeL4YJ2Jg7YWpjcmR2ZzdwbTcyXzUyZjVycWQ4YzI&hl=en](http://docs.google.com/Doc?docid=0AcmeL4YJ2Jg7YWpjcmR2ZzdwbTcyXzUyZjVycWQ4YzI&hl=en)

---

### Post by hikaricore on 2010-05-12
That doesn't really help.
I meant the terminal output.

---

### Post by DJ_Max on 2010-05-12
> **hikaricore said:**
> That doesn't really help.
I meant the terminal output.
My bad I thought that was in the report. Look at it again i updated it

---

### Post by hikaricore on 2010-05-12
I really can't think of anything that would cause that at all.
Wow is probably giving you a 132 error (general memory/video crash) and wine is spewing garbage.
Either this is video/driver/ram related or something in your wine install is facked up six ways from sunday.
As I asked before, you said you installed it from source at one point as well as repos..
Did you run a make uninstall before installing deb packages?  Or vice versa did you uninstall the packages before running make install?
There's really no other explaination for this.

---

### Post by DJ_Max on 2010-05-13
> **hikaricore said:**
> I really can't think of anything that would cause that at all.
Wow is probably giving you a 132 error (general memory/video crash) and wine is spewing garbage.
Either this is video/driver/ram related or something in your wine install is facked up six ways from sunday.
As I asked before, you said you installed it from source at one point as well as repos..
Did you run a make uninstall before installing deb packages?  Or vice versa did you uninstall the packages before running make install?
There's really no other explaination for this.
Installed from deb repo,
uninstalled

installed source

I also have opensuse dual booting on this laptop and I couldn't get wow and wine to work either.

---

### Post by pedro_orange on 2010-05-14
I think you'll find its graphics related.
I can get it working with an nVidia graphics card, but never an Intel.
Perhaps it's driver related.

---

