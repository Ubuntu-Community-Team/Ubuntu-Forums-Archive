---
title: "User's Primary Group"
date: 2010-05-23
forum: Security
---

### Post by holocene on 2010-05-23
I understand that Ubuntu follows the "User Private Group" practice, where the typical group "users" is not utilized, but each user is setup in his own group. This is fine and I understand the reasons.

But, where should I see the user listed as a member of his private group?

The natural place I would expect would be in the **[SIZE=1]System|Administration|Users and Groups[/SIZE] **application. However, when I call up ANY user's primary group there, there are no check boxes, meaning apparently no membership. (I do see other groups, such as admin, showing user membership.)

Now, I am familiar with 

[LIST]
[*]/etc/passwd indicates that the GID is 1000, which is borne out by /etc/group
[*]the command groups bears out that the user's primary group agrees with the above.
[*]/etc/group is also consistent.
[/LIST]
What am I misinterpreting with the graphical application "Users and Groups" ??

Forgive me for asking when things otherwise seem ok, but this is an issue that I can not explain.

Best Regards
Steve.

---

### Post by cdenley on 2010-05-24
It appears it doesn't list group members who have that group as their primary group. It only searches /etc/group for group memberships.

---

### Post by holocene on 2010-05-24
> **cdenley said:**
> It appears it doesn't list group members who have that group as their primary group. It only searches /etc/group for group memberships.

Ok. Very much appreciate the reply. I was beginning to wonder if the question was completely off base.

I am a noob at all this, but if /etc/passwd contains only the user's Primary Group, then there is a mystery because the GUI "users and groups" shows groups that I have separately added through that facility

Oh, well. Ubuntu has some quirks.

But, I love Ubuntu!

BTW, I could find no real explanation of User Private Groups in any Ubuntu doc; where I did find it was in Red Hat's doc. 

Regards
Steve.

---

