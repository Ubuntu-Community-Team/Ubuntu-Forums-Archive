---
title: "how make the changes on /etc/sudoers effective?"
date: 2009-02-12
forum: Security
---

### Post by itomer on 2009-02-12
hi, I followed some examples of modifying /etc/sudoers file and have made several changes.
e.g.   test ALL= /bin/ls # user 'test' is allowed to use /bin/ls

but after I logged in as 'test', I can still use the ls command as well as the other commands(cd, cp, etc..).
-----sorry for the misleading

According to my understanding, the /etc/sudoers means to indicate which user can do what, right?

I want to ask how to make the changes work?
do I need to restart the PC?

---

### Post by kerry_s on 2009-02-12
what? all you would need to do is change the permission so only root can execute it.

---

### Post by itomer on 2009-02-13
> **kerry_s said:**
> what? all you would need to do is change the permission so only root can execute it.
thanks very much for your reply.
I know that we can change the permission by your method or chmod.
but how can we get the same result via /etc/sudoers?

---

### Post by lykwydchykyn on 2009-02-13
Did you edit sudoers directly or use the visudo command?

---

### Post by itomer on 2009-02-13
> **lykwydchykyn said:**
> Did you edit sudoers directly or use the visudo command?

yes, i use 
sudo visudo -f /etc/sudoers

i followed the instructions in one post in the ubuntu administration guide, but i can not find it now.

---

### Post by kerry_s on 2009-02-13
did you check the man pages? (man sudoers)

i see the runas_spec kinda looks like what your trying to do, but not sure if thats what your after.

> 
Runas_Spec

A Runas_Spec is simply a Runas_List (as defined above) enclosed in a set of parentheses. If you do not specify a Runas_Spec in the user specification, a default Runas_Spec of root will be used. A Runas_Spec sets the default for commands that follow it. What this means is that for the entry:

 dgb    boulder = (operator) /bin/ls, /bin/kill, /usr/bin/lprm

The user dgb may run /bin/ls, /bin/kill, and /usr/bin/lprm -- but only as operator. E.g.,

 $ sudo -u operator /bin/ls.

It is also possible to override a Runas_Spec later on in an entry. If we modify the entry like so:

 dgb    boulder = (operator) /bin/ls, (root) /bin/kill, /usr/bin/lprm

Then user dgb is now allowed to run /bin/ls as operator, but /bin/kill and /usr/bin/lprm as root.


---

### Post by itomer on 2009-02-13
> **kerry_s said:**
> did you check the man pages? (man sudoers)

i see the runas_spec kinda looks like what your trying to do, but not sure if thats what your after.

yes, that is exactly what I am trying to do.

But the problem is that the user can still use the command after the modification of /etc/sudoers.
I think I will look into this tomorrow.
thanks again :-)

---

### Post by lykwydchykyn on 2009-02-13
Wait a minute; you're trying to PREVENT the user from using the command?  sudoers is not the file for that.

Probably what you need to do is create a group for the users that you want to be able to run the command, then change the permissions of the command to 750 and the ownership to root:newgroup.  For example:
```

#make it so that user test cannot run 'ls'
sudo groupadd run_ls
sudo chown root:run_ls /bin/ls
sudo chmod 750 /bin/ls
#Now add other users to the "run_ls" group, but not user "test"

```

That's the simplest way to do it.  You might also be able to create an apparmor profile to prevent the user from running the command without tinkering with its permissions and ownership (TBH, I wouldn't do a lot of tinkering with the permissions and ownership of basic system commands.  It could break your system in subtle ways).

If the above code doesn't do what you want, I'd suggest looking at apparmor.

---

### Post by itomer on 2009-02-13
sorry for the misleading information in the beginning, and I changed my original post. -_-bbb
my question is:
after adding a line in /etc/sudoers, e.g.: test ALL= /bin/ls

the user 'test' is supposed to only execute /bin/ls, but 'test' can still run the other commands.

I will have a look at apparmor. thanks for your advices.
by the way, the version is Ubuntu 8.10 Desktop.

---

### Post by lykwydchykyn on 2009-02-13
sudo only determines if you can run a command as root using the sudo command.  It does not limit in any way the commands you can actually run.

What you did in the sudoers file is give "test" the ability to run ls as root.

---

### Post by bodhi.zazen on 2009-02-13
> **lykwydchykyn said:**
> sudo only determines if you can run a command as root using the sudo command.  It does not limit in any way the commands you can actually run.

What you did in the sudoers file is give "test" the ability to run ls as root.

You would do this (limit commands / access) with apparmor.

---

### Post by kerry_s on 2009-02-13
> **lykwydchykyn said:**
> sudo only determines if you can run a command as root using the sudo command.  It does not limit in any way the commands you can actually run.

What you did in the sudoers file is give "test" the ability to run ls as root.

that was my thought to, the quickest way would be to change the permissions, then sudo can be used to use it, you don't have to install anything else like apparmor and deal with setting up another program to get the function. :confused:

---

