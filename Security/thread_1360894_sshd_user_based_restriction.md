---
title: "sshd user based restriction"
date: 2009-12-21
forum: Security
---

### Post by user4852 on 2009-12-21
I'm aware of the fact that you can use the allowuser directive in sshd_config to list the users that you want to let in. However for reasons specific to my setup I'm interested in having the list of such users in a separate file.
something like /etc/users.allow

I've been searching for a while and haven't found anything resembling a way to do this.

You guys know how to load an external list of users in sshd_config?

Any help appreciated, thanks!

---

### Post by BkkBonanza on 2009-12-22
I haven't checked thoroughly but I'm not aware of a #include type directive available for the config file. Given that one isn't available your next best bet is to use a file cat type operation or script to build the config as needed.

eg.

user list in /etc/ssh/users.allow
base cfg in /etc/ssh/base.conf

and script like this to reload the config when a change occurs,

#!/bin/bash
cat /etc/ssh/base.conf /etc/ssh/users.allow > /etc/ssh/sshd_config
kill -HUP `cat /var/run/sshd.pid`

(I didn't test this but I think the idea is fine)
(note those are backticks on the kill line not single quotes)
(since you have to do a reload anyway when a chg occurs there's no real downside to this method)

---

### Post by user4852 on 2009-12-22
I was hoping I missed something obvious but this confirms there are no includes possible. Thanks a lot for the script idea, you're a gentleman and a scholar.

---

### Post by bodhi.zazen on 2009-12-22
> **user4852 said:**
> I was hoping I missed something obvious but this confirms there are no includes possible. Thanks a lot for the script idea, you're a gentleman and a scholar.

You can use PAM :

[http://www.cyberciti.biz/tips/linux-pam-configuration-that-allows-or-deny-login-via-the-sshd-server.html](http://www.cyberciti.biz/tips/linux-pam-configuration-that-allows-or-deny-login-via-the-sshd-server.html)

---

### Post by Lars Noodén on 2009-12-23
> **user4852 said:**
> I'm aware of the fact that you can use the allowuser directive in sshd_config to list the users that you want to let in. However for reasons specific to my setup I'm interested in having the list of such users in a separate file.
something like /etc/users.allow


Use the **Match group** or **AllowGroups** directives instead.  When the user should be allowed to log in, add them to the group.  When they are not, take them out of the group.  

Trying to manage access on a user-by-user basis is not a recipe for success.  Using groups scales better anyway.

---

