---
title: "Samba and User Permissions"
date: 2015-02-18
forum: Server Platforms
---

### Post by forumsviewer on 2015-02-18
I am a bit confused and stomped. We have 10 users or so that have access to a particular folder which had many sub folders and files.  Recently some folders can only have files created by the user that originally created that folder.  This only happens on and off, but once a folder is owned by a user then that folder is forever a problem unless I go in and chmod,chgrp,chown that folder recursively.

So the structure is as follows:

/path/to/share which is owned by root:root and 777
then there is:  /path/to/share/subfolder1/file.txt
if subfolder1 is owned by Joe:nogroup then Susan cannot create files within subfolder 1.  She can access file.txt however.  if I go in and change it to root:root and 777 then all is good.

I understand that this is happening because of permissions, but I didn't change any smb settings and this only started happening.  I want anyone that has access to the /share/ folder to have access to all read/write/access anything deeper than /share/, even new folders and files created by other users.

Any help please?

---

### Post by volkswagner on 2015-02-18
Interesting, this is the third time in one week I see users wanting to share files owned by root via SAMBA.

Check [these]("http://ubuntuforums.org/showthread.php?t=2265708") other [two]("http://ubuntuforums.org/showthread.php?t=2265554") threads for some ideas with force group, create mask and directory mask settings on your share.

---

### Post by bab1 on 2015-02-19
> **forumsviewer said:**
> I am a bit confused and stomped. We have 10 users or so that have access to a particular folder which had many sub folders and files.  Recently some folders can only have files created by the user that originally created that folder.  This only happens on and off, but once a folder is owned by a user then that folder is forever a problem unless I go in and chmod,chgrp,chown that folder recursively.

So the structure is as follows:

/path/to/share which is owned by root:root and 777
then there is:  /path/to/share/subfolder1/file.txt
if subfolder1 is owned by Joe:nogroup then Susan cannot create files within subfolder 1.  She can access file.txt however.  if I go in and change it to root:root and 777 then all is good.

I understand that this is happening because of permissions, but I didn't change any smb settings and this only started happening.  I want anyone that has access to the /share/ folder to have access to all read/write/access anything deeper than /share/, even new folders and files created by other users.

Any help please?
@ volkswagner gives good advice.  Read the 2 links he provided.  The problems will all disappear when you setup the Linux file system branch that you want to share, configure the user accounts and then create the shares.

With multiple users you need to manage a common group and NOT USE the root user for sharing anything.  Permissions and ownership of existing files and directories should belong to users and users group(s), not root.  Another problem is the new files and directories that are subsequently created.  This needs to be managed at the file system level not the Samba application level.

My suggestion is to start with a reconfigured file system that takes into account all the users in a common user group (or groups if you need the separation) and adding all the users to that group.  This means that all Samba users should also be Linux users on the server.  Once you have the Linux file system configured the creation of the shares is simple.

What does the file system you are sharing look like?  Post he output of ```
ls -l /path/to/share

```...be specific, <path/to/share> is not good enough for me to help you.

Are the users both Linux users and Samba users?  Check the output of ```
getent passwd|grep 100
```...to list the Ubuntu users.
Check the output of ```
sudo pdbedit -l
```... to list the Samba users.  Ubuntu Linux users should have a UID/GID of 1000 or greater.  Do the Linux users also have a Samba user account?  Anonymous (guest) users are setup with the Samba configuration and we can do that if you need it. 

Once we get the users correct we can setup the file system.  Then we will create the shares.

---

### Post by forumsviewer on 2015-02-19
bab1 - Thank you for your assistance.  I am masking username and folder names but I believe the below information will make sense.

```

ls -l /media/share
output:
drwxrwxrwx 1 root             root             4.0K Feb  2 11:26 AAA
drwxrwxrwx 1 root             root                0 Nov 14 14:26 BBB
drwxrwxrwx 1 root             root             4.0K Jan  9 20:04 CCC
drwxrwxrwx 1 john               john                8.0K Feb 12 16:29 DDD
drwxrwxrwx 1 melissa           melissa            4.0K Feb 18 15:06 EEE

```

