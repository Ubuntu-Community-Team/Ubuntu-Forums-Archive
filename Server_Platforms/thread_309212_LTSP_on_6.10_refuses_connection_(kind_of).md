---
title: "LTSP on 6.10 refuses connection (kind of)"
date: 2006-11-29
forum: Server Platforms
---

### Post by drave on 2006-11-29
I'm just getting started with LTSP and am having problems connecting.

with a user that i know can log on via SSH and having run ltsp-update-sshkeys

I get a logon screen, put in my details, screen goes black with wait cursor, then returns to the logon screen ??

auth.log shows that the password was accepted and a session (via pam_unix) was opened but thats it, i cant find anything in the logs that points to why it just returns to the login and doesnt give me a desktop

tia

Dave

---

### Post by RedBoot on 2006-12-12
I am having the exact same trouble. Anyone out there with info on getting 6.10 LTSP working.  It seems so close!

---

### Post by fnjordy on 2006-12-14
Enable root login on the thin client:
```
$ sudo vi /opt/ltsp/i386/etc/passwd
```
Remove the "x" from the root line:
```
root::0:0:root:/root:/bin/bash
```
On the client switch to VT1 (Ctrl + Alt + F1) and login as root, then try to SSH to the server.

Also try logging in as the user using the server as a desktop.

---

### Post by kihai on 2006-12-20
Have you tried to delete (or just rename) /home/username/.gnome2/session ?

---

