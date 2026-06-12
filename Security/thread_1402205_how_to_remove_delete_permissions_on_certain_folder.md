---
title: "how to remove delete permissions on certain folders?"
date: 2010-02-08
forum: Security
---

### Post by keevill on 2010-02-08
I have a Ubuntu file server with a mix of 30+ users ( mix of windows and linux ).
All are members of the same group.
All need read write create access.
I want to prevent deletion of certain key folders.
How can I achieve this ?
sudo chmod -R nnnn ??

-keevill-

---

### Post by rookcifer on 2010-02-08
```
chmod 1770 /path/to/folder
```

This will allow the owner and group rwx access.  It won't allow "others" any access at all.  If you want to allow "others," simply change it to "chmod 1777."

At any rate, the above will allow the group members to create files in the directory but won't allow them to delete the directory or any files *they don't own*.  Keep in mind, if they do own the file, they *can* delete it.

The key to this is the "1."  This is known as the [sticky bit.]("http://www.linuxjournal.com/article/7727")  If you don't want to change any permissions of your directory but only want to add this sticky bit, instead of using the above command, you can simply use:
```

chmod +t /path/to/directory
```

---

### Post by yogesh.girikumar on 2010-02-10
Hi,
       You can make the files and folders immutable (meaning event the root can't delete it or modify it in any way) by using the chattr command.
       Do
   ```
$ sudo chattr +i <filename>
```      to make the file immutable. This is also applicable for directories. The '+i' makes it impossible to delete the file or modify it. So if you make a directory immutable, you can't add files to it or rename it or change its permissions even if you're root. But you can change the permissions of the files contained in it.
       
You can unset the sticky bit by typing the following in the terminal;
   ```
$ sudo chattr -i <filename>
```      You can view the attributes assigned to a file using the following command.
   ```
$ lsattr -l
```More on chattr : [http://en.wikipedia.org/wiki/Chattr](http://en.wikipedia.org/wiki/Chattr)   

Instead if you want only the owner of the file to be able to delete the file, you can use a sticky bit.
do ```
$ sudo chmod +t <filename>
```The 't' here is called a sticky bit or a "restricted deletion flag". It will prevent users from deleting or renaming files that they do not 'own' ( i.e. that they didn't create ).

The manpages of chattr and chmod are also informative.

---

### Post by Pritamsng on 2010-02-10
**[B]Sticky bit **[/B]

Sticky bits are mainly set on directories.
If the sticky bit is set for a directory, only the owner of that directory or the owner of a file can delete or rename a file within that directory.
Example:
Consider you have a directory " test ".
chmod it to " 777 ". This gives permissions for all the users to read, write and execute.
chmod +t test
Example: ls -al
drwxrwxrwt 2 a1 a1 4096 Jun 13 2008 .
-rw-rw-r-- 1 a1 a1 0 Jun 11 17:30 1.txt
-rw-rw-r-- 1 b2 b2 0 Jun 11 22:52 2.txt
From the above example a1 is the owner of the test directory. 
a1 can delete or rename the files 1.txt and 2.txt.
b2 can delete or rename the file 2.txt only.

---

### Post by keevill on 2010-02-16
> **rookcifer said:**
> ```
chmod 1770 /path/to/folder
```

This will allow the owner and group rwx access.  It won't allow "others" any access at all.  If you want to allow "others," simply change it to "chmod 1777."

At any rate, the above will allow the group members to create files in the directory but won't allow them to delete the directory or any files *they don't own*.  Keep in mind, if they do own the file, they *can* delete it.

The key to this is the "1."  This is known as the [sticky bit.]("http://www.linuxjournal.com/article/7727")  If you don't want to change any permissions of your directory but only want to add this sticky bit, instead of using the above command, you can simply use:
```

chmod +t /path/to/directory
```

Thank you for your help and apologies for the delay responding.
I followed this advice and did the following.

Created a folder a1,subfolder a2, subfolder a3. 

Then sudo chmod 777 a1 -R 
All users have full access inc delete of course.

Then I used sudo chmod +t a1 +R ( since I wanted the command to prevent subfolder deletion recursively )
It worked. No-one but the owner of the subfolders could delete them.

How do I remove the 'sticky bit' command to allow deletion on the main a1 folder?
Actually even the owner of the a1 main folder cannot delete it . Only the subfolders are deleted.
I am therefore stuck with a folder a1 which no-one can delete.

Not a big deal but before I roll out the command to main folders, I would like to know how to remove the 'sticky bit' command
Thx again for any help

---

### Post by kemra on 2010-02-16
Have you tried:

```
chmod -t /path/to/folder
```

I'm not in a place where I can test this right now but from memory that should work.

---

### Post by keevill on 2010-02-17
OK now I have got to a stage where I can achieve the following.

Create dir 'test'
sudo chmod 777 test
sudo chmod +t test
 
If user A creates a subfolder in test then only user A can delete .
If user B creates a subfolder let's say called 'Bfolder' then user A cannot delete it.
BUT if user A creates a subfolder inside 'Bfolder' then anyone can delete this subfolder and indeed any other subsequently created folders and nested folders.
It seems that the +t sticky is not recursive on subfolders created after the initial folder creation.
i.e the stick protection is ONLY on the firstly created one.

Is there a solution to protect nested folders which are created already? and WILL BE created in the future?

---

### Post by bluefrog on 2010-02-17
work with ACL. use ACL to set default permissions for given users/group on new file/folders (setfacl)

---

### Post by yogesh.girikumar on 2010-02-25
Hi,


       Permissions in Linux are not inherited. They are static in the sense that any child directories or files created under a certain parent directory need not have the same permissions as that of the parent directories. So you cannot automatically make child directories / files inherit permissions from parents.
       For this you can use a default ACL. A default ACL for a directory is passed on to the subdirectories and files. This can be set using the command
   ```
$ sudo setfacl -d -m user::rwx,user:<user 1>:---,user:<user 2>:--- <mydirectory>
```      This command will give give read write and execute permissions for the owner on the directory "mydirectory" It will revoke all permissions for "user 1" and "user 2". Replace user 1, user 2 with usernames and mydir with your file or directory name. ( Without the angle brackets "<",">" ).

       The -m is for modifying any existing ACL and the -d is to make it the default ACL. This will set read, write and execute permissions for the owner as the default permission. If this is set for a directory, the subdirectories and files contained in it will have read write and execute permissions for their respective owners as well.


       Make sure you have ACLs enabled in your filesystem.


       **This will however not prevent "root" user from being able to delete or rename your files**. More information about the setfacl command and acl command can be found from the man pages.

---

