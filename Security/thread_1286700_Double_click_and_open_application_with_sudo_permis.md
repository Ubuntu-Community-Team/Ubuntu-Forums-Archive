---
title: "Double click and open application with sudo permission"
date: 2009-10-09
forum: Security
---

### Post by blurboy on 2009-10-09
I have an application that can be opened in Terminal by entering the following command:
sudo ./MyApplication

The Terminal will then prompt me for my sudo password which I will need to enter manually.


Is there any way where I can just double click my application icon and run it directly with sudo permissions? Can I set it in the properties to automatically run it with sudo permissions which is something like setting "Run the program as an Administrator" in Windows?

---

### Post by Rich_Roast on 2009-10-09
You should be able to add "gksu" in front of whatever command it is using alacarte, if you're on Gnome, or directly edit the relevant .desktop file in ~/.local/share/applications/.

---

### Post by Rob_H on 2009-10-09
Are you trying to bypass the password check? You can do this by modifying /etc/sudoers. For example, if the command is "foo" and your username is "ray", you add a line like this:

```
ray ALL = NOPASSWD: /bin/foo
```

Couple of notes:

[LIST=1]
[*]You still need to prefix your command with sudo or gksu or kdesudo.
[*]You MUST use visudo to edit /etc/sudoers. Otherwise, you can break sudo completely!
[/LIST]

---

### Post by cdenley on 2009-10-09
If you want to create a "Run As Admin" option in the right-click menu:
```

sudo apt-get install nautilus-actions
nautilus-actions-config

```
[LIST]
[*]+Add
[*]Label: Run As Admin
[*]Icon: Execute
[*]Profiles>Main>Edit
[*]Path: /usr/bin/gksu
[*]Parameters: ./%f
[*]click "Conditions" Tab
[*]Filenames: *
[*]Mimetypes: application/x-executable ; application/x-shellscript
[*]OK
[*]OK
[*]Close
[/LIST]

log out of ubuntu, log back in

---

### Post by blurboy on 2009-10-09
> **cdenley said:**
> If you want to create a "Run As Admin" option in the right-click menu:
```

sudo apt-get install nautilus-actions
nautilus-actions-config

```
[LIST]
[*]+Add
[*]Label: Run As Admin
[*]Icon: Execute
[*]Profiles>Main>Edit
[*]Path: /usr/bin/gksu
[*]Parameters: ./%f
[*]click "Conditions" Tab
[*]Filenames: *
[*]Mimetypes: application/x-executable ; application/x-shellscript
[*]OK
[*]OK
[*]Close
[/LIST]

log out of ubuntu, log back in

followed ur detailed instructions.

after logging out and restarting the system, i dont see "Run As Admin" label when i right click an "application/x-exectuable" file

however the label did appear for "application/x-shellscript" .sh file

using ubuntu 9.04

---

