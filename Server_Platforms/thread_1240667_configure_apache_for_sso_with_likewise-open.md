---
title: "configure apache for sso with likewise-open"
date: 2009-08-14
forum: Server Platforms
---

### Post by ezueff on 2009-08-14
Hello, I'm new to the forums so I hope this is the right place for this question.  Has anyone managed to configure an Apache2 web-server on a Ubuntu box connect via kerberos to Active Directory for the purpose of SSO?  Or even without likewise-open?  I have only found spars documentation floating around the interweb from other Linux Flavors and I haven't been able to put all the piece together. Thanks in advance if you can point me in the right direction.

---

### Post by ezueff on 2009-08-17
I figured it out! The issue was not me.  Turns out that the 64bit version of Server 2003 is shiped with a bad 'ktpass' tool.  There is a hot fix on-line.

---

### Post by cbf305 on 2009-10-19
Hi ezueff,

Could you post a howto/instructions/URL on how you set this up?  I've been trying to get this going for a while now, and I am apparently missing something.

Thanks!

---

