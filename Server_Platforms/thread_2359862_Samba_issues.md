---
title: "Samba issues"
date: 2017-04-28
forum: Server Platforms
---

### Post by nickjea222 on 2017-04-28
I've been trying to fix this problem for a couple days now and can't find any recent posts on this issue, all i need is a drive shared with the rest of the network, no password or anything, when i try to run Samba I get:

```

Traceback (most recent call last):  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

```

there appears to be very old bugs reported on this but there doesn't seem to be any solution.

---

### Post by SeijiSensei on 2017-04-28
Did you run system-config-samba with sudo?

---

### Post by wildmanne39 on 2017-04-28
*Thread moved to **Server Platforms**.*

---

### Post by nickjea222 on 2017-04-28
When i run it with sudo i get

```

(system-config-samba:3827): IBUS-WARNING **: The owner of /home/nick/.config/ibus/bus is not root!
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 121, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 97, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory



```

---

### Post by nickjea222 on 2017-04-28
I may have fixed it, I changed the drives mount location to mnt/ then ran 'sudo nautilus' and created the share that way, I'm able to connect to and modify the contents of the drive from a separate windows machine now, is there any kind of security issue with doing it this way, I'm on a private secured network

---

