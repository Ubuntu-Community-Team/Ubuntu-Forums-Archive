---
title: "firmware version"
date: 2009-09-25
forum: Server Platforms
---

### Post by ub007 on 2009-09-25
I'm trying to find out the 'firmware revision' for my backpane ( backpane connected to the hard drives/raid set Which command would possibly fetch me that info??

Cheers
David:confused:

---

### Post by trundlenut on 2009-09-25
What is the server?  Different manufacturers have different tools available. Dell for example have OMSA which gives you all sorts of information on the hardware including firmware versions and with some effort can be installed on a Dell server running Ubuntu, you can either check it through a web interface or CLI.  I believe there are similar tools from other manufacturers.

The other way would be to watch the information that pops up on the screen while the machine boots, assuming you have a monitor attached of course.

---

### Post by ub007 on 2009-09-25
What i'm after is to get that info without having to rely on any manufacturer specific utilities...by querying the hardware using simple linux commands.....lspci,/proc values...those sorta stuff.....Any ideas?:popcorn:

---

