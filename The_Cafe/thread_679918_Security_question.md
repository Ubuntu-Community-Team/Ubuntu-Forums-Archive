---
title: "Security question"
date: 2008-01-27
forum: The Cafe
---

### Post by Mateo on 2008-01-27
Is it possible to prevent a user from seeing the contents of another users home directory?  For example, say there is 2 users, A and B.  What if you don't want A to see what's in B's home directory.  By that I don't just mean not having write permissions, or not having read permissions, but also not having permission to see the file names or anything.  Is this possible?

Also, can you give users permission to install applications, or can root only do that?  I would like to give certain users permission to install software, but that doesn't mean I want them to have the root password where they could do other root stuff.

Thanks.

---

### Post by peabody on 2008-01-27
Not sure about the installation-of-software part, however, to make it so other users can't see your home folder, just set it's permissions to rwx (read, write and execute) for owner only.

[Edit]

Actually, you can make it so that they can install software but nothing else.  Trouble is, you'll have to edit the sudoers file to do this.  **only ever do this through a terminal with the visudo command!**.  The line would look something like this and would be added to the user privilege specification:

```
testdude yourhostname=(root) /usr/sbin/synaptic
```

Where testdude is the username of the user and yourhostname is your hostname as setup when you installed (should be on your terminal prompt).  localhost didn't seem to work.

This will allow them to run synaptic, but nothing else.

---

### Post by Mateo on 2008-01-27
Thanks.

For the first part, if you set permissions to rwx for the owner only, could another user open that folder in Nautilus, or cd into it in the terminal and see the file names?  The goal is to not let them do even that.

---

### Post by peabody on 2008-01-27
> **Mateo said:**
> Thanks.

For the first part, if you set permissions to rwx for the owner only, could another user open that folder in Nautilus, or cd into it in the terminal and see the file names?  The goal is to not let them do even that.

They would have no way of doing that with those permissions.

But don't take my word for it, why don't you login as that user and see for yourself that it works?

---

### Post by Mateo on 2008-01-27
ohh, i see.  so setting the home directory as rwx, they don't have permission to "read" the home directory.  I like that.  Does it work for all recursive directories/files as well, even those that have yet to be created?

---

### Post by peabody on 2008-01-27
> **Mateo said:**
> ohh, i see.  so setting the home directory as rwx, they don't have permission to "read" the home directory.  I like that.  Does it work for all recursive directories/files as well, even those that have yet to be created?

No, but they would have to be sophisticated enough to guess the exact pathname of a file they wanted to look at.

If you are particularly paranoid, you can try this in a terminal.

```
find $HOME -type d -exec chmod 700 {} \;
```

That will recursively set every directory in your home folder to rwx only.

---

