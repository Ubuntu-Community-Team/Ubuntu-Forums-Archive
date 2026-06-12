---
title: "JJ server - list users, group using cli"
date: 2009-08-08
forum: Server Platforms
---

### Post by jclawson on 2009-08-08
Hello everyone,
I wanted to know if there was a way to list users and groups using the CLI. I have Ubuntu Server Jaunty Jackalope installed and I wanted to list all the users and groups for management purposes. I know that the users can be seen using the following command:


# cat /etc/passwd

but is there a more 'official' way of doing this? I know adduser is used for adding users and deluser is used for deleting users. Is there such a command line utility that will list all the users/groups on the command line?

Thanks in advance,

Jake Clawson

---

### Post by scorp123 on 2009-08-08
> **jclawson said:**
> Is there such a command line utility that will list all the users/groups on the command line?

The downside of using commands such as "cat /etc/passwd" is that they will only work if you indeed use the local passwd file for authentication. But it won't show e.g. LDAP or NIS users because their accounts use a different mechanism altogether.

So to really really catch all users (no matter whether local or logged in via LDAP, NIS, or whatever other mechanism) I'd suggest you use the **getent** command.

```
getent passwd
getent group 
```

The output will look identical as if you had used "cat /etc/passwd" ... which is OK I guess? So you get exactly all the fields and in the same order that you'd expect from using "cat" on the "passwd" file.

Other commands you might be interested in, e.g. **last**  ... When was the last time a user logged in? 

Sometimes I use this quickie script to check on the users that have a valid shell for some reasons (I don't care about blocked users that have /bin/false or /bin/nologin as their shell ...) and thus might login unless their password is disabled:
```
 getent passwd | grep -v false | grep -v nologin | cut -d: -f1
```

To look at the detail of just one specific user you could also specify the username:
```
getent passwd username
```

The above command would also work if your system is set e.g. to LDAP authentication (using "grep username /etc/passwd" would fail in that case because LDAP is not using that file ....)

---

### Post by jclawson on 2009-08-08
Thanks a lot! That was just what I was looking for although I was expecting a much more "beautified" output but that's not really a big issue. 

I am going to dig deeper into the getent utility. Seems to be a very useful one!

Once again, thanks. I had been all over the web for this question but to no avail. You solved it! :D

Jake Clawson

---

