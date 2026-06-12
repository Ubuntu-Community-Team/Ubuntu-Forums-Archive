---
title: "Permissions Hell....PLEASE HELP"
date: 2009-04-23
forum: Server Platforms
---

### Post by Thaumaturge Jay on 2009-04-23
Ok, so I have 3 sales men who each have a user name (directory) on my FTP server for their clients to privately upload files. i.e.  sales 1, sales 2, sales 3.  Clients logged into Sales 1's folder cannot see the contents of sales 2, etc etc etc.  I have these 3 folders set as their home directories.  All 3 of these are contained inside of "Productions" folder this way production can log in and retrieve files from any/all of the salesmen's folders with a single login.  However, when a client uploads a file into one of the sales folders it becomes locked to the owner and my prodction people cannot download the file off the server?


Just finished upgrading to ubuntu sever 9.04.

I'm not sure what I'm missing in the permissions to get this to work right?  I've tried to change the permissions to "create & delete files" as well as "read & write" for the production user on all 3 of the sales folders but this doesn't seem to help?  I need to have the privacy across the sales folders and I need production to be able to access all 3 with relative ease.

---

### Post by kamaji792 on 2009-04-23
Here is a quick reply.

There are 3 set of permissions for any file/directory.  1)Owner 2)Group 3)Everyone

So assuming that you don't allow access via Everyone.  Then to access a file you need to be the appropriate owner or a member of the appropriate group.

The sales directories are owned by the appropriate sales person/log-on. But all belong to the production group.

The Sales people should not be members of the production group.

Obviously the production people need to belong to the production group so they can access the files in all the directories.

Try a few file permission tutorials.

I will try and check how you got on tomorrow.

All the best

---

### Post by Thaumaturge Jay on 2009-04-24
Thanks, I am familiar with permissions, but I guess I just needed someone to slap me in the face and say "look stupid, do this!"

I won't have time this morning to get it right, but will tinker this afternoon and post my results.  Thanks again!

---

### Post by BkkBonanza on 2009-04-24
Here's an example,
```
[B]sudo chown sales1:prod /home/sales1
sudo chmod 660 /home/sales1[/B]

```
first 6 => sales1 owns the files and has rw perms.
second 6 => members of the group prod will have rw perms on the files.
last 0 => everyone else has no rights.

You can add user Bob to the prod group with,
**adduser Bob prod**
Then Bob has access to r/w the files in sales1 as well as sales1 who owns them. If you want prod to read but not write then use 640 instead.
Also should note that the exec bit needs to be set if you want someone to view directory listings so likely you may want 770 for above then.

Edit: it just occurred to me that you likely want files created in the directories to inherit the group id of the directory and not the group id of the owner. So to do that you need to set the setgid bit like this,
**sudo chmod g+s /home/sales1**

---

### Post by Thaumaturge Jay on 2009-04-24
> **BkkBonaza said:**
> 

Edit: it just occurred to me that you likely want files created in the directories to inherit the group id of the directory and not the group id of the owner. So to do that you need to set the setgid bit like this,
**sudo chmod g+s /home/sales1**


I think this is what I'm after, b/c client uploads file to sales1's folder then that stupid file takes on the owner and won't let me or the production user do anything to the file...


I'll play with this and see if it does it, Thanks!!

---

### Post by Thaumaturge Jay on 2009-04-24
Ok, now I've locked out all the sales users and cannot access those folders via ANY user?  Hmmm

---

### Post by Thaumaturge Jay on 2009-05-04
Ok, so I've got things back to the way they were, sorta...

I'm able to get the users logged in (sometimes) and upload files again, however they are still coming in locked to the user that uploaded...

Also, quite a bit of the time I can not get a user to connect to the server.  Meaning that the connection keeps timing out and then other times it connects just fine?  Not quite sure what is causing this.  Everyone I have test this gets right in, but seems like 75% of the clients that I NEED to have connect to it are having timing out issues?


Just don't get it...

---

