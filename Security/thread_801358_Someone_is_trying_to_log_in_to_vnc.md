---
title: "Someone is trying to log in to vnc"
date: 2008-05-20
forum: Security
---

### Post by gardara on 2008-05-20
Today I have been been getting popups from vnc, with misc IP's trying to connect to my laptop...

What I suspect is that someone has been scanning my IP range and checking if someone has port 5900 open... Or else I have no idea why my computer is under attack...

Thank god I have my vnc both protected with password and that I have to confirm the access from the desktop of my laptop....
But since I get this popup window to confirm the access to my desktop, then doesn't that mean the user has made it past my password? :confused:

Has anyone else been experiencing this?

Here is a screenshot of one of many popups I have gotten...

[IMG]http://img161.imageshack.us/img161/5518/screenshotsz5.png[/IMG]

---

### Post by Monicker on 2008-05-20
I regularly see attempts to connect to the default vnc port in my router logs.  It happens for every remote control app available.

I have no idea if that message means they authenticated successfully though.


EDIT:  I just tested, connecting from my desktop to my laptop.  I only got the popup you show if I enter the correct password.  If I enter a wrong password, I just get an authentication error from vncviewer, and no popup.

---

### Post by movieman on 2008-05-20
Leaving VNC open to the Internet is brave. The best solution is to restrict it to local connections only and use SSH port-forwarding to connect from a remote system.

Assuming you have secure SSH keys, of course...

---

