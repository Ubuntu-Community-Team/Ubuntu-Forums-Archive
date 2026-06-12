---
title: "How can &#305; track files history multiple server with which user make changes this files"
date: 2021-02-21
forum: Server Platforms
---

### Post by altinpark on 2021-02-21
[COLOR=#242729][FONT=Arial]Is there a method that I can use to keep track of who made changes in certain files on several servers (with the user connected to that machine, because all users have sudo authority and everyone is root and doing so) and when? I've tried svn and etckeeper, I can't keep track of which user has made the change in sv, and in etckeeper, commits are thrown on the root side in auto commit option, I can't follow who made the change. When there is a change I want to make (real time or with a check in a certain time, for example once an hour) 
1- The changed file and the change can be diff of the old and new version. 
2- which user made that change[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For example, you logged in to the server with the demo1 user with ssh and was rooted with the sudo su command, then a change was made in /etc/nginx/nginx.conf. How can I track this with etckeeper or another system including the changes made and who did it, I already have demos with svn and etckeeper, if you have a point to ask, please feel free to ask.[/FONT][/COLOR]

---

### Post by TheFu on 2021-02-21
**_Poor admin controls are your problem. Not tracking._**

Allowing more than 2 people unlimited sudo is foolish.  Providing all users access is borderline idiotic. Users should never have more access than needed on any system. Period.  If one user only needs sudo to view a log file, create a cmd_alias only for exact purpose in the sudoers file and provide that user only with that authority, no more.  If you need to allow modification of  /etc/nginx/sites-available/10xxxxxx for 1 userid, then setup a sudo Cmd_Alias just for that.  Don't let people touch /etc/nginx/nginx.conf.

On production systems, developers and end users shouldn't even have a login.  Force them to put their changes somewhere else, check them into a version control system, then they can request those changes be pulled into production, which would be automatic, after your peer-review process is complete.  No peer review, then don't pull the changes.

In theory, every sudo command is logged in the auth.log file, but there are ways around that which we won't spell out here. You can block using those commands in the sudoers file. This would force them to only use methods of sudo which are logged.  But really, they shouldn't even be allowed onto a production system directly.

If you need to keep hourly versions, but not as backups, you can use advanced file system methods built into LVM or ZFS to create hourly snapshots.  You'll want to clean the old snapshots out, since they do take storage as files are changed.  Snapshots are not backups. They just lock blocks for a specific point in time.

---

