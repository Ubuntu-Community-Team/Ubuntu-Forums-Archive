---
title: "[SOLVED] Wine disappeared"
date: 2009-01-04
forum: Wine
---

### Post by EnderEcho on 2009-01-04
So I completely removed Wine. Even from my menu because after I got ride of everything all the menus were still showing up. I wanted to start from scratch reinstalling WoW. Now I cant get it to show up on my menu again. I try and add item when editing the menu but I cant figure out how to do it.

I need help!

---

### Post by Meow27 on 2009-01-04
completely removed wine..... you mean the wine folder or the package?

(are you using wine 1.1.10? it had menu problems)

---

### Post by matteojg on 2009-01-05
Should you find that wine has disappeared from your apps. menu after the re-install, then try the following:

Places>Home Folder>Ctrl+H>.config>menus>applications.menu

Find this entry in the document:

<Menu>
<Name>wine-wine</Name>
<Deleted/>
</Menu>

Remove the <Deleted/> and save the document.

(see WineFAQ 6.27 [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ))

In the future try using the search bar to look for posts that already address your issue.

---

### Post by EnderEcho on 2009-01-07
That did it. Thanks!

---

