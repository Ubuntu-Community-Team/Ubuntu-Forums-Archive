---
title: "Emacs 23"
date: 2009-07-31
forum: The Cafe
---

### Post by Mornedhel on 2009-07-31
Emacs 23 was released two days ago (July 29th).

Do you guys use Emacs ? Vim ? Gedit/Kate ?

Something else entirely ?

---

### Post by lykwydchykyn on 2009-07-31
> **Mornedhel said:**
> Emacs 23 was released two days ago (July 29th).

Do you guys use Emacs ? Vim ? Gedit/Kate ?

Something else entirely ?

Yes.  To all of the above.

But the more I get used to Emacs, the more I find myself using it exclusively.

---

### Post by RATM_Owns on 2009-07-31
Vim FTW.

---

### Post by .Maleficus. on 2009-07-31
Vim, straight up.

---

### Post by Chilli Bob on 2009-07-31
Geany FTW!

---

### Post by Simian Man on 2009-07-31
vim

---

### Post by init1 on 2009-07-31
Nano for simple things, though ed can be very useful for deleting multiple lines at once.

---

### Post by Mornedhel on 2009-07-31
> **init1 said:**
> Nano for simple things, though ed can be very useful for deleting multiple lines at once.

Now I'm curious. How do you do that in ed, and how is it easier than vim's ndd (IIRC) and emacs' region selection or C-u n C-k ?

---

### Post by red_Marvin on 2009-07-31
> **Mornedhel said:**
> Now I'm curious. How do you do that in ed, and how is it easier than vim's ndd (IIRC) and emacs' region selection or C-u n C-k ?

```
$ ed
a
line one
line two
line three
line four
line five
.
[COLOR="red"]**2,4d**[/COLOR]
,p
line one
line five
Q
$
```

---

### Post by mr.propre on 2009-07-31
[http://ubuntuforums.org/showthread.php?t=1209327](http://ubuntuforums.org/showthread.php?t=1209327)

---

### Post by &#32 Greg on 2009-07-31
I actually started using Emacs 23 from CVS before it went stable. They did some nice theming work with it...

---

### Post by lykwydchykyn on 2009-07-31
> **  Greg said:**
> I actually started using Emacs 23 from CVS before it went stable. They did some nice theming work with it...

Is the final 23 version much different from the snapshot in the Jaunty repos?

---

### Post by &#32 Greg on 2009-07-31
> **lykwydchykyn said:**
> Is the final 23 version much different from the snapshot in the Jaunty repos?

No idea- I use Arch, for which there's a package that downloads the latest CVS build of Emacs. I used that a few days before 23 went stable.

---

### Post by nrs on 2009-07-31
If it weren't for the lack of pretty fonts I'd think I'd be content with 22, but I use 23.

---

### Post by hoagie on 2009-07-31
Nano

---

### Post by lykwydchykyn on 2009-07-31
> **nrs said:**
> If it weren't for the lack of pretty fonts I'd think I'd be content with 22, but I use 23.

+1

That's why I've been on snapshot.  I tried every terminal font in existence when I started using emacs, but nothing looked right on an LCD to me (especially sitting in the middle of a KDE4 desktop).

---

### Post by Mr. Picklesworth on 2009-07-31
Sorry, but that "other editor" poll answer has forced me to clarify: I use Scribes! :)

The feature list for Emacs 23 sounds kind of interesting, though.

---

### Post by Mornedhel on 2009-07-31
> **lykwydchykyn said:**
> Is the final 23 version much different from the snapshot in the Jaunty repos?

I use emacs-snapshot too. So far I haven't seen features from the new feature set that were absent in the snapshot, but obviously I haven't tested everything.

The things that make me the most happy right now are antialiasing for the X-enabled emacs, linum-mode in core, and daemon mode.

---

### Post by gnomeuser on 2009-07-31
I use gedit for many things just because it's easy and readily available, when in a console I use vim because my dad used vim before me and I grew up with it. I tried learning emacs once upon a time but it just seemed to complex for what I need. I am sure it's all powerful and stuff but I just need to edit simple things.

for programming I rely on the editor in MonoDevelop

---

### Post by jrusso2 on 2009-07-31
All I do with the text editor is modify text files for configuration.  A gui editor like gedit is what I use.  That's all I need.  I don't need VI or Emacs to do that.

Now if I am stuck with a machine that won't boot into GUI then I use PICO or even the MC editor.

---

### Post by ibutho on 2009-07-31
I mainly use G/VIM, but I compiled Emacs 23.1.1 from source and its pretty cool. I like the support for anti-aliased fonts and in the past this is one thing that put me off Emacs.

---

### Post by jpkotta on 2009-08-01
> **lykwydchykyn said:**
> Is the final 23 version much different from the snapshot in the Jaunty repos?

Probably not much different at all, but you can get the latest here: [https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

---

