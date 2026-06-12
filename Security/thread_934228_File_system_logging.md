---
title: "File system logging?"
date: 2008-09-30
forum: Security
---

### Post by sedd on 2008-09-30
Hi,

An important directory (not porn I promise) has gone missing. My wife says it was there yesterday, but today it's missing. And its really not there, locate turns up nothing. She says she doesn't remember deleting it. She goes into that directory every day, and she thinks maybe our 1 y/o son accidentally kicked the delete key, but I think that's unlikely because he would have had to kick Fn-Shift-Delete (I have a strange keyboard.) 

So I'm hoping that some kind of filesystem logging is enabled by default. If not, can anyone think of any other type of log that might have recorded this? I'm 99% sure that I've not been hacked, although I really don't know how to tell for sure.

Thanks for any help you can give me,
Scott

---

### Post by jms1989 on 2008-09-30
Its not a hidden directory by any chance? Does its name start with a period? Look in your trash to see it was deleted, normally a file doesn't disappear on its own unless its located on a bad sector of the hard disk.

---

### Post by sedd on 2008-09-30
I found it. She had accidentally moved it into another directory. Locate didn't find it because I didn't update the database. Noob mistake.

It's weird though that locate didn't find it _at all._ It didn't list it either at the old or the new location. I guess locate doesn't list files that have been moved, if it doesn't know where they've been moved to.

---

### Post by jms1989 on 2008-09-30
Glad to see you fix it. :) Now you can make the thread as solved.

---

