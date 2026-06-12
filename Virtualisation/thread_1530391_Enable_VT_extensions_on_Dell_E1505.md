---
title: "Enable VT extensions on Dell E1505?"
date: 2010-07-13
forum: Virtualisation
---

### Post by Benedolt on 2010-07-13
Hey all!

I am trying for the first time to seriously run Windows XP in VirtualBox on my Dell E1505 (MM061) under Lucid.
Well, the performance is really bad and I read somewhere that enabling VT-extensions in the BIOS would help.
I couldn't find that option though. 

How can I find out whether my computer has VT-extensions enabled or not?

Or maybe I don't even have the technical prerequisites? What do I have to look for? CPU specs? BIOS version?

Could you give me a hint there? Thanks a lot!

---

### Post by JustinR on 2010-07-13
VT-extensions should be recognized my default in VirtualBox and show up in the systems tab when setting up a virtual machine. If not, VT extensions will show up in your BIOS, if not then you don't have VT extensions.

---

### Post by Benedolt on 2010-07-14
Thanks Justin!

You mean the system tab you get when selecting the virtual machine and clicking settings? Then the VT-extensions should be mentioned under processor?

I don't see them... So my computer probably doesn't support them.

---

### Post by JustinR on 2010-07-14
Its under System > Advanced.

If your setup has that tab then VT Extensions will work.

---

### Post by Benedolt on 2010-07-14
Thanks a lot for your help, Justin!

Turns out, I don't have support for VT-extensions. Too bad, but good to know.

---

