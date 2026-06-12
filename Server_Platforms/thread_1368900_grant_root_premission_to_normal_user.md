---
title: "grant root premission to normal user"
date: 2009-12-31
forum: Server Platforms
---

### Post by smjd7 on 2009-12-31
hi
how can we grant root user permission to another user in ubuntu7 ldap server, so that 2nd user can manage like add remove client in ldap domain.

---

### Post by Lars Noodén on 2009-12-31
Here is a general description.  With more details, a more detailed suggestion can be made.

1) If it is a special type of administrative task, then make a new group for that activity and then add any users to it that should be able to do the task.  

2) Then figure out *exactly* which programs parameters are needed.  Could you post them please?  If some part vary from time to time, then you need to spend a bit of time to make a water-tight regex which will allow the needed options but exclude other tricks.
This is easiest with programs run via the shell, but can be granted to gui-based programs, too.

3) Then add that list of programs and parameters to /etc/sudoers and test it.  

After that, it should be possible for that user to carry out just that one specific task.

---

### Post by smjd7 on 2010-01-01
Dear Lars.
 
I hv ubuntu7 server installed and configure as Domain Controller(open Ldap Domain) and i join windows client to domain.
 
Now i use ROOT user to join windows client in domain,but i wana to create an other user same like Root(with full admin right) to do administrative task like join domain,disjoin domain,edit windows client registory etc,so my root user passwd would more secure.
 
if i create user in  /etc/suedors 
is it work with full right as root in all domain client?
 
thanks & regard
sajjad

---

