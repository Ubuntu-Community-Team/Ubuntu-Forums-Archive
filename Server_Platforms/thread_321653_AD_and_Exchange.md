---
title: "AD and Exchange"
date: 2006-12-19
forum: Server Platforms
---

### Post by bahn on 2006-12-19
What are the alturnatives to active directory and exchange. I have been using both these products for years they do the job but they also cost a pretty penny. I was hoping there were some people that were once windows admins such as my self that moved to linux that could shine some light on the subject.

---

### Post by elst on 2006-12-19
You've obviously seen the other discussion thread about this - functionality doesn't map exactly between Windows and *NIX, and in some areas *NIX systems are a bit behind (just as they are ahead in others).

Active Directory is a bundle of services: LDAP (user and resource directory), Kerberos (secure authentication), Group Policy, and software distribution. Similarly, Exchange is SMTP, mail filtering,   Webmail, shared calandaring, and IMAP-like mailbox management/access. The traditional approach is to get an Open Source component for each of these individual functions, and assemble them to fit your need, but products tend not to be bundled together and well-integrated.

The Hula software will break with tradition and offer a complete Open Source mail stack, but there have been various non-technical difficulties with the project, so there won't be a stable release for a while yet.

There is no Open Source AD killer yet, although Fedora Directory Server is well worth a look for the LDAP/directory services bit.

---

