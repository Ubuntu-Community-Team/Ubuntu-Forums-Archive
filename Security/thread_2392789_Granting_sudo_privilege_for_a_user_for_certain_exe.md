---
title: "Granting sudo privilege for a user for certain executables"
date: 2018-05-25
forum: Security
---

### Post by jsvidyad on 2018-05-25
Hello,

    I run ubuntu 16.04. I have a user who does not belong to the group 'sudo'. I want to allow that user to run just certain executables with sudo privileges. How can I achieve this?? I would like to get answers for the case in which that user has to enter his password to run those executables with sudo privileges and also for the case in which he can run those executables with sudo privileges without being asked for his password.

---

### Post by TheFu on 2018-05-25
sudo is extremely flexible and highly documented.  Letting 1 user or a group run 1 specific command with only 2 or 6 allowed options is supported.  sudo can be used for 1 userid to run a process as another userid, not just root.  Not requiring a password for some specific commands is possible too.   You can also limit which hostnames specific commands are allowed to be used on by different users.

All of these things are documented in the sudoers manpage.   **man sudoers** to access it.  Beware, if you screw up these settings, you might have to boot from alternate media to fix it.  I've had to do that a few times.

RunAs
RunAs_Member
Cmnd_Alias
Cmnd_List
Cmnd
Parameter
Parameter_List

are settings you probably want to look up. You can either hard-code the programs and users or abstract them using the settings for more flexibility.  Just depends on your needs.

For passwords or nopasswords needed, check out the NOPASSWD option.

Be very careful in allowing users to run as root with sudo any programs that allow shelling out.  Most editor allow this, for example. This is a huge security hole and sudo tried to solve it through config options to prevent it, but that wasn't 100%, so they made **sudoedit**.

there are a few different ways to configure the sudoers ... the main file and the .local file and the sudoers.d/ subdirectory.

And for a little extra fun, enable the "*insults*" mode. ;)

The sudoers manpage is a work of art, IMHO.

---

### Post by jsvidyad on 2018-05-26
Can you give me some examples on how to accomplish the two tasks I asked about??

---

### Post by TheFu on 2018-05-26
```
dgb     boulder = NOEXEC: (operator) /bin/ls, (root) /bin/kill, /usr/bin/lprm
```
is one. User dgb is now allowed to run /bin/ls as operator, but /bin/kill     and /usr/bin/lprm as root.

      ```
 ray     rushmore = NOPASSWD: /bin/kill, PASSWD: /bin/ls, /usr/bin/lprm
```

BTW, those examples are directly from the manpage and there are multiple, important, caveats.

---

### Post by jsvidyad on 2018-05-31
Hello,

    Thanks for the examples. But, what I was looking for was allowing a user who does not belong to the sudo group the ability to execute certain executables using sudo with the same privileges as a member of the sudo group. Can you please give me examples for this (with and without password)?

---

### Post by TheFu on 2018-05-31
I think you are missing something, since I've provided both links and examples for exactly that above.  Perhaps if you spell out exactly what you've done, the missing stuff will become clear?

---

