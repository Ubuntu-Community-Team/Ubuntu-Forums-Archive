---
title: "Wine &quot;Program Files&quot; submenu in applications"
date: 2010-06-13
forum: Wine
---

### Post by mirwanda on 2010-06-13
Hi everybody,

I accidentally deleted Wine "Program Files" submenu in "Applications" using Main menu editor.

how can I get it back?
uninstall and reinstall wont help.

any ideas?

---

### Post by cogadh on 2010-06-13
Go to /home/.config/menu and open the .menu file with your text editor. Find the entry that looks something like this:
```
<Name>wine-Programs</Name>
</Deleted>
<Menu>
```
Remove the "</Deleted>" line, save the file and you should be all set. You may have to log out and back in to see any changes.

---

### Post by mirwanda on 2010-06-13
Thanks cogadh, it works like a charm :)
I don't even need to logout.

---

