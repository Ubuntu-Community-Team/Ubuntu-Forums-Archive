---
title: "Something like an easter egg :/"
date: 2008-02-11
forum: The Cafe
---

### Post by Stex on 2008-02-11
If you're in for some form of surreal laugh: Press alt+f2 for the run application dialogue, type in # and press enter.

It opens up nautilus at "#" which seems to be the same collection of files & folders as the root directory, except everything is labeled "/". Which means opening anything shows the same page again... I wouldn't recommend editing anything while you're in there though, this is presumably a bug and editing stuff may well screw your folder layout up... I dunno.

I haven't filed a bug report, nor do I want assistance. Just wanted to share something that actually made me stop for a moment and think "WTF is that doing?"

:shock:

---

### Post by FuturePilot on 2008-02-11
Weird :shock:

---

### Post by Christmas on 2008-02-11
In KDE this brings the UNIX manual pages.

---

### Post by corney91 on 2008-02-11
Gives me my home folder in Thunar on Hardy...

---

### Post by red_Marvin on 2008-02-11
You want root, you get root ;)

---

### Post by jken146 on 2008-02-11
Does nothing for me.  # is a comment in BASH so it really shouldn't do anything.

---

### Post by billgoldberg on 2008-02-11
[[img]http://xs224.xs.to/xs224/08071/bug744.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs224&d=08071&f=bug744.png)

Does this open as root?

If it does this is a serious bug, and should be fixed.

---

### Post by red_Marvin on 2008-02-11
No, it does not open as root, it was just a joke based on the fact that the top directory (the root directory) is referred with a single forward slash.

---

### Post by Stex on 2008-02-11
Out of interest, all you non-gnome users. What happens when you point your file browser of choice to **file:///#** ?

---

### Post by corney91 on 2008-02-11
> **Stex said:**
> Out of interest, all you non-gnome users. What happens when you point your file browser of choice to **file:///#** ?
Can't find the file, both in Nautilus and Thunar....

---

### Post by Mr. Picklesworth on 2008-02-11
> **corney91 said:**
> Can't find the file, both in Nautilus and Thunar....

*Incorrect* :P
Actually, that's because of the version you are running. For any stable Ubuntus, this happens...

In Nautilus use "Go -> Location" in the menu (Ctrl+L), type "#" and press Enter. Gaze in horror.

It appears to be the root directory (file types determined quite smoothly), but with "/" as the name for everything there... Funny little bug.


Fortunately, gnome-vfs is deprecated now and - as you have seen - this does not happen in Hardy (with the gvfs-powered Nautilus). Instead, Nautilus says that it cannot handle the location, as it should.

---

### Post by macogw on 2008-02-11
> **Stex said:**
> Out of interest, all you non-gnome users. What happens when you point your file browser of choice to **file:///#** ?

Well, my file browser of choice is mxrvt, and "cd file:///#" gives a bash error.  Firefox just goes to / and lists things as normal.

---

### Post by Christmas on 2008-02-12
> **jken146 said:**
> Does nothing for me.  # is a comment in BASH so it really shouldn't do anything.
But don't type in a shell. Of course it does nothing in a shell, try typing it after you hit ALT+F2 for the Run box.

---

### Post by LaRoza on 2008-02-12
> **Stex said:**
> Out of interest, all you non-gnome users. What happens when you point your file browser of choice to **file:///#** ?

I get the same thing, everything named "/"

---

