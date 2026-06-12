---
title: "Force file permissions inside a directory"
date: 2012-05-15
forum: Server Platforms
---

### Post by AbsenteeSurgeon on 2012-05-15
Here's my situation:
I have an Ubuntu Server (12.04) that I'm running as an FTP and Samba file server. I have 5+ users adding/using files on the server. There are certain folders that I want everyone to use/see everything inside of. These are kind of "public" folders.
Problem:
File permissions are set client side during a transfer, not server side. So, by default, the files placed in these "public" folders are only accessible to the owner.
Solution:
I want to make it so that these permissions are set by the server. That is, any files place inside of these "public" folders will automatically be given rwx permissions for everyone, regardless of what options were set by the FTP client.

Is there any way to do what I've described above? Thanks!

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Here's my situation:
I have an Ubuntu Server (12.04) that I'm running as an FTP and Samba file server. I have 5+ users adding/using files on the server. There are certain folders that I want everyone to use/see everything inside of. These are kind of "public" folders.
By *everyone *, do you mean just these 5 users or to you mean any user logged in to the Samba server (other)?> 
Problem:
File permissions are set client side during a transfer, not server side. So, by default, the files placed in these "public" folders are only accessible to the owner.
I don't believe that the permissions are set at the client side.  The permissions are set at the Samba server side, by the OS utimatly.> 
Solution:
I want to make it so that these permissions are set by the server. That is, any files place inside of these "public" folders will automatically be given rwx permissions for everyone, regardless of what options were set by the FTP client.

Is there any way to do what I've described above? Thanks!
Sure there is.  Once again; do you mean rw permissions for the 5 users or do you really mean everyone (e.g. others).  The term others in Linux means everyone.  There are either *user, group or other* entities.

---

### Post by AbsenteeSurgeon on 2012-05-15
Sorry for not being specific enough. By "everyone", I mean the "others" entity in Linux. By permissions being set client side, I meant for files being transferred over FTP. And I'm not necessarily talking just about Samba permissions, but also about the file permissions on the Ubuntu server itself.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Sorry for not being specific enough. By "everyone", I mean the "others" entity in Linux.
I don't think you want to do that.  The only way I know to do that using the rwx permissions is by altering the *other *settings with **umask **.  It would be far better to put all mortal (regular) users in a group that would allow rw use.> 
By permissions being set client side, I meant for files being transferred over FTP. And I'm not necessarily talking just about Samba permissions, but also about the file permissions on the Ubuntu server itself.
If I understand correctly; you want to have a directory(s) and subdirectories that would allow access to those files for all mortal users.

You can provide an entire branch of any portion of file system  that all users in the group would have access to,  As I said before the best way is to add all those users to a group and allow that group access to the files.  The root folder of this would look something like this from the terminal```
drwxrwsr-x 3 root [COLOR="Red"]**users**[/COLOR] 4.0K 2011-04-11 20:58 [COLOR="RoyalBlue"]**files**[/COLOR]
```

If this is what you want then we can do that.  I am being picky and trying to get you to think about hierarchy in the file system.  The proper way to have multiple user file access is by controlling the group entity permissions.

---

### Post by AbsenteeSurgeon on 2012-05-15
I agree with you that it's a good idea to change to group permissions instead of "others" permissions, thanks for the suggestion.

The root folder *is* set up with permissions "drwxrwxrwx". The problem is that when users upload files over FTP, the files they upload have their own permissions, namely "drwx------".

I know how to change this on the server, and I know how to change permissions when uploading files myself. However, it would be super convenient if all of the file permissions inside of this root folder were *automatically* changed to "drwxrw----".

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> I agree with you that it's a good idea to change to group permissions instead of "others" permissions, thanks for the suggestion.

The root folder *is* set up with permissions "drwxrwxrwx". The problem is that when users upload files over FTP, the files they upload have their own permissions, namely "drwx------".
Can you post the terminal output of this so I can *see *it?  > 

I know how to change this on the server, and I know how to change permissions when uploading files myself. However, it would be super convenient if all of the file permissions inside of this root folder were *automatically* changed to "drwxrw----".

The automatically wish is doable with the sgid bit set on the permissions.  But first let's get specific now.  how many users are there and how many are going to be in the group we create (use)?  What is the directory structure you are going to use?  In a general way what are you using this for; web root or ...?

Once I have a better understanding, I can give you the specific commands to use to achieve this goal.

---

### Post by AbsenteeSurgeon on 2012-05-15
Using stock FTP client options, here's what uploaded files look like:

```
-rw------- 1 {username} users 147756752 May 15 10:38 {filename}
```

There will be a total of 8 users in the "users" group. This is being used as a file exchange/storage server for all eight of us. There are two hard drives that are the main communal storage drives, called them "Black 1" and "Black 2". They are both mounted to "/media/". All of this file exchanging will be happening over FTP, rarely will anyone be logged into the machine.

I'm also planning on sharing these files over Samba, but that's a secondary concern of mine. I imagine that once these permissions are sorted out, everything relating to Samba will fall right into place.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Using stock FTP client options, here's what uploaded files look like:

```
-rw------- 1 {username} users 147756752 May 15 10:38 {filename}
```

There will be a total of 8 users in the "users" group. This is being used as a file exchange/storage server for all eight of us. There are two hard drives that are the main communal storage drives, called them "Black 1" and "Black 2". They are both mounted to "/media/". All of this file exchanging will be happening over FTP, rarely will anyone be logged into the machine.

I'm also planning on sharing these files over Samba, but that's a secondary concern of mine. I imagine that once these permissions are sorted out, everything relating to Samba will fall right into place.

Creeping up to the answer...  ;-)

What is the output of this```
umount
```

Post the output of ```
ls -alt /media/
```

I assume that each drive will have one partition (using the entire drive)

As you say we can deal with Samba later.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> What is the output of this```
umount
```.

```
Usage: umount -h | -V 
       umount -a [-d] [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts] 
       umount [-d] [-f] [-r] [-n] [-v] special | node... 
```> **bab1 said:**
> Post  the output of ```
ls -alt /media/
```I assume that each drive will  have one partition (using the entire drive)

