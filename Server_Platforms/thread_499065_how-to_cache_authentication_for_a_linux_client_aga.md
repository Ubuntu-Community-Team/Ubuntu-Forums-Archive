---
title: "how-to cache authentication for a linux client against a AD server"
date: 2007-07-12
forum: Server Platforms
---

### Post by eradan on 2007-07-12
Hello,

I'm trying to cache the authentication credentials of a Linux user (using Feisty Fawn).
The authentication is against an Active Directory server. 
I've managed to add the client to the domain and everything is ok when the network is up.

Now, I would like to authenticate the user even when the network is down, for his ticket is still valid. In this way I can use a laptop even when the network is down or when the user is far from office.

I followed this how-to:

[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

I think I've made no errors but any time I try to authenticate when the network is down I receive this error in /var/log/auth.log:

Jul 12 10:57:43 kllinux00 gdm[5174]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=kl1034
Jul 12 10:57:53 kllinux00 pam_winbind[5174]: request failed: NT_STATUS_IO_TIMEOUT, PAM error was System error (4), NT error was N
T_STATUS_IO_TIMEOUT
Jul 12 10:57:53 kllinux00 pam_winbind[5174]: internal module error (retval = 4, user = `kl1034')
Jul 12 10:57:56 kllinux00 gdm[5174]: Couldn't authenticate user

Any idea?
Help would be *really*, *really* appreciated! 
Thanks,
Ivan

---

### Post by rickyjones on 2007-07-12
I'm interested in this as well if anyone knows of a way to get it working. :)

Thanks,

-Richard

---

### Post by jallison on 2007-07-12
I agree this would be very usefule. It could be similar to the way Apple does it with OS X. They have a check box labeled "Create mobile account at login" this in turn allows laptop users to access their systems when they are away from the office. I am sure we could do this using PAM and a stored Kerberos ticket...

---

### Post by eradan on 2007-07-13
Yeah jallison,
that's the idea!

I installed pam_ccreds but something went wrong...

---

