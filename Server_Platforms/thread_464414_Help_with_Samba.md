---
title: "Help with Samba"
date: 2007-06-04
forum: Server Platforms
---

### Post by Draugauth on 2007-06-04
Using Fiesty
Latest Samba from Synaptics

Able to see and browse network shares.

Unable to WRITE to the network shares.

Link to my smb.conf is
[http://members.cox.net/draugauth/smb.conf](http://members.cox.net/draugauth/smb.conf)

Any help would be GREATLY appreciated.

---

### Post by Andra on 2007-06-05
did you try
public = yes
or
valid users = ......
or
write list = .......

specify users or groups in "valid users" and "write list".

---

### Post by Draugauth on 2007-06-05
The Valid users worked.  THANK YOU very much.  Or as the Military says
Tango Victor Mike ;)

---

