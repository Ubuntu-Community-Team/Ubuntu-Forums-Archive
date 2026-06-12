---
title: "Wine installation error"
date: 2009-01-13
forum: Wine
---

### Post by ididntdoit52 on 2009-01-13
Alright I'm trying to install Counter Strike: Source but whenever I try I get an "Installation ended prematurely because of an error." error. Anyone know what the problem is and what I can do to fix it? As always thanks in advance for the help.

---

### Post by ididntdoit52 on 2009-01-13
I've tried installing with Wine, PlayOnLinux and even Crossover. None will work... Not sure what I'm doin' wrong.

---

### Post by cogadh on 2009-01-13
Have you installed Steam already?

Also, it might help if you try running the install from the terminal and post any output. Wine produces its own error messages that might explain what is happening.

---

### Post by ididntdoit52 on 2009-01-13
> **cogadh said:**
> Have you installed Steam already?

Also, it might help if you try running the install from the terminal and post any output. Wine produces its own error messages that might explain what is happening.

Steam is already installed its just the game that doesn't want to work. I might need a walk through for installing it from the terminal.  :( I'm still kind of a linux nub.

---

### Post by cogadh on 2009-01-13
Are you trying to install from a disk or through a Steam download?

---

### Post by ididntdoit52 on 2009-01-13
> **cogadh said:**
> Are you trying to install from a disk or through a Steam download?

disk

---

### Post by cogadh on 2009-01-14
In that case is is as simple as opening a terminal and typing:
```
wine /media/cdrom/setup.exe
```
Obviously change the path and executable name to match your actual drive path and executable name. If the installer file is a MSI file instead of an EXE, then do this instead:
```
wine start /media/cdrom/setup.msi
```
Wine will produce all its output in the terminal window, which may give an error message to explain what is happening.

---

### Post by ididntdoit52 on 2009-01-14
> **cogadh said:**
> In that case is is as simple as opening a terminal and typing:
```
wine /media/cdrom/setup.exe
```
Obviously change the path and executable name to match your actual drive path and executable name. If the installer file is a MSI file instead of an EXE, then do this instead:
```
wine start /media/cdrom/setup.msi
```
Wine will produce all its output in the terminal window, which may give an error message to explain what is happening.
Ah ya. Thats what I've been doing. Still doesn't work. :( I'll check to see if it gives an error message though.

---

### Post by ididntdoit52 on 2009-01-14
Alright heres what it says.

```
ryan@ryan-desktop:/media/cdrom$ err:msi:msi_cabextract FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"css.cab"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627

```

---

### Post by cogadh on 2009-01-14
That error could indicate a physical problem with the disk. Is the disk damaged or dirty in any way?

You know, if you already have Steam working, you *should* be able to install CS:S by downloading, rather than fighting with the disk. All you should need to do is click on the "Games" menu, choose "Activate a product on Steam...", then follow the Product Activation Wizard.

---

### Post by ididntdoit52 on 2009-01-14
> **cogadh said:**
> That error could indicate a physical problem with the disk. Is the disk damaged or dirty in any way?

You know, if you already have Steam working, you *should* be able to install CS:S by downloading, rather than fighting with the disk. All you should need to do is click on the "Games" menu, choose "Activate a product on Steam...", then follow the Product Activation Wizard.

Its not. I'll try downloading it though. Thanks for the help.

---

### Post by ididntdoit52 on 2009-01-14
> **cogadh said:**
> That error could indicate a physical problem with the disk. Is the disk damaged or dirty in any way?

You know, if you already have Steam working, you *should* be able to install CS:S by downloading, rather than fighting with the disk. All you should need to do is click on the "Games" menu, choose "Activate a product on Steam...", then follow the Product Activation Wizard.

It worked perfect! Thank you very much cogadh. :D

---

