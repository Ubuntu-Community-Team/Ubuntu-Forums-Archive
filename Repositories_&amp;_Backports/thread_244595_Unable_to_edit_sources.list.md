---
title: "Unable to edit sources.list"
date: 2006-08-26
forum: Repositories &amp; Backports
---

### Post by ronocdh on 2006-08-26
I do not have permission to save my sources.list file, so I can't add repositories to it. I've tried doing it through the GUI, by navigating to the file, but it won't let me overwrite the current file. I can Save As and choose a different name, but that doesn't really help me, because the new list isn't read.

I've also used $sudo gedit /etc/apt/sources.list, which does absolutely nothing, doesn't even pull up a window for me, just generates another prompt. Any ideas? I guess I don't fully grasp the idea of root permissions, but I thought that typing "sudo" would give me the right to do pretty much anything.

---

### Post by paddy1978 on 2006-08-26
Perhaps the problem could be that you're trying to edit it while something else is using it? I've had problems when forgetting Synaptic was open then trying to install stuff at the command line.

Does 'sudo' work for you otherwise? i.e. is your user account enabled to use 'sudo', it should be if it was the default account created at install. (Typing 'groups' will let you check - 'admin' should be listed.)

Perhaps the files somehow got the wrong permissions? Try:
```
ls -l /etc/apt/
```

This should give a line similar to:
```
-rw-r--r-- 1 root root  2934 2006-08-21 17:00 sources.list
```

This means that it's owned by root, and is read/write for root, and just read for others. If it doesn't look like this for some reason then that could be the cause (and post back if that's the case....).

---

### Post by ronocdh on 2006-08-26
Thank you for the response. This is what I got when I tried your suggestion: 

```
total 36
-rw-r--r-- 1 root root   30 2006-06-01 22:34 apt.conf
drwxr-xr-x 2 root root 4096 2006-06-01 22:39 apt.conf.d
-rw------- 1 root root    0 2006-05-30 20:51 secring.gpg
-rw-r--r-- 1 root root 1659 2006-08-26 15:08 sources.list
-rw-r--r-- 1 root root 1659 2006-08-26 15:21 sources.list.backup
drwxr-xr-x 2 root root 4096 2006-08-26 15:08 sources.list.d
-rw-r--r-- 1 root root 1782 2006-08-26 15:08 sources.list.save
-rw------- 1 root root 1200 2006-05-30 20:51 trustdb.gpg
-rw-r--r-- 1 root root 2393 2006-05-30 20:51 trusted.gpg
-rw-r--r-- 1 root root 2381 2006-05-30 20:51 trusted.gpg~
```

I have never had an issue with sudo before, but for some reason I don't have permission to edit this file! I've been working on it for two days, I'm about to reinstall. =/

---

### Post by paddy1978 on 2006-08-27
Really wierd - I can't think what might be causing this. A re-install should certainly cure it though!

On the off chance you haven't actually re-installed yet, then a final thing to try would be booting into recovery mode, where you get just the root prompt. Can you edit the file from there? (e.g. with nano):
```
nano /etc/apt/sources.list
```

If this works, you could just replace the file with a new version - e.g. from here [http://www.ubuntuforums.org/showthread.php?t=185758]("If you haven't yet re-installed then a final thing to try might be putting a new sources list in. I'm using this one [URL="http://www.ubuntuforums.org/showthread.php?t=185758")"]If you haven't yet re-installed then a final thing to try might be putting a new sources list in. I'm using this one [http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")[/URL]

---

### Post by tzulberti on 2006-08-27
You could also edit de source list form Synaptic (Settings, Repositories).

---

### Post by Cynical on 2006-08-27
Or you could delete it and create a new one

---

### Post by ronocdh on 2006-08-28
Thanks for the responses, guys. I did reinstall before I had a chance to view paddy's advice, and now I really wish I'd thought to try recover mode. Either way, the problem is indeed solved: I can edit sources.list on my fresh install!

As for deleting the file: the issue was one of permissions, so I couldn't move, delete, rename, or edit the file. In Synaptic, I know how to add repositories such as multiverse and universe, but can one add any respository, such as beerorkid's? (I was trying to get xgl running for pretty cube effects. I've since failed miserably and think that I shall give it up for the time being.)

Thanks again guys!

---

