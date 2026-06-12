---
title: "SVN and apache help"
date: 2009-08-06
forum: Server Platforms
---

### Post by karlw on 2009-08-06
I'm trying to host my SVN repo via HTTP using Apache + DAV.  I am currently hosting a django project out my apache server, and that seems to be working just fine.  

```

# Mod Python Module
LoadModule python_module  /usr/lib/apache2/modules/mod_python.so
LoadModule dav_module     /usr/lib/apache2/modules/mod_dav.so
LoadModule dav_svn_module /usr/lib/apache2/modules/mod_dav_svn.so

....

<Location /svn>
  DAV svn
  SVNPath /media/disk/svn
</Location>
```

Full apache config here: [http://dpaste.com/hold/76292/](http://dpaste.com/hold/76292/)

When I navigate to my the repo using my web browser, I get the following XML file:

```
<D:error>
<C:error/>
<m:human-readable errcode="13">Could not open the requested SVN filesystem</m:human-readable>
</D:error>
```

Looking at my apache error log, i see that apache tries to read the "svn/format" file, but access is denied.  I've read that setting the owner of the subversion repo to the user who is running the apache server.  So running "ps aux | grep apache" I see that my apache server is running with user "www-data".  So I changed the owner and group of the svn directory, recursively, but I still get the same error.  Is there anything that I missing?

---

### Post by karlw on 2009-08-07
here my apache error log when going to view the svn via http:

```
[Fri Aug 07 10:49:55 2009] [error] [client 192.168.1.3] (20014)Internal error: Can't open file '/media/disk/svn/format': Permission denied
[Fri Aug 07 10:49:55 2009] [error] [client 192.168.1.3] Could not fetch resource information.  [500, #0]
[Fri Aug 07 10:49:55 2009] [error] [client 192.168.1.3] Could not open the requested SVN filesystem  [500, #13]
[Fri Aug 07 10:49:55 2009] [error] [client 192.168.1.3] Could not open the requested SVN filesystem  [500, #13]
```

Also, everything in the svn directory has a 777 permissions.

---

### Post by karlw on 2009-08-08
I think I found the root cause of my issue.  My user www-data cannot read or write to the directory.  The test that I ran is as follows. I changed the SVNPath directory to a new svn repo in my home, I am able to get the repo to show up in my web browser. So here it works! So I then did a cp of the svn repo that worked from my home to my /media/disk.  Change my apache config, restarted my server, and now I'm getting the same old error.  Here is an ls -l of each directory that contains the SVN:

```

Does not work )-:
josh@NorthHaverbrook:~$ ls -l /media/disk/svn/
total 40
drwxr-xr-x 3 josh josh 4096 2009-08-07 11:50 branches
drwxr-xr-x 2 josh josh 4096 2009-08-07 11:50 conf
drwxr-xr-x 2 josh josh 4096 2009-08-07 11:50 dav
drwxr-xr-x 5 josh josh 4096 2009-08-07 11:50 db
-r--r--r-- 1 josh josh    2 2009-08-07 11:50 format
drwxr-xr-x 2 josh josh 4096 2009-08-07 11:50 hooks
drwxr-xr-x 2 josh josh 4096 2009-08-07 11:50 locks
-rw-r--r-- 1 josh josh  229 2009-08-07 11:50 README.txt
drwxr-xr-x 3 josh josh 4096 2009-08-07 11:50 tags
drwxr-xr-x 3 josh josh 4096 2009-08-07 11:50 trunk
Works (-:
josh@NorthHaverbrook:~$ ls -l /home/josh/svn
total 40
drwxr-xr-x 3 josh josh 4096 2009-02-02 22:09 branches
drwxr-xr-x 2 josh josh 4096 2008-11-30 18:27 conf
drwxr-xr-x 2 josh josh 4096 2008-11-30 18:27 dav
drwxr-sr-x 5 josh josh 4096 2009-02-17 20:56 db
-r--r--r-- 1 josh josh    2 2008-11-30 18:27 format
drwxr-xr-x 2 josh josh 4096 2008-11-30 18:27 hooks
drwxr-xr-x 2 josh josh 4096 2008-11-30 18:27 locks
-rw-r--r-- 1 josh josh  229 2008-11-30 18:27 README.txt
drwxr-xr-x 3 josh josh 4096 2009-02-02 22:09 tags
drwxr-xr-x 3 josh josh 4096 2009-02-02 22:09 trunk
josh@NorthHaverbrook:~$ 

```

The key, I think, is the /media/disk is the mount point for my external hard drive.  So I tried reading some info on /media/disk using the command "su www-data".  And I cannot read any files, I tried ls -l as user www-data.  What would cause a user to be denied from reading files with the same permissions on different parts of the file system?

I also changed the mount point of the disk to some place in my home, and got the same results (error).

---

### Post by its_me_gb on 2009-08-08
Could you try making www-data the owner of the svn directory?

```
sudo chown -R www-data:www-data /media/disk/svn
```

---

### Post by karlw on 2009-08-09
Just to put some closer on this thread, I was able to figure it out.  Well, I think "figure it out" is a pretty nice term. I hacked something out ...

I needed to change the owner of the disk directory as well as the svn dir.  My experience with perms is pretty light, but after i did a chown -R josh:josh /media/disk, I was able to get to access the repo over http.  

I just added authentication, I needed to include some modules, which I found listed here:

[http://forum.webfaction.com/viewtopic.php?id=343](http://forum.webfaction.com/viewtopic.php?id=343).

Over all I'm pretty happy with how this turned out.  Hope this can help someone in the future.

p.s.  I also remove the 777 perms on the repo, I made it a 770, and it works great.

---

### Post by bodhi.zazen on 2009-08-09
co works great over http and I allow that.

ci , however, is a bit more problematic. The problem I have not beeb able to solve with ci on svn over http is maintaining (tracking) who did the commit.

For this I use ssh . see : [http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

---

