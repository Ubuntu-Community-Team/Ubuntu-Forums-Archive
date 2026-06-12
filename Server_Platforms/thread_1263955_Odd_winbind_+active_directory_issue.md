---
title: "Odd winbind +active directory issue"
date: 2009-09-11
forum: Server Platforms
---

### Post by kamsar on 2009-09-11
I've got a server set up to authenticate against a Windows 2008 active directory.

Originally I used the directions at [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) to set it up, and it was working.

Today it's failing. I've tried pretty much everything I can think of, and I think it may be an issue with Samba using the short domain name.

Using kinit works fine as long as I use the full domain name (foo.net) - I can get a ticket for any valid domain user, including users in a trusted domain. However, when Samba starts up this is in winbind's log:

ads_krb5_mk_req: krb5_get_credentials failed for DCNAME$@SHORTDOMAINNAME (Cannot resolve network address for KDC in requested realm)

Logically this would be a DNS resolution issue but it doesn't seem to be - I can ping SHORTDOMAINNAME, DCNAME.SHORTDOMAINNAME, the long domain name (shortdomainname.net), all fine.

Next I used krb5.conf to map a new realm called SHORTDOMAINNAME to the domain controller. This didn't work because the domain controller expects to be contacted with the full domain name.

So my question is this: is there a way I can make samba quit referring to my domain by the old pre-windows-2000 style short name? The samba docs around what options really exist for net ads join were more than a little incomplete that I found anyway.

---

