---
title: "emacs custom keybindings"
date: 2009-07-16
forum: The Cafe
---

### Post by push_back on 2009-07-16
Hello anyone,
I'm having a weird problem, that may or may not have anything to do with using ubuntu.

I've defined some key bindings I want to use in my ~/.emacs, but they don't work.  More shockingly, emacs itself seems to think they should!
Here's my .emacs section of relevance: 

(global-set-key [M-p] 'previous-buffer)

when I enter the key combo (after saving & restarting emacs to make sure) it says:
M-p is undefined

when I enter the long command 'M-x previous-buffer', it says:
You can run the command `previous-buffer' with <M-p>

I'm confused.
Thanks for any input...

---

### Post by Barrucadu on 2009-07-16
Here you go :)
```
(global-set-key [?\M-p] 'previous-buffer)
```

M- and C- must be prefixed by a backslash. The question mark must be used after any spaces (and at the beginning). For example:
```
(global-set-key [?\C-x ?\C-u] 'undo)
(global-set-key [?\C-x ?g]    'goto-line)
```

---

### Post by push_back on 2009-07-16
huh.
Weird that I didn't find that anywhere else.  international online emacs consipracy?
But thanks, it works now.

---

### Post by Barrucadu on 2009-07-16
Could be, perhaps I just divulged knowledge which only senior emacsers should know without realising it :p

---

