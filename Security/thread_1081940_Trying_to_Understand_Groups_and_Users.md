---
title: "Trying to Understand Groups and Users"
date: 2009-02-27
forum: Security
---

### Post by sa125 on 2009-02-27
Hi - I'm trying to make sense of groups and users and the relationships between them. 

Can a user be a member in several groups, or is it one group for each user? If the former, then how is security handled? Does priority go to the highest group the user belongs to?

thanks!

---

### Post by Nepherte on 2009-02-27
A user can be in multiple groups and of course groups can contain multiple users. Each group is given some permissions. A user gets all the permissions of the groups it is in. For example, if you're in the admin group, you will be able to perform administration tasks, etc... Therere are no priorities.

---

### Post by lensman3 on 2009-02-27
As said before, you take on the characteristics of the group you are in.  To set your user ID to a group use "newgrp <grp>" and to list current the current assigned groups use "groups".  

I wouldn't add "root" to your group, because some things by the kernel aren't checked and are bypassed.  Such as "rm" as root doesn't check to see if file permissions are honored as root, the file is just blown away.  "rm" is aliased as "rm -i" to keep that from happening.

---

### Post by measekite on 2009-03-10
> **Nepherte said:**
> A user can be in multiple groups and of course groups can contain multiple users. Each group is given some permissions. A user gets all the permissions of the groups it is in. For example, if you're in the admin group, you will be able to perform administration tasks, etc... Therere are no priorities.

I have added users one thru six and have created groups A thru D.  I have then added users two, four and six to groups B and user one and five to group C.

I can then return to System:Admin:Users and Groups and see what I did.

[COLOR=Red]_**My Question:**_[/COLOR]

Where and how can I then assign rights and permissions to all of the groups?  I do see that I can assingn some rights to a specific user.

Lets say that I want full Admin rights for group B but only a portion of the rights to group C like maybe install application software.

---

### Post by measekite on 2009-03-10
Using Feisty how do you add a group to another group.  I can see how to add a user to a group.

---

### Post by InspiredIndividual on 2009-03-10
Group information is stored in /etc/group. This basically means you can grab all the members or group A individually and add them to group B using a simple for-loop. However, when the members of group A change, the members of group B do not automatically change as well. Therefor, this may not be what you're looking for. Of course, you can run the script every time after you add new group members. Maybe someone more experiences knows a prettier solution, but my suggestion will do the job. I'll be the first to admit it's not very elegant, though...

---

### Post by measekite on 2009-03-10
> **InspiredIndividual said:**
> Group information is stored in /etc/group. This basically means you can grab all the members or group A individually and add them to group B using a simple for-loop. However, when the members of group A change, the members of group B do not automatically change as well. Therefor, this may not be what you're looking for. Of course, you can run the script every time after you add new group members. Maybe someone more experiences knows a prettier solution, but my suggestion will do the job. I'll be the first to admit it's not very elegant, though...

Here is what I am looking for:

[SIZE=4]Situation:[/SIZE]
[B]
Group I[/B]
manny moe and jack

**Group II**
bozo and banzo
[B]
Group III[/B]
empty
[SIZE=4]
The Target[/SIZE]
**Group III**
Group I and Group II

[COLOR=Green]Now Group III essentially has manny, moe, jack, bozo and banzo[/COLOR]


[COLOR=Red]Now you create Group IV and move banzo to that group[/COLOR]

[COLOR=Green]Now Group III has manny, moe, jack and bozo[/COLOR]

[COLOR=Navy]I would also like to know how using the GUI if possible to select and assign various rights to a specific group that filters down to its users.  Then you can affect all of the users in a particular group at once.[/COLOR]

---

### Post by The Cog on 2009-03-11
You're looking at it from the wrong angle. Rather than creating a group of users (for instance, the accounts dept.) and then assigning whatever rights you think the should have to the group, you should make a group with the rights you need and then assign the users who need those right to that group. So the group is more concerned with categorising what its members can do than it is with categorising what type of people its members are. If that makes sense.

Here's an example. I have two projects on the go - a new warehouse construction and a new stock-control software roll-out. For these projects we need builders, programmers and accountants. The builders need access to the warehouse plans, the programmers need access to the stock-control project and the accountants need to interfere in both projects. The way to do it is not to create 3 user groups (builders, programmers, accountants) and worry how to give those groups the appropricate projects access. The way to do it is to create 2 groups (warehouse and stock-control) which have the appropriate rights and then give membership to those project groups to each of the users accordingly.

There are limitations in that a file/folder can only be allocated to one group. Users on the other hand can belong to many groups. This means that groups have to be organised around resource access rather than people types.

---

### Post by InspiredIndividual on 2009-03-11
A couple of questions:

After you've created Groups III and IV, do you still want banzo and the others to be members of groups I and II?

After you've created Group III (members: manny, moe, jack, bozo and banzo), do you want its members to reflect changes in Group I and II membership?

Regarding the assignment of various rights to group members, are you talking about 'User Privileges' you want to apply for all group members (System > Administration > Users and Groups > Properties > User Privileges)? As I understand it, these 'privileges' are de facto group memberships. For example, if 'jack' has 'Use CD-ROM Drives' checked in 'User Privileges', that means 'jack' is a member of the group 'cdrom'. Thus, managing privileges for groups boils down to adding all group members to another group.

