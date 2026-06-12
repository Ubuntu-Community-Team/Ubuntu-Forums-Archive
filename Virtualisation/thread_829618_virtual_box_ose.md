---
title: "virtual box ose"
date: 2008-06-15
forum: Virtualisation
---

### Post by mosaic2s on 2008-06-15
updated from 7.10 to 8.04 online. system updated when needed.

removed virtualbox 1.5.2 and re-installed virtualbox ose through repositories. does not run.

error message that is displayed given below

Could not load the settings file '/home/linux/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/linux/.VirtualBox/VirtualBox.xml', line 5, column 83.

any way this can be resolved?

---

### Post by vishzilla on 2008-06-15
Create a backup of the VirtualBox.xml file and delete the file. After deleting, try starting VBox

---

### Post by mosaic2s on 2008-06-15
did that by renaming the xml file.
it worked some, then asked for virtualbox-ose-modules-generic installation. which i did through root terminal.

it works again.
thanks.

---

