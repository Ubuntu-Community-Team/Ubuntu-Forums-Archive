---
title: "Dirvish &quot;fatal error (2) -- protocol incompatibility&quot;"
date: 2023-10-25
forum: Server Platforms
---

### Post by civilpolisen on 2023-10-25
What does "-- protocol incompatibility" really means?
Data is being copied for 15 minute.

```
ACTION: rsync -vrltH --delete --stats -D -pgo --numeric-ids --exclude-from=/srv/backup/lisa/20231023/exclude --link-dest=/srv/backup/lisa/20231020/tree 123.123.123.122:/ /srv/backup/lisa/20231023/tree
Backup-begin: 2023-10-23 23:03:54
Backup-complete: 2023-10-23 23:19:26
Status: fatal error (2) -- protocol incompatibility
```

---

### Post by MAFoElffen on 2023-10-25
You were using rsync remotely, where if it throws that error, it is usually if the versions are different between the two machines. That is the first thing I would check.

Second if the on the remote, maybe the .bashrc file displays text to console?

---

### Post by civilpolisen on 2023-10-27
Let me try to explain this view. We have this daily script running every night on the servers... quite common, I would assume.
The days are marked as red... but script is behind schedule, I can live with that!
The error and this thread is about the server and the computer named Lisa in the list.

The server Lisa is constantly failing! That's the issue! (Hugo is also failing, but that server is shut off... so, it's a different issue!)

---

### Post by MAFoElffen on 2023-10-27
Sideline Note: The Moderators are going to have a field day warning you not to post full graphics inline within a post, as many users viewing the Forum, that causes their browsers to balk... LOL. Better to just attach them to the post. Or better yet, copy the text to paste, edit to sanitize it, posted within CODE Tags.

The virtual server is 20.04, which is probably (trying to remember) rsync version 3.1.3... The host running the remote jobs is what? 22.04, which is rsync version 3.2.7...

Try this... ssh into that server using the 'user' that job uses for the remote connection...
```

touch ~/.hushlogin

```
That will disable the motd banner and try to disable any text echo'ed from .bashrc during the initial shh login connection of that user... Rerun the job to test. Or rather, maybe just rsync command that job uses with that server...

---

### Post by civilpolisen on 2023-11-01
Thank you for your reply! 
I will write the answer!
I pasted the line of code in the Terminal and then waited until the error occurred... 

```
rsync -vrltH --delete --stats -D -pgo --numeric-ids --exclude-from=/srv/backup/lisa/20231023/exclude --link-dest=/srv/backup/lisa/20231020/tree 123.123.123.122:/ /srv/backup/lisa/20231023/tree
```

Inside a user there are small log files and by remove all, but two files, solved the problem! It was some 780.000 files...!

I will edit this post when I know where these files are located, I thought I had the answer, but I was wrong...!
I'll be back! :-)

---

### Post by MAFoElffen on 2023-11-01
I understand. LOL... Yup. Been there.

---

