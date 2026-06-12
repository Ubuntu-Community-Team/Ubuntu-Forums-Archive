---
title: "batch job to start/stop transmission-daemon"
date: 2010-03-11
forum: Server Platforms
---

### Post by Hathadar on 2010-03-11
I would like to be able to simply run a shortcut file or batch file in a windows os to start or stop my transmission-daemon.
I was thinking about using putty to auto login and execute a file using the -m switch.  A problem I am running into is that /etc/init.d/transmission-daemon stop
requires the use of sudo.
That would require entering a password which would be automated and insecure or would require manually typing int he password.

How may I accomplish my goal?

---

### Post by Hathadar on 2010-03-11
Some helpful folks on #ubuntu helped me get as creating a regular user account with sudo access to /etc/init.d/transmission-daemon.  The timeout for sudo access is set to -1 so I dont have to enter the password.
This works well when logging in via putty.
I want to do the same thing with plink so as to set it up as a windows shortcut.

When I attempt to send the command in plink, I get this error:

Access granted
Opened channel for session
Started a shell/command
 
sudo: no tty present and no askpass program specified
Server sent command exit status 1
Disconnected: All channels closed

How can I overcome this error?

---

