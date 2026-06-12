---
title: "Broken executables in extensions in Firefox 3.6"
date: 2010-01-22
forum: The Cafe
---

### Post by lovinglinux on 2010-01-22
I thought would be interesting to let other users know about this. 

[http://blog.mozilla.com/addons/2010/01/22/broken-executables-in-extensions-in-firefox-3-6/](http://blog.mozilla.com/addons/2010/01/22/broken-executables-in-extensions-in-firefox-3-6/)

The blog post is targeting developers, but if you find that an extension doesn't work even with compatibility check overridden, they might be because of this.

Basically, they changed the way how extensions are extracted during installation and due to some issues, any extracted executable loses the permission to be executed. This only affects extensions with executables included (binaries, bash scripts...) and should be fixed on Firefox 3.6.1.

If you want to fix this problem for a particular extension, then locate the executable in the extension folder and change the permission accordingly.

---