```
drwxr-xr-x  6 root  root 4096 May 15 15:14 . 
drwxr-xrwx  7 scott root 4096 May 15 10:58 1TB Black 2 
drwxr-x--- 20 scott root 4096 May 14 22:42 2TB Green 
drwxr-xrwx  6 scott root 4096 May 14 22:42 1TB Black 1 
drwxr-xr-x 23 root  root 4096 May 14 19:02 .. 
drwxr-xr-x  2 root  root 4096 May 14 17:34 cdrom             
```Each hard drive indeed has one partition covering the entire drive. The 2TB Green drive is one that I plan to private to myself and not to include in the sharing.

---

### Post by bab1 on 2012-05-15
Sorry there.  I was distracted when I asked. I really wanted the output of ```
umask
```

Here is what I get```
 umask
0002

```

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> Sorry there.  I was distracted when I asked. I really wanted the output of ```
umask
```Here is what I get```
 umask
0002

```
My output is 0022

*EDITTED*

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> ...
```
drwxr-xr-x  6 root  root 4096 May 15 15:14 . 
drwxr-xrwx  7 scott root 4096 May 15 10:58 1TB Black 2 
drwxr-x--- 20 scott root 4096 May 14 22:42 2TB Green 
drwxr-xrwx  6 scott root 4096 May 14 22:42 1TB Black 1 
drwxr-xr-x 23 root  root 4096 May 14 19:02 .. 
drwxr-xr-x  2 root  root 4096 May 14 17:34 cdrom             
```Each hard drive indeed has one partition covering the entire drive. The 2TB Green drive is one that I plan to private to myself and not to include in the sharing.

I hate spaces in names.  :D  In a nutshell here is what we need to do;[LIST]
[*]Make sure that the system uses a umask of 0002
[*]Set the the correct group ownership (users?)
[*]Set the sgid bit on the top level directory
[*]set the correct permissions to the top level directory (recursively)
[/LIST]

Hopefully we have little or nothing in one of those partitions that we can start with.  If not then we will still be okay, but you may have to manually adjust some of the permissions on some files initially.  In the end you will have directories with the permissions of 775 (actually 2775) and files with permissions of 664 (0664) on the entire partition.

---

### Post by bab1 on 2012-05-15
The first part is fairly easy.  You need to edit the /etc/profile file (as root).  **At the very bottom of that file** you need to set the **[COLOR="Red"]umask[/COLOR]**.  Here is what the bottom of my /etc/profile file looks like```
if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

[COLOR="Red"]**umask 002**[/COLOR]

```

---

### Post by Morbius1 on 2012-05-15
> That is, any files place inside of these "public" folders will automatically be given rwx permissions for everyone, regardless of what options were set by the FTP client.Can't do the "x" part of that request but there is another way if you are interested. Make your target folder look and act like it's on an NTFS partition:

** Install bindfs
```
sudo apt-get install bindfs
```** Then just as a test run the following command on one of your folders:
```
sudo bindfs -o perms=0666:+D "/path with spaces" "/path with spaces"
```You will be mounting a folder **[COLOR=Blue]to itself[/COLOR]** with a "view" defined by "perms=0666:+D"

Every file added will have permissions 666 and every subfolder will have permissions of 777 regardless of what FTP, Samba, or even Linux thinks it's doing.

BTW, to reverse that just unmount it:
```
sudo umount "/path with spaces"
```If that works for you you can add the line ( without sudo ) to rc.local or better yet set up an upstart job to have this done at boot.

---

### Post by bab1 on 2012-05-15
> **Morbius1 said:**
> Can't do the "x" part of that request but there is another way if you are interested. Make your target folder look and act like it's on an NTFS partition:

** Install bindfs
```
sudo apt-get install bindfs
```** Then just as a test run the following command on one of your folders:
```
sudo bindfs -o perms=0666:+D "/path with spaces" "/path with spaces"
```You will be mounting a folder [COLOR=Blue]to itself[/COLOR] with a "view" defined by "perms=0666:+D"

Every file added will have permissions 666 and every subfolder will have permissions of 777 regardless of what FTP, Samba, or even Linux thinks it's doing.

BTW, to reverse that just unmount it:
```
sudo umount "/path with spaces"
```If that works for you you can add the line ( without sudo ) to rc.local or better yet set up an upstart job to have this done at boot.

For a user starting out, I would suggest learning the traditional way to set up a file system that users share.  But if the user wants to do this, who am I to say.  Whatever cocks your pistol.  I'm not a believer in complexity.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> I hate spaces in names.  :D  In a nutshell here is what we need to do;
[LIST]
[*]Make sure that the system uses a umask of 0002
[*]Set the the correct group ownership (users?)
[*]Set the sgid bit on the top level directory
[*]set the correct permissions to the top level directory (recursively)
[/LIST]

Hopefully we have little or nothing in one of those partitions that we can start with.  If not then we will still be okay, but you may have to manually adjust some of the permissions on some files initially.  In the end you will have directories with the permissions of 775 (actually 2775) and files with permissions of 664 (0664) on the entire partition.

I successfully did all of the above, except I'm not sure if I did the sgid bit correctly. Here's the result of:
```
ls -l /media/
```
```
drwxrwsr-x  7 scott users 4096 May 15 10:58 1TB Black 2 
drwxr-x--- 20 scott users 4096 May 14 22:42 2TB Green 
drwxrwsr-x  6 scott users 4096 May 14 22:42 1TB Black 1 
drwxr-xr-x  2 root  root 4096 May 14 17:34 cdrom 			
```

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> I successfully did all of the above, except I'm not sure if I did the sgid bit correctly. Here's the result of:
```
ls -l /media/
```
```
drwxrw**[B][COLOR="Red"]s[/COLOR]**[/B]r-x  7 scott users 4096 May 15 10:58 1TB Black 2 
drwxr-x--- 20 scott users 4096 May 14 22:42 2TB Green 
drwxrwsr-x  6 scott users 4096 May 14 22:42 1TB Black 1 
drwxr-xr-x  2 root  root 4096 May 14 17:34 cdrom 			
```

