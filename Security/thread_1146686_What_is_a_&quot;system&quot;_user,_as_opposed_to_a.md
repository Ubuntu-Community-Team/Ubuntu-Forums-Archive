---
title: "What is a &quot;system&quot; user, as opposed to a normal user."
date: 2009-05-02
forum: Security
---

### Post by mempman on 2009-05-02
According to the man page for "adduser," there are 2 types of users that can be added to a debian system.  These 2 users are normal and system.

Now what exactly is a system user?  What is the purpose of this?  

Also, if I'm trying to install a specific antivirus software (say, clamav), and this software requires the existence of a clamav user account, now would this clamav username be a normal or a system type?

Thanks in Advance.

---

### Post by koenn on 2009-05-03
a lot of unix/linux security depends on access to files and the right to execute them, and this is managed through user accounts. So programs need a user account in order to work. It's common to create a specific account for each application/service/daemon/... because this gives fine-grained control about what the program is allowed to do (eg don't mess with other programs' files)

user accounts each have a unique number, the UID. It's common to give programs an account with a low number (lower than 1000), and real people an account with a higher number (1000 and up) so that programs that check user accounts can easily distinguish between them should they need to.

It's also possible that some features are turned of for system accounts (eg no home dir, no interactive log-in,  ...)

---

### Post by jimhyslop on 2009-05-10
> **koenn said:**
> user accounts each have a unique number, the UID. It's common to give programs an account with a low number (lower than 1000), and real people an account with a higher number (1000 and up) so that programs that check user accounts can easily distinguish between them should they need to.


That's the only difference? So if I changed my UID to, say, 99, that would make my account a system account? And if I changed the UID for a system account, say 'backup', to 1500, that would make it a normal account?

Just making sure I understand.

-- 
Jim

---

### Post by albinootje on 2009-05-11
> **jimhyslop said:**
> That's the only difference? 

According to the adduser manual page, the system users go in the "nogroup" group (which is not the case on Ubuntu).

But also, those system users are non privileged, have no password set (*) or disabled (!), and often use /bin/false or /bin/sh instead of /bin/bash.

---

### Post by koenn on 2009-05-11
> **albinootje said:**
> According to the adduser manual page, the system users go in the "nogroup" group (which is not the case on Ubuntu).

But also, those system users are non privileged, have no password set (*) or disabled (!), and often use /bin/false or /bin/sh instead of /bin/bash.

essentially, the difference is in how other programs treat those accounts. As in the exemples you give: the adduser program creates them so they can't be used for interactive logins, and/or doesn't create a home dir, etc. 
It's my understanding that they're essentially just accounts, i.e. records in /etc/passwd, but distinguishable by their (arbitrary) low UID, and can therefore be given special threatment by other programs, by package maintainers, by distro maintainers, by sysadmins, ...

---

