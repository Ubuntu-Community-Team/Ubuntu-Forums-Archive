---
title: "Safely shutting down desktop from ssh, so apps can autosave."
date: 2010-08-23
forum: Security
---

### Post by kangarooks on 2010-08-23
Hi

This is **not** sudo shutdown -t now / sudo halt question :)

I've been trying for a while to figure out how to initate desktop shutdown while being logged in from remote to the desktop via ssh, in the same way that it gets shutdown via Gui Powerbutton Icon &#8594; Shutdown now...

With shutting down from gui, apps like open office writer can block shutting down when they have unsaved documents.

So far I only received advice to issue sudo halt, but this does not wait for all active desktop apps to save their stuff. ](*,)

I'm asking for a command that is issued by the Gui 'Powerbutton Icon &#8594; Shutdown now...' action.

Any help would be appreciated

Edit: using default gnome interface in plain ubuntu, desktop edition.

---

### Post by anomie on 2010-08-23
Assuming you're using GNOME...

Without actually accessing the DE, I haven't any idea. You might tinker with gnome-session-save(1) to see if it meets your needs.

---

### Post by Rubicon_82 on 2010-08-23
If you are only logged into the machine through an ssh shell, there is no way (that I know of) for GUI applications to present you with 'Save on Quit' dialogue boxes.  Rather than shutting the machine down, you could hibernate it.  Have a look at the '/usr/sbin/pm-hibernate' command, which is part of the pm-utils package.

---

### Post by kangarooks on 2010-08-23
Thanks for replies

@ anomie, thanks **gnome-session-save --logout** is almost what I'm after, if only there was a way to tell it to not go back to gdm but to halt machine afterwards...

@ Rubicon_82, hibernate is a no-go, since I have my home desktop pxebooted with root over NFS, so I don't have host-local swap

---

### Post by kangarooks on 2010-08-23
Whoa...

It was painful, but I managed to find the secret sauce:

```
DISPLAY=:0.0 dbus-send --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.RequestShutdown
```

It will cause the same behavior when logged in from ssh to a desktop, as when regular way - pressed **ó &#8594; Shut Down... &#8594; Shut Down** in the gui on the machine itself.

At times like this I feel the power of linux :P

:lolflag:

Thanks again for replies, they kinda lead me into that solution :)

---

