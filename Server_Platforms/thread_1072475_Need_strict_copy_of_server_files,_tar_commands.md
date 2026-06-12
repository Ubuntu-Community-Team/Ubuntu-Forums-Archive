---
title: "Need strict copy of server files, tar commands"
date: 2009-02-17
forum: Server Platforms
---

### Post by volkswagner on 2009-02-17
I am trying to relocate websites to a new server.

I am having trouble relocating an existing twiki site.

There is very little support for twiki, but I did find one recommendation for relocating.  It was vague, and uses tar commands.

I tried the following:

on the old server
```
tar czvf twiki-files.tar.gz
```  

on new server
```
tar xzvf twiki-files.tar.gz
``` 

Problem is, some directories were not copied correctly, ie: case was not honored.  

/UI was copied as /ui

This is causing havoc on the perl based scripts.

How can I issue a strict copy retaining permissions and file name structure.

---

### Post by cdenley on 2009-02-17
I'm pretty sure that tar command should preserve all permissions and all filenames. What filesystem are you trying to tar to and from?

You can also use rsync to go directly from server to server.

---

### Post by volkswagner on 2009-02-17
> **cdenley said:**
> I'm pretty sure that tar command should preserve all permissions and all filenames. What filesystem are you trying to tar to and from?

You can also use rsync to go directly from server to server.

Both servers are formatted as ext3.

I will give rsync a look.  I have yet to use it.  I am sure it is a tool that I should be familiar with by now.  I think there were approx 1700 files in the twiki root directory.  As it turns out only a hand full did not maintain the capital letters in the directory name.  

Since I wanted to do the transfer again to include recent site content, I created this thread to see if my tar variables were incorrect.

---

### Post by cdenley on 2009-02-17
You can check the arguments in the man page
```

man tar

```

c = create archive
f = use an archive file
z = use gzip compression
x = extract archive
v = verbose output

---

### Post by jimv on 2009-02-17
You could also use scp to copy the directory over.

scp -r user@server1:/directory/files user@server2:/directory/files

---

### Post by volkswagner on 2009-02-18
> **jimv said:**
> You could also use scp to copy the directory over.

scp -r user@server1:/directory/files user@server2:/directory/files

Thanks @jimv,

I am a new fan of scp.

I was not able to perform the function accross two servers via a third host though.  I tried the command above, I was prompted for password for server1, then it would fail to connect.  I tried clearing .ssh keys, etc., still no go.

I was however able to go from server1 to server2 while logged into ssh on server1.

```
scp -r /directory/files user@server2:/directory/files
```

Worked a treat.

Of course it did not keep permissions, but this was not an issue since, the user:group = myself:myself worked fine.  Keeping file structure was more important on this one.  

I still need to research rsync.

I am still baffled as to why tar changed some directories to lower case.

---

### Post by windependence on 2009-02-18
Volkswagner,

For future reference, rsync over ssh:

```
$ rsync -avz -e ssh remoteuser@remotehost:/remote/dir /local/dir/
```

You can set up ssh with keys if you want to do this in a cron script for backup.

-Tim

---

