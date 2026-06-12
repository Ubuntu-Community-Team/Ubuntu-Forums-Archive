---
title: "Restrict System Settings Option"
date: 2013-01-31
forum: Security
---

### Post by lingpanda on 2013-01-31
Anyway to remove a standard users ability to access system settings from the gear icon in Ubuntu 12.04LTS? Only want the Administrator or root to have access. At the very least require a password to access. Thanks.

---

### Post by Frogs Hair on 2013-02-03
You may want to start at the link.[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by sudodus on 2013-02-03
If you give that particular user the appropriate permissions (for example ***desktop user***) [s]he won't be able to do change any system settings, only change the own user's settings like background image font size etc, and edit the own .bashrc file to add aliases etc.

You can create user accounts, give and modify the permissions etc with the program
```
users-admin
```
which has different names in the GUI depending on the language selection.

---

### Post by Stonecold1995 on 2013-02-05
All System Settings is is an application which makes it easy to change configuration files in /home, it doesn't really change settings that affect the whole system.  If you somehow restricted access to the GUI, people would still be able to change the configuration files manually by editing them in /home.

Any options that require root access in System Settings ARE blocked for other users, because System Settings itself doesn't run with the correct permissions to edit root-owned files.  The sections which require higher permissions should look something like this (maybe different for you because I'm using KDE):

[img]http://www.pictureshack.us/images/80641_apply.png[/img]

They key means that you will need to enter the sudo password to apply the changes, and that can be restricted as Frogs Hair stated above.

---

