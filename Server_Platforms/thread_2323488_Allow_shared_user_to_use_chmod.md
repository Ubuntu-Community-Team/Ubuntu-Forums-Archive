---
title: "Allow shared user to use chmod"
date: 2016-05-05
forum: Server Platforms
---

### Post by crcarson on 2016-05-05
Shotwell in 16.04 changed the way they verify the .shotwell directory is writable by the user.  They now do a test change of the ACL's which caused a problem when the .shotwell directory is in a samba shared directory (yes, Shotwell says don't share the .shotwell but have a good setup that allows multiple computers to access the same photo library and works fine with the understanding only one user at a time).  How should I setup my samba share for that directory?  Have tried using "force user", "force group" and "acl group control = yes" but still get "operation not permitted" in response to a test chmod command.

---

### Post by TheFu on 2016-05-06
Just guessing here, but don't use samba. Use NFS.  Sorry if that isn't helpful.  NFS is faster and provides almost all Unix-style permissions.

---

### Post by crcarson on 2016-05-07
> **TheFu said:**
> Just guessing here, but don't use samba. Use NFS.  Sorry if that isn't helpful.  NFS is faster and provides almost all Unix-style permissions.

Thanks for the reply, it is helpful.  Using Samba because of Window shares that don't exists now, total Ubuntu Gnome and LUbuntu now.  Will look into changing to NFS.

---

### Post by crcarson on 2016-05-07
NFS doesn't solve my Shotwell problem but it does simplify my home network.  Guess the answer to allow picture viewing on my wife's system is to setup a limited userid under my ID to view pictures.

---

### Post by TheFu on 2016-05-07
If you setup a group with your and her userid, then make all the photo directories g+swrx with that shared-group as the gid, all future files and directories made in that location will have the group and g+w permissions automatically. No need to do the limited userid thing. 

If there are any lurkers reading. The only trick to using NFS is that userids/groupids (the numbers) need to be matched on all the systems.  Then ownership and groups will work fine.  It really only matters for the users/groups in the NFS storage, not all the lower-numbered userids/groups - though that can be helpful too if you want/need to share /usr/.  Normally just normal userids (people) and groups used by them need this setup.  Hope that is clear. Ask if it isn't.  

**System-A **
* username (thefu), userid: 1000, groupid: 1000
* username (thewife), userid: 1001, groupid: 1001
**System-B **
* username (thefu), userid: 1000, groupid: 1000
* username (thewife), userid: 1001, groupid: 1001

Next, create a new group - groupname: shared, groupid: 2000.  Put both thewife and thefu into that group. Do this on both systems.  In the shotwell directories, 
```
sudo chgrp -R shared /path/to/shotwell/storage
find /path/to/shotwell/storage -type d -exec chmod g+srwx {} \;
find /path/to/shotwell/storage -type f -exec chmod g+rw {} \;

```
That should cover it.  This is a standard method for sharing storage areas on all multiuser Unix systems with or without NFS.  The cool thing about this is that each userid doesn't need to allow logins on all the machines, they just need to be in the passwd/group files (or in LDAP) for the client NFS systems.

---

### Post by crcarson on 2016-05-07
The problem with Shotwell is that in 16.04 level they changed the way they verified that the Shotwell DB and thumbs are writeable.  They do this with an attempt to change the ACLs (like chmod 664 thumbs).  This fails under my wifes is because she doesn't own the files.  Had setup uids and gids so that under 15.10 Shotwell works for both my and my wifes ids.  Unless I've read it wrong the only way to change the permissions is by the owner or sudo.

Now running under NFS and have a limited user id to display the pictures on my wife's machine.

---

### Post by TheFu on 2016-05-07
If you post the **ls -alF** for the top shotwell data directory, perhaps we can help? Also the output for **id** for each userid would help.

Need to see the directory and file and subdirectory permissions with user, group and octal settings, please. You want something like this:
```
drwxrwsr-x  2 thefu shared  4096 Nov 12  2013 09/
```

