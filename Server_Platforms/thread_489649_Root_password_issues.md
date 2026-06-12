---
title: "Root password issues"
date: 2007-07-01
forum: Server Platforms
---

### Post by notaloafer on 2007-07-01
Whenever I try to change my root's password it always stays the same. its very strange.
In gnome, I can use users & groups to change the password and it works for gnome login. However whenever I use sudo in terminal, it won't accept this new password and makes me use my old one.

How do I change the root password for all instances? I'm trying to secure this server for web launch.

---

### Post by darkog on 2007-07-01
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_root_user.2Fmain_user_password_if_forgotten](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_root_user.2Fmain_user_password_if_forgotten)

---

### Post by tillo on 2007-07-01
When you launch sudo, it doesn't ask for the root password, but for the user one. If you don't want sudo to allow your normal user to launch root commands with the user password (I do not suggest you to do that, it's beter to modify your password too), just use "su -" and deactivate sudo running "visudo" and modifying the correct line. "man" and "google" are your best friends on that.

---

