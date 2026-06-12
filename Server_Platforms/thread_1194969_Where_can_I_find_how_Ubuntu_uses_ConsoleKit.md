---
title: "Where can I find how Ubuntu uses ConsoleKit?"
date: 2009-06-23
forum: Server Platforms
---

### Post by Kenzo on 2009-06-23
I'm trying to get an FTP client to send files to a Proftpd server.  The client/user session logs in okay but is closed after the following error
Jun 17 21:52:48 server-desktop proftpd: pam_ck_connector(proftpd:session): cannot determine display-device
I found that GetDisplayDevice is a method in ConsoleKit. The user/ftp client doesn't have a display device or keyboard or mouse.
I'm trying to find out how to change the PAM or ConsoleKit to prevent it checking for a display device for the user.
I'm really in the dark because I don't have much experience using Linux and I keep running into dead ends. Its like putting 20,000 piece jigsaw puzzle together with no picture of the completed item.

Any help or suggestions would be much appreciated.

---

