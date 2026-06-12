---
title: "What are the mouse/keyboard sequences for cut-and-paste on Ubuntu VirtualBox?"
date: 2015-04-15
forum: Virtualisation
---

### Post by Ron_Barak on 2015-04-15
[FONT=Helvetica Neue]I have a *non-graphical* Ubuntu installed inside VirtualBox under Windows.

I've installed VBoxGuestAdditions (and enabled *bidirectional* Drag'n'Drop - for the hell of it).[/FONT]
[FONT=Helvetica Neue]
However, none of the following will paste to the guest OS:
[/FONT]

[LIST]
[*]Shift+Ins
[*]Ctrl+v
[*]Ctrl+Shift+v
[*]Pressing right-click and left-click simultaneously (this emulates a middle-click on my laptop's two keys touch-pad).
[/LIST]
[FONT=Helvetica Neue]
[/FONT]
**What are the sequences for mouse/keyboard cut-and-paste in non-graphical Ubuntu under VirtualBox?**

[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]**Environment:**[/FONT]

[LIST]
[*]VirtualBox: 4.3.12 r93733
[*]VBoxGuest: 4.3.12
[*]Guest OS: Linux ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP x86_64
[*]Host OS: Windows 7
[/LIST]

---

### Post by TheFu on 2015-04-17
Just ssh into the virtual host using whatever ssh client you like and then use the built-in copy/paste.  If you are running X/Windows on the host you happen to be sitting behind (local or remote), it is select/paste using only the mouse - no keyboard needed.

I vaguely recall Putty on Windows working with select/paste too.

---

