---
title: "LDAP + NFS : failed to syncronize users files for &quot;roaming profile&quot;"
date: 2016-03-08
forum: Server Platforms
---

### Post by gabriele10 on 2016-03-08
Hello guys,

I'm installing my LDAP and NFS servers and working to get the roaming profile function. Now I have the users logging/authenticating directly into the LDAP server but their files seem to be not synchronized with the NFS, so the main goal which is to get the users files directly form the server to any NFS client host, it's not working.

I've checked the NFS-server systemctl and got the Active(exited) status. Autofs is Active(running).

Could someone help me on it?

Thanks in advance!!

---

### Post by gabriele10 on 2016-03-09
bump

?

---

### Post by gabriele10 on 2016-03-15
Someone pleeeeeease

---

### Post by darkod on 2016-03-15
So, are the LDAP server and NFS server two separate machines, or you have both roles on the same machine?

---

### Post by gabriele10 on 2016-03-23
Both on the same one. Do you have any idea about what could be the problem's source?

---

### Post by SeijiSensei on 2016-03-23
Does the server use LDAP as well for regular logins via [pam_ldap]("http://linux.die.net/man/5/pam_ldap")?  Do the UIDs and GIDs in the LDAP database match the equivalent values for the home directories?  You can check the latter quickly with 
```
ls -n /home
```
When a user logs in from a remote client, what UID/GID is he or she assigned?

I don't use LDAP so I'm just making some (hopefully educated) guesses.

---

### Post by darkod on 2016-03-23
Now I have more questions...

Usually the server holds the roaming profiles folder(s). If the same server is LDAP and NFS why would you have the folders/profiles on NFS share? To the server, that's local, no?

Are you trying to keep the profiles on the workstations?

What I have seen about roaming profiles (mostly on windows), in the user properties there is a setting with the path to the roaming profile folder, and that's usually on the server itself, not on the user's workstation.

PS. Check what Sensei mentioned above, I am still referring only to the type of the setup, not any actual issues. Because if it turns out it is better to change the setup, that might solve your issue(s).

---

