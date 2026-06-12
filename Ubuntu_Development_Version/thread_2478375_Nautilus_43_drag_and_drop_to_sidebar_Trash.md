---
title: "Nautilus 43 drag and drop to sidebar Trash"
date: 2022-08-24
forum: Ubuntu Development Version
---

### Post by reviczky2 on 2022-08-24
With the nautilus update to version 43 the drag and drop of files into the sidebar Trash gives the following error:

Error while copying "[filename]".
There was an error copying the file into trash:///.
Operation not supported.

Right clicking on a file and selecting "Move to Trash" works however.

Not sure whether this also happens with Wayland, but the livecd image with X11 has the same error.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290916&stc=1[/IMG]

---

### Post by Claus7 on 2022-08-25
Hello,

I get a similar behaviour: Error while creating to test.txt. The target doesn't support symbolic links.

Regards!

---

### Post by reviczky2 on 2022-08-25
A temporary workaround is to hold the shift button while doing the drag an drop. An update of gtk4 with the fix for X11 will solve this.

---

### Post by jbicha on 2022-08-26
Do you have a specific gtk4 issue, merge request, or commit you can point us to?

---

### Post by reviczky2 on 2022-08-26
[https://gitlab.gnome.org/GNOME/gtk/-/merge_requests/4982](https://gitlab.gnome.org/GNOME/gtk/-/merge_requests/4982)

---

