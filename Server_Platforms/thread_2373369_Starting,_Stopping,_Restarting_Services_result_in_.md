---
title: "Starting, Stopping, Restarting Services result in authentication from org.freedeskto"
date: 2017-10-05
forum: Server Platforms
---

### Post by ulrichkenneth on 2017-10-05
All, 

I just did a fresh clean install of Ubuntu Server 16.04 on my server.

I notice that when I go to start, stop, or restart a service I get the following.

[kenneth@server ~]$ systemctl stop some-daemon.service
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to manage system services or units.
Authenticating as: kenneth
Password: 

Now my question is, why is the server reaching out and getting authentication from org.freedesktop.systemd1.manage-units? Can I stop/uninstall this feature? 

I've done a little digging and found that it is something like polkit, but I can't find a clear definition of what that is. 

I don't want to add a username to the server for this org.freedesktop.systemd1.manage-units not to mirror the usernames on my server and end up locking me out.

---

### Post by wildmanne39 on 2017-10-05
*Thread moved to **Server Platforms for a better fit**.*

---

### Post by Doug S on 2017-10-05
> **ulrichkenneth said:**
> Now my question is, why is the server reaching out and getting authentication from org.freedesktop.systemd1.manage-units?
It isn't. It is just asking for super user authentication to execute the command. If you use "sudo" it will not ask for additional authentication.

Examples:

```
doug@s15:~$ [COLOR="#FF0000"]systemctl stop mysql.service[/COLOR]
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to stop 'mysql.service'.
Authenticating as: Doug Smythies,,, (doug)
Password:
==== AUTHENTICATION COMPLETE ===
```

```
doug@s15:~$ [COLOR="#FF0000"]sudo systemctl stop mysql.service[/COLOR]
[sudo] password for doug:
doug@s15:~$
```

---

### Post by ulrichkenneth on 2017-10-06
> **Doug S said:**
> It isn't. It is just asking for super user authentication to execute the command. If you use "sudo" it will not ask for additional authentication.

Examples:

```
doug@s15:~$ [COLOR=#FF0000]systemctl stop mysql.service[/COLOR]
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to stop 'mysql.service'.
Authenticating as: Doug Smythies,,, (doug)
Password:
==== AUTHENTICATION COMPLETE ===
```

```
doug@s15:~$ [COLOR=#FF0000]sudo systemctl stop mysql.service[/COLOR]
[sudo] password for doug:
doug@s15:~$
```

I feel like this is a security issue. Like if someone knows my password, they can just do it without needing sudo.

 Is there a way I can disable/uninstall this function?

---

### Post by Doug S on 2017-10-06
> **ulrichkenneth said:**
> I feel like this is a security issue. Like if someone knows my password, they can just do it without needing sudo.

 Is there a way I can disable/uninstall this function?Well, I also was running tcpdump when I did the stuff for my reply, and there was no external communication.
These commands are fairly fundamental, so I don't think you can disable them, nor should you. Just always use sudo so that the command itself is always run as root.

---

