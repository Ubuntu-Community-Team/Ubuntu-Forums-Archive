---
title: "where are programs kept?"
date: 2005-05-15
forum: Repositories &amp; Backports
---

### Post by rjs on 2005-05-15
ok, so i download whatever my new program is (in this case irb), then what? i want to use it, but dont know where aptitude put it? Is there a standard place that programs live on linux, if so where is it?

thanks,
-rjs

---

### Post by nad on 2005-05-15
From your pull down menus, pick Applications->Run Application, type it in and go.

For documentation about a program, open a terminal window and issue the command: man irb (for example).

---

### Post by rjs on 2005-05-15
Thanks heaps, but i still wonder where apps are kept, and also how do i add them to the main menu?

-rjs

---

### Post by nad on 2005-05-15
Binaries and other executables are typically placed in; /bin,/sbin,/usr/bin,/usr/sbin,/usr/local,/usr/share,/usr/games and other distribution specific places.

At a command prompt, type: echo $PATH  to see where your path variable points.

As to adding items to your menus, from the drop down menus pick: Applications highlight any menu item and right click. Highlight 'Entire Menu'. You will be given an option to 'add item'.

This feature is and has been sometimes broken. It is not entirely stable yet as far as I know.

---

### Post by rjs on 2005-05-15
thanks
-rjs

---

