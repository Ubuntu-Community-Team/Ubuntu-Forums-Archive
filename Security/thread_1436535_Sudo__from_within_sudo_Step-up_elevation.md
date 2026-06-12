---
title: "Sudo  from within sudo? Step-up elevation?"
date: 2010-03-22
forum: Security
---

### Post by paperplate9 on 2010-03-22
I have two executables:

- Script A
- Script B

Script A runs Script B.


Script A is owned root:accgroup, but a user will NOT be in accgroup, but can have a sudo entry to run Script A as (:accgroup).

Script B is owned exuser:exgroup and must be run with that effective owner/group.

The problem is how do I get Script A to execute Script B with the effective owner/group being exuser:exgroup?

What I thought was this:
1) add entry in sudoers so that a user can sudo -g accgroup ScriptA
2) add entry in sudoers so that the %accgroup can sudo -u exuser -g exgroup ScriptB

However, that doesn't work because sudo doesn't allow you to do that...e.g., elevate to someone else and then elevate to someone else.

The alternative is to add entries in sudo for the user for ScriptA and ScriptB. However, I don't want the user to be able to run ScriptB directly.

Any suggestions?

---

### Post by JackintheMox on 2010-03-22
Have you tried setting the suid + sgid bits on Script B?

---

### Post by paperplate9 on 2010-03-23
> **JackintheMox said:**
> Have you tried setting the suid + sgid bits on Script B?

Can't do setuid/setgid; against policy.

Also need to protect script B from getting run other than from within script A.

```

-r-xr-x---  1 root    accgroup           script_a.sh
-r-x------  1 exuser  exgroup            script_b.sh

user1@host$ groups
users

```Problem:
- user1 needs to be elevated to accgroup to run script_a.sh
- I then need to elevate from within script_a.sh to exuser:exgroup to run script_b.sh

Solution:
?

---

### Post by jrssystemsnet on 2010-03-23
> **paperplate9 said:**
> The problem is how do I get Script A to execute Script B with the effective owner/group being exuser:exgroup?

Do it the other way around.  Root can su to any user or group without a password; so allow access to run a script as root via sudoers, then have that script su willy-nilly to whoever you need it to be and run other scripts/commands as necessary.

sudo script1.sh

```
#!/bin/sh
# script.sh

su -c /path/to/some/command someuser
su -c /path/to/some/othercommand otheruser
```

etc, etc, ad infinitum, ad nauseam.

Don't forget to chown root script1.sh and chmod 400 script1.sh, to avoid little eyes reading it or little fingers modifying it.

---

