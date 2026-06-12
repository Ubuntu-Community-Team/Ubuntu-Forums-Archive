---
title: "Persistent file permissions (or another solution?)"
date: 2011-11-03
forum: Server Platforms
---

### Post by n4h0j on 2011-11-03
Hi everyone.

I have Ubuntu 11.10 x86_64 running on my file server at home. It is working as an automated torrent box, getting all torrents from RSS with Flexget. I use SortTv to automatically extract and sort everything depending on the file.

I also have a Samba server, and NFS server and a bunch of other scripts doing their thing all in the same directory, in my case /srv.

Now, I am wondering if there is a way to make sure that /srv always have rwx-properties for all users?

Right now I am running a cronjob every 5 minutes doing chmod -R 777 /srv. But, there must be a smoother way?

```
johan@ubuntuserver:~$ ls /srv/
total 48
drwxrwxrwx  2 johan nfs   4096 2011-10-25 22:03 backup
drwxrwxrwx 19 johan nfs   4096 2011-11-03 15:10 download
drwxrwxrwx  3 johan nfs   4096 2011-11-03 19:46 incomplete
drwxrwxrwx  2 root  root 16384 2011-10-25 21:19 lost+found
drwxrwxrwx  9 johan nfs   4096 2011-11-03 15:08 misc
drwxrwxrwx 10 johan nfs   4096 2011-11-03 15:22 movies
drwxrwxrwx  2 johan nfs   4096 2011-10-27 23:14 music
drwxrwxrwx 11 johan nfs   4096 2011-11-03 03:40 tv-series
drwxrwxrwx  2 johan nfs   4096 2011-11-03 19:44 watch

```

```
*/5 * * * * chmod -R 777 /srv/
```

This is what it should look like, I don't store anything exposed to the web here, so it should be ok to have 777, right?

---

### Post by SeijiSensei on 2011-11-03
Why not just make /srv owned by johan.nfs if it's not already?  You shouldn't have to update the permissions all the time.  What specific problem are you trying to fix?

Are there users that cannot write into these directories?  Make them members of group nfs.

You should be able to define a set of group memberships and permissions that will apply ad infinitum.  You might want to look into [setgid]("http://en.wikipedia.org/wiki/Setuid#setuid_and_setgid_on_directories") permissions if you can't figure out how to make things work with just normal permissions.

---

### Post by Jonathan L on 2011-11-04
> **n4h0j said:**
> ... automatically extract and sort everything depending on the file.
...
Now, I am wondering if there is a way to make sure that /srv always have rwx-properties for all users?

Right now I am running a cronjob every 5 minutes doing chmod -R 777 /srv. But, there must be a smoother way?


Hi Johan

To me it looks like you want all the newly-arrived files to be writeable by all your users.  The classical way to achieve this is to put all the users in a group G, make the directory setgid and G, and set the umask on all the file-creating programs to 002.    Then all the new files will be created group-writeable and in the group all the people are in.

Assuming your group is 'nfs' and your directory is /srv
```
chgrp nfs srv
chmod g+ws srv
umask 2
mkdir srv/newdirectory
touch srv/newfile
ls -ld srv srv/new*

drwxrwsr-x 3 root nfs 4096 2011-11-04 10:16 srv
drwxrwsr-x 2 root nfs 4096 2011-11-04 10:16 srv/newdirectory
-rw-rw-r-- 1 root nfs    0 2011-11-04 10:16 srv/newfile

```You'll see that the new file and directory are group nfs and group writeable, so would be writeable by all who are in the group.  Won't this achieve what you want?

(You'll need a chgrp -R G in the first place to get all the existing  groups correct, and a chmod -R g+ws on all the directories.)


It is almost never a good idea to make things 777 and one is likely to find surprises; plus of course (as you say) the crontab wait is a little inelegant.

Hope that's some use.

Kind regards,
Jonathan.

---

### Post by n4h0j on 2011-11-04
Thanks a lot for the advice! I will try this out right away. :)

Have a nice weekend!

---

