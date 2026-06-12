---
title: "Samba server sticky bit for common share."
date: 2015-10-27
forum: Server Platforms
---

### Post by gardenair on 2015-10-27
hi,
         I have two questions. I am configuring samba server and in it i add 10 users, by the command i add the users

```
# useradd user1
.
.
.
#useradd user10
```

I want that i may create a user but it should create its home directory by which the users can login to the desktop.what switch should I use with "useradd " command so a user should create without its home directory.The reason its this user will be login from windows machines "z" drive to keep its files over the network.

2- My second question is I have created a "common-share" to dump users files in their respective folders.I have assign 

```
# chmod –R  1750  common-share
```

and inside "common-share" there is a subsolder "user1" in which he keep his files.

```
#ls -l 
drwx r-x --T  user1  group1  4096  oct 27 18:31 user1
```


Now  when the user1 create a folder inside "user1" folder there is no sticky bit with it,  it show like

```
# ls -l

drwx r-x r-x  user1  group1  4096  oct 27 18:31 user1
```

Here I can not see the sticky bit ! what will be the reason ?


please guide me.
gardenair

---

### Post by bab1 on 2015-10-27
> **gardenair said:**
> hi,
         I have two questions. I am configuring samba server and in it i add 10 users, by the command i add the users

```
# useradd user1
.
.
.
#useradd user10
```

I want that i may create a user but it should create its home directory by which the users can login to the desktop.what switch should I use with "useradd " command so a user should create without its home directory.The reason its this user will be login from windows machines "z" drive to keep its files over the network.

There is no switch to do what you want.  **The user always needs a home directory ** to log in to the system or use a remote file share.  The home directory does not have to be located at /home/<some-user>, however.  The home directory can reside anywhere in the file system.
> 

2- My second question is I have created a "common-share" to dump users files in their respective folders.I have assign 

```
# chmod –R  1750  common-share
```

and inside "common-share" there is a subsolder "user1" in which he keep his files.

```
#ls -l 
drwx r-x --T  user1  group1  4096  oct 27 18:31 user1
```


Now  when the user1 create a folder inside "user1" folder there is no sticky bit with it,  it show like

```
# ls -l

drwx r-x r-x  user1  group1  4096  oct 27 18:31 user1
```

Here I can not see the sticky bit ! what will be the reason ?

The sticky bit is used to keep all users except the owner and root from deleting files from a directory.  This is not an inherited mode.  The sticky bit does not effect the umask when creating new files or directories.  All files will still be created with the permissions of 0664 and all directories will be created with permissions of 0775.  The only exception to this umask setting is when the root user creates files and directories.  The permissions would then be 0644 and 0755.

Did you make "group1" the primary group for user1?  Why are the permissions for this folder 0755 ```
drwx r-x r-x  user1  group1  4096  oct 27 18:31 user1
```

Most likely you should not be using a common directory with a sticky bit for all the users to share.  That would be the "public" directory we have talked about before.  You certainly can't use the directory with the permissions you have set (1750) as the only user account that can write to the directory is *user1*.  Not very common-share at all. 

You can use Samba to create a share that automatically allows *_each user to have their own private directory_*.  This is called a [homes] share.  A "public" share is normally a place where everyone can read/write and delete files.  If you want to limit the exposure to just a few users then you use a group that holds only those users that you want to have access.  Samba can serve a semi private share to only those remote users.

What exactly are you trying to do at this time?

---

### Post by gardenair on 2015-10-27
thanks "Bab1" for your kind reply.well regarding to my 1st question in my main linux box i can see all 10 users names of user which i have created for samba server.
It irritate me the list of users in the in the login dialog box. I just want that the user will create a user for samba server . As u said it is not possible  but still i ask any way....

My second issue is i want to create a public share ,in that public share each user has his/her own folder ,suppose "User1 Folder" ,  "User2 Folder "  and "User3 Folder".
Now each user will keep his file in his respective folder because each user will map his "z" drive with his own login name and password crated in samba .
The advantage is each user can not delete other files files and folder but they can copy and past files from one to another.This is due to 0750 permission.
The public drive i.e "z" drive is our office requirement .

Regards
gardenair

---

### Post by bab1 on 2015-10-27
> **gardenair said:**
> thanks "Bab1" for your kind reply.well regarding to my 1st question in my main linux box i can see all 10 users names of user which i have created for samba server.
It irritate me the list of users in the in the login dialog box. I just want that the user will create a user for samba server . As u said it is not possible  but still i ask any way....

You did not ask the correct question.  I never said you can't hide the login names on a desktop environment.  In fact, you are able to hide users.  On the other hand you also didn't state that you had added a GUI environment to your server install.  The default Ubuntu Server Edition has no GUI at all.  How would anyone know that what you really wanted advice on how to hide the users login when using a desktop environment?

What desktop environment did you install on your Ubuntu Server?
> 

My second issue is i want to create a public share ,in that public share each user has his/her own folder ,suppose "User1 Folder" ,  "User2 Folder "  and "User3 Folder".
Now each user will keep his file in his respective folder because each user will map his "z" drive with his own login name and password crated in samba .
The advantage is each user can not delete other files files and folder but they can copy and past files from one to another.This is due to 0750 permission.
The public drive i.e "z" drive is our office requirement .

Regards
gardenair
This is not truly a "public" share.  Your description is that of a [homes] share.  Read about [homes] setting up the [home] share [**here**]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/").  Then we can talk about how it can work for you.  As I said before, you can leave the directories at /home or you can move them to another location in the file system.  It all works the same.  I would only move them if I needed to backup the [homes] share along with all the other shares that I have located at* /srv/share/samba*.  This would be something like```

/srv/share/samba
                /home
                /data
                /pictures

```...or something close to this.

---

