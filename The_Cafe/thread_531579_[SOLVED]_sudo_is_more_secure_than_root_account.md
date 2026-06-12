---
title: "[SOLVED] sudo is more secure than root account ???"
date: 2007-08-21
forum: The Cafe
---

### Post by dewcansam on 2007-08-21
Here is a discussion for you all.

Is sudo better than a root account ?

Here is my argument:
Being new to Ubuntu and having used RH, Mandrake and others for years now. I have come to rely on the root/sysadmin account. Started using Ubuntu and loved it, didn't mind doing sudo or even sudo -i. Even reading that it is implemented this way for security reasons. However, I started thinking today that this is shouldn't be the case. My thought is this with a root account ONLY those who know the root password have root access. ANYBODY can do a 'sudo' command, even those people whom i do not want installing apps and such. So wouldn't sudo be more of a comprimise than a root account?

---

### Post by Dimitriid on 2007-08-21
Your user account effectively becomes as good as the "root" account, so other than perhaps being harder to kill systems by accident and the fact that sudo eventually times out, I do not think its that different or that much more secure.

---

### Post by happysmileman on 2007-08-21
Sudo-ing a command is just as secure as running that command as root.

But running stuff such as browsers as root is very insecure because a single security flaw could wipe out your hard drive, not just that users data

Oh and you can take away access for the "sudo" command, in fact when I created my brother's account he didn't even have access in the first place, I had to give him that access

---

### Post by Bachstelze on 2007-08-21
> **dewcansam said:**
> ANYBODY can do a 'sudo' command, even those people whom i do not want installing apps and such.

Wrong. Next time you want to make such statements about something, please read a bit about it before, okay ?

---

### Post by dewcansam on 2007-08-21
> **HymnToLife said:**
> Wrong. Next time you want to make such statements about something, please read a bit about it before, okay ?

Instead of blasting me try and educate me. I stated that I was new to the whole sudo command. 
How do you turn on / off the use of the sudo command of a particular user ?

However, now i am educated.
doing a man sudo resulted in reading that /etc/sudoers file is read in
less /etc/sudoers results in reading that anybody of the admin group can issue the sudo command
less /etc/group shows me who is in the admin group

problem solved

---

### Post by Bachstelze on 2007-08-21
So then insteaof just stating that "ANYBODY can do a 'sudo' command", you should have asked something like that :

"Okay, so Ubuntu uses that sudo thing instead of the root account I'm used to, but I don't understand how it can tell which users can run 'sudo' commands and which users cannot. Surely, not everyone can run commands as root with sudo, it ould be awfully insecure. Can anyone explain that to me please ?"

Don't you think it would be a better way to get help ?

---

### Post by alphomega on 2007-08-21
Dont forget that if you have an enabled root account and ssh opened in the filewall, only your root password needs to be hacked as the username is root.  With enforcing sudo the hacker will need to hack into your user account so will need to hack your username and password, then hack the sudo command with the super users password.

To check/edit your sudoers file just run visudo

---

### Post by kopilo on 2011-05-17
> **alphomega said:**
> Dont forget that if you have an enabled root account and ssh opened in the filewall, only your root password needs to be hacked as the username is root.  With enforcing sudo the hacker will need to hack into your user account so will need to hack your username and password, then hack the sudo command with the super users password.

To check/edit your sudoers file just run visudo
Or you could learn how to configure SSH correctly and not allow direct access to root. :p

[http://ubuntuforums.org/showthread.php?t=523477](http://ubuntuforums.org/showthread.php?t=523477)

---

### Post by el_koraco on 2011-05-17
necroposting! off with his head!

---

