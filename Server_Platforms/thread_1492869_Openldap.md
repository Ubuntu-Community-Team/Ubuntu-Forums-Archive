---
title: "Openldap"
date: 2010-05-25
forum: Server Platforms
---

### Post by IMadhavan on 2010-05-25
Hi
I tried to configure Ubuntu ldapserver.when i give the option slapadd -l init.ldif file it will give error which [B][U]Available database(s) do not allow slapadd  anyone can solve this issue

thanks in advance
[/U][/B]

---

### Post by bjorgein on 2010-05-26
Openldap has changed A LOT in the past few releases. Read and follow this guide [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html) to the bone for the first time around. LDAP is quite an extensive topic and is very finicky. I spent a few days getting used to it before being comfortable with starting my own build.

---

### Post by IMadhavan on 2010-06-02
Hi 
thanks for your reply.
Already i have followed this document, But i couldn't move on the 1st step itself. Because it **doesn't ask password **and other slapd configuration How did you reach it 

Please explain

---

### Post by calcium on 2011-01-04
I know this thread is v old but I too had this problem.
Just some info in case someone else might find it helpful.

Some background.

I was trying to run openldap on windows (under cygwin).

And what made this error away was that my slapd.conf had to have CRLFs.

So when I did a $flip -m slapd.conf, this error went away.

Yes, yes, I know this is a Linux forum but still, might give
some clues.

---