Permissions and ACLs are different things on Linux.  **setfacl** is the command and it works over NFS, but I find using ACLs obnoxious when they aren't often (99.99999% not) needed.

Since I don't use shotwell, I don't have any ideas about that program or if this should ever work.  Doing some research ... 
[https://askubuntu.com/questions/4293/how-to-setup-shotwell-for-multi-user-access](https://askubuntu.com/questions/4293/how-to-setup-shotwell-for-multi-user-access) says that the shotwell devs never intended for multiple users to share the same backend DB and they also say NOT to share the files over the network.  This makes zero sense to me and seems _lazy_ of them from my perspective.  I've never trusted any photo management tool, partially for that reason, but for many others too.  The shotwell FAQ has a warning against this too: [https://wiki.gnome.org/Apps/Shotwell/FAQ](https://wiki.gnome.org/Apps/Shotwell/FAQ) due to SQLite considerations.  [https://bugzilla.gnome.org/show_bug.cgi?id=715764](https://bugzilla.gnome.org/show_bug.cgi?id=715764) is a bug about using **any** network storage with Shotwell.

From the bug report:
> Having two computers (or two user accounts on the same computer) use the same
Shotwell database is what is not recommended. Hope that clears things up.

A new idea ....
So after reading all of that, I have an idea .... pick 1 machine to hold the files, don't use NFS.  Create a 3rd userid on the machine and both you and your wife use that other userid to access the shotwell DB by using **/usr/bin/sudo -H -u other-username /path/to/normal/shotwell &**.  Put that into a shotwell script.  Also setup both userids to be allowed to run sudo as the "other-username" with shotwell as the allowed command. You can limit options passed into shotwell or not, as required through the sudoers file.  The remote machine would use normal X/Windows to run the tool.  **ssh -X wifes-machine /path/to/shotwell-script** .  Normal X-forwarding needs to be allowed in the sshd config file on the remote box. Hopefully, you use a wired, gigE, connection - it will just be slower over wifi or 100base-tx, but it will still work.

---

### Post by crcarson on 2016-05-07
Here is an ls -la from the Shotwell directory.

[email]cliff@cliffps:~/share/MyPicLib/Family/.swfami[/email]ly$ ls -la
total 16
drwxrwxr-x  4 cliff cliff 4096 May  5 09:29 .
drwxrwxr-x 15 cliff cliff 4096 Jan 15 07:32 ..
drwxrwxr-x  2 cliff cliff 4096 May  7 18:06 data
drwxrwxr-x  4 cliff cliff 4096 May  3 15:09 thumbs


My wife is part of the cliff group and the uids and gids are the same on both systems.  My wife does have the ability to write to this directory.

Your solution is interesting but I've tried ssh -X on my home environment and it was not worth the effort.   To slow and buggy.

I saw all those Shotwell warnings about network sharing and am suspicious that this is the reason for the change in the code from 15.10 to 16.04.  The change certainly make network sharing more difficult.  I've been running Shotwell shared for over a year and experenced no problems but my wife usually only views and I do all the updates.

---

### Post by TheFu on 2016-05-08
The permissions missing are g+s on those directories and probably all sub-dirs. Don't know if this will help or not, but it won't hurt.

---

### Post by crcarson on 2016-06-22
Fix the problem (somewhat).  Because the Shotwell picture libraries have the same directory structure on  both my wifes system and my own I just copied the Shotwell database file and thumbs to a directory under my wifes home directory and start Shotwell pointing at that database.  She has full access to the shared picture library but cannot update the DB.

---

### Post by TheFu on 2016-06-22
Would running an rsync daily be something to try?
I've been using Plex Media server web interface to show slide shows from trips. Works well, once the photos are organized. 

I asked about this issue at a recent Linux conference. One of the main photo library tools was adding multi-workstation support for their tool according to someone in the audience. Think it was a KDE tool, but don't recall the name. Can only say that checking the changelog could be worth the effort.

---

