---
title: "On ssh root login access"
date: 2007-02-20
forum: Server Platforms
---

### Post by Nikron on 2007-02-20
My situation is this, I have a server install computer behind my firewall acting as my server.  Anyway, I want to allow people outside the router not to have root access, but computers inside the router to have access.  Anyone know how to set this up, or point me in the right direction?

Thanks.

---

### Post by Jussi Kukkonen on 2007-02-20
Don't allow root login over SSH, and don't give "outsiders" sudo-rights. That should do it.

Additionally, I suggest only allowing key-based logins if at all possible.

---

### Post by Nikron on 2007-02-20
> **Jussi Kukkonen said:**
> Don't allow root login over SSH, and don't give "outsiders" sudo-rights. That should do it.

Additionally, I suggest only allowing key-based logins if at all possible.

But wouldn't that block computers inside my network from gaining root access?  I absolutely need root access to this computer remotely, as remotely is the only way to access this computer.  (It has no keyboard, no moniter, no mouse...)  So, I need internal networks.. ie (192.168.2.*) computers to be able to have root/sudo rights.  However anything connecting thru my router should not be able to have root access.

---

### Post by conjur3r on 2007-02-20
Configure sudo (/etc/sudoers) so that only the accounts you specify can gain root access.  All other accounts are non privileged.  This means that you can log on with your account from anywhere (internal or external) and still have your privileges intact.

---

### Post by Jussi Kukkonen on 2007-02-21
Nikron, sudo rights are not given to IP addresses, they are given to users. Anything else wouldn't make sense, really.

Blocking root logins means that one cannot login as root, it does not prevent you from logging in as yourself and sudoing (if you are in *sudoers*). 

There are other things you should do to tighten your SSH security, like only allowing logins for specified users. Read *man sshd_config*.

---

### Post by MJN on 2007-02-21
Nikron, check out [http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html) - it seems to cover exactly what you're trying to achieve (i.e. SSH access to anyone except root from anywhere, and root access only from specific IP addresses).
 
Note the caveat that is utilises PAM hence will equally apply to any other server that relies on PAM for authentication.
 
Mathew

---

### Post by Nikron on 2007-02-21
> **MJN said:**
> Nikron, check out [http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html) - it seems to cover exactly what you're trying to achieve (i.e. SSH access to anyone except root from anywhere, and root access only from specific IP addresses).
 
Note the caveat that is utilities PAM hence will equally apply to any other server that relies on PAM for authentication.
 
Mathew

Exactly what I was looking for, thank you sir.

---

### Post by Nikron on 2007-02-21
At the link [http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html) it says you need to edit "/etc/pam.d/sshd", but I think on Ubuntu you need to edit "/etc/pam.d/ssh".

---

