---
title: "Starting GDM without a monitor attached"
date: 2009-09-25
forum: Server Platforms
---

### Post by sherl0k on 2009-09-25
Hey guys,

I'm having a tad of trouble here. I have a cluster of Ubuntu servers, and they're all headless. While needing a GUI on them isn't really a requirement, it's nice to have for the lesser-experienced members on my crew as opposed to them all trying to struggle through the shell.

When I first set them up, I had a monitor attached, the desktop was loaded, and I could VNC into them. Now that they're totally headless, if they need to be rebooted for whatever reason they no longer load GDM upon boot because there's no monitor/keyboard/mouse attached. I can't get GDM to load remotely via SSH either, so I'm wondering if anyone here has a method to get GDM to load, even when there's input/output devices attached, just the network connection.

Thanks in advance for anyone's help.

---

### Post by black_shadow on 2009-09-25
Hello

You can get them to autologin when they reboot.

Mike

---

### Post by sherl0k on 2009-09-25
So just enable autologin via GDM and it'll boot to the desktop? I'll give it a shot, thanks.

---

### Post by sherl0k on 2009-09-25
No dice there, sorry :| I rebooted one of my headless servers and I can't VNC. I have to attach a monitor to it before it will load GDM.

---

### Post by cdenley on 2009-09-25
If you want to get GDM loaded without a monitor, it might help to post the log file from the failed X session.
```

cat /var/log/Xorg.0.log

```
However, you don't need GDM running in order to connect remotely. In fact, it is a waste of system resources.
[https://help.ubuntu.com/community/VNC/Servers#tightvncserver](https://help.ubuntu.com/community/VNC/Servers#tightvncserver)

You could also use X tunneling with ssh.
```

ssh -X user@server gnome-panel

```

---

