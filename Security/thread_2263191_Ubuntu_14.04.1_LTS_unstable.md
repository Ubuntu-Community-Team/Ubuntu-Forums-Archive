---
title: "Ubuntu 14.04.1 LTS unstable"
date: 2015-01-30
forum: Security
---

### Post by inotekalt on 2015-01-30
Hello.
i tried to find out does somebody else expirienced such a problem and it looks like i can't find proper answer or solution.
I put in (as read in one ubuntu forum) this command CHMOD -R -V 777 *  in /etc/rc.local in order not to activate every time terminal window in a session to give all privileges to shared files.
After reboot my ubuntu get unstable sending errors information and not setting proper permisions to system.
I removed this comand and after restart it is the same.
Question is how to fix this error and give proper permissions to system in order to worka as it used to work.
Regards

---

### Post by newbie-user on 2015-01-30
Removing the command doesn't undo whatever it already did. What exactly were you trying to accomplish by doing that? I didn't fully understand your post.

---

### Post by fugu2 on 2015-02-01
I would have to say that YOU NEVER SHOULD RUN ```
 chmod -r 777 *  
``` from your rc.local script file. It opens all permissions to every file and directory contained within the current working directory, which I'm not even sure where that is. 
```
$ find / -type f -perm 777 2> /dev/null
```
This will find all the files on you system with 777 permissions
```
$ find / -type d -perm 777 2> /dev/null
```
This will find all the directories on you system with 777 permissions

---

### Post by oldos2er on 2015-02-01
> **inotekalt said:**
> Hello.
i tried to find out does somebody else expirienced such a problem and it looks like i can't find proper answer or solution.
I put in (as read in one ubuntu forum) this command CHMOD -R -V 777 *  in /etc/rc.local in order not to activate every time terminal window in a session to give all privileges to shared files.

Could you please post a link to this thread, or use the 'Report Post' button to let staff know about it? We do our best to remove posts that contain malicious commands, but obviously we can't find them all without help.

> **inotekalt said:**
> After reboot my ubuntu get unstable sending errors information and not setting proper permisions to system.
I removed this comand and after restart it is the same.
Question is how to fix this error and give proper permissions to system in order to worka as it used to work.
Regards

---

### Post by mujahied on 2015-02-03
I Am using the same but i figured it out myself

---

