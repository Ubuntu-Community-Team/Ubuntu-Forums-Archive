---
title: "Samba Sticky Bit Permissions with Windows"
date: 2012-12-11
forum: Security
---

### Post by Methus on 2012-12-11
Hello all!

I have a question I was wondering you all could answer for me. It deals with the sticky bit with Ubuntu 12.04 LTS, Samba, and a Windows client environment.

I have an Ubuntu 12.04 LTS server acting as a PDC and file server on a Windows client environment, mainly Windows XP Pro.
There's a particular share that I need to have users be able to read, write, and modify files, but CANNOT delete them.

I've read up both on these forums and others through Google searches that setting the stick bit on the folder containing the files would remedy this; that if I did that then only the owner of the file can delete it.

However, when testing this, the user can still delete the file. This is what I have specifically:

On the Linux level, I have the SUID, SGID, and sticky bit set on the folder, in this case called 'forms.' I did this so whenever a file is put in there, it sets the user to the folder owner (root) so the sticky bit would take affect (since the user isn't root), and the group is set to the folder's group, so that the users belonging to that group can still read and write to that folder.

On the Samba level, I have valid users set to the group that owns the folder, read only set to no so they can write to it, create mask to 0660, and directory mask to 0770, and guest is set to no.

When I have a regular user set a file in the share, it properly sets the group and owner correctly, but if he then tries to delete the file, he can. If I understand all this correctly though, he shouldn't be able to. 

So...what am I doing wrong exactly? *confused*

---

### Post by redmk2 on 2012-12-11
> **Methus said:**
> Hello all!

I have a question I was wondering you all could answer for me. It deals with the sticky bit with Ubuntu 12.04 LTS, Samba, and a Windows client environment.

I have an Ubuntu 12.04 LTS server acting as a PDC and file server on a Windows client environment, mainly Windows XP Pro.
There's a particular share that I need to have users be able to read, write, and modify files, but CANNOT delete them.

I've read up both on these forums and others through Google searches that setting the stick bit on the folder containing the files would remedy this; that if I did that then only the owner of the file can delete it.

However, when testing this, the user can still delete the file. This is what I have specifically:

On the Linux level, I have the SUID, SGID, and sticky bit set on the folder, in this case called 'forms.' I did this so whenever a file is put in there, it sets the user to the folder owner (root) so the sticky bit would take affect (since the user isn't root), and the group is set to the folder's group, so that the users belonging to that group can still read and write to that folder.

On the Samba level, I have valid users set to the group that owns the folder, read only set to no so they can write to it, create mask to 0660, and directory mask to 0770, and guest is set to no.

When I have a regular user set a file in the share, it properly sets the group and owner correctly, but if he then tries to delete the file, he can. If I understand all this correctly though, he shouldn't be able to. 

So...what am I doing wrong exactly? *confused*

The sticky bit only works if the user is NOT in the group and is NOT the owner of the file.  The best example of this is the /tmp directory.  it's set up exactly like you want.  A user who is NOT the owner or in the group can't delete that file.

Linux permissions are just that permissions.  There is no other "ownership" rights.  As the group rights are NOT inherited unless you specifically set that by SGID or SUID you can't use the sticky bit.  File permissions are slightly different from directory (folder) permissions.  The permissions rw are the same but the eXecute permissions mean different things x for files means a executable script or binary file.  A directory uses the X as meaning you can transit (descend into) that directory.

---

### Post by Methus on 2012-12-16
So, in essence, there isn't a way to have a directory where a group can share files, but be denied the privilege to delete them if they're not the owner/creator of said file? And that's because they are in the same group?

It just seems to me that this would be a feature many others would want. Or am I out in the cold on this one?

Would it work if the group was set differently (to one they are not in), but the permissions were set where everyone can read/write to the files?

---

### Post by Ms. Daisy on 2012-12-16
You can choose to allow a user to read a file but not write to it.  

But if they have permission to write to the file then they would also by default be able to delete it. Think about it- someone could open a word document, delete all the text, then save the empty word document thus effectively deleting it.

---

### Post by Methus on 2012-12-16
Yes, but the file itself would still be linked; it'd just be an empty file, but the file itself would still exist. I'm trying to find a way to keep non-owners of the file from unlinking it.

---

### Post by redmk2 on 2012-12-16
> **Methus said:**
> Yes, but the file itself would still be linked; it'd just be an empty file, but the file itself would still exist. I'm trying to find a way to keep non-owners of the file from unlinking it.

What is a "non-owner"?  All file are created with 3 types of users and 3 levels of permissions.  These are Linux permissions, not Samba permissions.  Samba permissions will not override Linux permissions.  You can provide exceptions to Samba permissions these but you have to live with Linux rules ultimately.

You also can create exceptions to the basic Linux permissions, but they are best use as exceptions and not the rules.  These are Linux file ACL's and file attributes.  The file attributes are set with chattr.  If a file's attribute is set to immutable it can't be removed unless the attribute is changed first.

The concept of "ownership" is not really accurate for Linux files and directories.  The user (owner) is the creator, but if you set permissions to rw for both the the owner and the group, both entities have the same permissions to act on that file.  If you were to add rw as the permissions then all users (the rest of the world) would have the same permissions.  

I control my user access by the group permission settings.  I only think of the owner as the user that created the file.  For my shared files I set the root directory of the share with 2775 permissions.  Then I set the group to one that holds all the users that need access to the share.  From then on all files have permissions of 664 and all directories have permissions of 775.

It might be helpful to deal with a specific set of circumstances (your actual problem) to push this forward.  The tools are there to achieve what you want but they may not be what you might think.

---

### Post by Methus on 2012-12-16
Okay, this is my scenario...

I administer an Ubuntu 12.04 LTS server for a local police station. This network is setup on a Samba domain with roaming profiles and file shares. A particular file share contains database files for a records management system program that is installed on all of the client computers (Windows XP Pro). Everytime a user logs in, this particular share is mapped to a network drive based on the fact that they are in the group that has access to that share.

I have it, in Linux, where the directory containing these files are set as rw for the group, so any user logging in to a client machine can open these files with the program and add information to it. However, if for any reason in the future an employee becomes disgruntled, I don't want them to be able to go into the share and delete all of the database files.

In short, I need the directory open to group for rw access for this program, but I do NOT want them to be able to outright delete (unlink?) the files in the share.

---

### Post by redmk2 on 2012-12-16
> **Methus said:**
> Okay, this is my scenario...

I administer an Ubuntu 12.04 LTS server for a local police station. This network is setup on a Samba domain with roaming profiles and file shares. A particular file share contains database files for a records management system program that is installed on all of the client computers (Windows XP Pro). Everytime a user logs in, this particular share is mapped to a network drive based on the fact that they are in the group that has access to that share.

I have it, in Linux, where the directory containing these files are set as rw for the group, so any user logging in to a client machine can open these files with the program and add information to it. However, if for any reason in the future an employee becomes disgruntled, I don't want them to be able to go into the share and delete all of the database files.

In short, I need the directory open to group for rw access for this program, but I do NOT want them to be able to outright delete (unlink?) the files in the share.

How do you create inheritance of the group in sub-directories and files; or do you at this time?  Why can't you just delete the user if you demote or terminate them?  You do run backups on the data; right?  Do you have many files like this?  Do you know how hard links (not soft links) work?  How many users are in the group?

---

### Post by Methus on 2012-12-16
> How do you create inheritance of the group in sub-directories and files; or do you at this time?
I have it set in Samba to force the user to root and the group to the appropriate group for all files within the share directory.

> Why can't you just delete the user if you demote or terminate them?
A disgruntled employee could be caused by numerous things: demotion, cut of paycheck or hours, write-up, an argument, etc. In these occurrences the employee still needs access to the file share and the database for his job.

> You do run backups on the data; right?
Every morning at 0300 when the database files are less likely to be locked from use.

> Do you have many files like this?
There's about 110 files in this particular share that needs to be protected.

> Do you know how hard links (not soft links) work?
Originally I did not, but I just did some skimming and light reading on it. From what I understand, a soft link acts like a redirect to the original filename, which points to the inode with the data.
A hard link acts as another filename that points to the inode itself.

> How many users are in the group?
This is a small department, so there are currently only 9 users.

---

### Post by redmk2 on 2012-12-16
> **Methus said:**
> I have it set in Samba to force the user to root and the group to the appropriate group for all files within the share directory.
There are much better ways of doing this.  In fact when you do this you loose the use of group called "others".  It's much better to set this up in the linux file system (ext4?) > 

A disgruntled employee could be caused by numerous things: demotion, cut of paycheck or hours, write-up, an argument, etc. In these occurrences the employee still needs access to the file share and the database for his job.
I won't comment on the  social aspects of employees, other than you have to have some faith in there integrity,> 

Every morning at 0300 when the database files are less likely to be locked from use.
You could easily back the data up hourly with rsnapshot.> 

There's about 110 files in this particular share that needs to be protected.
If these files are all hardlinked to another subdirectoy that only a few had access to then the files could not be deleted until BOTH links to the inode are removed.  In other words deleting the link in the shared directory WOULD NOT delete the file.> 

Originally I did not, but I just did some skimming and light reading on it. From what I understand, a soft link acts like a redirect to the original filename, which points to the inode with the data.
A hard link acts as another filename that points to the inode itself.
Allowing you to protect yourself.> 


This is a small department, so there are currently only 9 users.

Are you creating new files on a daily basis?

Here are some ideas of things you can do.  Create a group that has rw rights in the share.  Set the GID bit on the root directory (chmod 2775) and use chgrp to change the group to this group (you can use *sambashare* or create your own.  I created a group named *smbusers*.  This means you can get rid of the ***force ***commands in you share definition.

At this point if your users become untrustworthy you can remove them from the group and the will have no access to the share.  

If you like, you can hard link all of the files to another directory that has only root access (you so have root access I assume).  I this way only you can finally delete the files.  FYI (hard links take up no real extra space as there is only one file with 2 links.

The biggest problem is the need to have RW without the ability to delete a file.  You will never be able to this as RW includes the right to delete.  The only other option is to look at ACL's.  I don't use ACL's  because each one is individual and it becomes a mess to administrate them.  But as you have only 9 users...

So in short you can use SGID and group inheritance along with hard links and or ACL"s

If you want to do this I would create a test share so you can see every step of the way what happens.  As always YMMV.

---

### Post by Methus on 2012-12-17
Files are written to and changed daily in this particular share.

I like the idea of placing hard links within a secure directory. I might implement this as a security precaution.

As for snapshot, well... the way the department wants to handle backups is for a weekly full backup to be put in place, and then a daily differential backup after that. At the end of the week, the backups are placed on an external hard drive, and this drive is then taken to the city hall and locked up.

I've been working on a Perl script to make tar.bz2 archives of the necessary files. I'm working on a solution for when the files are locked and cannot be archived, and for differential backups using tar.
It's been a great learning experience so far, I must say.

Thank you for all the help with this.

---

### Post by redmk2 on 2012-12-17
> **Methus said:**
> Files are written to and changed daily in this particular share.

I like the idea of placing hard links within a secure directory. I might implement this as a security precaution.

As for snapshot, well... the way the department wants to handle backups is for a weekly full backup to be put in place, and then a daily differential backup after that. At the end of the week, the backups are placed on an external hard drive, and this drive is then taken to the city hall and locked up.

I've been working on a Perl script to make tar.bz2 archives of the necessary files. I'm working on a solution for when the files are locked and cannot be archived, and for differential backups using tar.
It's been a great learning experience so far, I must say.

Thank you for all the help with this.

Read up on rsnapshot.  It uses hardlinks to make backup copies for hour, day, month year. The whole thing is written in PERL.  

Edit:  I want you to look at how the hardlinks are created in a script.  Not so much for the backup aspects.

---

### Post by Methus on 2012-12-17
Well noted. Thank you again for your help in pointing me in the right direction and guiding my learning in this experience. I have definitely discovered a whole new aspect of Linux I had no idea was there (the deal with inodes in particular).

---

### Post by redmk2 on 2012-12-17
> **Methus said:**
> Well noted. Thank you again for your help in pointing me in the right direction and guiding my learning in this experience. I have definitely discovered a whole new aspect of Linux I had no idea was there (the deal with inodes in particular).
You're welcome.  If you want practical help rather than just the theory on setting up a test share let me know.

---

### Post by mailmuncher2000 on 2013-07-08
I know this is an old post but I had similar question which I think I have understood now so I am just putting it out there in case it is helpful to someone else searching for this. Also I don't think Methus' is original question got answer completely so here goes. Please correct me if I am wrong.

Lets say you have a directory called "Docs" permissions as follows (note: no sticky bit)
```
drwxrwx--- 2 root users 4096 Jul  8 04:47 Docs
```

And two files inside the directory "Docs" file1 created by alice and file2 created by bob with permission as follows:
```
-rw-r----- 1 alice alice    5 Jul  8 00:28 file1
-rw-r----- 1 bob bob       9 Jul  7 21:52 file2
```

In this case bob would be able to delete file1 even though he has only read access to the file (in either owner or group permissions). Actually it is the permissions on the directory that determine if bob can delete the file so in this case bob has write permissions on the directory (because he is in the "users" group).

Now lets say we add a sticky bit to "Docs"
```
sudo chmod +t Docs
```

And so now "Docs" permission becomes (with sticky bit):
```
drwxrwx--T 2 root users 4096 Jul  8 04:47 Docs
```

Now bob will not be able to delete alice's file1 because of the Sticky bit.... I think this is what you wanted Methus. In this case only the owner (alice) of file1 can delete it.

If you want to implement this with Samba just use "force directory mode = 1000" in the /etc/samba/smb.conf config file for the your share and then every folder you create under that share will have the sticky bit set. See [this]("http://www.samba.org/samba/docs/man/manpages/smb.conf.5.html#FORCEDIRECTORYMODE"). More specifically "force directory mode" does a 'OR'ing of permission bits so that every permission number will have 1 in the beginning eg: 0755 OR 1000 = 1755 => folder with sticky bit.

Example smb.conf code:
```
[Docs]
        writeable = yes
        path = /Docs
        force directory mode = 1000
```

With regard to Setting the SUID/SGID bits you might wanna check this [link]("http://www.howtoforge.com/linux_setting_suid_sgid_bits") out.

---

