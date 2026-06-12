---
title: "system-config-samba error on 8.04 server"
date: 2008-04-27
forum: Server Platforms
---

### Post by ginjabunny on 2008-04-27
I have just installed 8.04 server amd64 (to replace my 7.10 system), I included SMB when installing and then later installed xorg/gdm/gnome-core, most things seem to be fine, but then I installed system-config-samba and when I run it nothing appears, if I run as root in terminal I get the following error

Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 41, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 118, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 93, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file

Samba is working and I can access shares from Windows as I updated the config file manually, I checked the setup with Webmin and did the initial user setup from there. 

I am not sure if this is a known bug or is it something I have done or not done? It seems to be looking for /etc/libuser.conf.
I have installed everything using apt (except webmin) so any dependencies should have been met.

Any ideas?

---

### Post by skathrein on 2008-04-27
System-Config-Samba is also crashing for me every time I try to run it.  I've tried to reinstall both it and samba itself but it doesn't help.  I'd like to if anyone else has had this problem.
Thanks.

---

### Post by skathrein on 2008-04-27
Check out [this thread]("http://ubuntuforums.org/showthread.php?p=4818637&posted=1#post4818637").
The following command worked for me (thanks to cb951303):
```
sudo touch /etc/libuser.conf
```

---

### Post by ginjabunny on 2008-04-28
thanks skathrein, that fixed it, a bit of sloppy programming, it should create it for you if not there.

---

