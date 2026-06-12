---
title: "LDAP = sudo breaks?"
date: 2006-10-06
forum: Server Platforms
---

### Post by Dalik on 2006-10-06
I have installed openLDAP and I also configured client auth (server and client are the same computer).
I am able to login via LDAP which is great, but when I had logged into my local user account I noticed I wasnt able to use any applications that required sudo authentication.

The update application failed to launch after I put in my password.
I tried to "sudo gedit" with my local user password (was working before the LDAP install) but this failed to launch.  

How can I allow sudo to grant me root rights when needed?
And or how can I grant a user in LDAP sudo access to update the system etc.

I ended up reinstalling ubuntu because I wasnt able to change anything as I locked myself out of root access.

Cheers.

---

### Post by bluefrog on 2006-10-06
you may have to change things in /etc/pam.d/common-* files
(that's what I have done myself)

Reinstalling was a bit too much in my mind as you could have entered ubuntu in recovery mode and edited files from console.

---

