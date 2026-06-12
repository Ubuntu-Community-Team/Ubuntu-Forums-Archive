---
title: "Creating a Security-Less User"
date: 2011-04-05
forum: Security
---

### Post by Falkoner on 2011-04-05
I'm trying to modify an existing user so that any files they create can be at least read(although writing and execution would be nice) by any other user.

The reason is because I need the daemon running my Apache server to be able to access files created by a daemon running under this user, files which will be created and accessed in real-time.

Any help is appreciated :)

---

### Post by Drenriza on 2011-04-05
log on the user you want to make the changes for and type

```
umask 1337
```

This will do so your user is the only one (besides root) who can delete any files created by the user.
Set the users rights to read + write
groups read + write
all others read + write + execute

This will not change any existing files created by the user. But all new files created by this user gets these rights.

Was it this you were looking for?

---

### Post by Falkoner on 2011-04-05
If I understand you correctly, logging into my user and typing umask 1337 will make it so all other users can read, write, and execute files he creates, but only that user and root will be able to delete those files, if that's the case, then that solution works.

The fact that the mask was 1337 makes me think the previous post was a joke, that and it's outside the range of umask, so can I get some serious help?

Does umask 000 solve my problem?

---

### Post by BkkBonanza on 2011-04-05
umask is may be what you need. See **man umask** or try the [wiki]("http://en.wikipedia.org/wiki/Umask"). You would need to run it before thre daemon starts as it doesn't have a permanent effect.

Another, perhaps better, way is to use the ["set gid" bit]("http://en.wikipedia.org/wiki/Setuid"). If the files will always be in a certain location then you can affect how they are created by making that location chmod g+s.
eg.

sudo chgrp www-data /var/www/dafiles
sudo chmod g+s /var/www/dafiles

(which makes files created in that directory get the groupd id of the directory rather than the process creating the files)

---

