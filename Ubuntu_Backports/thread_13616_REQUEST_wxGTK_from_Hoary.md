---
title: "REQUEST: wxGTK from Hoary"
date: 2005-02-01
forum: Ubuntu Backports
---

### Post by Quest-Master on 2005-02-01
Now, it seems the reason wxPython in Warty uses GTK1 is not because of it's compilition and packaging, but that of wxGTK's. 

I *am* extremely eager on getting wxPython/GTK to GTK2 so I can enjoy using it, so I am hoping this is the reason.

The wxGTK from Hoary (2.5. something) doesn't break anything either from what I've collected, and doesn't face the problems jdong had when trying to compile wxPython.

Also: wxGTK is wxWidgets for Linux, not a seperate toolkit or anything of the sort.

---

### Post by rufius on 2005-02-10
[QUOTE=Quest-Master]Now, it seems the reason wxPython in Warty uses GTK1 is not because of it's compilition and packaging, but that of wxGTK's. 

I *am* extremely eager on getting wxPython/GTK to GTK2 so I can enjoy using it, so I am hoping this is the reason.

The wxGTK from Hoary (2.5. something) doesn't break anything either from what I've collected, and doesn't face the problems jdong had when trying to compile wxPython.

Also: wxGTK is wxWidgets for Linux, not a seperate toolkit or anything of the sort.[/QUOTE]
 I'll look into the backport.

---

### Post by jdong on 2005-02-10
I'd be concerned about this new WxGTK breaking binary compatibility with the version in Warty. Can you provide some solid evidence that this problem wouldn't exist?

---

### Post by rufius on 2005-02-10
[QUOTE=jdong]I'd be concerned about this new WxGTK breaking binary compatibility with the version in Warty. Can you provide some solid evidence that this problem wouldn't exist?[/QUOTE]
 I did some research and currently you cannot concurrently install both wxGTK 2.4 and wxGTK 2.5 or else you'll break the system and until all such things are updated to a working condition that will be one backport that'll have to wait. I am building python 2.4 as a backport though just to note for any of you interested in playing with that :).

---

