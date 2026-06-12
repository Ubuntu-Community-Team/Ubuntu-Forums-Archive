---
title: "AccountsService in a computer lab setting"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Space_Balls on 2012-03-29
I'm curious if anyone else is running/going to run 12.04 in a computer lab, since the current state of precise creates a few problems.

Currently, the preferred desktop session for users ist stored/read using AccountsService.
In an environment with nfs homes + ldap accounts, this setting would at best be saved on a per computer basis.

I have gotten around that part by mounting /var/lib/AccountsService/ using nfs from a server on all my clients. This way, all account information is stored on the server. But as far as I am concerned, this kind of information belongs into the LDAP, and the NFS workaround adds unnecessary complexity.

So at least in theory, GDM/lightdm should be able to access this information. Apparently though, this only works when the greeter is set up to display the user selection/face browser.
In my case, privacy concerns and common sense dictate that the user list is disabled. (Who would want to look through a list of ~2000 users to find his name?)

So has anyone worked out workarounds for this case? Using KDM might work, since as far as I know, it still works using the "legacy" .dmrc file in the users home directory.


**The following bug reports concerning this situation exist:**
"[*lightdm ignores session selection of ldap users*]("https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/897212")"
"[*Using the "other" login option ignores accountsservice default user session*]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/965256")"

On a side note, the removal of the language selector from the login screen isn't very user friendly either. [(LP #873710)]("https://bugs.launchpad.net/unity-greeter/+bug/873710")

---

### Post by robfantini on 2012-04-05
Hello

 We have the same issue.  Our openldap works fine with lucid and squeeze.

 We'll try using a fuse mount of  /var/lib/AccountsService for now.

 I hope this bug is fixed before Precise is released.

OK  fuse did not work, as it is not started soon enough...

 May try nfs..

---

