---
title: "SSH AllowUsers"
date: 2011-11-28
forum: Security
---

### Post by DapperMe17 on 2011-11-28
If one adds new users of SSH to the AllowUsers line, will those new users also have also be added as new users in the System Settings, under Users and Groups?

Thanks

---

### Post by teward on 2011-11-28
Usually, yes, because AllowUsers defines which people with accounts on the system/server may use SSH to connect.  For example, if I have the users "Foo", "Bar", and "Baz", and I want to allow only Foo and Bar to use SSH, then in the config I'd say "AllowUsers" and define Foo and Bar on that line.

(Offtopic Note: Is Security Discussions where this thread belongs?  This'd seem to be a basic SSHd Config question)

---

### Post by DapperMe17 on 2011-11-28
Ok great! 

Then I will have to first add a new user in the system settings, then add that same user to the SSH config file with "AllowUsers". 

Thank you!

---

### Post by bodhi.zazen on 2011-11-29
> **DapperMe17 said:**
> Ok great! 

Then I will have to first add a new user in the system settings, then add that same user to the SSH config file with "AllowUsers". 

Thank you!

You can also allow group ;)

---

### Post by Bachstelze on 2011-11-29
> **EvilPhoenix said:**
> Usually, yes, because AllowUsers defines which people with accounts on the system/server may use SSH to connect.  For example, if I have the users "Foo", "Bar", and "Baz", and I want to allow only Foo and Bar to use SSH, then in the config I'd say "AllowUsers" and define Foo and Bar on that line.


That was not the question. The answer to OP's question is definitely no.

*EDIT:* If I understood it correctly... Just adding a user to AllowUsers will not automatically create an account for that user.

---

### Post by CharlesA on 2011-11-30
> **Bachstelze said:**
> That was not the question. The answer to OP's question is definitely no.

*EDIT:* If I understood it correctly... Just adding a user to AllowUsers will not automatically create an account for that user.

If I read it right, then you are correct.

You'd have to create the user and then add their username to the sshd_config file.

That being said, it is easier to just add them to a group such as "sshusers" and just allow that group access.

---

### Post by Lars Noodén on 2011-11-30
> **CharlesA said:**
> That being said, it is easier to just add them to a group such as "sshusers" and just allow that group access.

+1

Groups are the best way to manage permissions.  See [AllowGroups](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html).

---

