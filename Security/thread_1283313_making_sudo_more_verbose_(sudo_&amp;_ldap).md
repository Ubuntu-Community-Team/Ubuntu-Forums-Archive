---
title: "making sudo more verbose (sudo &amp; ldap)"
date: 2009-10-05
forum: Security
---

### Post by supremedalek on 2009-10-05
I need to be able to have sudo check in ldap if a given user can sudo. What is the best way to do that? Currently what I have been doing is to add something like

sudoers_base ou=SUDOers,dc=domain,dc=com

to /etc/ldap/ldap.conf (as ubuntu does not have a ldap.conf.sudo file) and then install sudo-ldap (after removing plain sudo). I also have sudoers defined in /etc/nsswitch.conf,

```
passwd:         files ldap
shadow:         files ldap
group:          files ldap
sudoers:        ldap files

```

But, when I try it out, 

```
raub@tickets:~$ sudo pwd
[sudo] password for raub:
raub is not in the sudoers file.  This incident will be reported.
raub@tickets:~$ 

```

It does not seem to be authenticating. From /var/log/auth.log,

```
Oct  5 09:10:15 tickets sudo: pam_unix(sudo:auth): authentication failure; logname=raub uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=raub

```

Ok, probably the question should be what is going on, but the most important question to me is: how can I have sudo be a bit more verbose on its logging, telling me what it used to check if the user can sudo?

---

### Post by Lars Noodén on 2009-10-05
Can you get group information rather than check users, have sudo check groups.

```
%dirusers ALL=(ALL) NOPASSWD: /bin/pwd
```


What do you have in /etc/pam.d/sudo ?
That's probably where you can increase logging, since it seems it was pam that made the log entry.


[http://www.sudo.ws/sudo/readme_ldap.html](http://www.sudo.ws/sudo/readme_ldap.html)
[http://www.sudo.ws/sudo/man/sudoers.ldap.html](http://www.sudo.ws/sudo/man/sudoers.ldap.html)
[http://www.sudo.ws/pipermail/sudo-users/](http://www.sudo.ws/pipermail/sudo-users/)

---

