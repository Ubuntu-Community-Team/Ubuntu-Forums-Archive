---
title: "&quot;Authenticate&quot; hangs when changing password"
date: 2008-06-04
forum: Server Platforms
---

### Post by novalis112 on 2008-06-04
Greetings,

I have a somewhat obscure situation here, but I'll bet somebody knows exactly what's happening!  I have setup an Ubuntu 8.04 server from the alt CD using the LTSP option.  That more or less worked as expected out of the box, so my next step was to configure it to do user authentication from a Windows 2003 Active Directory server.  After several days and multiple different tutorials each claiming to achieve my goal, I have finally arrived at success!  Users may now log in to the LTSP server using their Windows Domain credentials, but if they use the "System->Preferences->About Me" application to change their password, it hangs when they click "Authenticate" (after entering their current password).  This only occurs for users who log in using domain accounts.  Users who already have local accounts on the LTSP server do not have this problem.  All users can change their passwords from the command line using kpasswd, so this issue is specific to the "About Me" application.

I'm sure I haven't given enough information about my current configuration, so hit me with your questions and I'll do my best!

---

