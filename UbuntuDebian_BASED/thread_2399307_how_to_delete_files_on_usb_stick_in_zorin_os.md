---
title: "how to delete files on usb stick in zorin os?"
date: 2018-08-23
forum: Ubuntu/Debian BASED
---

### Post by snails22 on 2018-08-23
title

---

### Post by sisco311 on 2018-08-23
elaborate

---

### Post by snails22 on 2018-08-23
i want to delete some files on my usb stick but when i highlight the files then right click there isn't an option to delete them and i can't move them to the trash can either

---

### Post by hrsetrdr on 2018-08-23
Which file manager are you using?

You can use the terminal, navigate to the usb drive's directory and remove the files that you wish.   Be careful using rm, be sure to type "rm --help" in terminal for usage and examples.

---

### Post by yancek on 2018-08-24
Do you just have data on the usb stick?
What filesystem type, Linux or a windows filesystem?
Since the usb is not part of your user /home directory, you will need admin/root permissions in most cases so use sudo.  Using sudo to open the file manager if that is what your prefer, you can highlight and use Shift/Delete to delete the highlighted files.  Make sure the only files highlighted are the ones you want to delete.

---