There may well exist a GUI that performs this operation, but I do not know it. That doesn't mean there isn't any, but I'm not an expert. The only way I can see to do what you want is to write a little bash script, so I'm afraid I cannot help you with a GUI.

---

### Post by measekite on 2009-03-11
> **InspiredIndividual said:**
> A couple of questions:
After you've created Groups III and IV, do you still want banzo and the others to be members of groups I and II?


Banzo is the only one who was moved to Group IV

> **InspiredIndividual said:**
> 
After you've created Group III (members: manny, moe, jack, bozo and banzo), do you want its members to reflect changes in Group I and II membership?


Yes.  When one group is nested (child group) inside another group I would want changes in the nested group to be reflected in the parent group.

> **InspiredIndividual said:**
> 
Regarding the assignment of various rights to group members, are you talking about 'User Privileges' you want to apply for all group members (System > Administration > Users and Groups > Properties > User Privileges)? As I understand it, these 'privileges' are de facto group memberships. For example, if 'jack' has 'Use CD-ROM Drives' checked in 'User Privileges', that means 'jack' is a member of the group 'cdrom'. Thus, managing privileges for groups boils down to adding all group members to another group.


That is what I also thought.  But here is what I would like to know.  Lets say you create in System>Users and Groups.....  two new groups called [COLOR=Green]Accounting[/COLOR] and [COLOR=Green]Marketing.[/COLOR]

Now let say you had 20 different privileges called one thru twenty.  You want to assign all of the **odd privileges to Accounting** and the **even ones to Marketing**.  There is a way to do that in the Windows GUI but I do not see how to do that in Ubuntu/Linux.

Also lets say I want to had the 'Use CD-ROM Drives' group with all its privileges to the Marketing group; I do not even see a way to do that either.

Maybe these are just limitations of Linux?

> **InspiredIndividual said:**
> 
There may well exist a GUI that performs this operation, but I do not know it. That doesn't mean there isn't any, but I'm not an expert. The only way I can see to do what you want is to write a little bash script, so I'm afraid I cannot help you with a GUI.

Maybe someone else who stumbles on this post has an answer.  I just think this is lacking in Linux.  I am suprised Windows is more advanced in this area.:popcorn:

---

### Post by measekite on 2009-03-11
> **The Cog said:**
> You're looking at it from the wrong angle. Rather than creating a group of users (for instance, the accounts dept.) and then assigning whatever rights you think the should have to the group, you should make a group with the rights you need and then assign the users who need those right to that group. So the group is more concerned with categorising what its members can do than it is with categorising what type of people its members are. If that makes sense.

Here's an example. I have two projects on the go - a new warehouse construction and a new stock-control software roll-out. For these projects we need builders, programmers and accountants. The builders need access to the warehouse plans, the programmers need access to the stock-control project and the accountants need to interfere in both projects. The way to do it is not to create 3 user groups (builders, programmers, accountants) and worry how to give those groups the appropricate projects access. The way to do it is to create 2 groups (warehouse and stock-control) which have the appropriate rights and then give membership to those project groups to each of the users accordingly.

There are limitations in that a file/folder can only be allocated to one group. Users on the other hand can belong to many groups. This means that groups have to be organised around resource access rather than people types.

Thanks.

If I understand you are talking about folders and then assigning the rights (read,wrtie,execute etc) to a specific group as in the following example:

Groups are Accountants and Marketing
Folders are Numbers and Customers

The Accountants group has permission for Numbers and The Marketing group has permissions for Customers as assigned in the permissions tab of the properties of the folder.

[COLOR=Navy]I still can only assign one group to a folder instead of multiple groups to a folder.  I also cannot see how I can nest groups inside another. If I could do that then I could assign a parent group to a folder and all of the child groups inside would have access.[/COLOR]

But I am looking for more:

Let say I create two groups:  Basic Hardware and Advanced Hardware.  I then take inventory on all of the hardware in my computer and make assignments to each group and then assign users according to the level of hardware access I want.  I do not see how I can do that.

You comments and others will be appreciated.

---

### Post by bodhi.zazen on 2009-03-11
> **measekite said:**
> [COLOR=Navy]I still can only assign one group to a folder instead of multiple groups to a folder.  I also cannot see how I can nest groups inside another. If I could do that then I could assign a parent group to a folder and all of the child groups inside would have access.[/COLOR]

But I am looking for more:

Let say I create two groups:  Basic Hardware and Advanced Hardware.  I then take inventory on all of the hardware in my computer and make assignments to each group and then assign users according to the level of hardware access I want.  I do not see how I can do that.

You comments and others will be appreciated.

You can do this with several tools.

I suggest you use ACL's :

[http://tlug.dnho.net/?q=node/171](http://tlug.dnho.net/?q=node/171)

[http://ubuntuforums.org/showthread.php?t=145741 ]("http://ubuntuforums.org/showthread.php?t=145741")

The second link is a nice discussion, see pot #9 for ACL.

Other options would be something such as Apparmor or SELinux.

The third solution may be sudo (you can configure sudo to use groups and assign commands which groups have access to , although your question is with files so not as helpful).

---

### Post by bodhi.zazen on 2009-03-11
Threads merged as it is essentially the same question and same solutions.

---

