---
title: "Cedega and GPLv3"
date: 2006-05-12
forum: The Cafe
---

### Post by Gannin on 2006-05-12
If I understand it correctly, the GPLv3 doesn't take kindly to open-source code and proprietary code being mixed together.  Again as I understand it, this is exactly what Cedega does.  Cedega borrows code from the Wine project to help further its own project.  If Wine adopts the GPLv3, and I'm sure it will, then Cedega will either have to continue to work off of the last GPLv2 Wine code they have and go from there, or some interesting things could happen.  Comments?

---

### Post by nocturn on 2006-05-12
[QUOTE=Gannin]If I understand it correctly, the GPLv3 doesn't take kindly to open-source code and proprietary code being mixed together.  Again as I understand it, this is exactly what Cedega does.  Cedega borrows code from the Wine project to help further its own project.  If Wine adopts the GPLv3, and I'm sure it will, then Cedega will either have to continue to work off of the last GPLv2 Wine code they have and go from there, or some interesting things could happen.  Comments?[/QUOTE]

AFAIK, this is not going to be a problem, besides, the wine project could grant an exception to cedega.

What might be a problem is that cedega may need to support DRM for some stuff to work and that would clash with v3.

---

### Post by FISHERMAN on 2006-05-12
AFAIK(I'm no expert), Wine used to have a BSD licence.
And Cedega is based is based on the BSD-licenced version of Wine.
So as long as they don't use the mere recent GPL-versions of Wine, Cedega cannot be stopped.

---

### Post by YokoZar on 2006-05-12
[QUOTE=Gannin]If I understand it correctly, the GPLv3 doesn't take kindly to open-source code and proprietary code being mixed together.  Again as I understand it, this is exactly what Cedega does.  Cedega borrows code from the Wine project to help further its own project.  If Wine adopts the GPLv3, and I'm sure it will, then Cedega will either have to continue to work off of the last GPLv2 Wine code they have and go from there, or some interesting things could happen.  Comments?[/QUOTE]
1) Wine is LGPL, not GPL
2) Cedega does not use LGPL Wine code, but instead a 3-year old branch of the Wine tree that was licensed under the MIT license (which basically let them do whatever they wanted with it.)  Wine adopted the LGPL precisely because Cedega was taking the Wine code and not contributing back.
3) No code for Wine written in the past 3 years has gone into Cedega.  The projects don't work together at all.

---

### Post by Gannin on 2006-05-12
And there, ladies and gentlemen, is a brief history lesson for you.

---

