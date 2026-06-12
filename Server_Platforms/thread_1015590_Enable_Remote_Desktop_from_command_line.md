---
title: "Enable Remote Desktop from command line"
date: 2008-12-18
forum: Server Platforms
---

### Post by barry505 on 2008-12-18
I have a server running Ubuntu Server 8.10. I'm installing the Ubuntu desktop and would like to connect to the desktop remotely. I don't have a monitor or keyboard attached to the server. Is there a way of turning on Remote Desktop Sharing on this server using only the command line?

---

### Post by iponeverything on 2008-12-19
Run:
```

export DISPLAY=:0.0
/usr/lib/vino/vino-server
```

---

### Post by bluefrog on 2008-12-19
if you want remote desktop you will be obliged to log in automatically onto the server first.
/etc/gdm/gdm.conf
AutomaticLoginEnable=true
AutomaticLogin=your-user

invoke-rc.d gdm restart

**activate remote desktop**
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

disable prompt to authorize the connection
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false

**encode your password in base64 using a file and assign it**
echo password > file
base64 file
gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password result-of-passwd-encoding

**select the authentication method**
gconftool-2 -s -t list --list-type=string /desktop/gnome/remote_access/authentication_methods \[vnc\]

You should be able to connect to the remote desktop.

If you don't want to activate autologin then you should install vncserver.

---

