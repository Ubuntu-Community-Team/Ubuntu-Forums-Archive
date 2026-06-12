---
title: "Gnome-terminal window closes after executing certain commands"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by Aesso on 2014-03-13
Greetings! A few days ago, after upgrading one of my machines to Trusty I now have this weird problem where if I open gnome-terminal and try to run ordinary commands such as **[FONT=courier new]ls[/FONT]**, the terminal window just closes. No error message, no segfault, just closes. This does not happen from a virtual console (Ctrl-Alt-F1, etc.). 

Here is all I have to do to make this happen:
[HR][/HR]1. Open a terminal (Ctrl-alt-T)
2. Type **[FONT=courier new]ls[/FONT]**, press enter

OR  try to use [FONT=courier new]**sudo**[/FONT] [*anything*]

Window closes almost immediately.
[HR][/HR]
I later had a thought and decided to install xfce4-terminal, then I ran gnome-terminal from within it and managed to capture this error message:

```
Vte-2.90:ERROR:/build/buildd/vte3-0.34.9/./src/vtestream-file.h:319:_file_write: assertion failed: (_file_isopen (f) || !len) 
``` 
Incidentally the xfce term does not crash. After doing a quick search, it looks a lot like [this old bug]("https://bugs.launchpad.net/ubuntu/+source/vte3/+bug/903401") from Precise, except in my case I can actually *open* the terminal window. I tried purging and reinstalling libvte3 but no go. I've been hoping that an update would come out and fix this problem, but I'm completely up to date at the moment. Anyone else having this issue? Any ideas?

---

### Post by el_sordo on 2014-08-14
Hi,

Check the permissions on the /tmp directory. It needs to have rwx as well as sticky bit turned on....chmod 1777 should do the trick.

---

### Post by oldos2er on 2014-08-17
Trusty was officially released this past April, so no longer qualifies as a development version. Closed.

---

