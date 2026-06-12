---
title: "SHUTDOWN DELAY TIME - How to change it?"
date: 2015-01-18
forum: Ubuntu/Debian BASED
---

### Post by ttiihone on 2015-01-18
Oh, PLEASE help me! I have Linux debian 7.7.0 i386-amd64 underVBox 4.3.20 and here is the problem:

When I open the menu from Linux's top-right corner and click SHUT DOWN..., it shows the dialog box with choices, and that Linux guest will automatically shutdown after **60 seconds **and [U]I need to change that delay value to 3 seconds. I don't want to - and I will not re-click the Shut Down -button on the shown dialog - and that's it. Period. ;)

By Googling I found these "instructions" for UBUNTU:

None of this worked on my 13.04 system. In the end I re-compiled gnome-sessiongsm_shell.c and gsm_logout_dialog.c change #define AUTOMATIC_ACTION_TIMEOUT from 60 to 5

I'm new to Linux and I don't understand anything about this, so I need your guys' help!

Here are my questions:

[LIST=1]
[*]What is a GNOME-SESSION? Or GNOME-SESSION-MANAGER?
[*]Do I need to INSTALL it?
[*]Do I need to DOWNLOAD it? And from WHERE
[*]HOW do I install it?
[*]How do I RECOMPILE it?
[*]Where are the files gsm_shell.c and gsm_logout_dialog.c located?
[/LIST]

Please try to bear my ignorance and try to advice me like I was a 6-year old retard kid. :p I've had enough of unspecific instructions that only make everybody mad.

Thank You all in advance!
______________________________
// Tommi Tiihonen //

---

### Post by howefield on 2015-01-18
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

