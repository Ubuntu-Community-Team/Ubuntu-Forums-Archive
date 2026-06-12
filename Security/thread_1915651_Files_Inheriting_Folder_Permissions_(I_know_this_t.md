---
title: "Files Inheriting Folder Permissions (I know this topic has been beaten to death)"
date: 2012-01-26
forum: Security
---

### Post by travlemon on 2012-01-26
Hello,

I know this topic has been beaten into the ground countless times, but I just can't seem to resolve the issue.

_**My Setup:**_
I have a junky old Dell desktop machine running Ubuntu 10.04LTS.  Although this is the desktop Ubuntu, I'm using it as a very light server for storing my files and accessing them from other machines, via Samba.  All drives have EXT4 partitions.

I have about 4 different users that have personal documents, and they should be the only ones who can access their own documents.  For those folders, I assigned the corresponding user as the "owner" of the folder with full access.  I then assigned that user's group for the "Group" permission and delegated full access.  Others have no access.

For public folders, most users have read & execute access to the folder, and some users have full access.  "Others" have no access, as "Others" sounds to me like other users on the machine, as well as guests who come onto the network temporarily.

By the way, this is a workgroup, so any user that is on the server is also on any machine accessing the server over the network.  Also, the server stays signed in as root while it's running.

**_The Problem:_**
I must note that I am a Windows user and I'm incredibly familiar with Windows permissions.  The Linux thing is a hobby for me and I love the OS, and the permission system is going over my head.

I have a simple goal:  I have some private folders and some public folders.  In a folder that only I have access to, I may have a file that I decide I want to share to other users.  The easiest way for me to do it is to quickly copy it over to a folder that everyone as access to.  This is how I'd do it in Windows anyway.

In my Linux scenario, if I copy a file from my private folder to a public one, then I will become the owner and the file inherits the Group.  As far as permissions, I don't know what the rhyme or reason is, as the file's permissions won't even look close to what the folder's permissions are.

_**Ideal Solution:**_
What my ultimate goal is for this, is to basically have the files inherit the same Owner, Group, and Others permissions as their new parent folder when they are copied, movied, or created.  Also I'd like them to inherit the same Owner and Group

Also, I've played around with umask and nothing seems to change when I copy/move/create new files, regardless of my umask settings.

In any event, any help is much appreciated!

---

### Post by redmk2 on 2012-01-27
> **travlemon said:**
> Hello,

I know this topic has been beaten into the ground countless times, but I just can't seem to resolve the issue.

_**My Setup:**_
I have a junky old Dell desktop machine running Ubuntu 10.04LTS.  Although this is the desktop Ubuntu, I'm using it as a very light server for storing my files and accessing them from other machines, via Samba.  All drives have EXT4 partitions.

I have about 4 different users that have personal documents, and they should be the only ones who can access their own documents.  For those folders, I assigned the corresponding user as the "owner" of the folder with full access.  I then assigned that user's group for the "Group" permission and delegated full access.  Others have no access.

For public folders, most users have read & execute access to the folder, and some users have full access.  "Others" have no access, as "Others" sounds to me like other users on the machine, as well as guests who come onto the network temporarily.

By the way, this is a workgroup, so any user that is on the server is also on any machine accessing the server over the network.  Also, the server stays signed in as root while it's running.

**_The Problem:_**
I must note that I am a Windows user and I'm incredibly familiar with Windows permissions.  The Linux thing is a hobby for me and I love the OS, and the permission system is going over my head.

I have a simple goal:  I have some private folders and some public folders.  In a folder that only I have access to, I may have a file that I decide I want to share to other users.  The easiest way for me to do it is to quickly copy it over to a folder that everyone as access to.  This is how I'd do it in Windows anyway.

In my Linux scenario, if I copy a file from my private folder to a public one, then I will become the owner and the file inherits the Group.  As far as permissions, I don't know what the rhyme or reason is, as the file's permissions won't even look close to what the folder's permissions are.

_**Ideal Solution:**_
What my ultimate goal is for this, is to basically have the files inherit the same Owner, Group, and Others permissions as their new parent folder when they are copied, movied, or created.  Also I'd like them to inherit the same Owner and Group

Also, I've played around with umask and nothing seems to change when I copy/move/create new files, regardless of my umask settings.

In any event, any help is much appreciated!
> **travlemon said:**
> Hello,

I know this topic has been beaten into the ground countless times, but I just can't seem to resolve the issue.

_**My Setup:**_
I have a junky old Dell desktop machine running Ubuntu 10.04LTS.  Although this is the desktop Ubuntu, I'm using it as a very light server for storing my files and accessing them from other machines, via Samba.  All drives have EXT4 partitions.

I have about 4 different users that have personal documents, and they should be the only ones who can access their own documents.  For those folders, I assigned the corresponding user as the "owner" of the folder with full access.  I then assigned that user's group for the "Group" permission and delegated full access.  Others have no access.

For public folders, most users have read & execute access to the folder, and some users have full access.  "Others" have no access, as "Others" sounds to me like other users on the machine, as well as guests who come onto the network temporarily.

By the way, this is a workgroup, so any user that is on the server is also on any machine accessing the server over the network.  Also, the server stays signed in as root while it's running.

**_The Problem:_**
I must note that I am a Windows user and I'm incredibly familiar with Windows permissions.  The Linux thing is a hobby for me and I love the OS, and the permission system is going over my head.

I have a simple goal:  I have some private folders and some public folders.  In a folder that only I have access to, I may have a file that I decide I want to share to other users.  The easiest way for me to do it is to quickly copy it over to a folder that everyone as access to.  This is how I'd do it in Windows anyway.

In my Linux scenario, if I copy a file from my private folder to a public one, then I will become the owner and the file inherits the Group.  As far as permissions, I don't know what the rhyme or reason is, as the file's permissions won't even look close to what the folder's permissions are.

_**Ideal Solution:**_
What my ultimate goal is for this, is to basically have the files inherit the same Owner, Group, and Others permissions as their new parent folder when they are copied, movied, or created.  Also I'd like them to inherit the same Owner and Group

Also, I've played around with umask and nothing seems to change when I copy/move/create new files, regardless of my umask settings.

In any event, any help is much appreciated!

Sometimes Windows experience is a hindrance to understanding Linux file permissions.  The best way to handle access to directories and files is to not be too worried about who the owner of any file is.  The group is what controls access. 

If we create a group called *public *and and add all users to it, what is the the practical differences in rw are to the following? files```
-[COLOR="Red"]rw[/COLOR]-rw-r--  1 redmk2 public  53K 2011-11-02 12:19 test
-[COLOR="Red"]r[/COLOR]--rw-r--  1 redmk2 public  53K 2011-11-02 12:19 test
```

The answer is -- nothing!  The owner can RW  with either set of permissions.  As a matter of fact anyone in the group *public can also delete the file too.*

This does not mean you can't restrict the files from being deleted by anyone but the owner.  You need to use extended permissions and set the umask to 002.  Setting the umask to 002 is traditionally the way to setup the file systems on a host that is used for file sharing.  This provides directories with 0775 permissions and files with 0664 permissions.  You can set the umask for the host in /etc/profile.  Just add a line at the very bottom with this in it```
umask 002
```

I have a directory called *share* and the permissions on that directory is *3775* and the ownership looks like this```
drwxrw**[COLOR="Red"]s[/COLOR]**r-[COLOR="Blue"]**t**[/COLOR] 11 redmk2 public 4.0K 2010-01-04 14:35 share
```

This directory has the setguid bit set (red) and any file that is made has the group *public *set.  It also has the *sticky bit *set (blue) so that only the owner of the file can delete it.

You can find information on extended file permissions [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

---

### Post by travlemon on 2012-01-27
> **redmk2 said:**
> Sometimes Windows experience is a hindrance to understanding Linux file permissions.  The best way to handle access to directories and files is to not be too worried about who the owner of any file is.  The group is what controls access. 

If we create a group called *public *and and add all users to it, what is the the practical differences in rw are to the following? files```
-[COLOR=Red]rw[/COLOR]-rw-r--  1 redmk2 public  53K 2011-11-02 12:19 test
-[COLOR=Red]r[/COLOR]--rw-r--  1 redmk2 public  53K 2011-11-02 12:19 test
```The answer is -- nothing!  The owner can RW  with either set of permissions.  As a matter of fact anyone in the group *public can also delete the file too.*

This does not mean you can't restrict the files from being deleted by anyone but the owner.  You need to use extended permissions and set the umask to 002.  Setting the umask to 002 is traditionally the way to setup the file systems on a host that is used for file sharing.  This provides directories with 0775 permissions and files with 0664 permissions.  You can set the umask for the host in /etc/profile.  Just add a line at the very bottom with this in it```
umask 002
```I have a directory called *share* and the permissions on that directory is *3775* and the ownership looks like this```
drwxrw**[COLOR=Red]s[/COLOR]**r-[COLOR=Blue]**t**[/COLOR] 11 redmk2 public 4.0K 2010-01-04 14:35 share
```This directory has the setguid bit set (red) and any file that is made has the group *public *set.  It also has the *sticky bit *set (blue) so that only the owner of the file can delete it.

You can find information on extended file permissions [**_[COLOR=Blue]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

Hi,

Thanks for the informative response!  I'm making a little more sense out of it now. I set the "Set User ID" and "Set Group UID" properties, and that seems to be helping a lot.  Even though my server is signed in and running under the Root user, I actually never do much work to it on the server itself.

Most of my actions involve me creating/copying/moving/deleting files from my own username.  There were many times where I saved a file to a public folder, but other users couldn't access it.  Now that I set the UID and GUID, the permissions are functioning a bit more like I was hoping they would. 

Thanks very much for helping me tighten down the permissions!  Again, it's no urgency, as it's strictly a hobby and it's only implemented at home.  But I do prefer that certain users can't barge into the folders of other users, as some documents are personal.

---

### Post by redmk2 on 2012-01-27
> **travlemon said:**
> Hi,

Thanks for the informative response!  I'm making a little more sense out of it now. I set the "Set User ID" and "Set Group UID" properties, and that seems to be helping a lot.  Even though my server is signed in and running under the Root user, I actually never do much work to it on the server itself.

Most of my actions involve me creating/copying/moving/deleting files from my own username.  There were many times where I saved a file to a public folder, but other users couldn't access it.  Now that I set the UID and GUID, the permissions are functioning a bit more like I was hoping they would. 

Thanks very much for helping me tighten down the permissions!  Again, it's no urgency, as it's strictly a hobby and it's only implemented at home.  But I do prefer that certain users can't barge into the folders of other users, as some documents are personal.

I meant to mention something about leaving the server unattended with the root (or any user for that matter) logged in.  

You should not have to have anyone logged in to the server for it to operate successfully as a file server.  There are non-shell accounts running the server at all times.  The root user should never be left running a logged in shell.  Do you have problems connecting when no one is logged in?

You should use a common group on your file system that you are sharing.  Did you do that?

---

### Post by travlemon on 2012-01-27
> **redmk2 said:**
> I meant to mention something about leaving the server unattended with the root (or any user for that matter) logged in.  

You should not have to have anyone logged in to the server for it to operate successfully as a file server.  There are non-shell accounts running the server at all times.  The root user should never be left running a logged in shell.  Do you have problems connecting when no one is logged in?

You should use a common group on your file system that you are sharing.  Did you do that?

It has been a long time since I've ever needed to do anything to the server.  I think the original reason I left it signed in is because I have lucky backup set up to run at startup and run scheduled backups.  Also, hard drives weren't mounting automatically, so I had to sign in and manually click on them in Nautilus so they would mount.

Another reason was that I don't have one giant hard drive for storage, I 3 different drives that make organization a big tough.  So I made a script to mount folders in the same way you might use virtual directories on an FTP server.  I am far from a server guru, and even further from a Linux guru.  Most of this could probably be taken care of with fstab, but I didn't really know about it at the time.  Also, I just plain didn't know that root should not be logged in, though I haven't had problems with it.

As far s the group you are mentioning, I have a group called "users" which was meant to be the main group that would provide basic access for non-administrator users.

However, I think I will be reverting back to a regular Windows server, as I'm far more comfortable with the permissions I know it much better.  It's a bit more practical for my setup, but of course I'll be keeping my Linux desktops!

---

