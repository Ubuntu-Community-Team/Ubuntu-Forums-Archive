---
title: "samba as domain controller"
date: 2009-01-16
forum: Server Platforms
---

### Post by ryanfx on 2009-01-16
I followed this guide exactly to setup a samba windows domain controller.  I am having issues connecting to it from a Vista machine though.

[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)

When I give my correct credentials for the user "steve" on the linux box running the controller I receive the error:

The specific computer account could not be found.  Contact an administrator to verify the account is in the domain.  If the account has been deleted unjoin, reboot, and rejoin the domain.


however when I give it anything BUT the right password it says:

Logon failure: unknown username or bad password

so it has to be talking to the server.. it is resolving whether the password is correct or not and then fails.  Google yields nothing relevant that I can find.  Any information on this?  I'll gladly post up logs if you'd like to see any just let me know which ones.

---

### Post by cmnorton on 2009-01-18
Here are some links.

[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)
[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

---

