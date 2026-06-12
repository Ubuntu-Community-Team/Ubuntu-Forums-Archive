---
title: "Nginx and Rsync"
date: 2013-02-27
forum: Server Platforms
---

### Post by Rpgglitchy on 2013-02-27
Hello again!

So, I recently made a setup with Nginx as a load balancer to 2 webservers. And I installed rsync on both the webservers. 
Now I am in some kind of trouble. 
When I installed Rsync, I made a crontab file that syncs the var/www/ directory from each server with each other, every minute.
The thing is that if I edit something on my first server and the minute from the second server is over, all is deleted and it looks just like it was on webserver 2. 

I need to have something that makes it sync whenever a change is made and then syncs with second server and vice versa.

Hope you can help me!

Thanks in advance!
Greetings :guitar:

---

### Post by Pimentel on 2013-02-27
If you don't want to deal with block-level replication I suggest you to try [Lsyncd]("https://code.google.com/p/lsyncd/"), it will do what you are looking for. Lsyncd's daemon watches a directory recursively for events and replicates it asynchronously in near real-time, which will help keeping you from getting incoherence between nodes. It's secure, reliable and fairly easy to use. You can find tutorials for building HA webservers with it, and if for some reason it doesn't fit your needs, the next step before Fuse/GlusterFS would be [Csync2]("http://oss.linbit.com/csync2/").

Just bear in mind that if you are looking for replicating databases as well, you'll need to look somewhere else (DRBD, MySQL Cluster/Replication).

---

### Post by Rpgglitchy on 2013-03-01
Hi again, thx for your reply!

I am having some trouble with Lsyncd, Doesn't seem to co-operate with me :p
So I was wondering if there was some way to use some sort of script that notices when a file is changed in a directory and run the Rsync command?
As I have seen some cool Ubuntu magic so far, that seems rather doable. But I lack the experience to come up with anything :D

Or maybe someone has a link to a good Lsync tutorial? I dunno really.. 

But thx in advance! ^^

Greetings :guitar:

---

### Post by markbl on 2013-03-01
If you just want bidirectional sync then look at unison in the standard packages.

---

### Post by Rpgglitchy on 2013-03-01
Thank you for your reply!
I tried Unison and it works like a charm!
Thx again :D

Greetings :guitar:

---

