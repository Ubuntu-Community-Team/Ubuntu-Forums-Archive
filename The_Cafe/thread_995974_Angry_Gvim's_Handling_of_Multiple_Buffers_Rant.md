---
title: "Angry Gvim's Handling of Multiple Buffers Rant"
date: 2008-11-28
forum: The Cafe
---

### Post by IshikawaNakano on 2008-11-28
The way GVim handles multiple files is very inflexible, time consuming, and frustrating.

You HAVE to look at all the buffers in a tab.

You can not move buffers from one tab to another. You have to close it in one tab and open in in another.

Tabs cannot be moved around once created.

If you open a quickfix menu in one tab you cant look at it from another tab.

If you open a quickfix and click on an error it doesn't move to the buffer with the file open in it or open a new buffer with that file. It closes the file you were working on and opens the one with the error. Then you have to reopen the file.

GVim should handle multiple buffers and tabs like Eclipse or Visual Studio. Each Tab can contain one buffer. That tab can then be moved to other groups of tabs where the tabs are "stacked" on top of each other. Groups can be resized, minimized, or detached from the main window. If you don't know what I mean just open eclipse and see how it works.

---

### Post by hessiess on 2008-11-28
What good is it posting on the Ubunt Linux support forum? Go complain to the developers of Vim ;)

Pearsonally I use Vim a lot, but vertually neaver use tabs, just splits.

---