I see it on Black 1 and 2.  see the **[COLOR="Red"]s[/COLOR]** in the line?

Now we need to chmod file system with```
chmod -R u=rwXs,g=rwXs,o=rX la "Black 1"
```  Don't forget the "" (like "Black 1" and "Black 2")

**Edit:** Did you put all the users in the *users group*?

---

### Post by Morbius1 on 2012-05-15
> **bab1 said:**
> For a user starting out, I would suggest learning the traditional way to set up a file system that users share.  But if the user wants to do this, who am I to say.  Whatever cocks your pistol.  I'm not a believer in complexity.
That's fine I wasn't presenting this as a better way just another way. There is no traditional way ( that I know of ) in Linux to fulfill the exact requirement of automatically saving a file with permissions of 666  ( unless you do something goofy like setting umask to 000 ). Your way of using groups, the setgid bit, and umask ( although in 12.04 the umask is already set to 002 by default ) is the traditional way and there's noting wrong with it in my book ;)

---

### Post by bab1 on 2012-05-15
> **Morbius1 said:**
> That's fine I wasn't presenting this as a better way just another way. There is no traditional way ( that I know of ) in Linux to fulfill the exact requirement of automatically saving a file with permissions of 666  ( unless you do something goofy like setting umask to 000 ). Your way of using groups, the setgid bit, and umask ( although in 12.04 the umask is already set to 002 by default ) is the traditional way and there's noting wrong with it in my book ;)

Earlier in the conversation the idea of allowing world writes (others with rw) on a file decided.  We would **not allow** that.  Poor form.

---

### Post by Morbius1 on 2012-05-15
But in the case of a Samba share you have now replaced a public share with a private share requiring all remote users to authentication themselves to make sure they are a member of the correct group.

---

### Post by bab1 on 2012-05-15
> **Morbius1 said:**
> But in the case of a Samba share you have now replaced a public share with a private share requiring all remote users to authentication themselves to make sure they are a member of the correct group.

**Edit:**This is not really an accurate way of looking at it.  Even the user nobody is the result of authentication.  I have anonymous user access to my Samba shares.

~~~

All of my Samba shares work fine with this file system setup.  The OP and I have also discussed this point.  This is OT, if you want to discuss this PM me.

---

### Post by Morbius1 on 2012-05-15
You have a nice day.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> I see it on Black 1 and 2.  see the **[COLOR=Red]s[/COLOR]** in the line?

Now we need to chmod file system with```
chmod -R u=rwXs,g=rwXs,o=rX la "Black 1"
```  Don't forget the "" (like "Black 1" and "Black 2")

**Edit:** Did you put all the users in the *users group*?

I put all of my users in the *users* group yes.

When running the above code, I got errors in changing the files/directories I'm not the owner of:
```
chmod: chaing permissions of {file}: Operation not permitted
```
I tried running the code in sudo and it gave me this error:
```
chmod: cannot access 'la': No such file or directory
```

Other than that the code ran just fine

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> I put all of my users in the *users* group yes.

When running the above code, I got errors in changing the files/directories I'm not the owner of:
```
chmod: chaing permissions of {file}: Operation not permitted
```
I tried running the code in sudo and it gave me this error:
```
chmod: cannot access 'la': No such file or directory
```

Other than that the code ran just fine

Dang cut 'n paste.  it's from a script I have.  You should use ```
sudo chmod -R u=rwXs,g=rwXs,o=rX "Black 1"
```

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> Dang cut 'n paste.  it's from a script I have.  You should use ```
sudo chmod -R u=rwXs,g=rwXs,o=rX "Black 1"
```

Alright, that command successfully ran for both of the hard drives.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Alright, that command successfully ran for both of the hard drives.

What does it look like in the subdirectories?  You should see all the files and directories with the group ownership as *users * and the directories as 775 with *sgid*.  Did this happen?  Post some output for some of this ```
ls -lt subdir
ls -lt subdir/anothersubdir
```

Try and look at the subdirectories from a remote machine.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> What does it look like in the subdirectories?  You should see all the files and directories with the group ownership as *users * and the directories as 775 with *sgid*.  Did this happen?  Post some output for some of this ```
ls -lt subdir
ls -lt subdir/anothersubdir
```Try and look at the subdirectories from a remote machine.

All of the directories I looked at were basically identical, here's small sample:

```
drwsrwsr-x 360 scott users 16384 May 15 10:58 Music 
drwsrwsr-x   2 scott users 16384 May 13 20:48 lost+found 
drwsrwsr-x  10 scott users  4096 May 13 14:53 Systems 
drwsrwsr-x  28 scott users  4096 May 10 15:30 Movies 
```

Logging in from FTP works, and I can successfully navigate through all the appropriate directories

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> All of the directories I looked at were basically identical, here's small sample:

```
drwsrwsr-x 360 scott users 16384 May 15 10:58 Music 
drwsrwsr-x   2 scott users 16384 May 13 20:48 lost+found 
drwsrwsr-x  10 scott users  4096 May 13 14:53 Systems 
drwsrwsr-x  28 scott users  4096 May 10 15:30 Movies 
```

Logging in from FTP works, and I can successfully navigate through all the appropriate directories...and the the files all have 664 as the perms with the group users?

I would **chown** the **lost+found **directory recursively back to root:root

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> ...and the the files all have 664 as the perms with the group users?

I would **chown** the **lost+found **directory recursively back to root:root

Here's what a typical file looks like: (all of them look the same)

```
-rwsrwsr-x 1 barry users 4096 May 15 12:25 {filename}
```

And I chown'd the lost+found directories back to root:root.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Here's what a typical file looks like: (all of them look the same)

```
-rwsrwsr-x 1 barry users 4096 May 15 12:25 {filename}
```

And I chown'd the lost+found directories back to root:root.

