---
title: "Group permissions on directories and files"
date: 2011-01-23
forum: Server Platforms
---

### Post by gpinkston on 2011-01-23
Greetings,
A friend and I are at a loss. 
Scenario:
Server 10.10

We have created a group xxxx on the server, and both of us are members of the group.

Now in the home directory we created a directory of xxxx. With user1 as owner and group xxxx.

We both have access to it without any issues. We can save files there open etc.

Now the issue we have is when user1 saves a file. It's saved with there uid, and the gid is there personal gid, not the xxxx that we set the folder for. And it's set for write for them, however user1 only has read access to the file.

We need to have all directory’s and files saved with the group of xxxx. So we both have the ability to modify all files in that directory tree.


Any assistance would be greatly appreciated.

---

### Post by amra.sonntag on 2011-01-23
```
usermod -gid Group username
```

This way you force the specified Group as primary Group for your user. And it should solve your problem.

You might wanna try this with a non admin user first - not that you delete all others groups by accident and look yourself out of sudoers.

---

### Post by gpinkston on 2011-01-23
Thank you for your response.  
I can set the user default group to xxxx however if i have other directorys that are controled by groups that I'm a member of, then I would still have the issue there as well. But now the group would be defaulting to xxxx. What I need is a way to make all files existing as well as new have my user id, and the directories default group.

---

### Post by egpetrich on 2011-01-28
You should be able to solve your problem with the setgid (set group id) permissions bit in the directory.
```
mkdir -p my_new_directory
chgrp common_group my_new_directory
chmod g+rwxs my_new_directory

```Once the setgid bit is set, any new files or directories created in "my_new_directory" should be part of the "common_group" group.

- Eric Petrich

---

