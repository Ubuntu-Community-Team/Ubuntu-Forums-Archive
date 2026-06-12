---
title: "LTSP Gnome Hangs on Logout"
date: 2007-06-21
forum: Server Platforms
---

### Post by dccollie on 2007-06-21
I've setup a LTSP server with Feisty by installing the ltsp-server-standalone package.  I have everything setup and working with two test machines configured as thin clients.  However, whenever a user tries to logout it hangs before completing the logout process.  The system is not hard locked and X can be killed via 'ctrl-alt-backspace'.  

The culprit appears to be dbus-launch because when I manually kill it the logout will continue as normal and return to the LDM prompt.  Other running processes include gconfd, xscreensaver, and dbus-daemon.  I've checked through the logs and nothing appears to be out of the ordinary.  I'm also able to login normally on the machine without any issues.

I'm at a loss at how to proceed debugging this.  Has anyone else experienced this problem?  Any suggestions on where to start debugging?

---

### Post by tshade on 2007-12-10
I also have the same problem with Gutsy 7.10 Edubuntu. No idea on how to debug it, but I think that maybe we'll be able the bug if we check some logs and send them to mainstream.

---

