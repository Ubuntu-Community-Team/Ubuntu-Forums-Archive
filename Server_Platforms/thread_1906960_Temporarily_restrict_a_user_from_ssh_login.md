---
title: "Temporarily restrict a user from ssh login"
date: 2012-01-10
forum: Server Platforms
---

### Post by lykwydchykyn on 2012-01-10
I have an ssh server which various users log into to gain access to my network.

I need the ability to temporarily "toggle" a given user's ability to log in.

What's the most effective way to do this?  I was thinking of writing a script to change the user's shell to /bin/false, but I didn't know if there was a way around this.

---

### Post by Habitual on 2012-01-10
> **lykwydchykyn said:**
> ...I was thinking of writing a script to change the user's shell to /bin/false, but I didn't know if there was a way around this.

Change their password involves additional steps.
I'd do as you suggested. :)

---

### Post by lykwydchykyn on 2012-01-10
> **Habitual said:**
> Change their password involves additional steps.
I'd do as you suggested. :)

Changing the password isn't even an option, since (a) I need to be able to re-enable when necessary and (b) they use key-based authentication.

So is the shell the most effective method?

---

### Post by Habitual on 2012-01-10
> **lykwydchykyn said:**
> Changing the password isn't even an option, since (a) I need to be able to re-enable when necessary and (b) they use key-based authentication.

So is the shell the most effective method?

I'd say it is.

---

### Post by jchung on 2012-01-10
You could add the 'AllowGroups' config to your sshd_config file.

Basically, create a group like 'sshusers' and configure your SSH daemon to only allow members of the sshusers group to log in.

Then, to disable a user's SSH login, you remove them from the group. To enable their SSH login, you add them to the group.

Joo

---

### Post by Lars Noodén on 2012-01-10
Actually I was going to suggest the reverse of that, [DenyGroups](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html).  

```

DenyGroups lockedout

```

Then add or remove that user from a group with a script.

```

#!/bin/sh

if groups ${1} | grep lockedout; then
  gpasswd --delete ${1} lockedout && echo ${1} enabled
else
  gpasswd --add ${1} lockedout && echo ${1} disabled
fi

```

---

### Post by SlugSlug on 2012-01-10
could you not just 
```
sudo passwd USER -l   
```

and lock the account?

---

### Post by Lars Noodén on 2012-01-10
> **SlugSlug said:**
> could you not just 
```
sudo passwd USER -l   
```

and lock the account?

From what I've tried, using SSH keys for authentication bypasses the lock.

---

### Post by jchung on 2012-01-11
> **Lars Noodén said:**
> Actually I was going to suggest the reverse of that, [DenyGroups](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html).  

```

DenyGroups lockedout

```

Then add or remove that user from a group with a script.

```

#!/bin/sh

if groups ${1} | grep lockedout; then
  gpasswd --delete ${1} lockedout && echo ${1} enabled
else
  gpasswd --add ${1} lockedout && echo ${1} disabled
fi

```

That works too. And a useful little script to simplify the whole process. 

Personally still prefer using Allowgroups instead of Denygroups, as I'd rather have a default deny all policy instead of a default allow all policy.

Joo

---

### Post by Azdour on 2012-01-12
Hi,

Would you still have to restart the ssh service after using DenyGroups or AllowGroups?

---

### Post by Lars Noodén on 2012-01-12
> **Azdour said:**
> Would you still have to restart the ssh service after using DenyGroups or AllowGroups?

The only thing needed for the user to be permitted or disallowed login is to add or remove them from the group.  That's one line with [gpasswd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gpasswd.1.html). 

Also, it's easier to toggle group membership than to swap out the shell.  Setting the shell to [font=Courier New]/bin/false[/font] works, too, but you lose the original value whether it was bash (default), ksh, zsh or tcsh.

---

### Post by jchung on 2012-01-13
> **Azdour said:**
> Hi,

Would you still have to restart the ssh service after using DenyGroups or AllowGroups?

Only the first time you add the line or whenever you change the listed groups on the line.

Otherwise, you just add/remove accounts from the groups specified in the config.

---

### Post by Lars Noodén on 2012-01-13
@lykwydchykyn, what solution did you finally arrive at?

---

### Post by lykwydchykyn on 2012-01-13
I'm going with the deny groups thing, though my script locks the password too just for extra measure.  I had to modify it some in an attempt to get it to work on SLES and Ubuntu (turns out there's no way to do that -- SLES's gpasswd and usermod commands are totally different -- so I just rewrote for both).

Default deny would be more technically secure, I guess, but this is only to block the occasional "problem child".

---

