---
title: "Ubuntu 8.04 server + Mac OS 10.5 ldap + ssl auth woes"
date: 2008-09-23
forum: Server Platforms
---

### Post by djtopper on 2008-09-23
I've been chewing on this for a while.  I've been able to do a "dummy" authentication from my Mac client to my Ubuntu server using no ssl or even a password.  But whenever I try to add a password, with or without SSL the client simply won't authenticate.   None of the logs tell me anything.

I've just set up SSL thinking it would somehow force a specific, compatible, type of password on the Mac side.  No dice.

I'm using slappasswd to set the passwords, which defaults to SHA.  Is this correct for Mac OS?  I've tried MD5 too with no luck.

Please help.  This is driving me nuts.  I can't even seem to find out what password algorithm Mac OS wants via LDAP!?!?!

Thanks,

DT

EDIT:  ok the issue may be something else.  When I use SSL on the LDAP server side, I can no longer authenticate w/ a blank password.  So currently the only way I can authenticate from Mac OS to LDAP (Ubuntu) is w/o SSL and w/ no password.  ;-(

---

