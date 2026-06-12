---
title: "Persistent control of access to certain apps with groups and permissions"
date: 2009-01-02
forum: Security
---

### Post by sboddy on 2009-01-02
Hi all,

The system in question is in a family house, and I wish to block certain programs from children. Now the obvious way is to set up a parent group, and adjust the binaries permissions from:
```
-rwxr-xr-x root:root
```
to:
```
-rwxr-x--- root:parent
```

My uncertainty is about when these programs get updated through apt. Will apt retain these permissions? I could swear I read of a file that post-upgrade would "fix" permissions. But maybe I'm thinking of another system, as I can't find anything resembling that.

I've done the usual google/forum search, but I'm not finding anything that is clear. Anyone know the answer? Alternatively if you had a better solution for blocking certain apps for kids, I'd love to hear it.

Thanks in advance.

---

### Post by HermanAB on 2009-01-02
The Ubuntu way to have a user with limited capabilities is to use sudo.

Read 'man sudo'.

Cheers,

Herman

---

### Post by sboddy on 2009-01-02
> **HermanAB said:**
> The Ubuntu way to have a user with limited capabilities is to use sudo.

Read 'man sudo'.

Cheers,

Herman

Thanks for the response, but I'm a little :confused: I don't want (or need) to run the program as a different user. That will just create a different permissions issue with the files saved by the program. I just want 2/4 user accounts to be able to run a program, and the other 2/4 accounts to not be able to run it. Perhaps I'm being dense, but I don't understand why I would want to start using sudo? It just seems overly complicated.

---

### Post by handydan918 on 2009-01-02
> **sboddy said:**
> Thanks for the response, but I'm a little :confused: I don't want (or need) to run the program as a different user. That will just create a different permissions issue with the files saved by the program. I just want 2/4 user accounts to be able to run a program, and the other 2/4 accounts to not be able to run it. Perhaps I'm being dense, but I don't understand why I would want to start using sudo? It just seems overly complicated.

Nah, your right. sudo is a non-sequiter here. 
You might be able to test your permissions-durability by setting them the way you want them and then doing ```
sudo apt-get remove<application-name> && apt-get install <application-name>
```

Just a thot...

What about removing the kids from the group "users", if that is the group privileged to run the app in question?
Prolly more than one way to skin this cat....

---

### Post by sboddy on 2009-01-02
> **handydan918 said:**
> Nah, your right. sudo is a non-sequiter here. 
You might be able to test your permissions-durability by setting them the way you want them and then doing ```
sudo apt-get remove<application-name> && apt-get install <application-name>
```

Just a thot...

What about removing the kids from the group "users", if that is the group privileged to run the app in question?
Prolly more than one way to skin this cat....

Yeah, but what else do the kids lose if they're removed from the users group?

As to your suggestion: I think removing the file then reinstalling it is probably not the same thing as an upgrade. Maybe I can come up with a boot script that checks and corrects the permissions if they're not what is desired.

OT: This is exactly the kinds of areas where Canonical should really be trailblazing. Yes, good things get done, but if you really want to make an impression, make it family friendly. Simple things like this require too much arsing about. Shared directories shouldn't bugger up because of permissions. Being able to monitor usage/sites/chats and so on should be easy to do, but optional.

---

### Post by The Cog on 2009-01-03
How about creating a script that changes the permissions? This would make it easy to reset them after an update (I'm not sure if an update will reset permissions but I think it is likely), and also serve as a reminder as to which applications you have modified. You could have it run as part of the boot-up sequence too.

---

### Post by bodhi.zazen on 2009-01-04
What application(s) are you trying to limit ?

---

