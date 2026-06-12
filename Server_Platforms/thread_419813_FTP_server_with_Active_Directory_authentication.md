---
title: "FTP server with Active Directory authentication"
date: 2007-04-23
forum: Server Platforms
---

### Post by Naatan on 2007-04-23
Hi, I was wondering if anyone would know of a way to make an ftp server on Linux authenticate over Active Directory (yes that's on winblows) 

I have done some research and testing myself and found a few ftp servers that should be able to authenticate over LDAP but AD doesn't really play by all of the LDAP rules and I didn't manage to get it working.

So is there anyone that knows of an FTP server that can be configured to do this?

By 'this' I mean assigning an OU in AD as the group with all the ftp users, when one of these users would connect he would connect into his own user directory..

Or something that works similar..

any reference at all is appreciated, thanks in advanced!

---

### Post by Naatan on 2007-04-25
bump

---

### Post by frodon on 2007-04-25
Proftpd can do it but for sure you will have to read some documentation to get it working but all the needed documentation is available though.
There's also a proftpd forum where you will get more accurate answers if you have some really specific questions :
[http://www.proftpd.org/](http://www.proftpd.org/)
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

---

### Post by Brazen on 2007-04-25
You are going to need to install Samba, attach it to the domain and then configure your ftp to use winbind authentication.  I _think_ that has something to do with the pam.d settings.  You'll want to look over the samba documenation to authenticating to a Windows domain.

---

### Post by garba on 2007-04-25
as long as your ftp server is PAM aware, you can configure PAM to use kerberos for authentication, then configure kerberos to use your win machine as auth server

---

### Post by commonplace on 2007-05-07
Are there any step-by-step guides for this? Everything I've found is outdated, or just hadn't worked. A few things seem like they've gotten me 'close' but nothing has actually gotten this working.

My setup is a Ubuntu 7.04 box running on a Windows 2000 Server Active Directory-based domain, and I want FTP access on the Ubuntu box authenticated via Active Directory. I don't really care how it's done, but I'd like it done, rather than duplicating all the users.

Anyone?

/Kevin

---

### Post by garba on 2007-05-07
what you want to achieve is very basic, all you need is take out the time to read a few howto's and you're all set, i know it would be nice to have things working out of the box on linux but alas, we're not there yet

anyway, i achieved that using wuftp on my linux box at the office and it works great, you need libkrb, libpam-krb, then configure /etc/krb5.conf and /etc/pam.d/wu-ftp and you're all set... if you don't want pam to get in the way you can look for some ftp servers natively supporting kerberos

hope this helps, regards, andre

---

