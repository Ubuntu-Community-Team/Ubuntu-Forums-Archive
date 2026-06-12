---
title: "xinetd and Xvnc4"
date: 2005-04-16
forum: Server Platforms
---

### Post by YorYor on 2005-04-16
Not sure if anyone else has tried this, but Xvnc4 (from the vnc4server package) insists on getting a password when connecting using vncviewer, even with the -securitytypes=none server_arg added.

Kept getting the message "no password set for VNC Auth"... removed vnc4server package and reverted to 3.3.3r7 and things were fine all over again.

Is that a bug with vnc4?

---

### Post by ron1n1 on 2005-04-16
Not sure if this will help, but  try running 'vncpasswd' as the user running vncserver, create a password, then start vncserver.

---

### Post by YorYor on 2005-04-19
[QUOTE=ron1n1]Not sure if this will help, but  try running 'vncpasswd' as the user running vncserver, create a password, then start vncserver.[/QUOTE]
 Tried that numerous times... still the same. It's wierd, really. With no change to password and any other setting, I uninstalled vnc4server (thus Xvnc points to the 3.3 version) and it's immediately fine.

---

### Post by quick_snack on 2005-05-07
[QUOTE=YorYor]Not sure if anyone else has tried this, but Xvnc4 (from the vnc4server package) insists on getting a password when connecting using vncviewer, even with the -securitytypes=none server_arg added.

Kept getting the message "no password set for VNC Auth"... removed vnc4server package and reverted to 3.3.3r7 and things were fine all over again.

Is that a bug with vnc4?[/QUOTE]
 After downloaded the vnc4server package I add the following to the inetd.conf:
```
5901 stream tcp nowait nobody /usr/bin/Xvnc4 Xvnc -inetd -query localhost -once securitytypes=none
```
I found out that the Xvnc in /usr/bin was the old one and Xvnc4 was present.
Then I altered the settings for remote login and enabled XDMCP ét voila I could log in remotely.

---

