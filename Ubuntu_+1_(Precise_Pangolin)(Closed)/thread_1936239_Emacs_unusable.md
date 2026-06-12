---
title: "Emacs unusable"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BeRoot ReBoot on 2012-03-05
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/941790](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/941790)

---

### Post by keithpeter on 2012-03-05
Hello BeRoot

Good heavens, yes, how strange.

I supose its because most of us use emacs23 with the tool bar &c

Cheers

---

### Post by prana on 2012-03-05
I am not using Ubuntu currently. I am using Xubuntu and I don't see this problem.

I also hide the menu and toolbar so it is possible that it may affect me if I moved to Ubuntu.

Anyway, seems like the bug is confirmed so it may be fixed before release.

---

### Post by BeRoot ReBoot on 2012-03-06
> **keithpeter said:**
> I supose its because most of us use emacs23 with the tool bar

Why would you do that, it's just a collection of redundant buttons whose functionality is more efficiently accomplished with keychords.

---

### Post by keithpeter on 2012-03-07
> **BeRoot ReBoot said:**
> Why would you do that, it's just a collection of redundant buttons whose functionality is more efficiently accomplished with keychords.

Because that is the default. I don't waste time changing that. I just ignore it. I have a couple of million pixels to fill.

So when I did, prompted by your post, I found the behaviour that you found. 

I'm thinking most GUI emacs users don't change the default, hence don't see the odd behaviour.

Keep with the meta :twisted:

---

### Post by lykwydchykyn on 2012-03-07
I guess they figure if you're the kind of person who disables the menu and toolbar, you must be hardcore enough to only need the minibuffer.  ;)

---

### Post by keithpeter on 2012-03-07
> **lykwydchykyn said:**
> I guess they figure if you're the kind of person who disables the menu and toolbar, you must be hardcore enough to only need the minibuffer.  ;)

Hello lykwydchykyn

or have

```
emacs -nw
```

aliassed to

```
emacs
```

in their .bashrc

Seriously, hope it gets fixed as I'm dithering around with org-mode, and I have added myself to the bug to see what happens.

---

### Post by PaulW2U on 2012-03-07
The command quoted in the bug report

```
emacs23 -Q --execute "(progn (tool-bar-mode 0)(menu-bar-mode 0))"
```

works as expected in KDE 4.8 and Gnome Shell.

---

### Post by keithpeter on 2012-03-08
> **PaulW2U said:**
> The command quoted in the bug report

```
emacs23 -Q --execute "(progn (tool-bar-mode 0)(menu-bar-mode 0))"
```

works as expected in KDE 4.8 and Gnome Shell.

And as expected in Unity 2d

---

### Post by PaulW2U on 2012-03-25
> **BeRoot ReBoot said:**
> [https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/941790](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/941790)

Bug now showing as fixed. :cool:

---

### Post by cmccauley on 2012-03-26
> **keithpeter said:**
> Hello BeRoot

Good heavens, yes, how strange.

I supose its because most of us use emacs23 with the tool bar &c

Cheers

Not sure that you can make that clearly unjustifiable statement - have you surveyed emacs users? Having said that, I'm one of the vast, vast majority of emacs users who do not use the toolbar, preferring the honest purity of the keyboard shortcuts. 

To be sensible for a second, I don't have the problem that the OP raised.

I do however have occasional screen corruption in emacs when scrolling around.


Chris

---

### Post by kmas on 2012-04-23
I have a question, under both 12.04 and 11.10, to access the menu, we are supposed to use M-` or F10, the first one is used by compiz and the second one will open some menubar(if in terminal you are opening the terminal's menubar). I'm not sure what keywords to use to find my answer, and doesn't look like a lot of people are bothered by this, what solution do you guys have, are there any easy keystrokes that have no been assigned in emacs that I can use to customize accessing the menu, typing M-x m.... is annoying, just to access the menu.

---

