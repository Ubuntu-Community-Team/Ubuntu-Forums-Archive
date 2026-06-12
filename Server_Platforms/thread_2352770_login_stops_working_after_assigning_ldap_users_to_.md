---
title: "login stops working after assigning ldap users to local groups"
date: 2017-02-15
forum: Server Platforms
---

### Post by flok123 on 2017-02-15
Hi,

I hope this is the right channel to post this question.

I have ldap set up and everything is working fine (including sudo). Now I was trying to assign local groups to my ldap users via the guide below:

- Add ```
*;*;*;Al0000-2400;audio,cdrom,dialout,floppy
``` to /etc/security/group.conf

- Create /usr/share/pam-configs/my_groups and add
  ```
Name: activate /etc/security/group.conf
  Default: yes
  Priority: 900
  Auth-Type: Primary
  Auth:
        required                        pam_group.so use_first_pass
```

- And finalize with
  ```
pam-auth-update
  /etc/init.d/nscd restart
```

This is the link to the original description:
[https://help.ubuntu.com/community/LDAPClientAuthentication#Assign_local_groups_to_users](https://help.ubuntu.com/community/LDAPClientAuthentication#Assign_local_groups_to_users)

After I do the changes and run the id command I can see that my user was added to the local groups which is what I wanted but any other login doesn't work any more. Not a local user nor a ldap user. I am basically locked out. The only way I can connect is via ssh and rsa-key but from there I can't get sudo rights any more. Good thing there are VMs for such tests...


auth.log has the following (first I log in via ssh and rsa-key and then I run sudo su which fails):
```

sshd[16690]: PAM (sshd) no control flag supplied
sshd[16690]: PAM (sshd) no module name supplied
sshd[16690]: PAM (other) no control flag supplied
sshd[16690]: PAM (other) no module name supplied
sshd[16690]: Accepted publickey for user1 from 10.10.1.252 port 56284 ssh2: RSA SHA256:mOvt3wzVWbqIMNSL85lEeInz2L27J6nYFwF5uYN
sshd[16690]: pam_unix(sshd:session): session opened for user user1 by (uid=0)
systemd-logind[920]: New session 31 of user user1.
sudo: PAM (sudo) no control flag supplied
sudo: PAM (sudo) no module name supplied
sudo: PAM (other) no control flag supplied
sudo: PAM (other) no module name supplied
sudo: pam_unix(sudo:auth): authentication failure; logname=user1 uid=2000 euid=0 tty=/dev/pts/10 ruser=user1 rhost=  user=user1
sudo: pam_unix(sudo:auth): auth could not identify password for [user1]
sudo:  user1 : 2 incorrect password attempts ; TTY=pts/10 ; PWD=/home/user1 ; USER=root ; COMMAND=/bin/su

```

Running Ubuntu 16.10

I hope there is somebody with PAM-powers who can help me with this.

Cheers

---

### Post by cariboo on 2017-02-15
This is probably better off here.

---

### Post by slvr32 on 2017-02-15
> **flok123 said:**
> 
- Add ```
*;*;*;Al0000-2400;audio,cdrom,dialout,floppy
``` to /etc/security/group.conf
[/CODE]

Thi is the link to the original description:
[https://help.ubuntu.com/community/LDAPClientAuthentication#Assign_local_groups_to_users](https://help.ubuntu.com/community/LDAPClientAuthentication#Assign_local_groups_to_users)


It looks like you have a typo in the A10000-2400 detail.

According to the documentation, this should be A10000, but you seem to have a lowercase L, where you should have a 1 (one).

Edit: Sorry, the lowercase L is correct (confirmed by OP).

OP reached out to me about the PAM/LDAP issue via email because I had previously made an edit in related documentation, but my edit was only related to a spelling/grammar correction.

---

