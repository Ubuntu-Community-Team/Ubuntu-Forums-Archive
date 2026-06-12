---
title: "gtkboard error"
date: 2005-04-12
forum: Repositories &amp; Backports
---

### Post by LordScorpo on 2005-04-12
How would I fix the following problem:
-------------------------------------------------------------------------------------------------------------------------------------

OMF file [/usr/share/omf/gnome-utils/gfloppy-ja.omf] does not validate against S
crollKeeper-OMF DTD: /usr/share/xml/scrollkeeper/dtds/scrollkeeper-omf.dtd
Unable to register /usr/share/omf/gnome-utils/gfloppy-ja.omf

Errors were encountered while processing:
 gtkboard

-------------------------------------------------------------------------------------------------------------------------------------

This error was encountered while trying to use the Synaptic Package Manager to setup gnome-chess (0.3.3-5).

---

### Post by Fab on 2005-04-13
[QUOTE=LordScorpo]How would I fix the following problem:
-------------------------------------------------------------------------------------------------------------------------------------

OMF file [/usr/share/omf/gnome-utils/gfloppy-ja.omf] does not validate against S
crollKeeper-OMF DTD: /usr/share/xml/scrollkeeper/dtds/scrollkeeper-omf.dtd
Unable to register /usr/share/omf/gnome-utils/gfloppy-ja.omf

Errors were encountered while processing:
 gtkboard

-------------------------------------------------------------------------------------------------------------------------------------

This error was encountered while trying to use the Synaptic Package Manager to setup gnome-chess (0.3.3-5).[/QUOTE]
 i got the same error
and it kept saying it on every package installed til i did apt-get remove gtkboard which said cant remove because its not installed, but got rid of the error anyway ;P

---

### Post by LordScorpo on 2005-04-14
Ummmm...

well the first time, I got this error:
-----------------------------------------------------------------------------------------------------------------------------------
E: gtkboard:  subprocess post-installation script returned error exit status 9
-----------------------------------------------------------------------------------------------------------------------------------

Then I tried it again, and it just rebooted my system. What happened?

---

