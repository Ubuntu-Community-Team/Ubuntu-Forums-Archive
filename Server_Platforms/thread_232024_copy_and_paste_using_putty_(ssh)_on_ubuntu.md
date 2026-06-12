---
title: "copy and paste using putty (ssh) on ubuntu ?"
date: 2006-08-08
forum: Server Platforms
---

### Post by michaluxa on 2006-08-08
Hi all,
Does anybody know how I can copy and paste in a terminal window opened by putty (a ssh connection). 

All I found when searching for an answer is that:

left-click the mouse copies and 
right-click pastes

Unfortunateley this does not work. I don't use the putty version for Windows but did a "apt-get install putty" on my ubuntu system. 

Grateful for any clues. Thanks.

Micha

---

### Post by dusu on 2006-08-08
Shouldn't you use middle button to paste ?

---

### Post by michaluxa on 2006-08-08
thanks dasu, that works well -great!

how do I do I copy from thew window? left or right mouse doesn't do it :-(

---

### Post by Klaidas on 2006-08-08
You cal also use Shift + Insert to paste

---

### Post by michaluxa on 2006-08-08
thanks, that works as well, still after the copy command though...
I tried various shift-xxx but could not copy FROM the terminal window...

---

### Post by dusu on 2006-08-08
This is strange, I tried it and it just works...
select and copy with left button, then paste with middle button (from or to the terminal...)

---

### Post by michaluxa on 2006-08-08
Thanks for your reply, I can select and copy with left mouse button and past with middle button into the SAME terminal window. 

But if I want to past FROM the putty terminal into another application i.e.gedit or openoffice writer, it doesn't work...

---

### Post by dusu on 2006-08-08
> **michaluxa said:**
> Thanks for your reply, I can select and copy with left mouse button and past with middle button into the SAME terminal window. 

But if I want to past FROM the putty terminal into another application i.e.gedit or openoffice writer, it doesn't work...

sorry but I'm dry on this one since it works on my computer :( 
(I tried gedit and oowriter)

can someone else help :confused:

---

### Post by FredSambo on 2006-08-08
you just select the text that you want to copy from the putty terminal with your left mouse button, it automatically copies it for you, so all you have to do is paste it into your new document (right-click paste or whatever).

---

### Post by FredSambo on 2006-08-08
...at least that's how it works in windows.  not sure why you'd need putty on linux though?

---

### Post by michaluxa on 2006-08-08
hi again,
thanks for your feedback...

My operating system is ubuntu (desktop and server) - not windows...

Unfortunately pasting by mouse or CTRL-V etc does not work as it should (only within the same terminal it does)  - that's why I have asked this here... ;-)

cheers,  Micha

---

### Post by oranlooney on 2007-12-16
This relates only to Gnome, Ubuntu's default desktop.

This is what I do to copy from PuTTY:
1. Select text by left-dragging
2. Middle click in a text field in another application.
*Do Not* select a block of text in the other application and try to replace it with a right click.  It won't work.  

I don't know if right-click paste will work for every application, but I know for a fact you can paste into Gedit this way.  

Here's why: Gnome handles the clipboard quite a bit differently than windows.  Basically, there are TWO different buffers, one that contains the most recently selected text and is pasted with right clicks, and another handled by Ctrl-X,C,V.  The two buffers don't communicate; text copied with Ctrl-C can only be pasted with Ctrl-V, and the current selection can only be pasted with a middle click.

That's also why you can't "paste over" a selected block of text with a right-click; as soon as you select it, it becomes the most recent selection.

There are several utilities that you might find useful; google "gnome clipboard."

---

### Post by rsw686 on 2007-12-16
Why do you need to use putty in linux? You can use a terminal. If you need to connect to a remote system a terminal and ssh will do it. Then you can copy/paste like normal.

---

### Post by oranlooney on 2008-01-12
Why PuTTY instead of ssh?

PuTTY has a little configuration GUI that lets you manage and store sessions,  handle those annoying backspace problems, and a bunch of other low-level terminal stuff I don't use much but is probably useful to someone.

I'm sure one could achieve the same effect by messing around with ssh command line switches and terminal settings, but I still don't know how one would store the different settings required by different servers without a custom script or something.  Maybe there's a way; I don't know everything.  

In any case, the alternative copy-and-paste is generally useful when working in GNOME.  Here's a source I googled up:
[URL="http://ubuntu.wordpress.com/2006/12/12/cut-copy-paste-clipboard-management/"]
http://ubuntu.wordpress.com/2006/12/12/cut-copy-paste-clipboard-management/[/URL]

---

