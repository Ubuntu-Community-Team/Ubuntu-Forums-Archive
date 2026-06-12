---
title: "Does Tar mark files as in use when archiving"
date: 2013-04-23
forum: Server Platforms
---

### Post by beboylips on 2013-04-23
Hello community,

As the title says, could anyone please tell me if tar is locking files as in use when creating an archive from them? I run a server that has its files constantly updated so they cannot be locked.

Thank you,
Beboy

---

### Post by Lars Noodén on 2013-04-23
tar takes the files as it finds them even if they are in use 'locked' or not.  If the lock file happens to be in the set of files that tar takes, then it will be taken, but only then.

---

### Post by ajgreeny on 2013-04-23
I'm not sure about tar, but I have a password protected p7zipped single text file which I use to store info that, whilst not of value to other people, is nevertheless not for general reading.  If I write to that text file when I have unzipped it and save the new version, a dialog box appears and asks if I wish to update the archive.  I presume the same would be true if there were more than one file in the archive, but I have never needed to try it out.  I would expect tar to act similarly but perhaps it does not do so.  Try it out on a few files to see what happens; you'll soon be able to see.

---

### Post by beboylips on 2013-04-23
So what happens when a file being archived by tar is being modified by a program at the same time?

---

### Post by Lars Noodén on 2013-04-24
> **beboylips said:**
> So what happens when a file being archived by tar is being modified by a program at the same time?

If it is written at precisely the same time as tar reads it, you will get a warning:

"file changed as we read it"

tar will read it anyway but will obviously only record what was available at the instant it read the file.  If there is a little pause in the writing and tar happens to read during that pause, there will be no warning.

I'm not sure how it would go with a giant file where the beginning gets changed before tar reads the end, but I expect it would give a similar warning.

---

