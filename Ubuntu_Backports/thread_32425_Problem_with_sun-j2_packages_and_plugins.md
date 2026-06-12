---
title: "Problem with sun-j2* packages and plugins"
date: 2005-05-07
forum: Ubuntu Backports
---

### Post by Mlehliw on 2005-05-07
First of all I assume if I install the sdk I don't need to install the jre package.

For the real question after I install the j2sdk package I have no java plugins. Even when I copy the *.so file from /plugins/i386/ns7/ into the various plugin folders for firefox, nothing ever happens. When I visit the following link all I get is a bunch of plugin not found errors. Is there a fix for this? Is anyone else having this problem?

file:///usr/lib/j2sdk1.5-sun/demo/applets.html

edit: Nevermind, I guess. I just found out I needed to make symbolic links although it seems odd why I needed to do this, it seems to be working anyway though.

---

