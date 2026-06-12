---
title: "Ubuntu file server using AD Authentication"
date: 2013-05-13
forum: Server Platforms
---

### Post by Arbiter on 2013-05-13
Hello all,

I am doing a project for work trying to minimize the number of Windows servers we need to license- I wish to use Ubuntu Server for our file server (which does little else than host Windows file shares) - would it be possible to have SAMBA use the Active Directory server (running on Win Server 2012) to authenticate users for the SAMBA shares?

I thank everyone in advance for their insight.

Best regards,

Arbiter

---

### Post by TheFu on 2013-05-13
Yes, this should work. Samba4 should do this out of the box, at least that is my understanding.
I've deployed Alfresco and connected users and authentication to LDAP (not AD) but there were lots of examples for AD specifically.

There are other AD-connect tools as well. I can't think of the name, but a few have been discussed on these forums in the last 30 days.

File and Print is the easy starting point to integrate Linux into a mostly Microsoft company. You should be successful at this.

---

### Post by SeijiSensei on 2013-05-13
I've used the hoary [pam_smb]("http://www.csn.ul.ie/~airlied/pam_smb/") module for this task, though we were authenticating against a 2003 AD server.  I don't know whether it would still work in more modern implementations.  At the time the client was still using the Linux mail server I built, so we used pam_smb as the authentication method for IMAP by adding the pam_smb module and creating the appropriate configuration file in /etc/pam.d/.

---

### Post by Arbiter on 2013-05-13
> **TheFu said:**
> Yes, this should work. Samba4 should do this out of the box, at least that is my understanding.
I've deployed Alfresco and connected users and authentication to LDAP (not AD) but there were lots of examples for AD specifically.

There are other AD-connect tools as well. I can't think of the name, but a few have been discussed on these forums in the last 30 days.

File and Print is the easy starting point to integrate Linux into a mostly Microsoft company. You should be successful at this.

Hi TheFu,

Thanks for your reply- are the tools you mentioned GUI or command line tools?

Regards,

Arbiter

---

### Post by TheFu on 2013-05-14
> **Arbiter said:**
> Thanks for your reply- are the tools you mentioned GUI or command line tools?

This runs on a Linux server.  *"We don't need no stinkin GUI."*

---

### Post by Arbiter on 2013-05-14
> **TheFu said:**
> This runs on a Linux server.  *"We don't need no stinkin GUI."*

lol Don't get that GUI stuff on you- it never comes out :-P

---

