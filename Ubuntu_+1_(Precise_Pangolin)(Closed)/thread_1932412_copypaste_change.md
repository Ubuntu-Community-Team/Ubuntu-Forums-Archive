---
title: "copy/paste change?"
date: 2012-02-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-02-27
It's not a big problem for me, and this is not a complaint, but I'm just curious about a change I've seen recently in how copy/paste works.  It's possible that it's due to a change I've made here in my system (but I don't think so).

I often copy/paste text from window to window and desktop to desktop.  Before, when I wanted to get some text from, say, a Firefox window, into a text file, I could just highlight the text with my mouse, switch desktops to a terminal window with a vi editing a text file and in input mode, and click my middle mouse button, then the text popped up in the file.

Now, to do this, I have to use the context menu on the first desktop to do an explicit Copy operation, then on the other desktop, use an explicit Paste operation to get the text to pop up.

I believe MS Windows also requires explicit copy/paste operations.

So is this a change in PP, or am I somehow misinterpreting what is happening?  Ordinarily, also, I am a different user when I do the Copy than when I do the Paste, so that might make a difference, and also I changed from using a vi that is vim-in-vi-emulation mode to a vi that is vim-doing-its-own-thing.

---

### Post by mc4man on 2012-02-27
Still works here, highlight, middle click (upper r. corner on my touchpad) will paste, no context menu used (same user

---

### Post by Gregory Lee on 2012-02-27
I just tested to see if same user (greg and greg) versus different user (greg and root) made a difference on my system.  It doesn't.  To make it work, even going from greg-owned to greg-owned, I still have to do explicit Copy and Paste using context menus.

---

### Post by sgage on 2012-02-27
Hmmm... middle-click paste is working fine here.

---

### Post by jpeddicord on 2012-02-27
No issues here either.

---

### Post by Gregory Lee on 2012-02-28
I did some further tests.  Implicit copy/paste works normally in a terminal window at the command line and using gedit or nano.  It also works normally for vim unless you have a .vimrc file (as I do) with this line uncommented: 
set mouse=a

So, it's a bug in vim.

---

### Post by jpeddicord on 2012-02-28
> **Gregory Lee said:**
> I did some further tests.  Implicit copy/paste works normally in a terminal window at the command line and using gedit or nano.  It also works normally for vim unless you have a .vimrc file (as I do) with this line uncommented: 
set mouse=a

So, it's a bug in vim.

Feature, actually. Vim has its own selection buffer, so it overrides middle-mouse. You can have it communicate with X to use that instead if you like.

[http://vim.wikia.com/wiki/Accessing_the_system_clipboard](http://vim.wikia.com/wiki/Accessing_the_system_clipboard)

---

### Post by Gregory Lee on 2012-02-28
> **jpeddicord said:**
> Feature, actually. _..._[]("http://vim.wikia.com/wiki/Accessing_the_system_clipboard")
How interesting!  My vim, according the output of "vim --version", was compiled without support for the X11 clipboard.  I guess I'll try the Gvim available from the Software Center.

---

### Post by xebian on 2012-02-28
> **Gregory Lee said:**
> How interesting!  My vim, according the output of "vim --version", was compiled without support for the X11 clipboard.  I guess I'll try the Gvim available from the Software Center.

I have stock vim from repo and copy/paste works fine so I think your problem is something else.

---

### Post by Gregory Lee on 2012-02-28
> **xebian said:**
> I have stock vim from repo and copy/paste works fine so I think your problem is something else.
I pointed out that copy/paste works fine with vim (part of the alpha 2 defaults) unless you do something special: during initialization of vim, set the "mouse" variable to the value "a".  I did that, because I wanted to be able to relocate my text cursor within a text by clicking my mouse at a new location.  It's just something I'm used to doing, and probably wouldn't matter to most.  If people don't screw around with their vim initialization, they will presumably not experience any problem.

Edit:  Okay.  I installed Gvim from repo, and now (1) "vim --version" shows "+xterm_clipboard", meaning I guess that X11 clipboard support is included in this version, (2) I can enable mouse support for the terminal version of vim without losing copy/paste with the mouse.  Now, it works the way I'm used to it working.

Thanks for all your help.

---

