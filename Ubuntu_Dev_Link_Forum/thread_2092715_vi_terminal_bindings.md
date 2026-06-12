---
title: "vi terminal bindings"
date: 2012-12-08
forum: Ubuntu Dev Link Forum
---

### Post by linux_noob0 on 2012-12-08
I'm using "set -o vi" in bash to use vi bindings.
Is there a way to remap some other key to <Esc>, it's a real pain.
.vimrc doesn't apply as it seems to be 'regular vi', I've tried .exrc, but it doesn't work.. Anyone? Thanks :)

---

### Post by japadamaray on 2012-12-08
You can do it in bash like this:
```
bind -m vi-insert [:vi-movement-mode
```
This would bind it to the **[** key.

You could also rebind Caps Lock to Escape. This can be done in the keyboard layout manager ([http://www.jveweb.net/en/archives/2010/11/making-better-use-of-the-caps-lock-key-in-linux.html#jveweb_en_017_01](http://www.jveweb.net/en/archives/2010/11/making-better-use-of-the-caps-lock-key-in-linux.html#jveweb_en_017_01)), or with:
```
xmodmap -e "clear Lock" && xmodmap -e "keycode 66 = Escape"
```

---

