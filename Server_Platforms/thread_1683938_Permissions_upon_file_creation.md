---
title: "Permissions upon file creation"
date: 2011-02-08
forum: Server Platforms
---

### Post by michellez on 2011-02-08
Hi all

Is ACL the best way to ensure the permissions of newly created files?

Basically I have a directory: /data/department

I've done chmod g+s on it so the group is correct on new files but I want new files to also have 775 permissions so the rest of the group can access these files fully. Currently they are created with the default 755 (which I want still every where out side of /data/department :)).

Thanks
Michelle

---

### Post by Morbius1 on 2011-02-08
Change the umask to 002 in /etc/profile so that all newly created files for every user will have permissions of 664 and not 644.

[COLOR=Blue]**EDIT**[/COLOR]: Didn't read the last line of your post. I'm getting sloppy, sorry

---

### Post by wormyblackburny on 2011-02-08
Change the ownership of the folder to your group:

chown root.yourgroup /data/department (makes root and your group the owner)

chmod 2775 /data/department

This assumes that anyone reading/writing is a member of that group. Additionally for security I would personally do chmod 2770 instead of 2775, that way anyone that is not a member of the group won't be able to read or write to the folder, but that's just me....

---

### Post by michellez on 2011-02-08
Morbius1: No worries. Thanks for trying though :)

wormyblackburny: Ah, is the 2 the bit that makes it stick on to new files/folders?

Cheers

---

### Post by vanadium on 2011-02-08
The "2" reflects the setgid bit. It assures that the group of newly created files is automatically set to "yourgroup" (in the example of wormyblackburny).

When I create a file, it will have, by default, vanadium:vanadium as user:group. If I am member of "yourgroup", I will be able to create a file in /data/department, because members of that group have write permissions there. In addition, the file I create there will automatically be assigned the group "yourgroup". User:group will be: vanadium:yourgroup.

If you want other members of that group to access all files fully by default, you will still need to change the umask, though. With the default umask, my new file would be vanadium:yourgroup rwxr-xr-x, so members of "yourgroup" will not be able to write to the file or delete it.

---

### Post by michellez on 2011-02-08
Yup. I've got the setting the group bit on new files but not the umask. How do I change the default on just this folder and it's contents, not the whole system default umask?

Thanks

---

### Post by wormyblackburny on 2011-02-08
Yes and no. The 2 is setting the groupid as the owner of the file (instead of the user that uploaded the file) and thus mirroring the permissions across the folder based on the permissions of the group in the folder. It's still kind of confusing to me too, but that is basically why you make the group the owner of the folder instead of a user. That means you can give group members access to RWX files but restrict non group members to say "read only". It does have its flaws though, because in this particular case if we are both members of the group I could potentially delete/modify your files that you uploaded since there is no user ownership of the files. It is the price you pay for having "collaborative" spaces :( 

