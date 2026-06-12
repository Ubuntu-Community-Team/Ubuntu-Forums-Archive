---
title: "Host key and keyboard integration not working with virtualbox [solved]"
date: 2014-11-19
forum: Virtualisation
---

### Post by geoffmen on 2014-11-19
I have been struggling with this problem for about an hour before I finally found the solution. Posting in case others encounter the same problem.

Running UbuntuGnome 14.04. Host key in virtualbox was not working such as the keyboard shortcuts to change display. Mini toolbar was not showing up either, and when I git [super] in the Windows Guest, the gnome-shell overlay would appear.

It turns out it's the "Show location of pointer" option that causes all this. It's in gnome-tweak-tool in the Keyboard and Mouse tab. Disabling this feature makes host key, keyboard integration and mini toolbar work again.

---

