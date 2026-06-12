---
title: "Terminal problem, what to do?"
date: 2016-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by peter240 on 2016-03-27
[ATTACH=CONFIG]268010[/ATTACH]

---

### Post by TheFu on 2016-03-27
Running any GUI program with sudo is dangerous for a few reasons.  You probably need/want to run it as **sudo -H nautilus**, if you must do this. Check the manpage for details.  Long-time Linux users have been discussing this issue for years and years.  My answer is the simple - don't run GUI programs with sudo or root.  When an edit is needed with elevated credentials, use "sudoedit". That is safe.  All other uses really aren't necessary when a good understanding of file and directory permissions is understood.

I don't recognize that other language, but it seems that network shares authenticated by a different userid are part of the problem.

In the meantime, you can create a new userid, login as that one and run nautilus without sudo.

Anyway - hope this helps.

---

### Post by grahammechanical on 2016-03-27
What you are seeing are common error messages that always appear when we  launch Nautilus from a terminal. I have been seeing stuff like that for  years.

> graham@sdb7-Dev:~$ sudo -H nautilus
[sudo] password for graham: 

(nautilus:3784):  Gtk-WARNING **: Failed to register client:  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files

** (nautilus:3784): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned  error 255: net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus still loads and is usable.

Regards

---

