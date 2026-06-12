---
title: "Good text editor?"
date: 2007-04-27
forum: The Cafe
---

### Post by volksman on 2007-04-27
Hey All!

I'm trying to find out if there is a good alternative to UltraEdit32 for the GNU world.  Its the one program I just can't seem to break away from Win32 yet and always have a VM running in the background so I can use it...Seems a little silly just for a powerful text editor.

Things a text editor MUST have for me to enjoy:

- open/save to FTP/SFTP
- Tabs for multiple open files
- re-open previously open files on startup
- syntax highlighting and auto indenting
- multiple indenting (IE highlight a group of lines and be able to indent them all at once)

I'm sure there is more but those are THE most important to me by far...

Any suggestions appreciated... :)

Thanks!

---

### Post by v8YKxgHe on 2007-04-27
You could try gPHPedit (it does more than PHP), or maybe Bluefish - I don't know though if they have open/save to FTP.

---

### Post by aysiu on 2007-04-27
I don't know about "open/save to FTP/SFTP," but you can try Kate and Konqueror.

---

### Post by KIAaze on 2007-04-27
Konqueror to edit files??? O.o
I know you can view text files inside Konqueror. But how can you edit them with it?

---

### Post by Knomefan_fan on 2007-04-27
> **volksman said:**
> Hey All!

I'm trying to find out if there is a good alternative to UltraEdit32 for the GNU world.  Its the one program I just can't seem to break away from Win32 yet and always have a VM running in the background so I can use it...Seems a little silly just for a powerful text editor.

Things a text editor MUST have for me to enjoy:

- open/save to FTP/SFTP
- Tabs for multiple open files
- re-open previously open files on startup
- syntax highlighting and auto indenting
- multiple indenting (IE highlight a group of lines and be able to indent them all at once)

I'm sure there is more but those are THE most important to me by far...

Any suggestions appreciated... :)

Thanks!

I always use UltraEdit32 when I'm on a Windows computer and I like it a lot. Try Kate - it can do everything that you are looking for except that it does not use tabs (it uses a list of open files instead). I like them both equally much.

A good thing with almost every KDE programs is that accessing files over SFTP (and many other protocols) is very easy. You just open the file "sftp://server/file" and it will open the remote file just as if it was a local one. You can also browse the remote server in the ordinary file dialog!

---

### Post by reclusivemonkey on 2007-04-27
Would you consider non-GUI apps?

If its power you are looking for Emacs and Vim are the SCUD missiles of text editing on the command line.

---

### Post by volksman on 2007-04-27
I'll try Kate out...thanks!

Non-gui...no thanks...not very handy for developing a pile of files at once....I use VIM all the time for touch ups and do love it but it just doesn't cut it for mass development....

---

### Post by meng on 2007-04-27
I think gVIM can open files in tabs, but I've never used it.

---

### Post by Nils Olav on 2007-04-27
I think you want something like KDevelop.

Also take a look a these: 

[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)
[http://en.wikipedia.org/wiki/Comparison_of_text_editors](http://en.wikipedia.org/wiki/Comparison_of_text_editors)

---

### Post by mech7 on 2007-04-27
Maybe you can run it under WINE ?

---

### Post by Nils Olav on 2007-04-27
> **reclusivemonkey said:**
> Would you consider non-GUI apps?

If its power you are looking for Emacs and Vim are the SCUD missiles of text editing on the command line.

They both can be graphical.

---

### Post by reclusivemonkey on 2007-04-28
> **meng said:**
> I think gVIM can open files in tabs, but I've never used it.

Vim itself can open tabs. Just 

```

:help tabnew

```

There are a whole host of commands to navigate between tabs, which should appear in the help as well.

There is very little vim can't do, its just so powerful that a lot of people just aren't aware of what you can do with it. The vim homepage has an excellent tips section;

[http://www.vim.org/tips/index.php](http://www.vim.org/tips/index.php)

The only trouble with vim is you could spend a lifetime using it and never learn all its features!

---

### Post by Bloodfen Razormaw on 2007-04-28
Kate.  It does everything you want.  Contrary to what has been said, Kate can use tabs.  It includes a plugin by default to use a tabbar, although tabs are not nearly as good as Kate's default method of providing a file list sidebar.  With that setup, tabs act like split windows, where you can have multiple tabs (which can then be split too) all which can point to an arbitrary location, even in the same files.

---

