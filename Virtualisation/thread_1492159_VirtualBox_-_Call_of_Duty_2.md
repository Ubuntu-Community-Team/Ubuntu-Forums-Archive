---
title: "VirtualBox - Call of Duty 2"
date: 2010-05-24
forum: Virtualisation
---

### Post by FinalShot on 2010-05-24
I just installed Call of Duty 2 on XP, installed DX9, and tried to run it, but I get a "unrecoverable dirextx error". I know it's not my hardware, works fine on actual xp not emulated.

Ideas? Worst case scenario I install XP on it's on partition.

---

### Post by Perkins on 2010-05-24
Games which require 3D acceleration are tricky.  Install the guest additions on your virtual system and tell it you want to use the (experimental) 3D support.  (I think this may only be available in the PUEL version)

This may or may actually work depending on whether everything CoD wants to do is supported yet or not.

---

