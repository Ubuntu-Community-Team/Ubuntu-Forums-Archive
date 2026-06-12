---
title: "usp problems (background color &amp; location)"
date: 2007-01-13
forum: Ubuntu System Panel
---

### Post by lorre on 2007-01-13
Hi,

I just installed usp on my system and have the following 2 issues (see attached screenshot):

1. The location of the menu is not directly below the (top) panel but there's gap. Is it possible to change the vertical location of the menu? I am using beryl.

2. My usp has 2 background colors, is it possible to have only one? 

Is it possible to open the menu with the windows key on my keyboard? 

A very neat menu, thanks!

Anton

---

### Post by chanders on 2007-01-13
1. Set the offset value to what you need in usp config
2. Check use_custom_color and associated values in usp config
You can access usp config by right clicking on the applet and selecting preferences

Not possible to use the windows key yet.

:-)

---

### Post by lorre on 2007-01-13
Thanks for the quick reply.

I tried right clicking within the applet but it does not bring up a menu where I can select 'preferences'. It seems that in the applet the right mouse button has the same effect as the left button; e.g. if I select 'Applications, Games' and press my right mouse button it will show the games. I am using version 0.41-1.

In addition I installed USPConfig (0.71-1). I was able to use custom colors. However I could not change the location of the applet; I tried every value (offset value is not listed) but none seem to effect the location of the applet itself.

One other issue I am having with the menu is that it does not remember which panes are closed. I like to have only the applications pane open but when I reboot (or restart X) all panes are open again. 

Hope you can help me further and thanks so far.

Anton

---

### Post by DBO on 2007-01-13
on a related note it would be nice if USP would set the background color of those eventboxes that end up white to the packground color of the rest of the panel even under normal conditions.  The recent plugin always uses white for example...  I tried this but figuring out the background color reliably seems considerably more difficult than setting it...

---

### Post by ~LoKe on 2007-01-13
He means right click on the taskbar entry.

---

### Post by chanders on 2007-01-13
> **lorre said:**
> I am using version 0.41-1

You are using the wrong version of  USP to get those items. You need to be using 1.91 Alpha.

---

### Post by lorre on 2007-01-14
I installed v1.91. The location problem seems to be solved by default in this version. However the menu is completely empty only the titles 'User', 'Applications' and 'System Management' and 'Recent' are visible.

Before installing 1.91 I completely removed the ~/.usp directory instead of only the ./usp/plugins directory could that have something to do with it?

---

### Post by lorre on 2007-01-14
I've installed v 0.41 removed the plugins (none) and reinstalled 1.91. Now I have the applications and searchbox but 'System management' is still empty.

---

### Post by Malac on 2007-01-14
> **lorre said:**
> I've installed v 0.41 removed the plugins (none) and reinstalled 1.91. Now I have the applications and searchbox but 'System management' is still empty.
right click the applet button choose preferences and check that the heights/width values for each plugin are set to something as they may be set to 0.

---

### Post by lorre on 2007-01-14
> **Malac said:**
> right click the applet button choose preferences and check that the heights/width values for each plugin are set to something as they may be set to 0.

Thanks! That did the trick, the height was set to 1.

---