I guess the easy way around that is suggesting that users keep "important" materials in their home directories or create a subfolder and use a 4 instead of a 2 to set it to user level permissions and restrict it using 4755 so that group and others do not have write permission...? This is a good man page to read on it, perhaps it will make more sense that way:
[http://www.manpagez.com/man/1/chmod/](http://www.manpagez.com/man/1/chmod/)

---

### Post by Morbius1 on 2011-02-08
The umask is universal I'm afraid and not restricted to that folder although if you think about it changing the umask to 002 from 022 isn't really that big of an issue since any new file created anywhere else by user morbius will save as:
owner:group = morbius:morbius
permissions = 664.

It's true that the group now has write permissions but the group is still only morbius. 

Anyway, another approach is to use bindfs: 
**HowTo: Create a shared directory for local users (with bindfs) : **[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by wormyblackburny on 2011-02-08
I'm not sure if you are right Vanadium. That is why we chown it to root.yourgroup so that the files are automatically set to be owned by root instead of the individual users. I'm going to test it out real quick and post the ls -la for the directory....gimme a few minutes

EDIT: Oops, the person who created the file still maintains ownership....

---

### Post by wormyblackburny on 2011-02-08
Looks like it worked for me... (this was done on RedHat5 but shouldnt make a difference)

[root@localhost ~]# su test
[test@localhost root]$ cd /operations/sales/
[test@localhost sales]$ echo "test" >> testfile.txt
[test@localhost sales]$ ls -la
total 24
drwxrwsr-x 2 root marketing 4096 Feb  8 13:19 .
drwxr-xr-x 3 root root      4096 Feb  8 13:15 ..
-rw-rw-r-- 1 test marketing   15 Feb  8 13:29 testfile.txt
[test@localhost sales]$ echo "test" >> testfile2.txt
[test@localhost sales]$ ls -la
total 32
drwxrwsr-x 2 root marketing 4096 Feb  8 13:29 .
drwxr-xr-x 3 root root      4096 Feb  8 13:15 ..
-rw-rw-r-- 1 test marketing    5 Feb  8 13:29 testfile2.txt
-rw-rw-r-- 1 test marketing   15 Feb  8 13:29 testfile.txt
[test@localhost sales]$ exit
exit
[root@localhost ~]# su test2
[test2@localhost root]$ cd /operations/sales/
[test2@localhost sales]$ vi testfile2.txt 
[test2@localhost sales]$ cat testfile2.txt 
test tested and saved
[test2@localhost sales]$ getfacl testfile2.txt 
# file: testfile2.txt
# owner: test
# group: marketing
user::rw-
group::rw-
other::r--

[test2@localhost sales]$ getfacl /operations/sales/
getfacl: Removing leading '/' from absolute path names
# file: operations/sales
# owner: root
# group: marketing
user::rwx
group::rwx
other::r-x

[test2@localhost sales]$

---

### Post by wormyblackburny on 2011-02-08
Guess i should have done a shell script to see if it carried over the executable bit.... I might try that later.

---

### Post by sisco311 on 2011-02-08
> **vanadium said:**
> The "2" reflects the setgid bit. It assures that the group of newly created files is automatically set to "yourgroup" (in the example of wormyblackburny).

When I create a file, it will have, by default, vanadium:vanadium as user:group. If I am member of "yourgroup", I will be able to create a file in /data/department, because members of that group have write permissions there. In addition, the file I create there will automatically be assigned the group "yourgroup". User:group will be: vanadium:yourgroup.

If you want other members of that group to access all files fully by default, you will still need to change the umask, though. With the default umask, my new file would be vanadium:yourgroup rwxr-xr-x, so members of "yourgroup" will not be able to write to the file or delete it.

Almost right. :) You don't need write permission on a file to delete it from a directory. You must have write permission on the directory and execute permission on the directory, the directory's parent, and all ancestor directories up to and including "/" (the root directory).

So, if the group *yourgroup* has write permission on the directory (and the sticky bit is not set), any user from *yourgroup* will be able to delete any file from the directory regardless of the ownership and permissions of the file.

See: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by vanadium on 2011-02-09
Indeed, i stand corrected.

This would then be where the sticky bit comes in: with the sticky bit set, only the owner of the file can delete the file.

> Yes and no. The 2 is setting the groupid as the owner of the file (instead of the user that uploaded the file)

The setgid bit sets the GROUP to the same group as the directory, not the user.
> but that is basically why you make the group the owner of the folder instead of a user.
A file/directory always has an owner and a group.
> 
That means you can give group members access to RWX files but restrict non group members to say "read only".
That is where user and group permissions come in. User permissions apply to the individual user, group permissions apply to any user that is member of the group.

The setgid bit allows you to automatically assign one specific group to a file in a specific directory. By default, the group would be the group of the user himself. With the setgid bit set, it will be the group of the directory.
> 
 It does have its flaws though, because in this particular case if we are both members of the group I could potentially delete/modify your files that you uploaded since there is no user ownership of the files. It is the price you pay for having "collaborative" spaces

No. this is where the sticky bit comes in. With the sticky bit set and the appropriate permissions set, any member of the group can create files and edit any file in the directory. However, only the creator of the file can remove the file.

> 
I guess the easy way around that is suggesting that users keep "important" materials in their home directories or create a subfolder and use a 4 instead of a 2 to set it to user level permissions and restrict it using 4755 so that group and others do not have write permission...?

I am not sure what the setuid does on a directory. Anyway "important" material can always be protected with more strict permissions.

In your scenario, you might need to
1) set umask 007 so that by default, user and group can do anything with a new file. "others" cannot even see the contents.
2) set the setgid bit on /data/department such that new files in that directory automatically do belong to "yourgroup". This way, any member of mygroup will be able to edit all files.
3) set the sticky bit on /data/department so that only the person who created a file, can delete it.

Further protection of more sensitive information is then to be set manually. Any user can restrict access to files he created by editing its permissions. Of course, you can instruct users to keep materials in their home directories as an alternative way to restrict access.

In other directories, owner and group are $USER:$USER by default. Thus, by default, no-one will be able to see files of another user.

As said before, the umask is a setting, although you can apply this on a per user basis. The default on Ubuntu is 0022, but you could have it automatically set to 0002 for users who need to collaborate in /data/department.

---

### Post by michellez on 2011-02-09
Cheers guys! :)

I have changed the umask in /etc/profiles and all is good. I see your point about how files else where created with the appropriate user group any way, so no issue.

---

### Post by wormyblackburny on 2011-02-09
Thanks for the clarification Van. I guess it all depends on how you want your environment set up.

---

### Post by vanadium on 2011-02-10
> **wormyblackburny said:**
> Thanks for the clarification Van. I guess it all depends on how you want your environment set up.
Ultimately, it is the administrator (for the whole storage) and the users (for their parts of the storage) who decide about the most convenient defaults for security. Security usually comes at the expense of convenience.

---

