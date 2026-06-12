---
title: "What Linux file manager is at par with the Win Explorer?"
date: 2019-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by hermin on 2019-02-12
Before I assumed the Win Explorer is just boiler plate, but it is not. Disappointingly e. g. „Duration“ as a column for .mp4 is not available, dragndrop from the window into a flashdrive icon does not work, pasting a file into the window of the filemanager impossible. There are more obstacles for a speedy work flow, these examples should suffice. A file manager is the most important software, at least for me. I read a few manuals, watched vids-no avail. As I am not Linux expert, am I right or wrong? Or did I miss something? Are there things only a Linux file manager can do?

---

### Post by howefield on 2019-02-12
Moved to "*Ubuntu, Linux and OS Chat*".

---

### Post by SeijiSensei on 2019-02-12
I use Dolphin, the native file manager for KDE.  Even if you're using vanilla Ubuntu, you can give Dolphin a try with 

```

sudo apt update
sudo apt install dolphin

```

It will bring in a bunch of KDE dependencies.  On modern drives, that's hardly an issue, but if you're tight for space on the main "/" directory, you might not want to take this route.

---

### Post by mastablasta on 2019-02-14
or less bling and more file power with Krusader or Midnight commander.

---

### Post by SeijiSensei on 2019-02-14
One thing I like about Dolphin on the KDE platform is how it makes remote connections pretty simple.  I use the "fish://" protocol to set up an SFTP connection to my remote web server.  Then I can move documents from local to remote with simple drag-and-drop.  (You can also use "sftp://" URLs as well.)  This feature depends on KDE's "kio-slaves." I don't know if they come along with a Dolphin installation on top of vanilla Ubuntu.

The "slaves" also work well for things like ripping CDs from within Dolphin.

---

### Post by ajgreeny on 2019-02-14
Thunar, which is the file-manager in Xfce4, Xubuntu, the OS I use, has a lot of custom actions available to add many things including **mediainfo** output, which will give the option of adding many items to the context menu from a right click.  I currently have 19 custom actions available and use most of them a great deal.

I am pretty certain there are similar utilities available also for nautilus in the form of extensions, and for the other file managers in the Ubuntu repos, so search for that when you know what information you need to find quickly from your file manager; there may well be an easy way to do it.

---

### Post by ubname on 2019-02-15
> **hermin said:**
> ... pasting a file into the window of the filemanager impossible. ...

I here you, maybe I am a bit dumb (or a lot dumb) but I cannot figure out, using "list mode" _that I prefer_, how to copy and the paste a file when in the destination dir you have enough files to fill up the available space.
If there is a way can someone tell me (us) how?
If indeed it is not possible, how can this be a thing in "gnome files"?
I infer the Gnome devs don't use Gnome (?), otherwise how can this be overlooked!

Thanks.

---

### Post by ajgreeny on 2019-02-15
What does Ctrl+V, the default for paste, do?  

I would expect it to paste any copied file or files in your clipboard into the currently active file manager folder; that is what happens with thunar and I can not imagine nautilus is any different.

---

### Post by ubname on 2019-02-16
Hi, ctrl-v paste the file, but the point is that it is not possible to paste using the mouse with right click menu;
anyway I already verified and at Gnome Gitlab there is a ticket for this issue so I assume they are working on it,
and hope it will be fixed.
Also I use the default file manager file file manager  not nautilus, that for your help anyway.

---

### Post by vanadium on 2019-02-16
This is indeed a rather serious flaw in nautilus in list mode. If there are sufficient files to fill the view, there is no place left where you can right-click to paste a file. You are always right-clicking a file, thus obtaining a file specific right-click menu.

In newer versions of nautilus, the general right-click menu (i.e., the one obtained if no file is selected) is available from right-clicking the breadcrumb in the path bar. In Ubuntu, we are currently stuck with an older version of nautilus, however.

There are ways around using the keyboard:
* Use Ctrl+V to paste
* Use Ctrl+F10 to display the general right-click menu.

---

### Post by Holger_Gehrke on 2019-02-16
Why right-click at all ? Just drag'n'drop between two file manager windows. Unless you're dropping the file(s) on a directory (in which case they will get copied or moved into that directory), this will do the expected thing. You can even force copy/move/link by holding shift/ctrl/ctrl+shift while releasing the mouse button (at least you could back when I was using nautilus (~ Ubuntu 12.04); I have switched to XUbuntu and Thunar since (on which this works just fine)).

Holger

---

