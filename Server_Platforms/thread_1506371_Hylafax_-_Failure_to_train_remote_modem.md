---
title: "Hylafax - Failure to train remote modem"
date: 2010-06-10
forum: Server Platforms
---

### Post by rogtek on 2010-06-10
Hello everyone!

I am trying to setup HylaFax server on Ubuntu 10.04 Server with an external COM Rockwell modem, but no success yet:confused:

Everything works fine except when I try to send fax. I get an error saying: Failure to train remote modem at 2400 bps or minimum speed.

I have searched Hylafax mailing lists but no luck.

Does anyone had the same problem? Any ideas to solve it?

PS: My setup is with Class 1 modem.

---

### Post by robots.jpg on 2010-06-11
Have you tested it with a different modem, or sending to different destinations?  Post the connection log if you can.

I've only used US Robotics and Multitech modems with HylaFAX, but I had similar problems receiving faxes from one specific location due to the quality of the connection.  Of course, the multi-function fax machines had no trouble.

---

