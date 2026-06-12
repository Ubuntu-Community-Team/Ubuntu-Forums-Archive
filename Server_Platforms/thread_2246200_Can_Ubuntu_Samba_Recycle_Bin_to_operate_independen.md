---
title: "Can Ubuntu Samba Recycle Bin to operate independently of the client windows machine"
date: 2014-09-29
forum: Server Platforms
---

### Post by tito3 on 2014-09-29
Can Ubuntu Samba Recycle Bin to operate independently of the client windows machine (no settings in them)?
Can deleted files restored directly from the Ubuntu Server?

---

### Post by bab1 on 2014-09-29
> **tito3 said:**
> Can Ubuntu Samba Recycle Bin to operate independently of the client windows machine (no settings in them)?
Can deleted files restored directly from the Ubuntu Server?

Yes,  but you need to set it up using a Samba VFS module.  See [here]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/VFS.html#id2651247") and [here]("http://www.samba.org/samba/docs/man/manpages/vfs_recycle.8.html").

This is not the Ubuntu Trash Bin.  It is a separate directory that you set up and provide access to.

[COLOR="#0000FF"]Edit: Here is an [example setup]("https://www.linkedin.com/today/post/article/20140701115354-112531065-enable-vfs-and-recycle-functionality-in-samba").[/COLOR]

---

### Post by tito3 on 2014-09-30
Thank you, but these not working for me!
Can reason be:
I setup in my Ubuntu server:
1. Raid 1
2. Samba config -> security = user -> not public shares, login only with user/password;
3. ACL extended file permission set to sub directories

---

### Post by bab1 on 2014-09-30
> **tito3 said:**
> Thank you, but these not working for me!
Can reason be:
I setup in my Ubuntu server:
1. Raid 1
2. Samba config -> security = user -> not public shares, login only with user/password;
3. ACL extended file permission set to sub directories

I can't see how any of these things would cause problems.  What error messages do you get?  What are the configuration settings you used?

---

### Post by tito3 on 2014-10-01
It not appear any error in samba logs nor testparm terminal command. When i delete a file it not ask for moving file into recycle bin.
 It ask: "Are you sure you want to permanently delete this folder?"

---

### Post by tito3 on 2014-10-01
this is my configuration:

[tstsmb]
path = /opt/tstsmb
# Enable the recycle bin ##
vfs objects = recycle
recycle:repository = .recycle
recycle:touch = Yes
recycle:keeptree = Yes
recycle:versions = Yes
recycle:noversions = *tmp, *temp, * obj, *TMP, TEMP*
recycle:exclude = *tmp, *temp, * obj, *TMP, TEMP*
recycle:excludedir = /recycle,/tmp,/temp,/TMP,/TEMP
# Enable the recycle bin ##

force user = root
valid users = @root,@modr,@common,root,@nogroup,nobody
write list = @root,@modr,@common,root,@nogroup,nobody
admin users = @root,root

---

### Post by bab1 on 2014-10-01
> **tito3 said:**
> this is my configuration:

[tstsmb]
path = /opt/tstsmb
# Enable the recycle bin ##
vfs objects = recycle
recycle:repository = .recycle
recycle:touch = Yes
recycle:keeptree = Yes
recycle:versions = Yes
recycle:noversions = *tmp, *temp, * obj, *TMP, TEMP*
recycle:exclude = *tmp, *temp, * obj, *TMP, TEMP*
recycle:excludedir = /recycle,/tmp,/temp,/TMP,/TEMP
# Enable the recycle bin ##

force user = root
valid users = @root,@modr,@common,root,@nogroup,nobody
write list = @root,@modr,@common,root,@nogroup,nobody
admin users = @root,root

I'm not sure why it doesn't work.  I know this works on one of my test shares```
vfs objects = recycle
recycle:repository = rubbish
recycle:keeptree = yes
recycle:versions = yes

```

Maybe your problem the *force user=root* and all the valid users.  But I can't be sure.  I created a simple share with just this```
[test]
        comment = Test Data
        path = /path/to/share
        browseable = yes
        writeable = yes
        vfs objects = recycle
        recycle:repository = rubbish
        recycle:keeptree = yes
        recycle:versions = yes

```
I did not want a hidden recycle bin so I named it rubbish and the directory appeared.

NOTE:  The warning is still there when you delete something, but I believe that is a Nautilus problem, not a Samba concern.  

My advice: create a test share that is simple and add on until it breaks.

---

