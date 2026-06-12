---
title: "Ubuntu on virtualBox  - How to enable visual effects"
date: 2008-11-04
forum: Virtualisation
---

### Post by newbe2007 on 2008-11-04
Hi all,
I installed Ubuntu on virtualBox and I want to enable visual effects (3d box desktop and..)
How to do it ?
I tried to enable it by system->preferences->appearance-> visual effects
but no luck.
any 1 know how?

---

### Post by Peter09 on 2008-11-04
Sorry isn't possible. VirtualBox shows the virtual machine a simple graphics card - no 3d effects. So its a no go.

---

### Post by Fracman on 2008-11-05
> **newbe2007 said:**
> Hi all,
I installed Ubuntu on virtualBox and I want to enable visual effects (3d box desktop and..)
How to do it ?
I tried to enable it by system->preferences->appearance-> visual effects
but no luck.
any 1 know how?

Click on System Tools -> Configuration Editor -> apps -> metacity-> general -> compositing_manager, it will give you shadowed windows and you'll be able to run applications that require a composite manager, like AWN or Screenlets, without the need for Compiz-Fusion :)

---

### Post by StefAndrew on 2008-11-05
> **Peter09 said:**
> Sorry isn't possible. VirtualBox shows the virtual machine a simple graphics card - no 3d effects. So its a no go.

What he said, because it uses a generic graphics adapter, it won't let you enable the 3D effects.  AFAIK there is no way to change the graphics adapter on the virtual machine.

---

### Post by Merk42 on 2008-11-06
> **Fracman said:**
> Click on System Tools -> Configuration Editor -> apps -> metacity-> general -> compositing_manager, it will give you shadowed windows and you'll be able to run applications that require a composite manager, like AWN or Screenlets, without the need for Compiz-Fusion :)

I'm interested in trying this, however I can't find the menu.
I have nothing called "System Tools" and if you just mean "System" there is nothing called "Configuration Editor" under "Preferences" nor "Administration"

---

### Post by reacocard on 2008-11-06
> **Merk42 said:**
> I'm interested in trying this, however I can't find the menu.
I have nothing called "System Tools" and if you just mean "System" there is nothing called "Configuration Editor" under "Preferences" nor "Administration"

alt+f2, type in gconf-editor.

---

### Post by Merk42 on 2008-11-06
> **reacocard said:**
> alt+f2, type in gconf-editor.

That did it.
Why are there GUI programs that aren't accessible through a GUI?

---

### Post by FrostyFlames on 2008-11-08
They don't want people screwing their computers up because the wanted to "play" with some settings they shouldn't.

Edit: by they, I mean the developers and anyone who does support.

---

### Post by reacocard on 2008-11-08
> **FrostyFlames said:**
> They don't want people screwing their computers up because the wanted to "play" with some settings they shouldn't.

Edit: by they, I mean the developers and anyone who does support.

Exactly. Also there is a menu entry for it, its just hidden by default. if you want gui access to it you can edit the menu to unhide it, or just point your file manager to /usr/share/applications and open it from there.

---

