---
title: "icon format"
date: 2006-12-10
forum: Ubuntu System Panel
---

### Post by 4tro on 2006-12-10
what is the format of the panel icon supposed to be.

---

### Post by ncappel1 on 2006-12-11
What do you mean exactly? Could you be more specific?

---

### Post by 4tro on 2006-12-11
what i meant was what filetype does usp expect and with what size?

---

### Post by chanders on 2006-12-13
USP will accept png and xpm for sure and I would advise using these. The size that you choose will be the one shown.

Hope this helps...

---

### Post by 4tro on 2006-12-14
then i must be understanding one of the options in gconf-editor totally wrong...
my idea was the icon is set with the option applet_icon_name

*edit
maybe i should tell what icon i mean exactly ... (A)
i mean the icon on the toolbar-button, which is the ubuntu logo now.

---

### Post by chanders on 2006-12-14
Try just putting 'computer' without the quotes and see if it changes... Icons in the gnome theme don't need an extension. If you need another icon use the full path with the extension...

---

### Post by 4tro on 2006-12-14
> **chanders said:**
> Try just putting 'computer' without the quotes and see if it changes... Icons in the gnome theme don't need an extension. If you need another icon use the full path with the extension...

using computer works.
but setting another icon with full path and extension doesn't work.

*edit
just tried the name of a custom icon in my /usr/share/pixmaps dir and now it works.
in my case 'beryl-manager'  without png extension

---

