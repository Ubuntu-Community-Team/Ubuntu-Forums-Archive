---
title: "pxelinux.0 error: not a valid image"
date: 2010-10-22
forum: Server Platforms
---

### Post by npinhao on 2010-10-22
I'm trying to install a ltsp server with Maverick 10.10 to use ThinCan DBE61C thin clients.
I've done everything "by the book" but I get the following message:

Loading <address...>/ltsp/i386/pxelinux.0 error: not a valid image

and from that the thin client keeps repeating...

What should I do to diagnose (and solve) the problem?

Thanks

---

### Post by npinhao on 2010-10-28
Just addind some more information:
The dhcp server configuration (the dhcp server is a Cisco server but the  ltsp server is a different machine) file includes the lines:
...
bootfile /ltsp/i386/pxelinux.0
next-server 10.10.13.9 
option 17 ascii "/opt/ltsp/i386"
...
I think everything is OK whith these lines and the problem is with the Ubuntu /pxelinux file and/or the DBE61C client, but if anyone finds an error...

---

### Post by npinhao on 2010-10-28
I have asked the same question (see bellow) on the Artec Group support (the producers of Thincan DBE61C) but until now I got no answer...

2nd Email to Artec support:
"A few days ago I asked your help with a serious error with your DBE61C and Ubuntu (10.10).
The problem is that the DBE61C is unable to load the pxelinux.0 image and returns the message:
"pxelinux.0 error: not a valid image"

Unfortunately your 5 business days have already passed without an answer.
Should I conclude that you are no longer supporting ThinCan products?"

---