And now on to Samba.  Do all of your users have both a user and samba user on the server?  Does Samba work as you want it to?

---

### Post by bab1 on 2012-05-15
> -rwsrwsr-x 1 barry users 4096 May 15 12:25 {filename}

I just noticed this is NOT just sgid.  You have set this to suid and sgid (6775).  You want the user to be reflected as the user creating the file and only the group *users*  to be forced.  You need to go back and correctly set chown.

Once again the group is the only entity the you use a set bit on (sgid only).

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> And now on to Samba.  Do all of your users have both a user and samba user on the server?  Does Samba work as you want it to?

The idea is that every person will have a Samba account with the same username and pass as their local account. I'm still setting that up.

Adding files through Samba is not behaving exactly as I'd like it to. When I add a file it looks like this:
```
-rwxr--r-- 1 scott users 0 May 15 19:02 Testfile.txt
```

when ideally it would look like this:

```
-rwxrwxr-- 1 scott users 0 May 15 19:02 Testfile.txt
```

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> I just noticed this is NOT just sgid.  You have set this to suid and sgid (6775).  You want the user to be reflected as the user creating the file and only the group *users*  to be forced.  You need to go back and correctly set chown.

Once again the group is the only entity the you use a set bit on (sgid only).

I just fixed this with the following command:

```
sudo chmod -R u-s {directory}
```

---

### Post by bab1 on 2012-05-15
> **bab1 said:**
> And now on to Samba.  Do all of your users have both a user and samba user on the server?  Does Samba work as you want it to?

> **AbsenteeSurgeon said:**
> The idea is that every person will have a Samba account with the same username and pass as their local account. I'm still setting that up.
This means there will be no anonymous yours.  Is this correct.  With the file system set up as it is you need to explicitly accommodate anonymous users.  It is easily done, but not required if all users are known and login.> 

Adding files through Samba is not behaving exactly as I'd like it to. When I add a file it looks like this:
```
-rwxr--r-- 1 scott users 0 May 15 19:02 Testfile.txt
```
File permissions are a result of many factors.  How did you create or transfer the file.  Some FTP apps can set a custom umask.  Samba can also be used to set a different (less restrictive permissions).  
> 
when ideally it would look like this:

```
-rwxrwxr-- 1 scott users 0 May 15 19:02 Testfile.txt
```
For files you want rw-rw-r--.  You do not want all files to be set to executable (x).  The execute bit is set on the directories only so the user can traverse or descend into a directoy.  So we have rwx rwx r-x on directories and rw- rw- r-- on files.  

If you don't have this then you had executable files in the directories when we did the chmod.  That's why I asked if there were a lot of files existing in "Black 1"

It may not make a difference to you.  The file has to be a script or an app that is a binary blob for there to be a problem.  To me it's housekeeping.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> I just fixed this with the following command:

```
sudo chmod -R u-s {directory}
```

Great!

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> This means there will be no anonymous yours.  Is this correct.  With the file system set up as it is you need to explicitly accommodate anonymous users.  It is easily done, but not required if all users are known and login.File permissions are a result of many factors.  How did you create or transfer the file.  Some FTP apps can set a custom umask.  Samba can also be used to set a different (less restrictive permissions).  

For files you want rw-rw-r--.  You do not want all files to be set to executable (x).  The execute bit is set on the directories only so the user can traverse or descend into a directoy.  So we have rwx rwx r-x on directories and rw- rw- r-- on files.  

If you don't have this then you had executable files in the directories when we did the chmod.  That's why I asked if there were a lot of files existing in "Black 1"

It may not make a difference to you.  The file has to be a script or an app that is a binary blob for there to be a problem.  To me it's housekeeping.

A test file I sent over Samba got permissions "-rwxr--r--".

A test file I sent over FTP got permissions "-rw-------".

Ideally both of these would be forced to get the permission tag "-rw-rw-r--"

I don't have a huge concern about binary files being executed on the server, maliciously or otherwise.

---

### Post by bab1 on 2012-05-15
> Adding files through Samba is not behaving exactly as I'd like it to. When I add a file it looks like this:
```
-rwxr--r-- 1 scott users 0 May 15 19:02 Testfile.txt

```
Let me take another wack at this.

In Samba you can also set up creation permission modes.  What does the smb.conf file look like?

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> Let me take another wack at this.

In Samba you can also set up creation permission modes.  What does the smb.conf file look like?

Okay, I think I'm starting to understand....

The default file creation and directory creation masks are set to 0700 for Samba. Would I need to change the file one to 0664 and directory one to 0775 to get the desired effect?

---

### Post by bab1 on 2012-05-15
> A test file I sent over FTP got permissions "-rw-------".
Umask can be set by the FTP program.  Look at the conf file for details.

Let's see the smb.conf file for samba?

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> Umask can be set by the FTP program.  Look at the conf file for details.

Let's see the smb.conf file for samba?

