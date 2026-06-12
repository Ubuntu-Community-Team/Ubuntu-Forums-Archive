---
title: "Regedit problem in Wine"
date: 2011-02-23
forum: Wine
---

### Post by Visvalor on 2011-02-23
Wine is really starting to annoy me. I'm trying to find and edit;

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="gdi"

But Wine has no Direct3D registry at all. Where do I go to install the WindD3D?

It does not come default, at least not on my machine.

Here is what is under Software\Wine

+>Crypto
>Debug
>DllOverrides
+>FileOpenAssociations
+>Fonts
>MenuFiles
+>MSHTML
>Temporary System Parameters

Where and how do I install DX support in Wine?

I've tried using Winetricks and installing dxd39 and all variants of Direct X I can find. Still nothing.

---

### Post by Visvalor on 2011-02-23
Solved with Winetricks. Still doesn't run my program though :P

---