```

getent passwd|grep 100
output:
totaladmin:x:1000:1000:Network Services,,,:/home/totaladmin:/bin/bash
john:x:1001:1001::/home/john:/usr/sbin/nologin
melissa:x:1002:1002::/home/melissa:/usr/sbin/nologin

```


```

sudo pdbedit -L
output:
nobody:65534:nobody
totaladmin:1000:Network Services
john:1001:
melissa:1002:

```

I do want to clarify that I do NOT have Samba setup with groups, only users and then I use smb.conf to put a user to read/write/access a particular share (such as the /media/share folder and sub folders).

What is weird is that for months everyone shared without any issues as it pertains to permissions.  However, only recently, without any patches or changes made to the Ubuntu box (atleast that I am aware of) some folders have permission issues.

---

### Post by bab1 on 2015-02-19
> **forumsviewer said:**
> bab1 - Thank you for your assistance.  I am masking username and folder names but I believe the below information will make sense.

```

ls -l /media/share
output:
drwxrwxrwx 1 root             root             4.0K Feb  2 11:26 AAA
drwxrwxrwx 1 root             root                0 Nov 14 14:26 BBB
drwxrwxrwx 1 root             root             4.0K Jan  9 20:04 CCC
drwxrwxrwx 1 john               john                8.0K Feb 12 16:29 DDD
drwxrwxrwx 1 melissa           melissa            4.0K Feb 18 15:06 EEE

```

All of these directories will allow any user to create a file in them.  the [COLOR="#0000FF"]rwxrwxrwx[/COLOR] allows for this.  All users have read(r), write(w) and eXecute(x) permissions (777).  Remember that any file created in those directories will have rw-rw-r-- permissions (664) and any directory will have rwxrwxr-x permissions (775) unless those objects are created by the root user.  Then you have 644 for files and 755 for directories.

What is the listings for the directory AAA and the directory EEE? 
> 
```

getent passwd|grep 100
output:
totaladmin:x:1000:1000:Network Services,,,:/home/totaladmin:/bin/bash
john:x:1001:1001::/home/john:/usr/sbin/nologin
melissa:x:1002:1002::/home/melissa:/usr/sbin/nologin

```

This is fine,
> 

```

sudo pdbedit -L
output:
nobody:65534:nobody
totaladmin:1000:Network Services
john:1001:
melissa:1002:

```

This is fine also.  Are there 3 humans on this network or are your user accounts both totaladmin and john?
> 

I do want to clarify that I do NOT have Samba setup with groups, only users and then I use smb.conf to put a user to read/write/access a particular share (such as the /media/share folder and sub folders).

Samba uses Linux groups.  There is nothing to "set up" other than to recognize the group in certain situations.  Samba can't give any user read/write/eXecute rights if Linux has not provided permissions via the Linux file system permissions.
> 

What is weird is that for months everyone shared without any issues as it pertains to permissions.  However, only recently, without any patches or changes made to the Ubuntu box (atleast that I am aware of) some folders have permission issues.
It is entirely due to permissions and ownership of newly created files and directories.

At this point we should add the Linux users to a common user group.  I tend to use groups that are already there by default.  There is a group named **users ** (whoda thunk!).  To add the users to this group you can use this invocation```
sudo adduser <username> users
``` After you have added all the users you can check your work with this```
getent group users
```.

With all of the users in a common group we can control access via the user group ownership and permissions alone. The user is not relevant and the others group is not relevant.

We can create a new directory and then share it.  The directory /media is not the correct place for you to store your Samba shares.  The system uses that location to automount and dismount temporary storage devices.  You can use or create other locations without changing the naming convention you have for Samba as the naming is //SERVER_NAME/SHARE_NAME.  The directory name is not important when locating shares.

I use the /srv branch of the file system.  It was specifically created to hold data that file servers provide (Samba and/or NFS).  So I would use the following  commands:

Create a directory to share```
sudo mkdir -p /srv/samba/test
```...check it with```
ls -l /srv/samba
```

The directory you are sharing (/srv/samba/test) needs to have the ownership of root:users and the permissions of 775.  This will allow all of your users in that group to have full access to that directory and therefore the share.  To change the group ownership you should use this invocation ```
sudo chgrp users /srv/samba/test
```

