---
title: "Group membership confusion"
date: 2010-09-29
forum: Security
---

### Post by brittonl on 2010-09-29
I am new to Linux and am trying to get my head around the way groups work.  I have entered the commands below and they seem to be giving conflicting views?  Should I not expect to see the /etc/group list mmellow as a member of users?

lester@zero:~/lab$ groups mmellow
users
lester@zero:~/lab$ cat /etc/group | grep users
users:x:100:


Thanks
Lester

---

### Post by sisco311 on 2010-09-29
> **brittonl said:**
> I am new to Linux and am trying to get my head around the way groups work.  I have entered the commands below and they seem to be giving conflicting views?  Should I not expect to see the /etc/group list mmellow as a member of users?

lester@zero:~/lab$ groups mmellow
users
lester@zero:~/lab$ cat /etc/group | grep users
users:x:100:


Thanks
Lester

Are you sure that those were the exact commands you entered?

If one removes the username from the groups command, then it makes perfect sense. ;)

Check out:
```
info coreutils 'groups invocation'
```

Oh, and don't pipe cat into grep:

```
lester@zero:~/lab$ groups 
users
lester@zero:~/lab$ grep users /etc/group 
users:x:100:

```

---

### Post by brittonl on 2010-09-29
Thanks for your prompt response.

I am sure those are the commands since I just copied and pasted from the terminal window.

Just typing 'groups' shows the current user access whereas I was trying to obtain the group membership of 'mmellow'.  It appears to be in the 'users' group using 'groups mmellow' but not if I interrogate the /etc/group file. 

Thanks for the grep advice I shall use your form in future, though both methods appear to show 'users' without any members.  In the past I've also used commands like:

'printenv | grep TERM'
'dmesg | grep Bluetooth'

Is there a way of knowing how to best use grep?

Thanks
Lester

---

### Post by sisco311 on 2010-09-29
> **brittonl said:**
> Thanks for your prompt response.

I am sure those are the commands since I just copied and pasted from the terminal window.

Just typing 'groups' shows the current user access whereas I was trying to obtain the group membership of 'mmellow'.  It appears to be in the 'users' group using 'groups mmellow' but not if I interrogate the /etc/group file. 


Oh, I see it now, users is the primary group of mmellow (you can check it in /etc/passwd).

[http://en.wikipedia.org/wiki/Group_identifier#Primary_vs._supplementary](http://en.wikipedia.org/wiki/Group_identifier#Primary_vs._supplementary)

> **brittonl said:**
> 
In the past I've also used commands like:

'printenv | grep TERM'
'dmesg | grep Bluetooth'

Is there a way of knowing how to best use grep?


In case you have to search a file, use the **grep PATTERN filename** syntax. In case you grep the output of a command, you obviously have pipe the STDOUT of the command to the STDIN of grep.

---

