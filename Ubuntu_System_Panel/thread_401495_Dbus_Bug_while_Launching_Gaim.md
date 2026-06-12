---
title: "Dbus Bug while Launching Gaim"
date: 2007-04-04
forum: Ubuntu System Panel
---

### Post by PWill on 2007-04-04
When I launch Gaim from USP, it gives me the error
"Gaim's D-BUS server is not running for the reason listed below

Failed to get connection: Failed to connect to socket /tmp/dbus-27gvLAW1E0: Connection refused"

This does not happen with the Gnome System Panel, or when running from the terminal, or when running from the Gnome Run Dialog; only when using USP.

It's very strange, and the Dbus plugin is important in Gaim for me.
This has been happening for a while now, but I just found out it was a problem in USP. I updated to the latest SVN, and it still occurs.

---

### Post by Malac on 2007-04-04
> **PWill said:**
> When I launch Gaim from USP, it gives me the error
"Gaim's D-BUS server is not running for the reason listed below

Failed to get connection: Failed to connect to socket /tmp/dbus-27gvLAW1E0: Connection refused"

This does not happen with the Gnome System Panel, or when running from the terminal, or when running from the Gnome Run Dialog; only when using USP.

It's very strange, and the Dbus plugin is important in Gaim for me.
This has been happening for a while now, but I just found out it was a problem in USP. I updated to the latest SVN, and it still occurs.
Is this from Favourites or the All Applications tab, if it is in All Applications can you try adding it to Favourites and seeing if it launches from there.
Can you attach the actual .desktop file and I'll see what I can do.
I don't use gaim so I'm operating blind as it were.

---

### Post by PWill on 2007-04-04
It happens when in favorites and when launched from the regular list.
I have tried modifying the gaim.desktop file already. I removed everything that I didn't need, such as translations.
I also made it run /usr/bin/gaim instead of gaim, even though I don't have another "gaim" in my $PATH. The .desktop now reads

```
[Desktop Entry]
Encoding=UTF-8
Name=Gaim Internet Messenger
GenericName=Internet Messenger
Categories:Network;
Exec=/usr/bin/gaim
Icon=gaim.png

```

---

