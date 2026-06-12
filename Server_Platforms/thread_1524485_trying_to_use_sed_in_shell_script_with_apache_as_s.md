---
title: "trying to use sed in shell script with apache as sudoer"
date: 2010-07-05
forum: Server Platforms
---

### Post by robowen on 2010-07-05
Hi All

does anyone know whether I should encounter a problem relating to output redirection when using sed from a shell script which is ran by apache?

I have given apache privileges in sudoers to run the shell script and the commands within it. However the problem is that when I check auth.log all commands are listed except the sed ones, yet if I run the shell script directly from the command line they work fine and are logged. 

So although I realise I probably have some permission issues to solve, I think its strange how sed commands are not being logged at all.

would also appreciate any advice on apache and sudoers, am I playing with fire here?

Im on lucid 10.04 server

Cheers
Rob

---

### Post by robowen on 2010-07-05
sorry, probably also useful to know that the script I mentioned is running other commands no problem where you would usually expect to encounter permission issues such as creating & copying directories and files, which all work fine, but sed doesn't

Also the sed commands are all redirecting output to a file

---

### Post by DaithiF on 2010-07-05
just a guess, but do you have apparmor running?  perhaps it is preventing the apache2 process from executing sed.  you could try disabling apparmor temporarily and see if the script then behaves as you expect.
```
sudo /etc/init.d/apparmor stop
```

---

### Post by robowen on 2010-07-05
hello, thanks for the suggestion but still no luck

tearing my hair out here! 

ah also as well, I am running the shell script via php shell_exec, dunno if that opens any doors

the strange thing is the rest of the script executes fine, basically it is a script which sets up a system on a subdomain, so all teh copying of files and database creation etc etc is all fine, but the bit where sed is involved isn't working, well not when it's executed by apache, works fine on the command line. 

Im just using sed to replace paths in the application config files so its nothing majorly complication. arrrrggggghhhh!

---

### Post by DaithiF on 2010-07-05
hmm, can you post an example of one of the sed commands, along with a line or two of an input file that it is trying to update

thanks

---

### Post by koenn on 2010-07-05
> **robowen said:**
> sorry, probably also useful to know that the script I mentioned is running other commands no problem where you would usually expect to encounter permission issues such as creating & copying directories and files, which all work fine, but sed doesn't

Also the sed commands are all redirecting output to a file
and apache has _write_ access to the location where the output file is to be created, and the file itselfif it already exists ?

---

### Post by robowen on 2010-07-06
Hi Guys

Thanks for responding to my posts, I appreciate your help. 

I have solved the problem which was down to permissions, which I had overlooked because I had tried running the script with apache temporarily given ALL privs in sudoers and it still didn't work - I would have thought that would have allowed apache to write to files owned by root? obviously not.

However I have some concerns over my sudoers file, I need to give apache privileges to rm / mkdir / cp / chmod etc, without passwords, which I think must be pretty insecure? does anyone have any suggestions for a safer way to do this? or is this ok? ...

# /etc/sudoers

Defaults        env_reset
Defaults:%www-data !requiretty

# User alias specification
User_Alias WEB = www-data

# Cmnd alias specification
Cmnd_Alias WEB_COMMANDS = /var/accounts/test.sh, /var/accounts/testd.sh, /etc/init.d/apache2, /etc/init.d/bind9, /usr/sbin/useradd, /usr/sbin/userdel, /bin/echo, /bin/cp, /bin/rm, /bin/sed, /bin/mkdir, /bin/chmod, /bin/chgrp, /bin/chown, /usr/sbin/a2ensite, /usr/sbin/a2dissite, /usr/bin/mysql, sr/bin/crontab

# User privilege specification

root    ALL=(ALL) ALL

%sudo ALL=(ALL) ALL

%admin ALL=(ALL) ALL

WEB ALL=(ALL) NOPASSWD:WEB_COMMANDS


Cheers
Rob

---

