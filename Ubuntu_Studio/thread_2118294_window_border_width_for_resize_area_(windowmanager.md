---
title: "window border width for resize area (windowmanager)"
date: 2013-02-20
forum: Ubuntu Studio
---

### Post by iwl on 2013-02-20
Hi group,

I like the ubuntu studio desktop much more then all that experiments of ubuntu and kde 4 - good things need no change.

Only the window border area is to small and it is hard to catch it for resizing the window.

I think it is possible to define a little space beside the window border sensitiv for window resize - seems to be so with standard ubuntu.

Does anybody have an idea where to look for.

I think this is also an issue for an bug report where can I send it to?

---

### Post by Innernet on 2013-02-20
For my 12.04 case, using Ambiance theme :

Go to :
Places > Computer > file system > usr > share > themes > Ambiance > metacity-1 > metacity-theme-1.xml

Or, open terminal, :
Applications > Accessories > Terminal
and type

gksudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml

Change values "1" and "1" and "1"  with "5" and "5" and "5" for left, right and bottom
Save the edited values.
Close the editor
Restart machine.

For other themes;  I suppose selecting the theme of interest would yield a file with similar parameters, and the change of border dimensions should be similar.  Not tried other.

Saving the original file to be able to return to its default should be a good precaution.

Come back with results.

---

### Post by jejeman on 2013-02-21
You can use shortcut to manipulate the windows. It is much faster.
Default is ALT. 
ALT+left click - move; ALT + right click - resize.

---

