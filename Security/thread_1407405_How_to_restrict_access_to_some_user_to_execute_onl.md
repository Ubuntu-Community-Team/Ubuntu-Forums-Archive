---
title: "How to restrict access to some user to execute only &quot;top&quot; command?"
date: 2010-02-15
forum: Security
---

### Post by abcuser on 2010-02-15
Hi,
I am using Ubuntu 9.10 and I would like to add new user to my Ubuntu server computer. But this users must have only the following access:
1. access to connect from remote computer using ssh
2. execute "top" command

and nothing else!

This user should not have any access to any other commands like "ls", "ps", etc. No other access at all!
Regards

---

### Post by tjoff on 2010-02-15
Most shells, also bash, seems to have the -r (restricted) option.
From "man bash":

"
RESTRICTED SHELL
If bash is started with the name rbash, or the -r option is supplied at
invocation, the shell becomes restricted.  A restricted shell  is  used
to set up an environment more controlled than the standard shell.  It
behaves identically to bash with the exception that the  following  are
disallowed or not performed:

·      changing directories with cd

·      setting or unsetting the values of SHELL, PATH, ENV, or BASH_ENV

·      specifying command names containing /

"
 and so on ...

---

### Post by ushills on 2010-02-15
This method should work, just change the command that can be run.  I use this over ssh with rdiff-backup and the user backup

[http://www.cmdln.org/2008/02/11/restricting-ssh-commands/](http://www.cmdln.org/2008/02/11/restricting-ssh-commands/) 

or this  

[http://chihungchan.blogspot.com/2008/08/restrict-ssh-to-run-specific-command.html](http://chihungchan.blogspot.com/2008/08/restrict-ssh-to-run-specific-command.html)

Prepend the authorized_keys with the format

```
command="*whatever*"ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAwyAsd3AkcO2Oi3nN71WCTdSg/= machine@server

 
```

---

### Post by bodhi.zazen on 2010-02-15
> **ushills said:**
> This method should work, just change the command that can be run.  I use this over ssh with rdiff-backup and the user backup

[http://www.cmdln.org/2008/02/11/restricting-ssh-commands/](http://www.cmdln.org/2008/02/11/restricting-ssh-commands/) 

or this  

[http://chihungchan.blogspot.com/2008/08/restrict-ssh-to-run-specific-command.html](http://chihungchan.blogspot.com/2008/08/restrict-ssh-to-run-specific-command.html)

Prepend the authorized_keys with the format

```
command="*whatever*"ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAwyAsd3AkcO2Oi3nN71WCTdSg/= machine@server

 
```

+1 to the use of ssh + keys + forced commands.

You can use rbash, but understand it is not too difficult to break out of a restricted shell.

If you need something more, use apparmor. Create a restricted shell ;)

---

