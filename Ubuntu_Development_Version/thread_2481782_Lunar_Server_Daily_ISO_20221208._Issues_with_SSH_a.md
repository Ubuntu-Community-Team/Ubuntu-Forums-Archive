---
title: "Lunar Server Daily ISO 20221208. Issues with SSH and restarting services."
date: 2022-12-08
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2022-12-08
In the new Live Installer, selecting install openssh server... well, lol.


It gets installed. It is not enabled. Enabled and started manually after the install. I remember that as changed during 22.10. Port is now listening, but cannot connect to it via ssh. (???) 

EDIT: Is strange. Not a "no-path" problem. Connecting client just sits there until canceled, with no errors, but doesn't try to connect either. Nor does it time out.

On upgrading packages, has new restarting services, where desktop gives a text-based widget, where you can use the <spacebar> to select and has important services pre-selected. Server gets a list with Numbers (1. First Service, etc) where you type out the list, delimiting with a coma, with the last option as restart all, Indicates that you can restart a range. That does not work in selecting a range...

Filing bugs on openssh-server. Filing a bug on apt for the restarting services...

---

### Post by TheFu on 2022-12-08
I thought in 22.10, systemd was implementing the old xinetd method of starting services?  That's why the sshd wasn't already running. It should be spawned by systemd, on-demand.
[https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189](https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189) is hopefully clearer.
As usual, systemd making things easier ... er ... isn't.

---

### Post by MAFoElffen on 2022-12-08
Understood. But... openssh-server should at least be listening on port 22, which it wasn't listening at all. It wasn't until
```

[s]sudo systemctl enable ssh
sudo systemctl start ssh[/s]

```
And even though it says it is now enabled... Nothing. I can ping it. I can see the port listening. Nothing.

Now I tell you, it installed in no time at all, so I lose nothing in re-installing it, so... Wait one...

EDIT:
Reinstalled (fresh) and "this time" worked right out of the box... ???

---