Samba smb.conf:
```
# 
# Sample configuration file for the Samba suite for Debian GNU/Linux. 
# 
# 
# This is the main Samba configuration file. You should read the 
# smb.conf(5) manual page in order to understand the options listed 
# here. Samba has a huge number of configurable options most of which  
# are not shown in this example 
# 
# Some options that are often worth tuning have been included as 
# commented-out examples in this file. 
#  - When such options are commented with ";", the proposed setting 
#    differs from the default Samba behaviour 
#  - When commented with "#", the proposed setting is the default 
#    behaviour of Samba but the option is considered important 
#    enough to be mentioned here 
# 
# NOTE: Whenever you modify this file you should run the command 
# "testparm" to check that you have not made any basic syntactic  
# errors.  
# A well-established practice is to name the original file 
# "smb.conf.master" and create the "real" config file with 
# testparm -s smb.conf.master >smb.conf 
# This minimizes the size of the really used smb.conf file 
# which, according to the Samba Team, impacts performance 
# However, use this with caution if your smb.conf file contains nested 
# "include" statements. See Debian bug #483187 for a case 
# where using a master file is not a good idea. 
# 
 
#======================= Global Settings ======================= 
 
[global] 
 
## Browsing/Identification ### 
 
# Change this to the workgroup/NT-domain name your Samba server will part of 
    workgroup = workgroup 
 
# server string is the equivalent of the NT Description field 
    server string = %h server (Samba, Ubuntu) 
 
# Windows Internet Name Serving Support Section: 
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server 
#   wins support = no 
 
# WINS Server - Tells the NMBD components of Samba to be a WINS Client 
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both 
;   wins server = w.x.y.z 
 
# This will prevent nmbd to search for NetBIOS names through DNS. 
    dns proxy = no 
 
# What naming service and in what order should we use to resolve host names 
# to IP addresses 
;   name resolve order = lmhosts host wins bcast 
 
#### Networking #### 
 
# The specific set of interfaces / networks to bind to 
# This can be either the interface name or an IP address/netmask; 
# interface names are normally preferred 
;   interfaces = 127.0.0.0/8 eth0 
 
# Only bind to the named interfaces and/or networks; you must use the 
# 'interfaces' option above to use this. 
# It is recommended that you enable this feature if your Samba machine is 
# not protected by a firewall or is a firewall itself.  However, this 
# option cannot handle dynamic or non-broadcast interfaces correctly. 
;   bind interfaces only = yes 
 
 
 
#### Debugging/Accounting #### 
 
# This tells Samba to use a separate log file for each machine 
# that connects 
    log file = /var/log/samba/log.%m 
 
# Cap the size of the individual log files (in KiB). 
    max log size = 1000 
 
# If you want Samba to only log through syslog then set the following 
# parameter to 'yes'. 
#   syslog only = no 
 
# We want Samba to log a minimum amount of information to syslog. Everything 
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log 
# through syslog you should set the following parameter to something higher. 
    syslog = 0 
 
# Do something sensible when Samba crashes: mail the admin a backtrace 
    panic action = /usr/share/samba/panic-action %d 
 
 
####### Authentication ####### 
 
# "security = user" is always a good idea. This will require a Unix account 
# in this server for every user accessing the server. See 
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html 
# in the samba-doc package for details. 
#   security = user 
 
# You may wish to use password encryption.  See the section on 
# 'encrypt passwords' in the smb.conf(5) manpage before enabling. 
;    encrypt passwords = yes 
 
# If you are using encrypted passwords, Samba will need to know what 
# password database type you are using.   
;    passdb backend = tdbsam 
 
    obey pam restrictions = yes 
 
# This boolean parameter controls whether Samba attempts to sync the Unix 
# password with the SMB password when the encrypted SMB password in the 
# passdb is changed. 
    unix password sync = yes 
 
# For Unix password sync to work on a Debian GNU/Linux system, the following 
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for 
# sending the correct chat script for the passwd program in Debian Sarge). 
    passwd program = /usr/bin/passwd %u 
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
 
# This boolean controls whether PAM will be used for password changes 
# when requested by an SMB client instead of the program listed in 
# 'passwd program'. The default is 'no'. 
    pam password change = yes 
 
# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections 
    map to guest = bad user 
 
########## Domains ########### 
 
# Is this machine able to authenticate users. Both PDC and BDC 
# must have this setting enabled. If you are the BDC you must 
# change the 'domain master' setting to no 
# 
;   domain logons = yes 
# 
# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of the user's profile directory 
# from the client point of view) 
# The following required a [profiles] share to be setup on the 
# samba server (see below) 
;   logon path = \\%N\profiles\%U 
# Another common choice is storing the profile in the user's home directory 
# (this is Samba's default) 
#   logon path = \\%N\%U\profile 
 
# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of a user's home directory (from the client 
# point of view) 
;   logon drive = H: 
#   logon home = \\%N\%U 
 
# The following setting only takes effect if 'domain logons' is set 
# It specifies the script to run during logon. The script must be stored 
# in the [netlogon] share 
# NOTE: Must be store in 'DOS' file format convention 
;   logon script = logon.cmd 
 
# This allows Unix users to be created on the domain controller via the SAMR 
# RPC pipe.  The example command creates a user account with a disabled Unix 
# password; please adapt to your needs 
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u 
 
# This allows machine accounts to be created on the domain controller via the  
# SAMR RPC pipe.   
# The following assumes a "machines" group exists on the system 
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u 
 
# This allows Unix groups to be created on the domain controller via the SAMR 
# RPC pipe.   
; add group script = /usr/sbin/addgroup --force-badname %g 
 
########## Printing ########## 
 
# If you want to automatically load your printer list rather 
# than setting them up individually then you'll need this 
#   load printers = yes 
 
# lpr(ng) printing. You may wish to override the location of the 
# printcap file 
;   printing = bsd 
;   printcap name = /etc/printcap 
 
# CUPS printing.  See also the cupsaddsmb(8) manpage in the 
# cupsys-client package. 
;    printing = cups 
;   printcap name = cups 
 
############ Misc ############ 
 
# Using the following line enables you to customise your configuration 
# on a per machine basis. The %m gets replaced with the netbios name 
# of the machine that is connecting 
;   include = /home/samba/etc/smb.conf.%m 
 
# Most people will find that this option gives better performance. 
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html 
# for details 
# You may want to add the following on a Linux system: 
#         SO_RCVBUF=8192 SO_SNDBUF=8192 
#   socket options = TCP_NODELAY 
 
# The following parameter is useful only if you have the linpopup package 
# installed. The samba maintainer and the linpopup maintainer are 
# working to ease installation and configuration of linpopup and samba. 
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' & 
 
# Domain Master specifies Samba to be the Domain Master Browser. If this 
# machine will be configured as a BDC (a secondary logon server), you 
# must set this to 'no'; otherwise, the default behavior is recommended. 
#   domain master = auto 
 
# Some defaults for winbind (make sure you're not using the ranges 
# for something else.) 
;   idmap uid = 10000-20000 
;   idmap gid = 10000-20000 
;   template shell = /bin/bash 
 
# The following was the default behaviour in sarge, 
# but samba upstream reverted the default because it might induce 
# performance issues in large organizations. 
# See Debian bug #368251 for some of the consequences of *not* 
# having this setting and smb.conf(5) for details. 
;   winbind enum groups = yes 
;   winbind enum users = yes 
 
# Setup usershare options to enable non-root users to share folders 
# with the net usershare command. 
 
# Maximum number of usershare. 0 (default) means that usershare is disabled. 
;    usershare max shares = 100 
 
# Allow users who've been granted usershare privileges to create 
# public shares, not just authenticated ones 
    usershare allow guests = yes 
    username map = /etc/samba/smbusers 
    security = user 
;    guest ok = no 
;    guest account = nobody 
 
#======================= Share Definitions ======================= 
 
# Un-comment the following (and tweak the other settings below to suit) 
# to enable the default home directory shares. This will share each  
# user's home director as \\server\username 
;[homes] 
;   comment = Home Directories 
;   browseable = no 
 
# By default, the home directories are exported read-only. Change the 
# next parameter to 'no' if you want to be able to write to them. 
;   read only = yes 
 
# File creation mask is set to 0700 for security reasons. If you want to 
# create files with group=rw permissions, set next parameter to 0775. 
;   create mask = 0700 
 
# Directory creation mask is set to 0700 for security reasons. If you want to 
# create dirs. with group=rw permissions, set next parameter to 0775. 
;   directory mask = 0700 
 
# By default, \\server\username shares can be connected to by anyone 
# with access to the samba server. Un-comment the following parameter 
# to make sure that only "username" can connect to \\server\username 
# The following parameter makes sure that only "username" can connect 
# 
# This might need tweaking when using external authentication schemes 
;   valid users = %S 
 
# Un-comment the following and create the netlogon directory for Domain Logons 
# (you need to configure Samba to act as a domain controller too.) 
;[netlogon] 
;   comment = Network Logon Service 
;   path = /home/samba/netlogon 
;   guest ok = yes 
;   read only = yes 
 
# Un-comment the following and create the profiles directory to store 
# users profiles (see the "logon path" option above) 
# (you need to configure Samba to act as a domain controller too.) 
# The path below should be writable by all users so that their 
# profile directory may be created the first time they log on 
;[profiles] 
;   comment = Users profiles 
;   path = /home/samba/profiles 
;   guest ok = no 
;   browseable = no 
;   create mask = 0600 
;   directory mask = 0700 
 
[printers] 
    comment = All Printers 
    browseable = no 
    path = /var/spool/samba 
    printable = yes 
;    guest ok = no 
;    read only = yes 
    create mask = 0700 
 
# Windows clients look for this share name as a source of downloadable 
# printer drivers 
[print$] 
    comment = Printer Drivers 
    path = /var/lib/samba/printers 
;    browseable = yes 
;    read only = yes 
;    guest ok = no 
# Uncomment to allow remote administration of Windows print drivers. 
# You may need to replace 'lpadmin' with the name of the group your 
# admin users are members of. 
# Please note that you also need to set appropriate Unix permissions 
# to the drivers directory for these users to have write rights in it 
;   write list = root, @lpadmin 
 
# A sample share for sharing your CD-ROM with others. 
;[cdrom] 
;   comment = Samba server's CD-ROM 
;   read only = yes 
;   locking = no 
;   path = /cdrom 
;   guest ok = yes 
 
# The next two parameters show how to auto-mount a CD-ROM when the 
#    cdrom share is accesed. For this to work /etc/fstab must contain 
#    an entry like this: 
# 
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0 
# 
# The CD-ROM gets unmounted automatically after the connection to the 
# 
# If you don't want to use auto-mounting/unmounting make sure the CD 
#    is mounted on /cdrom 
# 
;   preexec = /bin/mount /cdrom 
;   postexec = /bin/umount /cdrom 
 
[Music] 
    path = /media/1TB Black 2/Music 
    writeable = yes 
;    browseable = yes 
    guest ok = yes             
                                     
        
```

