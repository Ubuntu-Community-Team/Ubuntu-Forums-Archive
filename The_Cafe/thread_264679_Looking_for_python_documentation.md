---
title: "Looking for python documentation"
date: 2006-09-25
forum: The Cafe
---

### Post by saracen on 2006-09-25
The disks-admin application that existed in Dapper and previously has been taken out of Gnome (and hence Edgy).  The reason being apparently is that it requires a rewrite using the new infrastructure used by upstream e.g. using hal to list devices.  Since this was the only method to mount filesystems using a GUI, it's quite a big loss of functionality for average users because now their only recourse is to manually edit the /etc/fstab file.

Seems like this would be quite easy to write using Python, PyGTK, and the python-dbus / python-hal bindings, at least to provide the basic functionality of mounting and unmounting filesystems.  So I looked around for some documentation on those bindings, but what I found was sparse and not too useful.  I'm wondering if anyone has experience with those bindings or if anyone knows where I can get some good documentation on the API's.

---

