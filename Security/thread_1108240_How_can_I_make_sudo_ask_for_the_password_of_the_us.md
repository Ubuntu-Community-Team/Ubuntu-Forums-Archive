---
title: "How can I make sudo ask for the password of the user specified by &quot;-u&quot;?"
date: 2009-03-27
forum: Security
---

### Post by KIAaze on 2009-03-27
I want the following behaviour:
-Ask for the password of the invoking user by default.
-Ask for the password of the user specified by "-u" otherwise.

How can I achieve this?

edit:
I tried adding "Defaults targetpw", but it doesn't work as expected:
When I try to use "sudo -u SUPERUSER", it gives me a permission denied message.
So when no root password is set, I completely loose the ability to edit /etc/sudoers.
[http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options](http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options)

> Note that if the targetpw Defaults option is set (see sudoers(5)) it is not possible to run commands with a uid not listed in the password database.
Mmh, yes, so how can I add the uid to the password database???

---

### Post by cariboo on 2009-03-27
I'm not sure what you are trying to do. Are trying to run a command as another user. You can use su to switch to another user eg:

```
su username
```

you will be asked for the users password, and then you can enter the command.

From what you wrote it looks like you want to change to a user named SUPERUSER, do you have a user with that name on your computer?

Jim

---

### Post by KIAaze on 2009-03-27
SUPERUSER was just to make it clear that it's an account with superuser permissions.

I'm trying to find a way to create a centralized user account which has root permissions, but requires a password. (basically a root account with a different name)
The idea is to ask for a unique password no matter which user launches the application, while still keeping the standard behaviour of sudo for other uses, which is to ask for the user's password.

However, I'm starting to understand why this might be impossible.
If I could run:
```
sudo -u joe COMMAND
```
and have it ask me for the password of non super-user joe, while still executing COMMAND as root (that's what I wanted), anybody could gain root privileges.

"-u" specifies what user to run the command as, not what password to ask for. :/

The only way I currently see would be to create a user account **which has a password**, but doesn't require a password to run commands as root (using NOPASSWD in /etc/sudoers).
Then one could run:
```
sudo -u SUPERUSER sudo COMMAND
```

P.S.: That's the app I'm trying to do this for: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol) ;)
And it would have to be graphical using gksu/kdesu of course.

The perfect solution would be to change the permissions on every command the app needs to run as root, so it can run it using the special user account.

Mmh, while typing, I just thought of simply adding the special user to the root group... ^^'
Will investigate further as soon as possible.

---

### Post by HermanAB on 2009-03-27
Sounds like you are going about things the wrong way.  I think all you need to do is edit the /etc/sudoers file and set up a group that can only do certain actions.

---

### Post by KIAaze on 2009-03-27
Then why does "sudo -u SUPERUSER visudo" not work if SUPERUSER is part of the "admin" group and the /etc/sudoers file contains:
```
%admin ALL=(ALL) ALL
```
?

---

