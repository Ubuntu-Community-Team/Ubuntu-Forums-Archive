---
title: "untrusted users"
date: 2014-01-08
forum: Server Platforms
---

### Post by micahpage on 2014-01-08
I am goign to make a server with a forum... with multiple users under a group 'untrusted'. (well if it makes it easier i might just have all of them log into one user under untrusted group). I want everyone in the untrusted group to have limited commands.

I found a way to prevent the fork bomb, but not sure as if it works or not:
in /etc/security/limits.conf i added 
```
@untrusted soft nproc 50
@untrusted hard nproc 80
```

Although i am not sure how to limit the commands to them? I am not sure as what else to do to secure the server as well.

Also is there a way to resitrict their access to only /var/www/forum and its subdirectories?

---

### Post by CharlesA on 2014-01-08
Make /var/www/forum their home directory and jail them to that directory.

A forkbomb eats up all system resources by spawning a ton of processes, setting the hard and soft limits help prevent the system from hard locking in the event someone runs a forkbomb.

With that being said, why do these "untrusted" users need access to the server?

---

### Post by micahpage on 2014-01-08
thanks for the quick response CharlesA
well they are essentially trustworthy...but i figure to add an extra layer of security on, just in case. But mainly to download/install add plugins to the forum as needed.  And as everyone there is helping foot the bill for hosting/domain purchase, it makes them feel comfortable For example: 
in case myself abandons it, so they can still download new mods for the forum, etc.

---

### Post by CharlesA on 2014-01-08
That makes sense. Using sftp and jailing them to their "home directory" sounds like a step in the right direction. If you want to only give them sftp access, that would prevent them from logging into a console and running commands.

I don't know if that is what would work for your environment or not.

Otherwise, don't give them sudo access and you should be "ok" as long as they don't do something stupid like rm -rf the /var/www/ folder.

Backup, backup, backup.

---

### Post by micahpage on 2014-01-09
> as long as they don't do something stupid like rm -rf the /var/www/ folder.
thats what i was thinking of something like this:

```
sudo chgrp untrusted /bin/rm
sudo chmod 700 /bin/rm

-rwx------ 1 root untrusted 55888 Nov 19  2012 /bin/rm



```

but then i would have to go through a series of potentially dangerous commands, and hope that it would not interfere with the purpose of them being there in the first place

---

### Post by CharlesA on 2014-01-09
Well, those permissions give them no access to the rm file, so I guess that would work. It seems a bit overkill though, assuming they need to delete a file.

The best thing to do is keep regular backups and train the users in the proper commands. That way, if they mess up, you can restore from backups and all will be back to normal.

---

### Post by micahpage on 2014-01-09
will do
thank you very much for your help and quick responses

---

### Post by rmstock2 on 2014-01-09
You might also consider using a restricted shell, like restricted bash :

[SIZE=2][FONT=fixedsys]**RESTRICTED SHELL**[INDENT]If **bash** is started with the name **rbash**, or the **-r** option is supplied at
       invocation,  the  shell becomes restricted.  A restricted shell is used
       to set up an environment more controlled than the standard  shell.   It
       behaves  identically  to bash with the exception that the following are
       disallowed or not performed:
[/INDENT]
[INDENT=2]
changing directories with **cd**

              setting or unsetting the values of **SHELL**, **PATH**, **ENV**, or **BASH_ENV**

              specifying command names containing** /**

              specifying  a  file  name containing a **/ **as an argument to the **.**
              builtin command

              Specifying a filename containing a slash as an argument  to  the
             ** -p** option to the **hash** builtin command

              importing  function  definitions  from  the shell environment at
              startup

              parsing the value of **SHELLOPTS** from  the  shell  environment  at
               startup

              redirecting output using the >, >|, <>, >&, &>, and >> redirect-
              ion operators

              using the **exec** builtin command to replace the shell with another
              command

               adding  or  deleting builtin commands with the **-f **and **-d **options
               to the **enable** builtin command

               Using the  enable  builtin  command  to  enable  disabled  shell
               builtins

               specifying the **-p** option to the **command** builtin command

               turning off restricted mode with **set +r** or **set +o restricted**.
[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
These restrictions are enforced after any startup files are read.

       When a command that is found to be a shell script is executed (see [B]COM-
       MAND EXECUTION[/B] above), **rbash** turns off any restrictions  in  the  shell
       spawned to execute the script.
[/INDENT]
 
**SEE ALSO**
       [/FONT][/SIZE][INDENT][SIZE=2][FONT=fixedsys]_Bash_ _Reference_ _Manual,_ Brian Fox and Chet Ramey
       _The_ _Gnu_ _Readline_ _Library_, Brian Fox and Chet Ramey[/FONT][/SIZE]
       _The_ Gnu _History_ _Library_, Brian Fox and Chet Ramey
       _Portable_  _Operating_  _System_  _Interface_ _(POSIX)_ _Part_ _2:_ _Shell_ _and_ _Utili-_
       _ties_, IEEE
       _sh_(1), _ksh_(1), _csh_(1)
       _emacs_(1), _vi_(1)
       _readline_(3)
[/INDENT]

---

