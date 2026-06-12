---
title: "encrypt/remove bash log?"
date: 2005-11-03
forum: Server Platforms
---

### Post by MindSpore on 2005-11-03
I saw on some guide somewhere suggesting to encrypt the bash log..  I'm not sure where this is, or how to go about encrypting it... maybe it's possible just to disable it so there is no bash log?

---

### Post by niko_ on 2005-11-03
hi, you can always disable .bash_history (bash log) with pointing HISTFILE somewhere else, best case HISTFILE= would disable it. 

type this and it will disable your bash history under your user:

> echo "HISTFILE= ;rm -rf ~/.bash_history" >> ~/.bash_profile;

this removes your .bash_history + disables any future logging.

---

