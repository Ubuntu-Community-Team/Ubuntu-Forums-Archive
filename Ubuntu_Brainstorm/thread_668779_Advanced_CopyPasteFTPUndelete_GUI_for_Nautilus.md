---
title: "Advanced Copy/Paste/FTP/Undelete GUI for Nautilus"
date: 2008-01-15
forum: Ubuntu Brainstorm
---

### Post by omegamormegil on 2008-01-15
I have an idea for a new graphical copy/paste interface, with some new features.  

Basically, when you right click, copy and then paste a file in Nautilus, the Copy File progress window would have a Pause and Resume button, along with an Advanced dropdown.  Multiple file copies would be qued up on the same window.  

The advanced options would include copying files across a network, or to an ftp site, and the ability to cap the transfer rate. Also, file movement/copying history would be available, and you could have an undo button with unlimited undos.  This could be extended to undo-ing file deletion, which would move the file from the trash back to where it had been.  

It could be called something like the "File Transfer Manager", and would be also be accessible from the Ubuntu Menus.  

I think this would be a great addition to Ubuntu!  I've always wanted to be able to click the non-existent Pause button on the Copy window.  It would also be helpful in keeping track of lost files after tidying up your home folder, as well as confirming that moved files arrived safely.  

Any thoughts?

---

### Post by BungaMan on 2008-01-16
try to suggest it at [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)

---

### Post by xlinuks on 2008-01-16
IMHO What you're requesting is pretty interesting and pretty difficult (especially the "file movement history with unlimited undos"), but some ideas wouldn't require too much work to come true, like the pause button.

---

### Post by zekopeko on 2008-01-16
here is something to read:

[http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/](http://blogs.gnome.org/alexl/2007/11/23/file-operations-in-nautilus-gio-and-adventures-in-the-land-of-policykit/)

watch the video.

---

### Post by scuzzell on 2008-02-09
[SuperCopier2]("http://download.chip.eu/en/SuperCopier2-v1.9-Beta_177535.html") is what I use on my Windows boxes. I would love to have the same features available in ubuntu.

---

### Post by 23meg on 2008-02-09
> 
Basically, when you right click, copy and then paste a file in Nautilus, the Copy File progress window would have a Pause and Resume button, along with an Advanced dropdown. Multiple file copies would be qued up on the same window.

The advanced options would include copying files across a network, or to an ftp site, and the ability to cap the transfer rate. Also, file movement/copying history would be available, and you could have an undo button with unlimited undos. This could be extended to undo-ing file deletion, which would move the file from the trash back to where it had been.

All these features except capping the transfer rate are made possible by and planned for the gvfs-enabled Nautilus. Multiple files are already queued in one window.

> It could be called something like the "File Transfer Manager", and would be also be accessible from the Ubuntu Menus. 

I don't think there's need for a separate manager. Nautilus is already the file manager; it should handle everything related to file operations without too much complication.

---

