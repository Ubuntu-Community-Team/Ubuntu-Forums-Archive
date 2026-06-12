---
title: "rsync struggle"
date: 2009-03-29
forum: Server Platforms
---

### Post by ?xunil on 2009-03-29
i am trying to set up rsync on my ubuntu home server (whos ip is 192.168.1.99) to back up my windows pc.  i followed this tutorial... [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync) ...to setup rsync on the server.  i am using this tool... [http://www.itefix.no/i2/node/10650](http://www.itefix.no/i2/node/10650) ...on my windows machine.

when i try to do a test run from my windows machine i am prompted for my password and after entering it i get the following message...
> @ERROR: auth failed on module BOTTLE rsync error: error starting client-server protocol (code 5) at main.c(1504)

here is my command from windows...
> rsync -rav /cygdrive/d/test 192.168.1.99::BOTTLE

here is my rsyncd.conf...
> [BOTTLE]
  comment = desktop backups
  path = /media/store/bottle
  read only = no
  list = yes
  uid = nobody
  gid = nogroup
  auth users = thirsty
  secrets file = /etc/rsyncd.secrets
  log file = /var/log/rsync_btl.log

rsyncd.secrets has one entry for user thirsty.

any suggestions???

---

### Post by hyper_ch on 2009-03-29
I never used rsync with profiles - are you sure you need it that way? Wouldn't normal

rsync [options] from to

be enough?

---

### Post by BkkBonanza on 2009-03-29
In your [BOTTLE] profile you specify uid nobody and gid nogroup.
This means the rsynd daemon accesses the files as that user. Are you sure the files in question have read/write permissions for nobody/nogroup? In particular if you are backing up to that location you would have to have full permission to the folder /media/store/bottle for any user. It may not seem obvious but you may need exec permission on the directory to be able to create files inside.

---

### Post by doogy2004 on 2009-03-29
I use samba on my server and DirSyncPro on my XP machine to perform backups.  I simply mapped the shared folder on my server to a drive letter on my XP machine, then configure DirSyncPro to syncronize the folders I want to the mapped drive.

---

### Post by ?xunil on 2009-03-31
> **BkkBonaza said:**
> In your [BOTTLE] profile you specify uid nobody and gid nogroup.
This means the rsynd daemon accesses the files as that user. Are you sure the files in question have read/write permissions for nobody/nogroup? In particular if you are backing up to that location you would have to have full permission to the folder /media/store/bottle for any user. It may not seem obvious but you may need exec permission on the directory to be able to create files inside.

here is the info on "bottle"...
drw-rw-rw-  2 nobody  nogroup  4096 2009-03-28 16:04 bottle

i also tried this...
drwxrwxrwx  2 nobody  nogroup  4096 2009-03-28 16:04 bottle

is either of these correct?

thanks,
j

---

### Post by ?xunil on 2009-03-31
> **hyper_ch said:**
> I never used rsync with profiles - are you sure you need it that way? Wouldn't normal

rsync [options] from to

be enough?

could you post an example?

thanks,
j

---

### Post by BkkBonanza on 2009-03-31
If you want to try without a profile then you use rsync directly like this,

rsync -vztpr /path/to/my/files user@remote_site:/path/to/where/to/put

I have given options v verbose, z compress xfer with gzip, t keep filetime, p keep file perms, r recurse subdirs (lets you move a whole file tree). However, I would also suggest that it's a good idea to use rsync with ssh since rsync by it's own is not secure/encrypted. You can do this by modifying the command slightly...

rsync -vztpre "ssh -2" /path/to/my/files user@remote_site:/path/to/where/to/put

This opens a ssh tunnel to run the rsync command through. In this case you don't need rsyncd running anywhere since ssh knows how to start rsync. This is the way I usually use it and I have a small script so I don't have to remember the details for common xfers I do to my server.

I've never used rsync with use nobody so I don't know if there is odd behavior. I always just use real users. Your second permissions exmaple above is full open 777 so should definitely not have permission problems, though it is maybe not very secure either.

Just type,

man rsync

for all the info on rsync.

---

### Post by ?xunil on 2009-04-01
thanks!  the ssh method works for me.

---

