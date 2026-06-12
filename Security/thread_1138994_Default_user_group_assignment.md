---
title: "Default user group assignment"
date: 2009-04-26
forum: Security
---

### Post by IsAB on 2009-04-26
I think that i've messed up my working user's account trying to add myself to a group using a shell command like :

```

usermod -G <groupname> <username>

```
..thus replacing all my current group memberships, instead of :
```

usermod -a -G <groupname> <username>

```
...to append the group to my existing ones

I've allready added me to the 'users' group, are there any other groups that i should be a member of?

---

### Post by Titan8990 on 2009-04-26
admin

adduser is the command you should use to add a user to a group in Debian based systems.

---

### Post by IsAB on 2009-04-27
Thank you.

---

### Post by ktritty on 2010-05-17
Hello.

I ran ```
sudo usermod -aG <group> <user>
```

How do I check my work by running a command

```
<command> <options> <user>
```

that will output all of the groups of which user is a member?

Thanks!

---

