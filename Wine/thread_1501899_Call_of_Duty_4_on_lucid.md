---
title: "Call of Duty 4 on lucid?"
date: 2010-06-04
forum: Wine
---

### Post by Frozzer on 2010-06-04
Hey guys, this is the first time I ask for help here because usually it's already been solved, but I haven't found anything to this problem.

I'm trying to install CoD4 in my Lucid Linx, it installs just fine, but I can't launch the game.

First I tried with Playonlinux and it gives me this error when I want to launch the game:

```
err:module:import_dll Loading library binkw32.dll (which is needed by L"Z:\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") failed (error c0000020).
err:module:import_dll Loading library mss32.dll (which is needed by L"Z:\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") failed (error c0000020).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe" failed, status c0000135

```I guess it can't find the dll files, but they're on the game folder, I did also copy them to .wine/drive_c/windows/system32 and nothing.

Then I tried to install using [this guide]("http://www.fsckin.com/2008/02/21/how-to-run-call-of-duty-4-cod4-modern-combat-in-linux/"), same problem.

Also tried with cedega 6.0 and 7 (the last one, don't know which is it) but it just wouldn't launch any installer.

Anyone knows how to fix this?

---

### Post by asdfoo on 2010-06-05
a) install the game in its default location
b) cd to the install directory then launch the main executale

---

### Post by Frozzer on 2010-06-05
Well, that didn't work, same error

```
err:module:import_dll Loading library binkw32.dll (which is needed by L"C:\\Archivos de programa\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") failed (error c0000020).
err:module:import_dll Loading library mss32.dll (which is needed by L"C:\\Archivos de programa\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe") failed (error c0000020).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Activision\\Call of Duty 4 - Modern Warfare\\iw3sp.exe" failed, status c0000135
```The files are already there, any other ideas?

---

