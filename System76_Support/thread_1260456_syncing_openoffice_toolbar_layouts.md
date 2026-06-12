---
title: "syncing openoffice toolbar layouts?"
date: 2009-09-07
forum: System76 Support
---

### Post by glacialfury on 2009-09-07
I've successfully managed to set up a home dir syncing solution with unison, including firefox bookmarks.  I've been unsuccessful finding exactly what needs to be synced for the layout of openoffice apps to transfer over.

For example, I customize most of my toolbars and arrange them in a non-standard way; this is time consuming, I fiddle with it frequently, and manually propagating those changes to my other computer is a hassle.

Does anyone know where/which config file stores these toolbars and their layout in openoffice, so that I can add that file/folder to my sync list?

Regards,

David

---

### Post by jdb on 2009-09-07
> **glacialfury said:**
> I've successfully managed to set up a home dir syncing solution with unison, including firefox bookmarks.  I've been unsuccessful finding exactly what needs to be synced for the layout of openoffice apps to transfer over.

For example, I customize most of my toolbars and arrange them in a non-standard way; this is time consuming, I fiddle with it frequently, and manually propagating those changes to my other computer is a hassle.

Does anyone know where/which config file stores these toolbars and their layout in openoffice, so that I can add that file/folder to my sync list?

Regards,

David

I don't know where the defaults are stored but I have noticed that all custom toolbars & their layouts are stored with the document.

Save an empty document as a template.
To start a new document with the same layouts, select template & then the name of the template you saved.

In version 3.1.1 my templates are saved in
~/.openoffice.org/3/user/template/

jdb

---

### Post by Hagar Delest on 2009-09-08
Some hints here: [[Tutorial] The OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426). See the *.xcu files related to each component.

---

### Post by glacialfury on 2009-09-10
Thank you both for your replies; I'll play around with the solutions offered and see what works.  Your rapid responses are, as always, appreciated.

---

