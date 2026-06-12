---
title: "Clipboard Gibberish in SWG"
date: 2010-02-12
forum: Wine
---

### Post by zami on 2010-02-12
In the game Star Wars Galaxies, I'm getting gibberish when copy'n'pasting.   Not just from Linux apps to the game, but from the in-game notepad to itself.

It looks like little boxes and a few random letters.

Curiously, copy'n'paste from say, Windows Notepad to Linux gEdit (and the reverse) works just fine.

Any clues what would cause this?

Could it be related to the built-in "middle mouse button pastes whatever is highlighted" tool of Gnome?  Can that option be disabled? 

[s]
I was going to give these Wine related clipboard options a try 
[http://www.witch.westfalen.de/Wine-HOWTO/wineclipboard.html](http://www.witch.westfalen.de/Wine-HOWTO/wineclipboard.html)
but I can't locate either file referenced - .winrc or wine.conf
Are these files I make and place myself?
[/s] edit: nevermind that idea - just realized that page is dated 2003. Heh.

Thanks for any input!

Ubuntu 9.10
Wine 1.1.31

-zami

---

### Post by asdfoo on 2010-03-12
> **zami said:**
> In the game Star Wars Galaxies, I'm getting gibberish when copy'n'pasting.   Not just from Linux apps to the game, but from the in-game notepad to itself.

It looks like little boxes and a few random letters.

Curiously, copy'n'paste from say, Windows Notepad to Linux gEdit (and the reverse) works just fine.

Any clues what would cause this?

Could it be related to the built-in "middle mouse button pastes whatever is highlighted" tool of Gnome?  Can that option be disabled? 

[s]
I was going to give these Wine related clipboard options a try 
[http://www.witch.westfalen.de/Wine-HOWTO/wineclipboard.html](http://www.witch.westfalen.de/Wine-HOWTO/wineclipboard.html)
but I can't locate either file referenced - .winrc or wine.conf
Are these files I make and place myself?
[/s] edit: nevermind that idea - just realized that page is dated 2003. Heh.

Thanks for any input!

Ubuntu 9.10
Wine 1.1.31

-zami

sounds like a bug in Wine, try upgrading to 1.1.40 if it still fails check the appdb and bugzilla (you may need to report a new bug)

---

