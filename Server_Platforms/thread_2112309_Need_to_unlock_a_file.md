---
title: "Need to unlock a file"
date: 2013-02-04
forum: Server Platforms
---

### Post by scegg on 2013-02-04
Hello.

I typed a command to lock a file to make sure that all users, includes root, cannot change the file (read only).
But sadly, I forget that command.

Is there any one know that command and how to reverse it?
Thanks.

sudo or chmod are not the solution.

---

### Post by scegg on 2013-02-04
chattr +i to lock,
chattr -i to unlock....

I got this by google and have no way to delete this post.@@

Thanks all any way.

---

### Post by volkswagner on 2013-02-04
If you only changed permissions, chmod is the answer.

What are the current permissions?

```
ls -al /path/to/file
```

If you used some other command, but cant remember, you can check your history.

```
less .bash_history
```

---