Now the beauty part.  When a user creates a file or directory the ownership is like this:  john:john.  We want this to always be this john:users.  This can be achived with the sgid (set group ID) bit set.  On an empty directory like /srv/samba/test this is easily done with this invocation```
sudo chmod 2775 /srv/samba/test
```...the leading 2 is the sgid bit and you can see it with ```
ls -l /srv/samba
```...the permissions should look something like this```
drwxrw**[COLOR="#FF0000"]s[/COLOR]**r-x  2 root users 4.0K Feb 19 15:30 test
```...the s (in red) is the sgid bit set.

You can test the access by a locally logged in user with this```
touch /srv/samba/test/touch.test
```... then use this to check the ownership and permissions```
ls -l /srv/samba/test
```

Once we have created the file system infrastructure we can create a share and test a remote users setup.

---

### Post by forumsviewer on 2015-03-07
bab1 - I owe you an apology and thank you.  I apologize I haven't replied sooner and I thank you for the time, effort and DETAILS FOR UNDERSTANDING in your post.  

I have followed your instruction and logic.  It makes sense, and as you mentioned, the beauty part is enforcing that the group is the same recursively when someone makes a new file or folder within a folder that has the 2775 chmod done to it.

however, i have followed your instruction and the group is not continuing down.

I first created the group share (instead of users)
I added root, john and melissa to group share
when I run 'getent group share' it lists ```
share:x:999:root,john,melissa
```

I then proceeded with your instructions of sudo making a directory, changing the group of that newly created directory to share and then ran sudo chmod 2775 new-directory.  When I run ls -l /srv/new-directory I get:
```
drwxrwsr-x 1 root            share           0 Mar  7 13:28 new-directory
```
(only difference I see in mine versus yours is that mine ends sr-x 1 and yours ends in sr-x 2)
I then, in Windows, using the Samba user john go into this new-directory after logging into file server and create a text file named 'map-network-drive.txt'.  When I go into this new-directory in CLI and run ls -l it lists:
```
-rwxrw-r-- 1 john john 0 Mar  7 13:29 map-network-drive.txt
```

As you can see, it does john:john which is exactly what we don't want.  We want john:share.  I've also tried it in the CLI and same thing (root:root) when I touch a file using sudo touch in the new-directory that is part of the share group.  
I have changed default group for john using:
```
sudo usermod -g share john
```
when I do id john :
```
uid=1001(john) gid=999(share) groups=999(share)
```

Any suggestions on why even with the 2775 chmod to a folder and then creating a file in it will be the username:username and not username:share without first changing the default group of the user?  Or is that how it is suppose to work (therefore I should change default group of john and melissa to 'share')?  

Another strange activity is that the folder created didn't include the sgid in the sub folders created.  For example, in /srv/new-directory i create a folder using user john as john-directory.  The /srv/new-directory/john-directory has group as share but lists it as drwxr-xr-x (missing the rws).  So when I login using melissa then melissa cannot create files in that folder.

Secondly, after I get this working with some test folders, do you have some instruction on updating all of the currently existing folders/files?  Would I just -R put them to share group and then -R a 2775 chmod?

---

### Post by bab1 on 2015-03-07
Sometimes you do yourself a disservice by changing things without knowing what you are doing.  I would have first asked; "why does this happen?".

The Debian/Ubuntu ***User Private Group*** paradigm is well documented.  The simple explanation is that the user should always have the primary group be a group with the users name and no users defined.  This provides the needed framework to allow user-group rw permissions upon file creation (775).  This is the default for Ubuntu users OTHER THAN ROOT.

Windows users may or may not follow this convention.  I defined the share to that it really didn't matter, but we may have to go further than what you have now.

My suggestion is to return every thing back to the default primary user-group as far as the test user is concerned.  Make sure the user is added to the group **share**.  The directory that you are sharing should be /srv/samba/test and the entire path to /srv/samba should have 755 permissions.  The /srv/samba/test directory should have the ownership of root:share and the permissions should be 2775.  When you test the inheritance with the command *touch*, do not use root to do that.  Root has a different umask than normal users.  All files that root creates have file permissions of 644 and directory permissions of 755.  Not what you want.

