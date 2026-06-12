---
title: "Best solution for backup /home/user to datacenter"
date: 2010-08-23
forum: Server Platforms
---

### Post by maikel.b on 2010-08-23
[FONT=Calibri][SIZE=3]Hello, I am looking for the best solution for backup, I want to backup the /home/user[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I know about rdiff, and rsync but is there a better solution for backup these folder.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]And the security must be good, [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The backup I want to make is from a server to a server in a datacenter.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Both servers are running on UBUNTU 9.10[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Thanks for your solutions… Greetz [/SIZE][/FONT]

---

### Post by Thijs Koetsier on 2010-08-23
Hello maikel,

Can you explain why the options you gave are not sufficient for you? 

Backing up file folders can be done in several ways and a cronjob with rsync usually is a good way of doing it, but there are others like tarballing and using ncftp, but the result still is the same.

---

### Post by LightningCrash on 2010-08-23
Are they on public networks or internal networks? If internal, NFS mounts and tar work fine.
Don't forget the output of sfdisk for your partition layout.

---

### Post by maikel.b on 2010-08-23
> **Thijs Koetsier said:**
> Hello maikel,

Can you explain why the options you gave are not sufficient for you? 

Backing up file folders can be done in several ways and a cronjob with rsync usually is a good way of doing it, but there are others like tarballing and using ncftp, but the result still is the same.

rdiff works with ssh, with ssh i must exchange the keys from server to server in data-center.

When i have 10 customers i got 10 pair of keys who can login on the server, i want backup files from the server on client side, to data-center side trough ssh but the clients can't login with the command line at the data-center side..  Because this is an security issue, is there a way that i can use rdiff and the clients can't login to the server side??

Or is rsync a better option? Thanks

---

### Post by maikel.b on 2010-08-23
> **LightningCrash said:**
> Are they on public networks or internal networks? If internal, NFS mounts and tar work fine.
Don't forget the output of sfdisk for your partition layout.


The clients are somewhere in Holland, and the server in a data center.

The connections between client server and data center server must be encrypted..

rdiff and rsync i know, bud is there a other backup program that i can use for more then one relations of me to backup??

Greetz Thanks !

---

### Post by tcpjack on 2010-08-23
One thing you can do is setup ssh keys as root user.  Then use the rsynv -a flag to save all the permissions.  Then you can handle all of the /home directory at once, while saving the correct permissions.

The only downside obviously is having a password-less root ssh key.  What I do is 100% lock down the system, disallow all access except from my IP only with only my ssh key with a heafty password.

I hope this helps.

---

### Post by maikel.b on 2010-08-23
> **tcpjack said:**
> One thing you can do is setup ssh keys as root user.  Then use the rsynv -a flag to save all the permissions.  Then you can handle all of the /home directory at once, while saving the correct permissions.

The only downside obviously is having a password-less root ssh key.  What I do is 100% lock down the system, disallow all access except from my IP only with only my ssh key with a heafty password.

I hope this helps.


Oke, this is a solution for me, i should try this one, thanks for your solution...

:p

---

