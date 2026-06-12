---
title: "SVN does not store old revisions.."
date: 2007-07-25
forum: Server Platforms
---

### Post by Naatan on 2007-07-25
Hi,

I have subversion setup on my Ubuntu server but I just found out that it does not seem to store older revisions, I tried to restore an older version of a file and got the error message that the file could not be found in the repository..

Now it does have a complete history but it does not seem to store the actual data of the file..

Perhaps I'm doing something wrong, or maybe it's a setting I have to configure..

can anyone help me?

---

### Post by Naatan on 2007-07-25
man, posted on 2 big forums and no replies.. isn't there anyone here able to help?

---

### Post by jtc on 2007-07-25
How about pasting the commands you've been using, the responses you've gotten, information about your repository, etc? If you want people to help you really need to give them something to work with.

---

### Post by meatpan on 2007-07-25
Can you show the svn command you ran, and the associated error output?

You should be able to update a revision to an older version by running 'svn update -r <number>' where <number> is the old revision number.

The same is true for checking out an old revision.  Run 'svn checkout -r <number>'

---

