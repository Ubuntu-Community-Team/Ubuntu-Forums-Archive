---
title: "virtualbox - query"
date: 2008-02-04
forum: Virtualisation
---

### Post by mosaic2s on 2008-02-04
using amd 2800+. gutsy host and xp as host with 512mb and 32mb video ram.
unable to run autocad 2004 though installation went fine. the icon shows hourglass for a while then remains silent.

---

### Post by AndyCooll on 2008-02-04
Not clear on what you are asking.

Are you saying you cannot get Autocad working in a Windows XP Virtualbox environment?

:cool:

---

### Post by hyperair on 2008-02-04
..Gutsy as host and XP as guest you mean? Either way, 3d support for Guest OS in Virtualbox is currently nil or preliminary from what I've heard. So I doubt autocad will run.

---

### Post by mosaic2s on 2008-02-05
sorry for typo error.
gutsy is host and xp as guest os.
autocad 2004 installs but does not run.

---

### Post by hyperair on 2008-02-05
Autocad requires 3d capabilities which Virtualbox doesn't provide.

---

### Post by mosaic2s on 2008-02-09
wud that imply that autocad lite - only 2D version - will run?

---

### Post by mosaic2s on 2008-02-09
if no 3D capability in virtual box guest os, then blender for xp within guest os should not work.
it does.

vedute demo version runs within host os xp.

reals 3D runs too.

any other way?

---

### Post by hyperair on 2008-02-09
Seriously? But Direct3D totally refuses to run. Well this is news to me. =\

---

### Post by AndyCooll on 2008-02-09
VirtualBox itself doesn't directly use the graphics card in your machine, You could have a top of the range graphics card or an ancient one installed it makes no difference. Virtualbox only sees it's own "emulated" bog standard graphics card.

Therefore what will run are any programs that would run on a standard Windows machine with a bog standard graphics card.

:cool:

---

### Post by mosaic2s on 2008-02-12
Installed bricscad trial version on guest os xp. it works.

why not autocad?

---

### Post by mosaic2s on 2008-02-22
installed turbocad within xp. it imports 3d files and allows many 3d functions.

---