---

### Post by bab1 on 2012-05-15
> # File creation mask is set to 0700 for security reasons. If you want to 
# create files with group=rw permissions, set next parameter to 0775. 
;   create mask = 0700 
 
# Directory creation mask is set to 0700 for security reasons. If you want to 
# create dirs. with group=rw permissions, set next parameter to 0664. 
;   directory mask = 0700 

Above is the pertinent part of the [global] section of the smb,conf file.  Edit this file as root (sudo).

The first part (create mask) is for setting the permissions on a file set that to 0664 and remove the ; from the left side of the line.

The second part is for directory permissions.  Set that for 3775 and remove the ; from the left side of the line.

Restart the samba daemon (smbd) or reboot the system and see what you get.  It should be right after that.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> Above is the pertinent part of the [global] section of the smb,conf file.  Edit this file as root (sudo).

The first part (create mask) is for setting the permissions on a file set that to 0664 and remove the ; from the left side of the line.

The second part is for directory permissions.  Set that for 3775 and remove the ; from the left side of the line.

Restart the samba daemon (smbd) or reboot the system and see what you get.  It should be right after that.

Awesome! Samba is working perfectly with the permissions now! 

My FTP permissions are still not working, however. Here's the config file for vsftpd:

```
# Example config file /etc/vsftpd.conf 
# 
# The default compiled in settings are fairly paranoid. This sample file 
# loosens things up a bit, to make the ftp daemon more usable. 
# Please see vsftpd.conf.5 for all compiled in defaults. 
# 
# READ THIS: This example file is NOT an exhaustive list of vsftpd options. 
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's 
# capabilities. 
# 
# 
# Run standalone?  vsftpd can run either from an inetd or as a standalone 
# daemon started from an initscript. 
listen=YES 
# 
# Run standalone with IPv6? 
# Like the listen parameter, except vsftpd will listen on an IPv6 socket 
# instead of an IPv4 one. This parameter and the listen parameter are mutually 
# exclusive. 
#listen_ipv6=YES 
# 
# Allow anonymous FTP? (Beware - allowed by default if you comment this out). 
anonymous_enable=NO 
# 
# Uncomment this to allow local users to log in. 
local_enable=YES 
# 
# Uncomment this to enable any form of FTP write command. 
write_enable=YES 
# 
# Default umask for local users is 077. You may wish to change this to 022, 
# if your users expect that (022 is used by most other ftpd's) 
local_umask=766 
# 
# Uncomment this to allow the anonymous FTP user to upload files. This only 
# has an effect if the above global write enable is activated. Also, you will 
# obviously need to create a directory writable by the FTP user. 
#anon_upload_enable=YES 
# 
# Uncomment this if you want the anonymous FTP user to be able to create 
# new directories. 
#anon_mkdir_write_enable=YES 
# 
# Activate directory messages - messages given to remote users when they 
# go into a certain directory. 
dirmessage_enable=YES 
# 
# If enabled, vsftpd will display directory listings with the time 
# in  your  local  time  zone.  The default is to display GMT. The 
# times returned by the MDTM FTP command are also affected by this 
# option. 
use_localtime=YES 
# 
# Activate logging of uploads/downloads. 
xferlog_enable=YES 
# 
# Make sure PORT transfer connections originate from port 20 (ftp-data). 
connect_from_port_20=YES 
# 
# If you want, you can arrange for uploaded anonymous files to be owned by 
# a different user. Note! Using "root" for uploaded files is not 
# recommended! 
#chown_uploads=YES 
#chown_username=whoever 
# 
# You may override where the log file goes if you like. The default is shown 
# below. 
#xferlog_file=/var/log/vsftpd.log 
# 
# If you want, you can have your log file in standard ftpd xferlog format. 
# Note that the default log file location is /var/log/xferlog in this case. 
#xferlog_std_format=YES 
# 
# You may change the default value for timing out an idle session. 
#idle_session_timeout=600 
# 
# You may change the default value for timing out a data connection. 
#data_connection_timeout=120 
# 
# It is recommended that you define on your system a unique user which the 
# ftp server can use as a totally isolated and unprivileged user. 
#nopriv_user=ftpsecure 
# 
# Enable this and the server will recognise asynchronous ABOR requests. Not 
# recommended for security (the code is non-trivial). Not enabling it, 
# however, may confuse older FTP clients. 
#async_abor_enable=YES 
# 
# By default the server will pretend to allow ASCII mode but in fact ignore 
# the request. Turn on the below options to have the server actually do ASCII 
# mangling on files when in ASCII mode. 
# Beware that on some FTP servers, ASCII support allows a denial of service 
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd 
# predicted this attack and has always been safe, reporting the size of the 
# raw file. 
# ASCII mangling is a horrible feature of the protocol. 
#ascii_upload_enable=YES 
#ascii_download_enable=YES 
# 
# You may fully customise the login banner string: 
#ftpd_banner=Welcome to blah FTP service. 
# 
# You may specify a file of disallowed anonymous e-mail addresses. Apparently 
# useful for combatting certain DoS attacks. 
#deny_email_enable=YES 
# (default follows) 
#banned_email_file=/etc/vsftpd.banned_emails 
# 
# You may restrict local users to their home directories.  See the FAQ for 
# the possible risks in this before using chroot_local_user or 
# chroot_list_enable below. 
#chroot_local_user=YES 
# 
# You may specify an explicit list of local users to chroot() to their home 
# directory. If chroot_local_user is YES, then this list becomes a list of 
# users to NOT chroot(). 
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that 
# the user does not have write access to the top level directory within the 
# chroot) 
#chroot_local_user=YES 
#chroot_list_enable=YES 
# (default follows) 
#chroot_list_file=/etc/vsftpd.chroot_list 
# 
# You may activate the "-R" option to the builtin ls. This is disabled by 
# default to avoid remote users being able to cause excessive I/O on large 
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume 
# the presence of the "-R" option, so there is a strong case for enabling it. 
#ls_recurse_enable=YES 
# 
# Customization 
# 
# Some of vsftpd's settings don't fit the filesystem layout by 
# default. 
# 
# This option should be the name of a directory which is empty.  Also, the 
# directory should not be writable by the ftp user. This directory is used 
# as a secure chroot() jail at times vsftpd does not require filesystem 
# access. 
secure_chroot_dir=/var/run/vsftpd/empty 
# 
# This string is the name of the PAM service vsftpd will use. 
pam_service_name=vsftpd 
# 
# This option specifies the location of the RSA certificate to use for SSL 
# encrypted connections. 
rsa_cert_file=/etc/ssl/private/vsftpd.pem 			
```