[COLOR="#0000FF"]Edit:  Do NOT include the user root in the user-group you use.  Root can always access the directory and never should be using Samba to access a share. [/COLOR]

After you have set this up show me the results of ```

getent group share

getent passwd john

ls -l /srv/samba/  ###### Use this so I have a known (to me) directory setup
 
```

In addition post the share definition from the smb.conf file.

In the end it is better to ask questions before you start mucking about on your own.  This you did about populated directory permissions, as it is different.  You will make every file eXecutable .  This will happen if you use 2775 recursively.  We can deal with that situation after we get the share up and running.

---

### Post by forumsviewer on 2015-03-08
Hi BAB1

I should clarify a few items that I didn't explain previously as I didn't know if it was relevant but I feel as though it is now.

1.  The reason for using /media/share is because it is a mounted partition setup only for samba share.  Would you still advise mounting to /srv/samba if the only use of the server is samba file server?  I'm not sure of a pro or con of donig so.

2.  totaladmin user is the Ubuntu server admin user that I am using to make changes, run sudo, edit smb.conf, etc.  I also use it when using sftp as I've found sftp works faster remotely than mounting the samba share as a network drive in Windows.  Only totaladmin can login to the Ubuntu server.

3.  john and melissa do not have a password or credentials to login to the Ubuntu server and were only created to map network drive in Windows and use the samba share.

With this being said if I leave john, melissa and totaladmin primary default group as their own username then the 2775 does nothing as anything created will have the group of the user that created it (since creating a file/folder/etc are done using map network drive in Windows or for totaladmin sftp.)  Does my use case described above make sense to change totaladmin, john and melissa primary group to the group 'share' so that anything created has the share group?

Just want to clarify before I essentially start over from square one.  Thank you as always,

---

### Post by bab1 on 2015-03-08
> **forumsviewer said:**
> Hi BAB1

I should clarify a few items that I didn't explain previously as I didn't know if it was relevant but I feel as though it is now.

1.  The reason for using /media/share is because it is a mounted partition setup only for samba share.  Would you still advise mounting to /srv/samba if the only use of the server is samba file server?  I'm not sure of a pro or con of donig so.
> 
I'm not sure what you mean here.  The file system on the partition is what is mounted and that file system can be mounted anywhere in the original file system.  Problems occur when the choice of mount point is used for other means.  The directory /meda is one of those places.  It  is used as the mount point for removable media and the udev routines work on it.  I want you to use what I said while we are testing.  Whatever you want to use late is up to you.  The file system is well thought out.  See here: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")


2.  totaladmin user is the Ubuntu server admin user that I am using to make changes, run sudo, edit smb.conf, etc.  I also use it when using sftp as I've found sftp works faster remotely than mounting the samba share as a network drive in Windows.  Only totaladmin can login to the Ubuntu server.

3.  john and melissa do not have a password or credentials to login to the Ubuntu server and were only created to map network drive in Windows and use the samba share.

Two thoughts here:
1.  The user totaladmin does not make the changes.  Root does when you call sudo (Switch User Do) and root uses different permissions when creating files and directories.  You need to learn how to set the system up to allow mortal users (you and I) to have access to the files they need.  My wife uses Linux and has no real notion of sudo or root.  She has access to files and directories that I set up outside of /home and /media.

2. If a user needs to access a Samba share then they need to be both a Linux user and a Samba user (via smbpasswd -a) or use guest access (as nobody:nogroup).  Another reason to set this up correctly at first.
> 
With this being said if I leave john, melissa and totaladmin primary default group as their own username then the 2775 does nothing as anything created will have the group of the user that created it (since creating a file/folder/etc are done using map network drive in Windows or for totaladmin sftp.)  Does my use case described above make sense to change totaladmin, john and melissa primary group to the group 'share' so that anything created has the share group?

Nope.  Return the users to the defaults.  Then we can begin again.  If you want me to help you follow what I'm doing, ask questions, but don't start off in your own direction.  I have an end result,  It is the correct way to do things.  I've found over the last 20+ years that the correct way is the best way to manage Linux.
> 

Just want to clarify before I essentially start over from square one.  Thank you as always,
We should start over at ALL THE DEFAULTS.

---

