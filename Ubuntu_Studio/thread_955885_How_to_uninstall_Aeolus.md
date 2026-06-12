---
title: "How to uninstall Aeolus?"
date: 2008-10-22
forum: Ubuntu Studio
---

### Post by AudioDef on 2008-10-22
I have a program in Ubuntu Studio I don't want - Aeolus. In Synaptics, uninstalling Aeolus wants to uninstall ubuntustudio-audio-plugins, which I want to leave installed. 

Can I fix this? Or does ubuntustudio-audio-plugins exist solely for Aeolus?

---

### Post by Stochastic on 2008-10-22
Ubuntustudio-audio-plugins is a metapackage.  It itself, has no data/info other than the list of packages that it requires.  When it is installed, other programs are then installed - once installed, it has no purpose and can be removed freely.  Aeolus is one of those requirements (just another audio plugin included in the ubuntustudio suite) so you can safely remove aeolus and ubuntustudio-audio-plugins without seeing your whole suite of ladspa plugins go out the window.

---

### Post by AudioDef on 2008-10-22
Thanks, Stochastic!

---

