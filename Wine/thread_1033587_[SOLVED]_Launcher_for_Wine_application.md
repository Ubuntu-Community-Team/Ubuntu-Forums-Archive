---
title: "[SOLVED] Launcher for Wine application"
date: 2009-01-07
forum: Wine
---

### Post by PoopyTheJ on 2009-01-07
I have an application that runs flawlessly through wine when either choosing open with or double clicking in gnome. The problem is the need to navigate through a bunch of folders to find the application, this isn't a problem for me, but the rest of the employees in the organization aren't tech savvy enough to handle it. So I created a launcher to the application and when running the app through the launcher the application errors out. The problem is the application is a database being hosted on a windows server, when starting from the launcher I get a Z:\home\user\datasource.dbf does not exist error. The database is actually located at /media/applications/rest.of.path. How do I fix this?

---

### Post by Simian Man on 2009-01-07
I had similar problems and here is what I did to fix them.

Create a script with the following in it:
```

cd /wherever/the/program/is; wine name-of-program.exe

```

Then move that to somewhere in your PATH (like ~/bin) and add a menu entry to run this script.

---

### Post by PoopyTheJ on 2009-01-07
ok, thanks! Please forgive my ignorance but how do I create a script?

---

### Post by PoopyTheJ on 2009-01-07
got it, jfgi doh! Thanks!

---

