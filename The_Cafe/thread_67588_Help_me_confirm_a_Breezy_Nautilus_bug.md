---
title: "Help me confirm a Breezy Nautilus bug"
date: 2005-09-20
forum: The Cafe
---

### Post by jdong on 2005-09-20
I'm finding that Breezy's Nautilus has problems deleting weirdly named files, but the package maintainer doesn't seem to be able to reproduce it.

If you're running Breezy, I'd like for you to try out this procedure. It's absolutely harmless.



1) Go to your desktop

2) Right click, say Create Document->Empty File...

3) When it waits for a filename, type in "I - Am - Your - Worst - Nightmare" (no quotes, spaces between dashes)

4) Try to delete the file with the Delete key, and by right-clicking and Moving To Trash.

On my system, the delete key and the right-click menu do not do anything. Dragging to the trash can shows a "Cannot move to trash, permanently Delete?" message, and is able to permanently delete the file.


When you reply back, please include the following information:

1) Ubuntu Version (**BREEZY** only) -- specify the last time you've updated
2) Did it delete correctly?
3) What filesystem are you using where you created the file (ext3, reiserfs, etc)

---

### Post by dabear on 2005-09-20
1) Ubuntu version: Breezy, last updated september 20.
2) Yes, had no problem deleting the file. move to thrash worked fine too
3) ext3

---

### Post by jyank on 2005-09-20
1) Breezy, updated Sept. 20 about 20 minutes ago
2) Yep, both ways
3) ext3

---

### Post by jdong on 2005-09-20
fascinating... reiserfs issue. Time to follow-up on bug report. Also, time to switch to ext3 when building my new system later this week :)

---

