---
title: "Server with GUI, can't get elevated privileges with Chrome Remote Desktop"
date: 2015-04-28
forum: Server Platforms
---

### Post by crono1412 on 2015-04-28
Hey all!

Not sure if this is the right place, but it seemed appropriate.  I've set up a home media server using ubuntu server and plex.  Initially I was going to try and run command line only, but, being somewhat of a noob, I ended up installing a desktop environment.  I use chrome remote desktop to connect, and here's where the problem comes in.  None of the desktop applications can get elevated privileges.  The dialog for the su password just doesn't appear.  This is the error software center gives me

```
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.794'}): org.debian.apt.install-or-remove-packages
```

This only occurs when connecting through remote desktop.  If I sit down physically at the machine and connect a monitor and log in, things function as they should.

I'm not sure if the problem is with linux configuration, chrome remote desktop, or a third thing.  I have another linux machine (running kubuntu desktop) which is not effected, so I'm pretty sure there's a configuration issue somewhere.

Can anyone help me get this sorted out?

EDIT:  Per the post [here]("http://askubuntu.com/questions/218961/software-cant-be-installed-or-removed-because-the-authentication-service-is-no"), trying to start polkit-gnome-authentication-agent-1 returns the following error

```
(polkit-gnome-authentication-agent-1:17295): polkit-gnome-1-WARNING **: Unable to determine the session we are in: No session for pid 17295
```

---

