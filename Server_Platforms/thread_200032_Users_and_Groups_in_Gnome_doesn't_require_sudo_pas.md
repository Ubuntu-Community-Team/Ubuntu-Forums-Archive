---
title: "Users and Groups in Gnome doesn't require sudo password"
date: 2006-06-19
forum: Server Platforms
---

### Post by JeffreyRatcliffe on 2006-06-19
Users and Groups in Gnome doesn't require a sudo password.

This strikes me as not secure, going on downright dangerous. Especially as the Kubuntu equivalent and adduser seem to (according to [https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")).

Any opinions on this?

Jeff

---

### Post by Joeb on 2006-06-19
Are you sure you weren't in an application that required the administrator password prior to the User Group applet?  gksu (which is called to launch users-admin) will remember the password for several minutes to keep you from having to enter it multiple times (same with sudo when using the command line).

---

### Post by JeffreyRatcliffe on 2006-06-20
I've just tried again and this time I DID have to enter the password. Could have sworn I it wasn't that soon after using Synaptic last time... :-?

Thanks. :-)

---

