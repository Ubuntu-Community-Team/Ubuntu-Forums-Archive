---
title: "Sudo stopped working"
date: 2008-07-28
forum: Security
---

### Post by scottburton11 on 2008-07-28
Sudo worked five minutes ago and now doesn't - all I get is 

```

scott@app1:~$ su root
Password: 
su: Authentication failure

scott@app1:~$ sudo -s
[sudo] password for scott: 
scott is not in the sudoers file.  This incident will be reported.

scott@app1:~$ su -
Password: 
su: Authentication failure



```

I can authenticate normal users, and su to other users. However, other users in /etc/sudoers also can't sudo. 

I have a feeling a reboot would fix this, but I can't. I also don't have physical access to the machine.

Anyone know what's going on here?

---

### Post by kdorf on 2008-07-28
My best guess is you edited the sudoers file without using visudo, and made a typo somewhere.

---

### Post by scottburton11 on 2008-07-28
It's a good guess, but it didn't happen. I think there's actually a different error message associated with a broken /etc/sudoers

I didn't execute any commands - one minute it worked, now it won't. I'm going to call one of the local monkeys for a restart in a few minutes, but I thought I'd ask around here first.

---

### Post by panhandle on 2008-07-28
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=639171&highlight=user+sudoers](http://ubuntuforums.org/showthread.php?t=639171&highlight=user+sudoers)

---

### Post by scottburton11 on 2008-07-28
Thanks for the link.

I figured out what the problem is. I added some users - my login and other admins - to a new group using usermod -G without the -a flag, removing them from the admin group inadvertently. I already had sudo, which is why I didn't notice it until much time had elapsed.

Now to talk some monkeys through a single-user boot....

---

### Post by aysiu on 2008-07-28
Just a side note, you probably don't want to use *sudo -s* ever. It gives you a root terminal but with a user's environment, which can leave you with some user config files owned by root. ```
sudo -i
``` is the preferred way to get a persistent root prompt.

---

### Post by scottburton11 on 2008-07-29
> **aysiu said:**
>  ```
sudo -i
``` is the preferred way to get a persistent root prompt.

Great tip, thanks!

---

