---
title: "automatic acount creation and removal"
date: 2014-06-13
forum: Server Platforms
---

### Post by mye nyme on 2014-06-13
let me start out by saying that LDAP is not an option primarily because  an LDAP server would not be accessible from many of the machines.

the  goal is to be able to add or remove user accounts on a set of machines.  Adding an account means in addition to setting up the usual skeletons,  creating it with the "right" userid/group ID, and copying in limited new  initial data such as authorized_keys or a git repository after the  accounts created.

do any tools exist for doing this?

thanks

---

### Post by TheFu on 2014-06-13
Rex, Puppet, Ansible, Chef, CfEngine, SaltStack ... probably a few others.  I'd suggest Ansible since it doesn't require anything extra to be installed on the remote machines - normal default distro installations has all the dependencies already. Plus it works over ssh and uses sudo.  For upto 1,000 machines, ansible is the easy choice.

---

### Post by mye nyme on 2014-06-13
thanks for the quick reply. I really appreciate it

---

