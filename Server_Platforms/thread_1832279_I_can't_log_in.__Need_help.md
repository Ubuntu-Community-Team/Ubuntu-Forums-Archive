---
title: "I can't log in.  Need help"
date: 2011-08-24
forum: Server Platforms
---

### Post by pepsifx357 on 2011-08-24
Hey guys, I was trying to connect my Ubuntu machine to an Active directory on our network for samba.  I was going by this tutorial:

[http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html](http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html)


I got to this part ```
net ads join -U Adminstrator@$FQDN_OF_YOUR_DOMAIN
```I got some kind of problem and restarted SSH.  

"kinit kdc reply did not match expectations while getting initial credentials"

Now I can't log in anymore.  At all, not even with Active Directory names.

I was looking online for default common-auth ect. files.  I guess I should have backed those up before I went messing with things.  So basically all authentication on my machine is screwed.  Anyone have any idea of what i could do?

Thanks

---

### Post by pepsifx357 on 2011-08-30
bump

---

### Post by Wayne_V on 2011-08-30
I would boot recovery mode and undo any changes ....

---

