---
title: "Upgraded to Netatalk 2.2 &amp; now PAM is pissed"
date: 2011-08-09
forum: Server Platforms
---

### Post by sdmike6 on 2011-08-09
I'm running Ubuntu 11.04 x64 
I upgraded to Netatalk 2.2 and I've hit a wall. 

I'm authenticating netatalk with an external LDAP server but for some reason pam is confused. 

Here's my output when I authenticate with the server:

[CODE
Aug 10 11:07:42 vault afpd[14400]: PAM (netatalk) illegal module type: %PAM-1.0
Aug 10 11:07:42 vault afpd[14400]: PAM (netatalk) no control flag supplied
Aug 10 11:07:42 vault afpd[14400]: PAM (netatalk) no module name supplied
Aug 10 11:07:42 vault afpd[14400]: PAM (netatalk) illegal module type: include
Aug 10 11:07:42 vault afpd[14400]: PAM pam_parse: expecting return value; [...common-session]
Aug 10 11:07:42 vault afpd[14400]: PAM (netatalk) no module name supplied
Aug 10 11:07:53 vault afpd[14405]: PAM (netatalk) illegal module type: %PAM-1.0
Aug 10 11:07:53 vault afpd[14405]: PAM (netatalk) no control flag supplied
Aug 10 11:07:53 vault afpd[14405]: PAM (netatalk) no module name supplied
Aug 10 11:07:53 vault afpd[14405]: PAM (netatalk) illegal module type: include
Aug 10 11:07:53 vault afpd[14405]: PAM pam_parse: expecting return value; [...common-session]
Aug 10 11:07:53 vault afpd[14405]: PAM (netatalk) no module name supplied

[/CODE]

I went searching for system-auth but it doesn't exist.

Am I missing something here?

---

### Post by sdmike6 on 2011-08-10
Anyone?

I'm still stuck....

---

