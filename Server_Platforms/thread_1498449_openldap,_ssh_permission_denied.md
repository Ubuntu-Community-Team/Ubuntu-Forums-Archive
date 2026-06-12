---
title: "openldap, ssh permission denied"
date: 2010-05-31
forum: Server Platforms
---

### Post by DaveVentresca on 2010-05-31
Hey there Ubuntu land
  my openldap server is working correctly, i am able to add groups and users with ldapaddgroup & ldapadduser, but when i go to test the user with an ssh login, it says permission denied (publickey,password).

e.g. /# ssh testuser@localhost
> testuser@localhost's password: (i enter pwd here)
>Permission Denied, please try again.

does that 3 times, then boots me out of ssh

could ldapscripts be assigning my users some weird funky password that I don't know?

---

### Post by WinstonChurchill on 2010-05-31
What do the SSH Daemon logs say? (Probably in /var/log/messages - look for the 'sshd[####]' prefix)

---

### Post by DaveVentresca on 2010-06-01
got that working, i can ssh in. however, now i need to be able to graphically log in from any machine. when i tried to do this nautilus does not have the permissions to create the desktop or anything else. What do I need to do?

---

