---
title: "What are Primary and Secondary Group ?"
date: 2011-02-15
forum: Security
---

### Post by honey_bee on 2011-02-15
I need a little guidance regarding to groups in Linux. In Linux we have two types of groups.

(a) Primary group    	Denoted by small g
(b) Secondary Group	Denoted by large G	

Can any one explain it what is primary group and what is Secondary Group.

thanks.
honey

---

### Post by SeijiSensei on 2011-02-15
In /etc/passwd you'll see a primary group assigned to each user like this:

```
john:x:1001:1001:John:/home/john:/bin/bash
```

User "john" here has uid 1001 and his primary group is also 1001.  When john creates files, they will be owned by john and assigned to group 1001.  

john can also belong to other ("secondary") groups.  These assignments are made in /etc/group:

```
someusers:x:500:john,jill,jack,harry
```

Here john, jill, jack, and harry also belong to the group called "someusers" with gid 500.  So john will also have the privileges of this group, but files he creates won't be assigned to this group.  They will be assigned to group 1001 instead since that's his primary group.

Does this help?

---

### Post by honey_bee on 2011-02-17
thanks "SeijiSensei" for your reply. Well I am showing following how I add "john"  Primary  group ?

**Creating user**

[PHP]adduser john[/PHP]

**Now adding password**

[PHP]passwd john[/PHP]

**Now adding into group**
[PHP]groupadd fisrgroup[/PHP]

**Now adding user join into group i.e firstgroup**
[PHP]usermod -d firstgroup john[/PHP]

**for secondary group** 

[PHP]groupadd secondgroup[/PHP]

**Creating users**
[PHP]adduser john,jill,jack,harry [/PHP]

**Now adding into group**
[PHP]groupadd secondgroup[/PHP]

**Now adding user john,jill,jack,harry  into group i.e secondgroup**
[PHP]usermod -d secondgroup john,jill,jack,harry[/PHP]

please guide me that my steps are correct or not ?

---

### Post by SeijiSensei on 2011-02-17
The answer lies in the contents of /etc/passwd and /etc/group.  Did the users get created and assigned to the correct groups?  Did the groups get created and the users added to them?

Usually I just create a user with adduser letting it create a default primary group with identical name and gid = uid.  If I need to put a user into another group, I just edit /etc/group directly and add the username to the end of the entry for the group.  I also create groups manually by editing /etc/group.  I like being able to choose gid's for non-standard groups I create.

---

### Post by honey_bee on 2011-02-18
thanks for the reply. Well there are few things which are confusing me.In **useradd** command there is -g and -G and in **usermod** there are again same switch i.e -g and -G .

-g  is for primary group
-G for secondary group

I hope i am going correct ?

---

