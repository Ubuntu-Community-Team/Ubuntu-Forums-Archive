---
title: "unixODBC and PHP"
date: 2011-10-13
forum: Server Platforms
---

### Post by fresler on 2011-10-13
The version of unixODBC that's in the Ubuntu repository is 2.2.14 which has a bug in it that causes a segmentation fault when a field from a database query is null. 2.3 fixes this bug.  How can I get 2.3 installed?  I've tried the following:
[LIST]
Installed 2.3 from source. It seems my system is still using 2.2.14.
[/LIST]
[LIST]
Removed unixODBC (apt-get remove unixodbc). However, this also removes php5-odbc which I need.
[/LIST]
Can anyone help?

---

### Post by karlson on 2011-10-13
> **fresler said:**
> The version of unixODBC that's in the Ubuntu repository is 2.2.14 which has a bug in it that causes a segmentation fault when a field from a database query is null. 2.3 fixes this bug.  How can I get 2.3 installed?  I've tried the following:
[LIST]
Installed 2.3 from source. It seems my system is still using 2.2.14.
[/LIST]
[LIST]
Removed unixODBC (apt-get remove unixodbc). However, this also removes php5-odbc which I need.
[/LIST]
Can anyone help?

Have you tried installing php5-odbc from source?

If you want to remove unixodbc without removing php5-odbc I suggest using dpkg rather then apt-get, but be prepared that packages depending on the one you have removed may work correctly.

---

