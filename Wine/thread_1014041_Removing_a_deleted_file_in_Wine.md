---
title: "Removing a deleted file in Wine"
date: 2008-12-17
forum: Wine
---

### Post by wewhitt on 2008-12-17
Hello there,
In Ubuntu I have installed and deleted off some programs in Wine. Specifically UltraVNC -- I discovered a better way of doing things. This program did not have a uninstall feature and for the life of me I can't figure out the "add / remove software" part to Wine. I got frustrated and simply deleted the files and emptied the trash. I apologize, but sometimes learning this Linux can be frustrating. Now that I'm settled and getting back into it ... I've noticed under "Applications/Wine/Programs" the software I deleted is still there listed under Accessories. 

Ekkkk

What do I do now? How do I completely remove this from the "list" and ensure that this doesn't happen again with a proper procedure on how to safely remove programs from Wine. 

Any help would be greatly appreciated!!

Thank you,

Bill

---

### Post by jorj82 on 2008-12-17
> **wewhitt said:**
> This program did not have a uninstall feature and for the life of me I can't figure out the "add / remove software" part to Wine. I got frustrated and simply deleted the files and emptied the trash.

Applications>Wine>Uninstall Wine Software
Pick your app in the menu and click 'Uninstall'

> **wewhitt said:**
> I've noticed under "Applications/Wine/Programs" the software I deleted is still there listed under Accessories. 
What do I do now? How do I completely remove this from the "list" and ensure that this doesn't happen again with a proper procedure on how to safely remove programs from Wine.

Right click on 'Applications' then click 'Edit Menus' Find the app in the list and uncheck the box.

Hope this helps :)

---

### Post by wewhitt on 2008-12-17
That worked perfectly!

The uninstall part didn't see the program anymore. I figured that would happen since I deleted all the files manually -- not knowing how to add/remove files in Wine. The deselection of the menu items cleaned it up so now I don't have to worry about them accidently being opened. It's wierd to think about them being there, but deselected and not deleted out. I am happy with it for now - I am a bit anal when it comes to programs and dead end links. If there is a procedure to permantly delete them out of the Menu -- I would entertain that.

Thank you for helping me clean up my mistake I appreciate it!! I love this forum -- it's been a life saver for sure!!

---

### Post by jorj82 on 2008-12-17
When you're editing the menus, you can also right click the shortcuts and choose to delete.

---

