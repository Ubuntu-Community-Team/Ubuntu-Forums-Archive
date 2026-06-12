---
title: "automatically create home directories on login"
date: 2009-12-01
forum: Server Platforms
---

### Post by serge.fonville on 2009-12-01
I'm trying to setup an LDAP environment.
The same system is running the LDAP- server and client.
 
Now I wan't to automatically create the homedirectories on login.
I added 'session optional pam_mkhomedir.so skel=/etc/skel/ umask=0022'  to common-session.
 
But when I login with an ldap user I get 'Could not chdir to home directory /home/serge: No such file or directory'
 
What additional steps do I need to take to make this working?
 
Thanks in advance!

---

### Post by KiLaHuRtZ on 2009-12-01
Try this ...

```
session		**required**	pam_mkhomedir.so skel=/etc/skel/
```

---

### Post by serge.fonville on 2009-12-03
Thx for the reply.
 
Unfortunately this did not resolve it.
 
Now when I login over ssh. it immediately closes the connection.
 
when I login locally I get
> id: cannot find name for group with id 10000
But it then has created the homedirectory.
 
I looked at /etc/pam.d/sshd
 
But I do not see anything weird in it.
It includes all the common-* files
 
So mkhomedir seems to be doing it's job, but not when ssh is used
 
Are there any additional steps I need to take to enable mkhomedir on ssh?

---

### Post by KiLaHuRtZ on 2009-12-03
Looks like your client machine cannot find your GID.  Are you exporting groups out via LDAP as well?  If not, this may be your problem.  It can't create the home directory because the users group does not exist.

---

### Post by serge.fonville on 2009-12-03
After adding the group to LDAP the error is gone.
 
I am still not able to login over ssh.
 
When I look at the permissions of my home directory.
I see they are nobody.nogroup 755 for . and 644 for .profile
 
in auth.log it says
```
pam_mkhomedir(sshd:session): unable to change perms on copy /home/serge/.profile: Operation not permitted
error: PAM: pam_open_session(): Permission denied
```
 
perhaps there is something wrong with my pam config

---

### Post by serge.fonville on 2009-12-03
I figured the user homes were on an nfs share and no user is allowed to change permissions from the applicable machine.
 
So it is 'kinda' solved.
 
Thanks for all the help!

---

