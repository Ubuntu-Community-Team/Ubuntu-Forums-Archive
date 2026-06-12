---
title: "Would using svn to backup be stupid?"
date: 2010-11-12
forum: The Cafe
---

### Post by nolag on 2010-11-12
I was thinking, I know svn is meant for version controll, but I would it be a bad idea to use it to backup my system?
 
Considering how it works I was thinking that the inital commit would be huge, but after that it would not take too much space, right?  I would use a recursive add to make sure that I get all new folders and files.  
 
I know it was not the intent of svn, but how different is svn from shadow copy windows offers?  They both only commit differences in files, they both allow restorepoints to dates/times.  
 
I guess the only things I would need to think of is how to stop duplicate files from being created if something is copied (not svn copied) by a user.
 
A part of me is saying "Don't do it it's horrible" another part it like why?
 
Looking for any feedback!
 
Thanks 
 nolag

---

### Post by doorknob60 on 2010-11-12
I've heard good things about using git for backup, I don't see why svn would be any different. Go for it.

---

### Post by freebeer on 2010-11-13
Have you looked at rsync for backups?  Rock solid in my experience.

---

### Post by Barrucadu on 2010-11-13
I did consider git for backing up my system, but instead went for incremental backups with rsync. No real reason, I could just find more information about using rsync as a backup utility, so I went with that.

However, I do have several git repos which I use to backup/publish some things (my config files in ~, for example).

---

### Post by Tibuda on 2010-11-13
yes, you better use git, bzr or mercurial

---

### Post by nolag on 2010-11-15
Thank you all for your replies, I will look into these programs.  I was thinking about what I initially asked and only thought of one actual problem, what happens if I want to add something to a repo online or something XD.

---

### Post by /dev/zlow on 2010-11-15
This is a good idea, let us know your results!

---