As you can see, I tried setting local umask to something ridiculous just to see if it was working, but unfortunately it didn't change the permissions of the file I added.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> Awesome! Samba is working perfectly with the permissions now! 

My FTP permissions are still not working, however. Here's the config file for vsftpd:

```
# Example config file /etc/vsftpd.conf 
# 
# The default compiled in settings are fairly paranoid. This sample file 
# loosens things up a bit, to make the ftp daemon more usable. 
# Please see vsftpd.conf.5 for all compiled in defaults. 
# 
# READ THIS: This example file is NOT an exhaustive list of vsftpd options. 
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's 
# capabilities. 
# 
# 
# Run standalone?  vsftpd can run either from an inetd or as a standalone 
# daemon started from an initscript. 
listen=YES 
# 
# Run standalone with IPv6? 
# Like the listen parameter, except vsftpd will listen on an IPv6 socket 
# instead of an IPv4 one. This parameter and the listen parameter are mutually 
# exclusive. 
#listen_ipv6=YES 
# 
# Allow anonymous FTP? (Beware - allowed by default if you comment this out). 
anonymous_enable=NO 
# 
# Uncomment this to allow local users to log in. 
local_enable=YES 
# 
# Uncomment this to enable any form of FTP write command. 
write_enable=YES 
# 
# Default umask for local users is 077. You may wish to change this to 022, 
# if your users expect that (022 is used by most other ftpd's) 
local_umask=766 
# 
# Uncomment this to allow the anonymous FTP user to upload files. This only 
# has an effect if the above global write enable is activated. Also, you will 
# obviously need to create a directory writable by the FTP user. 
#anon_upload_enable=YES 
# 
# Uncomment this if you want the anonymous FTP user to be able to create 
# new directories. 
#anon_mkdir_write_enable=YES 
# 
# Activate directory messages - messages given to remote users when they 
# go into a certain directory. 
dirmessage_enable=YES 
# 
# If enabled, vsftpd will display directory listings with the time 
# in  your  local  time  zone.  The default is to display GMT. The 
# times returned by the MDTM FTP command are also affected by this 
# option. 
use_localtime=YES 
# 
# Activate logging of uploads/downloads. 
xferlog_enable=YES 
# 
# Make sure PORT transfer connections originate from port 20 (ftp-data). 
connect_from_port_20=YES 
# 
# If you want, you can arrange for uploaded anonymous files to be owned by 
# a different user. Note! Using "root" for uploaded files is not 
# recommended! 
#chown_uploads=YES 
#chown_username=whoever 
# 
# You may override where the log file goes if you like. The default is shown 
# below. 
#xferlog_file=/var/log/vsftpd.log 
# 
# If you want, you can have your log file in standard ftpd xferlog format. 
# Note that the default log file location is /var/log/xferlog in this case. 
#xferlog_std_format=YES 
# 
# You may change the default value for timing out an idle session. 
#idle_session_timeout=600 
# 
# You may change the default value for timing out a data connection. 
#data_connection_timeout=120 
# 
# It is recommended that you define on your system a unique user which the 
# ftp server can use as a totally isolated and unprivileged user. 
#nopriv_user=ftpsecure 
# 
# Enable this and the server will recognise asynchronous ABOR requests. Not 
# recommended for security (the code is non-trivial). Not enabling it, 
# however, may confuse older FTP clients. 
#async_abor_enable=YES 
# 
# By default the server will pretend to allow ASCII mode but in fact ignore 
# the request. Turn on the below options to have the server actually do ASCII 
# mangling on files when in ASCII mode. 
# Beware that on some FTP servers, ASCII support allows a denial of service 
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd 
# predicted this attack and has always been safe, reporting the size of the 
# raw file. 
# ASCII mangling is a horrible feature of the protocol. 
#ascii_upload_enable=YES 
#ascii_download_enable=YES 
# 
# You may fully customise the login banner string: 
#ftpd_banner=Welcome to blah FTP service. 
# 
# You may specify a file of disallowed anonymous e-mail addresses. Apparently 
# useful for combatting certain DoS attacks. 
#deny_email_enable=YES 
# (default follows) 
#banned_email_file=/etc/vsftpd.banned_emails 
# 
# You may restrict local users to their home directories.  See the FAQ for 
# the possible risks in this before using chroot_local_user or 
# chroot_list_enable below. 
#chroot_local_user=YES 
# 
# You may specify an explicit list of local users to chroot() to their home 
# directory. If chroot_local_user is YES, then this list becomes a list of 
# users to NOT chroot(). 
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that 
# the user does not have write access to the top level directory within the 
# chroot) 
#chroot_local_user=YES 
#chroot_list_enable=YES 
# (default follows) 
#chroot_list_file=/etc/vsftpd.chroot_list 
# 
# You may activate the "-R" option to the builtin ls. This is disabled by 
# default to avoid remote users being able to cause excessive I/O on large 
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume 
# the presence of the "-R" option, so there is a strong case for enabling it. 
#ls_recurse_enable=YES 
# 
# Customization 
# 
# Some of vsftpd's settings don't fit the filesystem layout by 
# default. 
# 
# This option should be the name of a directory which is empty.  Also, the 
# directory should not be writable by the ftp user. This directory is used 
# as a secure chroot() jail at times vsftpd does not require filesystem 
# access. 
secure_chroot_dir=/var/run/vsftpd/empty 
# 
# This string is the name of the PAM service vsftpd will use. 
pam_service_name=vsftpd 
# 
# This option specifies the location of the RSA certificate to use for SSL 
# encrypted connections. 
rsa_cert_file=/etc/ssl/private/vsftpd.pem 			
```

