---
title: "what if 'uninstall wine software' does not work"
date: 2010-09-07
forum: Wine
---

### Post by stijnblommerde on 2010-09-07
ubuntu version: ubuntu 10.04.1

issue: i would like to remove application launchers and clean up the registry after manually removing wine software from virtual c drive

tried to uninstall itunes: 
applications - uninstall - uninstall wine software - itunes - remove. 
this did not work

i removed the contents of virtual c drive: 
applications - wine - browse C:drive - removed its contents
now i want to remove the application launchers and clean up the registry

how do i do this?

thanks a lot!

---

### Post by Bulletproofmask on 2010-09-21
I was having this same problem and found a partial answer on another site.  It seems that the Wine menu is stored outside of the ~/.wine directory.  Just navigate to:

~/.local/share/applications/wine/Programs/

and delete the folders there for iTunes and/or whatever other programs you have removed.  This should remove the folders and icons from Applications>Wine>Programs.

Hope this helps you some.

---

