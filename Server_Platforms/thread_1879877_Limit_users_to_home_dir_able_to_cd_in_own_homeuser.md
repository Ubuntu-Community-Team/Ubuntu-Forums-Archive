---
title: "Limit users to home dir: able to cd in own /home/user"
date: 2011-11-12
forum: Server Platforms
---

### Post by Jonher937 on 2011-11-12
Hi!

What I basicly want to do is to limit the users to their own /home/user directory. 
So they can't cd back to /home/

But they should be able to cd to /home/user/dir1 /home/user/dir2 and so on.

I have tried rbash but it deactivates all cd commands.

****EDIT*****
It will be used to limit users to cd over ssh

Any ideas? 

Thanx! 
/ Jonher937

---

### Post by memilanuk on 2011-11-12
This thread looks very similar to what you are asking...

[http://ubuntuforums.org/showthread.php?t=1876221](http://ubuntuforums.org/showthread.php?t=1876221)

---

### Post by Lars Noodén on 2011-11-12
If you're going to be limiting access via SSH then you can use the built-in [ChrootDirectory](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html).  Note that the directory that you chroot to must be owned by root and not writeable by anyone else.

---

### Post by apollothethird on 2011-11-12
> **Jonher937 said:**
> Hi!

What I basicly want to do is to limit the users to their own /home/user directory. 
So they can't cd back to /home/

But they should be able to cd to /home/user/dir1 /home/user/dir2 and so on.

I have tried rbash but it deactivates all cd commands.

****EDIT*****
It will be used to limit users to cd over ssh

Any ideas? 

Thanx! 
/ Jonher937

You can make /home "chmod go-r".  This way they won't be able to read the content of "/home" directory, but they could still go to the other directories you specified should be available.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Jonher937 on 2011-11-12
Thank you for the reply!

But I want to do this so it affects about 200users.
This seems like a long procedure for every user.

---

### Post by apollothethird on 2011-11-12
> **Jonher937 said:**
> Thank you for the reply!

But I want to do this so it affects about 200users.
This seems like a long procedure for every user.

You're welcome.

The command I gave you takes less than two seconds to execute.  It'll affect all users and only has to be typed in once.  It'll affect all current and future users.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Lars Noodén on 2011-11-12
> **Jonher937 said:**
> Thank you for the reply!

But I want to do this so it affects about 200users.
This seems like a long procedure for every user.

This will chroot all users that are members of the group "webmasters"

```

Match group webmasters
   ChrootDirectory /home
   X11Forwarding no
   AllowTcpForwarding no
   ForceCommand internal-sftp

```

(from sshd_config)

---

### Post by Jonher937 on 2011-11-12
> **apollothethird said:**
> You're welcome.

The command I gave you takes less than two seconds to execute.  It'll affect all users and only has to be typed in once.  It'll affect all current and future users.



Is there any way to undo this if it doesn't work like I want?

---

### Post by apollothethird on 2011-11-12
> **Jonher937 said:**
> Is there any way to undo this if it doesn't work like I want?

By default the attribute chmod 755.  So you can change it back by typing:

```

chmod 755 /home

```Or you can type:

```

chmod go+r

```Both will bring it back to the default.

By the way the modified mode with "chmod go-r" is "chmod 711".

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

