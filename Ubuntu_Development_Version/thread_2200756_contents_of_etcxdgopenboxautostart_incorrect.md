---
title: "contents of /etc/xdg/openbox/autostart incorrect?"
date: 2014-01-20
forum: Ubuntu Development Version
---

### Post by vasa1 on 2014-01-20
Can someone please post the contents of that file if you haven't changed it?

In 13.10, there's a bit that goes like this:

```

# If you want to use XFCE config tools...
#
#xfce-mcs-manager &
```
I feel that "xfce-mcs-manager" is wrong.

---

### Post by kansasnoob on 2014-01-20
From Trusty:

```
#
# These things are run when an Openbox X Session is started.
# You may place a similar script in $HOME/.config/openbox/autostart
# to run user-specific things.
#

# If you want to use GNOME config tools...
#
#if test -x /usr/lib/i386-linux-gnu/gnome-settings-daemon >/dev/null; then
#  /usr/lib/i386-linux-gnu/gnome-settings-daemon &
#elif which gnome-settings-daemon >/dev/null 2>&1; then
#  gnome-settings-daemon &
#fi

# If you want to use XFCE config tools...
#
#xfce-mcs-manager &

```

---

### Post by vasa1 on 2014-01-21
@kansasnoob, thanks for posting. I'll ask someone (?) to fix that.

---

