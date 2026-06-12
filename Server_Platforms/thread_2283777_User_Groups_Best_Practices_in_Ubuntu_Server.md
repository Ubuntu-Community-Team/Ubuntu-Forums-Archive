---
title: "User Groups Best Practices in Ubuntu Server"
date: 2015-06-24
forum: Server Platforms
---

### Post by fs_tigre on 2015-06-24
Hi,

I recently decided to manage my own web server (Ubuntu/Nginx) and as best practices I went and disabled the root user and created a new one with root privileges. When I created the new user I didn't specify what group to add it to, this is how I created it.

```
adduser newUserName
```

Then I added to the sudo group

```
gpasswd -a newUserName sudo
```

What confuses me is that when I type ***cat /etc/group*** to see all groups there is a group with the name of the user I created.

```
root
...
newUserName

```
So I started wondering if the way I created the new user is the right way to do it or it's better to create a group first and then add any user with the same privileges to the same group.

Can someone suggest a best practice to manage users/groups in Ubuntu Server or direct me to where I can find more information?

What would happen if I create a new group with the same privileges as the existing user and move the existing user newUserName to this folder? 

I guess I'm looking to have a better understanding of how users are typically managed in Ubuntu Server.

Thanks a lot.

---

### Post by TheFu on 2015-06-24
In a corporate environment, LDAP is used to hold all user accounts.
In a smaller environment (fewer than 10 users), local accounts are used.

adduser/useradd is how to make new users.  Both work, one creates the HOME and the other doesn't.  In Ubuntu, whenever a new userid is added, they get their own group. This may or may not be desired in a corporate environment. Guess it is better to have it than not.  When you understand groups more fully, it will be clear why this can be good and bad at the same time.

In reality, most ubuntu servers don't have end-user accounts at all.  We use deployment accounts for the application(s) running on the server and use DevOps tools to manage these and the rest of the server.  Every company does it a little differently, so whatever I say might not be the way others do it.  I've seen all sorts of different methods to managing users in different companies. Most were larger and used centralized LDAP/AD authentication.

The main thing is to be consistent - whether that means following a written script, wiki page with steps, using a bash/python/ruby/perl script or using some DevOps tool really doesn't matter. Be consistent.

And have versioned backups.


Almost forgot - use the 'id' command to see which groups have membership. When using LDAP or another network authentication mode, looking in file in /etc/ just doesn't work. PAM is really flexible.

---

### Post by fs_tigre on 2015-06-24
Thank you for your comments.

---

