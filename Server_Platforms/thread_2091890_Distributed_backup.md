---
title: "Distributed backup?"
date: 2012-12-06
forum: Server Platforms
---

### Post by dudumomo on 2012-12-06
Hi guys,

Being more and more concerned about my backup solution, I am thinking using distributed backup solution with some friends of mine.

Like to duplicate 3 or 4 times in different places our backup. (Distributed backup to a limiter number of trusted peers)

I would prefer an encrypted solution, fault tolerant and smart enough to ensure there is always at least 1 or 2 copies. But nothing too big (100Gb may be)

(Something like that)

I've been trying Tahoe-lafs but it seems quite complex and not so smart (yet)

Does anyone is doing something similar? Any software to recommend (GluserFS, MooseFS, Ceph?) or a simple solution like FTP to upload and Rsync to mirror with some encryption somewhere....I don't know.

Thanks for any advice.

---

### Post by thnewguy on 2012-12-06
Assuming all the peers are running Linux (or any host running OpenSSH) then it will be fairly easy to sync all of your machines using rsync. Well, easy, but with a lot of steps.

Each peer should have accounts for each other person on their machine.
Each peer should be running OpenSSH
Each peer should either have a static address or a dynamic hostname

Once these pieces are in place you can sync your files to each computer using the rsync command.

I do this for my own data and it works pretty well as the connection is encrypted and rsync is pretty light on bandwidth.

---

### Post by Habitual on 2012-12-06
I had some success with the gluster (v3.2.5) filesystem.

Write to one "brick" and it's replicated to the other bricks.

glusterfs in a repo near you. :)

---

### Post by dudumomo on 2012-12-07
Thanks for the feedback.

I have to try gluster first I guess.

Any other suggestion?

Thanks !

---

### Post by sandyd on 2012-12-07
SparkleShare

Its still relatively new, and has a (few) bugs, but is cross platform compatible and runs through a ssh tunnel.

Simply, it works like dropbox (except that Dropbox uses S3). Files copied/moved/placed in the SparkleShare folder are sent to the server via ssh. As you have multiple clients connected, it works just like dropbox - the clients are synced with the server. For example, if a file is uploaded on computer 1, it will go into the server, then will propagate to computer 2, 3, and so on.

---

### Post by Jason80513 on 2012-12-07
I am going with the theory that the best backup is one that is simple and easy to verify.

rsync can be used to duplicate file systems at a point in time, or
tar can be used to make incremental backups.
scp can be used to copy files to another machine.
ssh can be used to run things remotely on various machines.
cron can be used to schedule this all to happen.

The whole script is a couple of lines long, and there are virtually no limits to what you can accomplish.

No GUI though.

---

### Post by dudumomo on 2012-12-07
Thanks sandyd,
However it is very similar to Dropbox or Owncloud and I am not looking for a sync solution.
With this solution, there will be only 2 copies (The client and the server) + it is not really distributed and every user cannot share the file of others.

Also, after trying GlusterFS, there is no encryption and no specific access rights (Except IP wise)

Thanks Jason80513, it is the easiest way and it might be the one to use. (With Ajaxplorer for example and Tar+Rsync+something to encrypt to do the transfert). But it is quite basic and not so robust. (But can do the trick)

The issue with tahoe-lafs is that it is too complex (Okay fault tolerant + encryption but how to access the data is complicated and need a big key (Which is not even secure at the end as it is impossible to remember it, so the user will write it on somewhere...)

I will try moosefs.

---

### Post by thnewguy on 2012-12-08
You could try Fish-Sync [http://fishsync.sourceforge.net/](http://fishsync.sourceforge.net/)
It's a fairly young project, but it lets you do what you're looking for. It offers both command line and GUI interfaces to sync multiple files between multiple hosts without need for a central authority and communication is encrytped.

---

