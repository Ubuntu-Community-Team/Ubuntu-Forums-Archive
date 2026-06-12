---
title: "/home/* permissions problems"
date: 2009-11-09
forum: Security
---

### Post by omegahalo on 2009-11-09
Hi Folks,

I have a backup script I've written that archives everything in the /home directory into a directory called /backup.  When I log in as super user (sudo bash) the script executes and the archive is created.  If I do not log in as the super user the archive is not created and no error is generated.  

The account that I'm running the script from is called Administrator.  I guess I'm trying to figure out the easiest way to make the Administrator account similar root, having permission to do everything.

---

### Post by EJeanmaire on 2009-11-09
> **omegahalo said:**
> Hi Folks,

I have a backup script I've written that archives everything in the /home directory into a directory called /backup.  When I log in as super user (sudo bash) the script executes and the archive is created.  If I do not log in as the super user the archive is not created and no error is generated.  

The account that I'm running the script from is called Administrator.  I guess I'm trying to figure out the easiest way to make the Administrator account similar root, having permission to do everything.

does 'Administrator' own the script (chown Administrator script.sh)?  Otherwise you will need to give execute privileges to to that file for everyone (chmod +x script.sh).  Also, Administrator will have to have privileges to access all the /home/* files.

---

### Post by Agent ME on 2009-11-09
You can't give other accounts root's abilities (unless there's some trick with access control lists or SELinux I don't know). You could use sudo to temporarily elevate another account to root, but doing that for this case in a script is just silly. Just make the archive script run as root directly.

---

### Post by Lars Noodén on 2009-11-10
> **EJeanmaire said:**
> does 'Administrator' own the script (chown Administrator script.sh)?  Otherwise you will need to give execute privileges to to that file for everyone (chmod +x script.sh).  Also, Administrator will have to have privileges to access all the /home/* files.

It doesn't matter who owns the script, just who runs it.
Put the script in /usr/local/bin or /usr/local/sbin
Make sure that the permissions are set so the script can be run.

[INDENT][FONT="Courier New"]chown u=rwx,g=rx,o=rx /usr/local/bin/script.sh[/FONT][/INDENT]

Then you can modify /etc/sudoers to allow a group of users to run that script as root. That group can have one user or it can have many.  

```

# members of the group backup can run this script
# but with no paramters
%backup        ALL=(ALL) SETENV: /usr/local/bin/backup.sh ""

```

There is a nasty trick called SUID, but that is a rather bad security hole and should be avoided.  

Make sure the script does not and cannot take any parameters or arguments and it should be fairly safe.  

If you want to be very careful:

 set the PATH explicitly inside the script or use full paths to the programs.  It should be something like this and without any 'dots': 
[FONT="Courier New"]PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin[/FONT]

 set the Internal Field Separator (IFS) explicitly. It should be something like this: 
[FONT="Courier New"]IFS=$' \t\n'[/FONT]

For the privacy of the other users, the output of the script (that which was being backed up) should be encrypted or at least not readable by anyone except the administrator.  Piping it through gnupg can give you good encryption.

---

