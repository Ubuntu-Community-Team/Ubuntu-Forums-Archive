---
title: "LTSP - set clients to run KDE?"
date: 2006-08-01
forum: Server Platforms
---

### Post by OMRebel on 2006-08-01
I installed the KDE desktop on my Edubuntu server.  Now I want to be able to make my clients use KDE instead of Gnome.  How can I force this?  When the client boots up to the login screen, there is no session for the client to chose from.  I do have that showing up on the server though.  How can I do this?  Reason for this change is because I'm needing to run the KIOSK to lock the clients down.

---

### Post by fnjordy on 2006-08-02
dupe

---

### Post by fnjordy on 2006-08-02
You could the last steps of this on the server:

[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)


Or edit /etc/gdm/gdm.conf and update DefaultSession= to whatever KDE is, it should be obvious from the SessionDesktopDir line:

```
# This is a directory where .desktop files describing the sessions live.  It is
# really a PATH style variable since 2.4.4.2 to allow actual interoperability
# with KDM.  Note that <dmconfdir>/Sessions is there for backwards
# compatibility reasons with 2.4.4.x.
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop

```

---

