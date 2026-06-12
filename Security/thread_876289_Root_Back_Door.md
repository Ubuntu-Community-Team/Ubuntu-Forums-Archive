---
title: "Root Back Door"
date: 2008-07-31
forum: Security
---

### Post by dennismoore1 on 2008-07-31
To become root without a password use the following code.
su
(do not type a password)
sudo su

you will be perminant root untill that terminal exits

---

### Post by tamoneya on 2008-07-31
first of all you dont need the first "su".  Also this isnt exactly a back door or an exploit.  If you are able to use the sudo command you have root privileges anyways.

---

### Post by aysiu on 2008-07-31
> **dennismoore1 said:**
> To become root without a password use the following code.
su
(do not type a password)
sudo su

you will be perminant root untill that terminal exits
If I type ```
su
``` and don't type a password, I get the error message ([color=red]circled in red[/color]) ```
su: Authentication failure
``` If I then type ```
sudo su
``` I'm prompted for a password ([color=green]as you can see circled in green[/color]).

So, no, this isn't a "root back door."

If you really want to become root without a password, just boot into recovery mode.

---

### Post by dje on 2008-07-31
> **dennismoore1 said:**
> To become root without a password use the following code.
su
(do not type a password)
sudo su

you will be perminant root untill that terminal exits

what probably happened was you performed a command with sudo a few minutes before (and since it doesn't ask you your password again for 15 minutes after putting in your password using sudo), therefore when you performed 'sudo su' and it did not ask you for your password giving the illusion that it is a 'back door' but it isn't ;)

dje

---

### Post by aysiu on 2008-07-31
> **dje said:**
> what probably happened was you performed a command with sudo a few minutes before (and since it doesn't ask you your password again for 15 minutes after putting in your password using sudo), therefore when you performed 'sudo su' and it did not ask you for your password giving the illusion that it is a 'back door' but it isn't ;)

dje
That still doesn't explain why it's okay to enter no password for *su*. There should still be an authentication failure for that first command.

---

### Post by dje on 2008-07-31
> **aysiu said:**
> That still doesn't explain why it's okay to enter no password for *su*. There should still be an authentication failure for that first command.

maybe it did, it certainly does for me, and he did not explain this in his post?

---

### Post by cdenley on 2008-07-31
> **dje said:**
> what probably happened was you performed a command with sudo a few minutes before (and since it doesn't ask you your password again for 15 minutes after putting in your password using sudo), therefore when you performed 'sudo su' and it did not ask you for your password giving the illusion that it is a 'back door' but it isn't ;)

dje

I agree. Try using "sudo -K", then show us the "back door".

---

### Post by sc0g on 2008-07-31
**sudo -i** is literally the same as **su -** on sudo-enabled Debian distros.

The reason you are able to do **sudo su** is because you probably haven't set a root password. By installation default, there is no root password on Ubuntu/Kubuntu/Xubuntu, etc...

---

### Post by Thorzilla on 2008-07-31
So is there a way to log out after performing all the commands you needed to, so that sudo asks you for a password the next time?

---

### Post by aysiu on 2008-07-31
> **Thorzilla said:**
> So is there a way to log out after performing all the commands you needed to, so that sudo asks you for a password the next time?
You can change the *sudo* timeout to 0 minutes by following [these instructions](http://ubuntuforums.org/showthread.php?p=116697#post116697).

---

### Post by Oldsoldier2003 on 2008-07-31
```
sudo -k
``` will revoke the users timestamp and require a password on the next sudo

---

### Post by kevdog on 2008-07-31
sudo su

Type all your commands


exit

Back into normal shell

---

### Post by Gun_Smoke on 2008-07-31
This whole thread could be forgotten if you just give your self root.  Use it if you want...

---

### Post by Oldsoldier2003 on 2008-08-01
> **Gun_Smoke said:**
> This whole thread could be forgotten if you just give your self root.  Use it if you want...
But of course on the Ubuntu Forums we don't advocate enabling the root account, we prefer to educate users on the Ubuntu security model which uses sudo...

---

### Post by Thorzilla on 2008-08-01
> **aysiu said:**
> You can change the *sudo* timeout to 0 minutes by following [these instructions](http://ubuntuforums.org/showthread.php?p=116697#post116697).

Cool! Thanks.

---

### Post by chaoman on 2009-03-20
If you want to never have to type in a password for sudo more than once, just tell it never time out and keep the terminal window open. Ubuntu rulz. Also, DOWN WITH DA PATRIOT ACT! ](*,)

---

### Post by cariboo on 2009-03-20
Another nercothread brought back from the dead. You can accomplish the same thing using:

```
sudo -i
```

Without having to modifying /etc/sudoers.

To @chaoman, you could have found something a little better for your first post. :)

Jim

---

