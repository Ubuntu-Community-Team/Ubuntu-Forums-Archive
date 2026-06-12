---
title: "How to deactivate root account but allow software to run as rool?"
date: 2011-06-23
forum: Server Platforms
---

### Post by TCarr on 2011-06-23
I'm setting up a server on a Cloud Server hosting service. When they installed Ubuntu 10.04, they set it up with "root" access. Meaning they created an account called "root" and gave us a password to log in.

Of course, I immediately created the admin (sudo) accounts for myself and the other administrator. However, being that we are most familiar with installing 8.04 LTS server on our own hardware, and thus set it up without root, we don't quite know how to get rid of the 'root' login, yet preserve the ability for our scripts and software to still run with root permissions.

Can anyone please provide steps or a link to a thread that has these steps?

Thanks.

---

### Post by capscrew on 2011-06-23
> **TCarr said:**
> I'm setting up a server on a Cloud Server hosting service. When they installed Ubuntu 10.04, they set it up with "root" access. Meaning they created an account called "root" and gave us a password to log in.

Of course, I immediately created the admin (sudo) accounts for myself and the other administrator. However, being that we are most familiar with installing 8.04 LTS server on our own hardware, and thus set it up without root, we don't quite know how to get rid of the 'root' login, yet preserve the ability for our scripts and software to still run with root permissions.

Can anyone please provide steps or a link to a thread that has these steps?

Thanks.

You don't *_create_ *a root account.  The root user is always there.  The uid is 0.  To see the root account try this from the CLI```
getent passwd|grep root
``` To see the group for root try this
```
getent group|grep root
```
Access to the account is obscured with an unknown password.  Rest assured the account is always there.  If you are concerned you can change the root password.  You could use 12 characters or more to prevent guessing.  You don't even have to remember it if you have sudo set up correctly and understand how to change the root password using sudo.  On the other hand if multiple users have sudo rights you should think of limiting the kinds of commands that these folks can execute with sudo root rights (e.g the passwd command).

Look to sudo configuration tutorials for insight.  

If you are the only one that will know the root password then there is no real problem as long as the password is strong enough to be uncrackable.

---

### Post by Bachstelze on 2011-06-23
@capscrew: You misunderstood. The system was installed with the root account enabled, and TCarr wants to disable it (i.e. revert to the default configuration).

@TCarr: Run [FONT="monospace"]sudo passwd -l root[/FONT] (as a user with sudo permissions of course).  That will give the root user a special password that is impossible to enter, which is what Ubuntu does by default.

---

### Post by crispy_420 on 2011-06-24
+1 to random password as is default

---

### Post by capscrew on 2011-06-24
> **Bachstelze said:**
> @capscrew: You misunderstood. The system was installed with the root account enabled, and TCarr wants to disable it (i.e. revert to the default configuration).

... 

I do understand.  The root account can't be created or deleted.  It is a misnomer to say it is disabled.  It is not disabled but rather it is locked from access by su or login.  Reseting the password via sudo <you know the command> allows this access.  There is no functional difference from knowing a non-hackable  password and not using it and having an inscrutable password for root and not using it.

---

### Post by doas777 on 2011-06-24
> **capscrew said:**
> I do understand.  The root account can't be created or deleted.  It is a misnomer to say it is disabled.  It is not disabled but rather it is locked from access by su or login.  Reseting the password via sudo <you know the command> allows this access.  There is no functional difference from knowing a non-hackable  password and not using it and having an inscrutable password for root and not using it.
 check  man [passwd]("http://unixhelp.ed.ac.uk/CGI/man-cgi?passwd") to see what -l does. I think you will agree 'lock/disable' is a good term for it. it is not random as has been mentioned. you are correct, when using sudo you are invoking root privilege and identity, but you are not logging in as root, since root will never accept any password for login while locked.

---

### Post by capscrew on 2011-06-24
> **doas777 said:**
> check  man [passwd]("http://unixhelp.ed.ac.uk/CGI/man-cgi?passwd") to see what -l does. I think you will agree 'lock/disable' is a good term for it. it is not random as has been mentioned. you are correct, when using sudo you are invoking root privilege and identity, but you are not logging in as root, since root will never accept any password for login while locked.

We've probably spent more time on this subject than need be.  Nonetheless```
 -l     This  option  is used  to  lock the specified account...
```To me this does not mean that the account is disabled in any way.  It does mean that there is no access to the account.  In addition the root account in this case still functions.  All processes owned by root still function.  This was a concern of the OP.

---

### Post by TCarr on 2011-06-24
Thank all of you for your replies in this discussion. I've issued the command that Bachstelze has given and it works for our purposes. I also thank you for the discussion as it brings some insight into exactly what is going on when one "locks" the account. This seems exactly what I was looking for.

---

