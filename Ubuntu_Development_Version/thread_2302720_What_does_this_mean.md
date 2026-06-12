---
title: "What does this mean?"
date: 2015-11-12
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-11-12
Changed to Xenial. When updating, I get this > sys:1: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded. What does this mean? What is Soup here? 
Apt-get dist-upgrade works anyway.

---

### Post by tista on 2015-11-12
@Chanath,

It's the warning from pygobject. Pygobject now warns if gi codes didn't explicitly require a version before importing.
So we don't have to worry about it, Python apps would work properly, developers should take care of this warnings though...

Developers should add the version requirement before import GObject like this:
```
import gi
gi.require_version("Soup", "2.4")
gi.require_version("SoupGNOME", "2.4")
```

Regards.
Tista

---

### Post by Chanath on 2015-11-14
Thanks, Tista

---

### Post by aturnwald on 2016-04-09
Hello, thank you, bcause since yesterday 8th Apr2016 on UBUNTU 16.04 after an update, the error occurs, and now I entered your 3 lines and it is fixed. 
Just when error came up open the file in /usr/share/appgrid/appdata/helpers.py and befor the import starts, enter the line above and all is fine.
Thank you very much, because I was really worried about that error, also I have no idea of the programming of python.

cu Toni

---

### Post by cariboo on 2016-05-10
Thread Closed.

---

