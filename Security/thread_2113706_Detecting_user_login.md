---
title: "Detecting user login"
date: 2013-02-08
forum: Security
---

### Post by coppermine on 2013-02-08
Hi all,

I did some search in order to find ways how to detect and act when some user logins on the system. I want to do the following: when user X logins, a script is run.

I will provide also some context. I am currently running a dedicated server located who knows where in a datacenter. I have full superuser privileges except direct access to the user root. The user root can be used by technicians to login on the system and carry out any operations they need to.
Well... I do not trust the root user since some sensitive data is stored in Truecrypt volumes. What I want to do, is when root user login is to unmount any truecrypt volumes.

Cheers

---

### Post by schragge on 2013-02-08
You probably can achieve this by including into */etc/pam.d/common-session* some additional PAM modules like [pam_succeed_if(8)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=pam_succeed_if") and [pam_exec(8)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=pam_exec"), but be aware that the root user can see and revert any changes to the login process you make.

:!: **NOTE:**
[indent][highlight]If you don't know your way around PAM then do not experiment with it on a remote machine: you easily can mess the login settings up to the point that you cannot login anymore.[/highlight][/indent]

---

### Post by coppermine on 2013-02-08
> **schragge said:**
> You probably can achieve this by including into */etc/pam.d/common-session* some additional PAM modules like [pam_succeed_if(8)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=pam_succeed_if") and [pam_exec(8)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=pam_exec"), but be aware that the root user can see and revert any changes to the login process you make.

:!: **NOTE:**
[indent][highlight]If you don't know your way around PAM then do not experiment with it on a remote machine: you easily can mess the login settings up to the point that you cannot login anymore.[/highlight][/indent]

Thanks! I have some experience with PAM but I will touch it if I am 100% sure what I am doing. Currently I think to run a script in a loop and check periodically, say every 1 min, whether root has logged in.

My main concern is that root should not mess around with my data. There are no other users on the system.

---

### Post by schragge on 2013-02-09
I guess then you can check it like this
```

if users | grep -q root; then
  echo root is logged in
else
 echo root is not logged in
fi

```

---

