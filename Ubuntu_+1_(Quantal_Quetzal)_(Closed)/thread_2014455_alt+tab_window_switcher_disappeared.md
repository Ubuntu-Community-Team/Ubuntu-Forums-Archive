---
title: "alt+tab window switcher disappeared"
date: 2012-07-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by TDK800 on 2012-07-02
Switched to the non-unity window switcher that doesn't group windows together, but after some updates in 12.10 it stopped working and has disappeared from CompizConfig Settings Manager's "Window Management" section also. Any ideas what's going on?

---

### Post by jerrylamos on 2012-07-02
Ubuntu updates erratically set standard defaults such as Alt-Tab and Alt-F4 to "Disabked".

No clue why they decide to do that.  

Go into Systems Settings > Keyboaard > Shortcuts > Navigation > Switch Applications then press Alt-Tab

I think I've got that right.

And some haven't worked for a long long time, like Ctrl-Alt-Del is listed as logout.  Just tried it today and it did work. I used to use it all the time for shutdown.  

Cheers, Jerry

---

### Post by mc4man on 2012-07-02
> **TDK800 said:**
> Switched to the non-unity window switcher that doesn't group windows together, but after some updates in 12.10 it stopped working and has disappeared from CompizConfig Settings Manager's "Window Management" section also. Any ideas what's going on?
The plugins were repackaged so you'll need to install "compiz-plugins" package to get many previously supplied or installed with ccsm plugins

As far as enabling - you may find that your initial attempt will unset all compiz plugins so you might want to make note of what is enabled prior to doing so

This will give you a string of what you currently have

```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins


```

---

