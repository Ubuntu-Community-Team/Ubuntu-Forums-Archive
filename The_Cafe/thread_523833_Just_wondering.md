---
title: "Just wondering"
date: 2007-08-12
forum: The Cafe
---

### Post by kerry_s on 2007-08-12
I was just wondering if any 1 else use's there text editor as a file manager?

The story:
I was showing a friend of mine how to get the most out of his low resource system, the low resource file manager we use is "mc" which to him was normal, because it's a file manager. So then i told him the text editor is also a kind of poor mans file manager, if you don't feel like using the terminal, he then gave me the most puzzled look i have ever seen, so i showed him & he was amazed, he apparently never thought past the text editor aspect of it, he just thought a text editor is a text editor and that's all it's good for.

So a little example, i'm going to use xedit:
Press alt+f2 type> xedit
you should see a blank page
now click load, you should see the equivalent of ls -a, now just click on a folder or file to view it. in xedit you can load what ever path you put it does not have to lead to a file.

Now a step up from that is say gedit, click on file> open. does that not look like a file manger? you can click open as many times as you want to move to the next folder/file.

Thoughts?

---

### Post by csimons on 2007-08-12
While it may be sufficient for simply browsing the file system, file managers are used for other things that this approach might not be able to accommodate.

According to the Wikipedia, "[file managers] are very useful for speeding up interaction with files. The most common operations on files are create, open, edit, view, print, play, rename, move, copy, delete, attributes, properties, search/find, and permissions."

So, I suppose one could escape the editor and perform shell commands to carry out these functions (like VIM's ! command), but the shell underneath would still be performing the operation, and thus two programs (the editor and the shell) would be required to perform a function that one program alone (the shell) could perform.

In Windows (since 95, I believe), one can move files around, create folders, rename files/folders, edit file properties/attributes/permissions, perform filetype-dependent operations (play, edit, etc.), etc. from within the open/save dialogs because they are essentially built off miniature Explorer windows, but I don't believe the current GUI dialogs in GNOME or KDE have yet reached this level of functionality.

Just my two cents.

---

### Post by kerry_s on 2007-08-12
> **csimons said:**
> While it may be sufficient for simply browsing the file system, file managers are used for other things that this approach might not be able to accommodate.

According to the Wikipedia, "[file managers] are very useful for speeding up interaction with files. The most common operations on files are create, open, edit, view, print, play, rename, move, copy, delete, attributes, properties, search/find, and permissions."

So, I suppose one could escape the editor and perform shell commands to carry out these functions (like VIM's ! command), but the shell underneath would still be performing the operation, and thus two programs (the editor and the shell) would be required to perform a function that one program alone (the shell) could perform.

In Windows (since 95, I believe), one can move files around, create folders, rename files/folders, edit file properties/attributes/permissions, perform filetype-dependent operations (play, edit, etc.), etc. from within the open/save dialogs because they are essentially built off miniature Explorer windows, but I don't believe the current GUI dialogs in GNOME or KDE have yet reached this level of functionality.

Just my two cents.


sorry, i meant just for browsing and modifing text file kind of file manager, instead of using cd & ls -a & nano. a text editor uses very little resources as compared to a file manager, but gives you a easier and faster look around your folders & files then say console/term. i use mc for actual file manager work, but i use the text editor like i would a file manager when i just need to work with text and i have used the "save as" to create, copy, rename, move.

---

### Post by Jucato on 2007-08-12
As far as I know, in KDE, the underlying system for the File dialog (the one you see when you want to Open or Save As) is actually a simplified version of the same underlying system used to display the files in the file manager. The file manager and file dialog share certain features, like different views (icon view, list view, etc), same drag and drop features, sorting, etc.

So in KDE, your idea isn't really that far off, at least in terms of the implementation. :)

---

### Post by kerry_s on 2007-08-12
> **Jucato said:**
> As far as I know, in KDE, the underlying system for the File dialog (the one you see when you want to Open or Save As) is actually a simplified version of the same underlying system used to display the files in the file manager. The file manager and file dialog share certain features, like different views (icon view, list view, etc), same drag and drop features, sorting, etc.

So in KDE, your idea isn't really that far off, at least in terms of the implementation. :)

i can do anything i do in a file manager, with just xedit & alt+f2(mine is bound to gmrun). i can run all the usual term commands mkdir,mv,copy,ln,etc... i can view thumbnails/pics with feh(feh -t ~/.icons or feh *.jpg, for single). there's just so many options. :)

---

