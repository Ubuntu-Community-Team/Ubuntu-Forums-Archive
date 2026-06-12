---
title: "Avahi and Netatalk"
date: 2010-09-14
forum: Server Platforms
---

### Post by Spoony_Man on 2010-09-14
I'll open by saying that I'm running Ubuntu Server 10.04

About a month ago I set up Netatalk and Avahi as a timemachine drive for my macbook... To start with everything was working great. However now I'm having trouble with the avahi-daemon at boot.

When I boot the server Avahi does not advertise Netatalk to my network, simply restarting the avahi-daemon fixes this immediately - however it is getting very irritating having to login to the server and restart the server everytime.

Some googling/searching here has suggested that the problem could be that Avahi is starting before Netatalk at boot - however I am yet to find out how to change the order in which they start... I have tried updating rc.d but to no avail...

Any help with this situation would be greatly appreciated.

---

