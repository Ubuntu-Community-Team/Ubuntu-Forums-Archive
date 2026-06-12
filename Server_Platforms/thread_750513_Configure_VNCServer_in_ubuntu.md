---
title: "Configure VNCServer in ubuntu"
date: 2008-04-09
forum: Server Platforms
---

### Post by andguent on 2008-04-09
Keep in mind that any valid user on the server should be able to SSH in using PuTTY from a Windows box and have full access to emacs and gcc. That way you have the power of using command line functions and not be limited by a graphical interface.

If you are wanting to use something more than emacs and gcc, one option is to experiment with x11vnc. I'm not sure how well you could initiate multiple GUI sessions from remote, but I'm sure it is possible. 

The easiest way to get the ball rolling is log into gnome at the monitor as the user, and then putty in as them and start x11vnc. I believe it will automatically try to link the console user session with the graphical session.

If that doesn't get what you need, keep searching. There definitely is someone out there that has it working.

---

