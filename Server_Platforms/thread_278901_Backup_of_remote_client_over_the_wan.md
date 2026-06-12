---
title: "Backup of remote client over the wan"
date: 2006-10-17
forum: Server Platforms
---

### Post by olemadsen82 on 2006-10-17
Hi.

I need to make backups of remote clients connected to the wan on different locations. Because its on the wan and its not possible to use any dynamic dns and such, i need the clients to establish a connection to the server, not the server connecting to the client as it would normally work.

I tried with backuppc and it actually has all the functions i need ( differetial backup, web interface and schedueling ). But it dosnt support client push.

I know there is a security problem with this solution, but its what i need.

The clients are winx machienes and the server is ubuntu.

Does anyone habe some good advice.

Thanks in advance.


....Sorry about the spelling....

---

### Post by MJN on 2006-10-17
Rsync will fit the bill - fast (only transfers the *parts* of the files that have changed and can support compression too), secure (tunnels over SSH), supports push/pull, can be restarted from where it last left off and is pretty straightforward to use given its simplicity (widely implemented/supported too if you get into difficulty - plenty of others will be able to help you).

[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)

Highly recommended!

Mathew

---

