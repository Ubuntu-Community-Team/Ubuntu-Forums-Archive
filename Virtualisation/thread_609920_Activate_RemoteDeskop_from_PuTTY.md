---
title: "Activate RemoteDeskop from PuTTY"
date: 2007-11-11
forum: Virtualisation
---

### Post by MadKillerX on 2007-11-11
Hi...
I have a Ubuntu 6.06 server in France that I want to see with RealVNC Viewer.
But when I try to connect I get this message:
Unable to connect to host: Connection refused (10061)

But PuTTy and WinSCP works great, do I have to activate RemoteDeskop before I can connect with RealVNC, if that's it how do I do it with PuTTy.

Or if that isn't the case, what do I have to do to get connectet with RealVNC?

---

### Post by scorp123 on 2007-11-11
Of course there has to be VNC instance on the remote computer or else this will not work! :)  And also: the port has to be open on the firewall (if there is a firewall). Best would be to tunnel it through SSH.

As you seem to have SSH access to the computer in question I'd suggest you install the needed packages first and then go from there.

---

### Post by MadKillerX on 2007-11-11
Witch packages do I need to connect with VNC

---

### Post by eitama on 2007-11-12
You need vito.
Comes with the server edition,
i am not sure about the desktop one,
But to enable it, you must have a work area logged on,
and you must once allow it.

  Auto Login
    1. In GUI/VNC Choose System->Adminsitration>Login Window>Security Tab
    2. Mark Enable automatic login, And choose the user.
    3. Done.

Enable VNC >
1. System > Preferences > Remote Desktop
2. Mark the appropriate allow for your enviorment.

---

