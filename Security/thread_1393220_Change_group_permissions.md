---
title: "Change group permissions"
date: 2010-01-29
forum: Security
---

### Post by karmic-koala on 2010-01-29
How do you change what actions can members of a group perform. When using the GROUPADD command there's no way to specify what members can or cannot do.

Also does invoking GROUPDEL affect membership of other groups? E.g.

groups user
user: user print web 

sudo groupdel print

should this affect user's membership of groups user or web?

---

### Post by bodhi.zazen on 2010-01-29
What are you wanting to do ?

You first add a group, assign users to groups, then specify permissions by ownership and permissions of files and directories.

If you need finer grain control, use acl.

Also take a look as what it meas to define a users primary group :p

---

