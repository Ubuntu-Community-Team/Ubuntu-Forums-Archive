---
title: "Anything I'm doing wrong?"
date: 2009-10-05
forum: Wine
---

### Post by MetroidJunkie2008 on 2009-10-05
I read, to run Fallout 3, I need to patch wine so I placed the patch file in /home/metroidjunkie/wine-1.0.1 and did sudo patch -p1 < patch-benv.diff

It gave me:

```
patching file dlls/wined3d/directx.c
Hunk #1 succeeded at 3915 with fuzz 2 (offset -452 lines).
Hunk #2 FAILED at 4112.
1 out of 2 hunks FAILED -- saving rejects to file dlls/wined3d/directx.c.rej
patching file dlls/wined3d/wined3d_main.c
Hunk #1 succeeded at 57 with fuzz 2 (offset -247 lines).
patching file dlls/wined3d/wined3d_private.h
Hunk #1 succeeded at 248 (offset -41 lines).

```

Of course, Fallout 3 still crashes when trying to start a new game. Did I patch it wrong? Wine version 1.1.30, version Windows Vista. I can't test terminal output for Fallout 3 because there are spaces in the file location, which confuses the terminal. Ubuntu is 9.04 if that matters.

---

### Post by asdfoo on 2009-10-06
> **MetroidJunkie2008 said:**
> I read, to run Fallout 3, I need to patch wine so I placed the patch file in /home/metroidjunkie/wine-1.0.1 and did sudo patch -p1 < patch-benv.diff

It gave me:

```
patching file dlls/wined3d/directx.c
Hunk #1 succeeded at 3915 with fuzz 2 (offset -452 lines).
Hunk #2 FAILED at 4112.
1 out of 2 hunks FAILED -- saving rejects to file dlls/wined3d/directx.c.rej
patching file dlls/wined3d/wined3d_main.c
Hunk #1 succeeded at 57 with fuzz 2 (offset -247 lines).
patching file dlls/wined3d/wined3d_private.h
Hunk #1 succeeded at 248 (offset -41 lines).

```

Of course, Fallout 3 still crashes when trying to start a new game. Did I patch it wrong? Wine version 1.0.1, version Windows Vista. I can't test terminal output for Fallout 3 because there are spaces in the file location, which confuses the terminal. Ubuntu is 9.04 if that matters.


1.0.1 is about a year old, the patch is meant for a newer version of Wine.  eg. 1.1.30 is the newest.

---

### Post by MetroidJunkie2008 on 2009-10-07
> **asdfoo said:**
> 1.0.1 is about a year old, the patch is meant for a newer version of Wine.  eg. 1.1.30 is the newest.

Must've read it wrong or something. In Synaptic Package Manager, it says 1.1.30

---

### Post by hikaricore on 2009-10-07
You realize that you can't install WINE through synaptic and patch right?

You're going to have to uninstall WINE from a package manager, patch the correct version of the source, and compile the entire thing.

---

### Post by MetroidJunkie2008 on 2009-10-07
I patched a newer Wine source but the installation's giving me problems now. ```
FreeType development files not found. Fonts will not be built.
Use the --without-freetype option if you really want this.
``` Adding that doesn't help.

---

### Post by hikaricore on 2009-10-07
> **MetroidJunkie2008 said:**
> I patched a newer Wine source but the installation's giving me problems now. ```
FreeType development files not found. Fonts will not be built.
Use the --without-freetype option if you really want this.
``` Adding that doesn't help.

```
sudo apt-get build-dep wine
```

You won't be able to compile wine without it's dependencies.

---

### Post by MetroidJunkie2008 on 2009-10-07
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I had Wine beforehand, I uninstalled it as instructed and now I'm trying to install the patched source.

---

### Post by hikaricore on 2009-10-08
Right and to compile it you need to install a lot of required packages.

> sudo apt-get build-dep wine

Should install everything you need, if it doesn't I don't know what to tell you.

---

### Post by MetroidJunkie2008 on 2009-10-08
> **hikaricore said:**
> Right and to compile it you need to install a lot of required packages.



Should install everything you need, if it doesn't I don't know what to tell you.

Check the output I pasted in my response, there isn't anything it will install, the installation claims it needs some kind of FreeType but trying to sudo apt-get install that returns no package found.

---

### Post by hikaricore on 2009-10-08
I'd imagine it needs libfreetype6-dev.
Make sure you have the src repos in your sources.list?

You should probably read up on adding/enabling the various sources in the repos: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by MetroidJunkie2008 on 2009-10-08
Okay, second time trying to install it, it didn't give me the error, so I assume it finally realized FreeType is already installed. Fallout 3 now works with the patch, too bad it's lagging so much. :P

---