As you can see, I tried setting local umask to something ridiculous just to see if it was working, but unfortunately it didn't change the permissions of the file I added.

I don't use vsftp at all.  I'll bet that if you set the umask to what you want (002 or 0002) it will work after you reload or reboot the system.  If it doesn't you need to Google it.  Sorry, no vsftp goodness here.

Have you tried sFTP this is OpenSSH that looks (and work) like FTP.  You would need to install OpenSSH server on the file server.

I'm gone for the next few hours.  I'll check back then.

---

### Post by AbsenteeSurgeon on 2012-05-15
> **bab1 said:**
> I don't use vsftp at all.  I'll bet that if you set the umask to what you want (002 or 0002) it will work after you reload or reboot the system.  If it doesn't you need to Google it.  Sorry, no vsftp goodness here.

Have you tried sFTP this is OpenSSH that looks (and work) like FTP.  You would need to install OpenSSH server on the file server.

I'm gone for the next few hours.  I'll check back then.

This actually worked perfectly! Now new files have the permission "-rw-rw-r--" and new directories have "drwxrwsr-x" in both FTP and Samba!

I can't thank you enough for all of the help you've given me today! I'm sure that you've not only helped me, but you've also helped anybody in the future who's having a similar issue.

---

### Post by bab1 on 2012-05-15
> **AbsenteeSurgeon said:**
> This actually worked perfectly! Now new files have the permission "-rw-rw-r--" and new directories have "drwxrwsr-x" in both FTP and Samba!

I can't thank you enough for all of the help you've given me today! I'm sure that you've not only helped me, but you've also helped anybody in the future who's having a similar issue.

Just before I turn this machine off...

I'm glad it all worked out.  Now if you want to restrict one of your users rw access you can just remove them from the group.  The hard part is setting it up.  It makes the administration easy.

---

