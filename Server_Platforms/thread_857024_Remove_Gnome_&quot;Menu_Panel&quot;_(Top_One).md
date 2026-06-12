---
title: "Remove Gnome &quot;Menu Panel&quot; (Top One)"
date: 2008-07-12
forum: Server Platforms
---

### Post by Benismyhorse on 2008-07-12
Hi, just a quick question (I hope),
I want the top panel of gnome (Menu Panel) to be remove by default on everyones account, as it will not be needed.
If possible is there a command I could add to a Log on Script that would remove it.
Thanks

---

### Post by bluefrog on 2008-07-12
comment 3 lines in /usr/share/gnome/default.session

man default.session

---

### Post by Benismyhorse on 2008-07-12
Here is a copy of my default.session file what do I need to comment out?

# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=4
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3

Thanks

---

### Post by nadrimajstor on 2010-01-19
But if you still need some functionality from gnome-panel don't kill it, try this:
Start gconf-editor. Navigate to:
/apps/panel/general/toplevel_id_list
Go for Edit key and delete unwanted panel(s) 

But after session restart, they are restored.
/apps/panel/default_setup/toplevel_id_list
looks promising but not a complite solution... :(

---

