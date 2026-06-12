---
title: "disable shutdown for non sudoers"
date: 2005-12-08
forum: Server Platforms
---

### Post by moment on 2005-12-08
Hello,
How can I set my ubuntu server to shut down from Gnome only by sudoers? I know that in terminal it can only be done by root but in Gnome you can easliy halt the system and it doesn't ask for the root password.

cheers
Hamid

---

### Post by moment on 2005-12-17
Ok just in case anybody is interested to know:
Apparently there is no way to ask for the password if a user halts the system from gdm's gnome-panel. But you could disable this feature completely by turning off the "SystemMenu" variable in "/etc/gdm/gdm.conf":

```

SystemMenu=false
```

---

### Post by nagilum on 2005-12-18
Of course there's a way, enable the 'Secure actions menu' setting in the GUI-tool or add 'SecureSystemMenu=true' to /etc/gdm/gdm.conf (already in there, just uncomment). Then you'll be asked for a password when using shutdown or one of the other actions. IIRC it's the root password though, not sure if it works with sudoers.

---

### Post by moment on 2005-12-18
Yes that's partially true. But you would be still able to halt the system from the gnome-panel > System > Log out menu. This is very stupid IMO.

---

