---
title: "Understanding Unix style permissions"
date: 2010-07-20
forum: Security
---

### Post by NMFTM on 2010-07-20
I'm having a little bit of trouble understanding Unix style filesystem permissions and would like a better explanation.

On Windows, you can go to a file's permissions and it's clearly stated who can do what. You can choose between individual users or groups such as 'everyone' or certain types of users such as 'domain users'. You could create a clear cut list of every single user/group on the system and what their permissions for a file are and have it neatly displayed in a list.

On Unix, we have octal permissions and sticky bits. I understand the whole concept of rwxrwxrwx (777). The first three are what the file owner can do, the second is what the main group the user belongs to can do, and the third is what other users can do.

But, when you view a file's permissions you are only getting the permissions as they apply to the user that owns the file. For example, as I understand it, if I viewed a file that only the root user had rwx permissions on and everyone else could only read. The permissions would show up as rwxr--r-- (744). But, those same permissions would show up to any user as 744 as well. Since the last 3 characters are what applies to "other users" (pretty vague). How would someone know what users in particular those permissions apply to? There could be one "other user" that can rwx that file and another "other user" that can't.

Also, why just stop with the main group? What about other groups? A the user Foo's main group he belongs to might be Foo. But he could also belong to the groups Boo and Zoo, which belong to other users and would give him full rwx permissions over Boo and Zoo's files just as if he were Boo or Zoo.

Then you have the whole sticky bit thing that makes it so that files can be owned by the same person and at the same time be made use of (to varying degrees) by other users. To chmod the UID you'd chmod 2777 or for GID 4777 (just an an example). I did this for a file and it allowed a standard user account who was previously unable to run the command to be able to run it. But, how can that work when I didn't anywhere specify what particular user (or groups of users) that sticky bit applies to?

I'm confused about this whole thing to the point that I'm not even sure exactly what questions I should be asking or even if my examples are even 100% correct. I just sort of ranted about some specific things that floated to the top of my head. Permissions are easy to understand when your running a Unix-like system  on a single user desktop. Because the only users/groups you have are  root, the single user, and various system users/groups that you don't  really need to worry about. So a file with rwxr--r-- means that only the  Root user (not even members of his group) can edit the file and you  can't unless you use sudo. Because the "other user" in the last 3  characters always just means you. But, things seem to get a whole lot  more complicated when you start adding in multiple users. Can someone explain this or link to a "for dummies" article that can explain all of this to me in a way that someone who's used to Windows style permissions can make a connection between the two OS families and their way of handling these things?

---

### Post by NMFTM on 2010-07-20
Post edited due to thread merger.[]("http://ubuntuforums.org/showthread.php?t=1535295")

---

### Post by lykwydchykyn on 2010-07-20
"Windows Style Permissions" are known as ACLs (Access Control Lists), and you can enable ACL permission in Linux if you wish to. Instructions for doing so are here:

[https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)

As for Unix permissions, the basic stuff is pretty simple:
Every file has an owner (uid) and a group (gid)
The owner permission affect what the owner can do
The group permissions affect what users in the file's gid group can do (nothing to do with the owner's groups, other than that the default gid for new files is the owner's primary gid).
The "everyone else" is not vague at all.  It literally means "everyone else" -- any other user on the system.  There is not an account on the system that is not part of this group.

The sticky bit stuff is a little weird and inconsistent, but it's rarely used or needed.

Anyway, that link above is probably a good place to start.

---

### Post by lykwydchykyn on 2010-07-20
I guess I should forewarn you that Linux uses POSIX ACLs, which are in many ways subtly different from Windows ACLs.  If you aren't careful you can really tie yourself in knots with POSIX ACLs, they aren't really a cure-all for Windows->Linux transitioning.

In general it's a lot safer to try to model your permissions using only Unix-style permissions if you can -- and in most cases you can, believe it or not.

Can you give an example of a scenario that you wouldn't know how to handle with only Unix permissions?

---

### Post by NMFTM on 2010-07-20
Post edited due to thread merger.

---

### Post by NMFTM on 2010-07-20
> **lykwydchykyn said:**
> Every file has an owner (uid) and a group (gid)...
The group permissions affect what users in the file's gid group can do (nothing to do with the owner's groups, other than that the default gid for new files is the owner's primary gid).
Aha, so the fact that all of the files in my /home directory are apart of the my group and all of the other files are a member of Root's group doesn't mean that I can't change what group is the primary group and give that group it's own permissions. I get that, but I have another problem with this (see bottom of post).
> **lykwydchykyn said:**
> The "everyone else" is not vague at all.  It  literally means "everyone else" -- any other user on the system.  There  is not an account on the system that is not part of this group.
 Oh, I thought that it was more complicated than that.
> **lykwydchykyn said:**
> Can you give an example of a scenario that  you wouldn't know how to handle with only Unix permissions?
I think I might have one. Like you said above, since "everyone else" is literally everyone else on  the system. What would happen if there was a file that I wanted  different users to have different permissions on? Then the rwx values  wouldn't really be for everyone else, since the other users would have  different permissions in relation to it.

For example, since all files belong to a group, which in turn has it's own rwx permissions. What would happen if I had a company with three groups of employees. Office workers, engineers, and the managers. All three groups would have their own folders that they'd have at the very least have 660 access to (since you might not want employees being able to execute files).

But, what if I wanted to make a folder that was accessible to all three groups of people but with different permissions. Say, a folder that held company press statements. I'd want the manager's files have 770 access. While office worker's files had 660 so that they could edit the press statements for spelling mistakes and engineer's files only had 440, since they're busy designing the company's products and don't need to be modifying press statements for any reason.

The files would have an owner (manager users - 7 / rwx) a group (manager group - 7 rwx) and than all other users, which is conflicted between office workers who can read and edit but not execute and engineers who can only read. Although, in reality I don't know why managers would need to execute files in a press release folder. But we'll just pretend they would need permission to do so for some reason, just for the sake of argument. In this case, how could you set permissions without using an ACL?

---

### Post by rookcifer on 2010-07-20
> **NMFTM said:**
> 
But, when you view a file's permissions you are only getting the permissions as they apply to the user that owns the file. 

I'm not quite sure what you mean by this.  if I run ls -al on a directory and look at permissions on all the files within it, they will be the same permissions whether I am doing this as root or a user.  That is, if Alice owns a file, she always owns the file unless she or root changes ownership.

> For example, as I understand it, if I viewed a file that only the root user had rwx permissions on and everyone else could only read. The permissions would show up as rwxr--r-- (744). But, those same permissions would show up to any user as 744 as well. 

Not following you here.  What you described (a file with 744 permissions) will hold no matter who on the system is checking permissions.  If root owns that file, then everyone else will fall under "Group" or "Other" and since the group and other permissions are read only, this means *everyone* except root can only read the file.

> Since the last 3 characters are what applies to "other users" (pretty vague). How would someone know what users in particular those permissions apply to? 

By looking at who the owner of the file is and who is in the group (if anyone).  The "other" users would be people who are either not the owner or not in the group.  Literally, it means *everyone* else.

> There could be one "other user" that can rwx that file and another "other user" that can't.

No, an "other" user is always an "other" user.  I am not sure where you are getting this view that permissions are somehow relative to the observer (general relativity perhaps?) ;)  

> Also, why just stop with the main group? What about other groups? A the user Foo's main group he belongs to might be Foo. But he could also belong to the groups Boo and Zoo, which belong to other users and would give him full rwx permissions over Boo and Zoo's files just as if he were Boo or Zoo.

You can check who the group owner of a file is by "ls -l".  The group will be the second listing.  For instance:

-rwxr-xr--  1 rookcifer **rookcifer**    14194 2010-07-09 01:17 test_file

The name in bold is the name of the owning group.  This means that the group in this case can read and execute and the "others" can only read. You can check who is in what group by looking in /etc/group.  

> Then you have the whole sticky bit thing that makes it so that files can be owned by the same person and at the same time be made use of (to varying degrees) by other users. To chmod the UID you'd chmod 2777 or for GID 4777 (just an an example). I did this for a file and it allowed a standard user account who was previously unable to run the command to be able to run it. But, how can that work when I didn't anywhere specify what particular user (or groups of users) that sticky bit applies to?

You seem to be confused what the sticky bit does.  From Wikipedia:

> The most common use of the sticky bit today is on directories. When the sticky bit is set, only the item's owner, the directory's owner, or the superuser can rename or delete files. Without the sticky bit set, any user with write and execute permissions for the directory can rename or delete contained files, regardless of owner. Typically this is set on the /tmp directory to prevent ordinary users from deleting or moving other users' files. This feature was introduced in 4.3BSD in 1986 and today it is found in most modern Unix systems.

Without the sticky bit being set, anyone with r-x permissions can delete or create files.  If the sticky bit is set, only the owner of the file (and root of course) can delete the files, *even if other users have r-x permissions.*  So basically the sticky bit is a way to allow people to write to a directory without deleting files.  

> So a file with rwxr--r-- means that only the  Root user (not even members of his group) can edit the file and you  can't unless you use sudo. 

You are confusing permissions with *ownership.*  If a file has the permissions of rwxr--r--, this says **nothing** about who owns it!  Bob could own the file, and if that's the case, Bob will have rwx permissions to the file.  (Don't get side-tracked with root, he is all powerful and permissions do not apply to him).  Remember, the permissions system on Unix is like so:

User -- Group -- Other

The User can be ANY user on the system (not just root).  

I think you are just looking at the rwxrwxrwx bit of the permissions and are ignoring who the owner and group might be.  The file's permissions say **nothing **about who the owner and group is.  All it does it outline the permissions for each category: User, Group, Other.  You must first know who these people are in order to know what the permissions mean.

---

### Post by lykwydchykyn on 2010-07-21
> **NMFTM said:**
> 
Although, in reality I don't know why managers would need to execute files in a press release folder. But we'll just pretend they would need permission to do so for some reason, just for the sake of argument. In this case, how could you set permissions without using an ACL?

I'm not feeling terribly imaginative this morning, so I'll go ahead and say you're right.  This will require ACLs.

---

### Post by bodhi.zazen on 2010-07-21
With standard Linux permissions you have 3 groups

Owner of the file / directory
The group membership of the file / directory
Other - everyone else

If you need finer grain control , they you need to use ACL.

See: [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

This week DistroWatch did a write up on ACL

[http://distrowatch.com/weekly.php?issue=20100719](http://distrowatch.com/weekly.php?issue=20100719)

There is a graphical front end for ACL , 

[http://rofi.roger-ferrer.org/eiciel/?s=1](http://rofi.roger-ferrer.org/eiciel/?s=1)

but it is not as feature rich as the command line.

There are some minor variations in the file systems in terms of enabling acl , with ext2/3/4 you need to add a line in fstab and remount the file system. jfs acl is enabled by default. I am not sure about xfs or btrfs

---

### Post by NMFTM on 2010-07-21
Thanks for the responses everyone.

Why don't Unix-like systems include ACL's by default and why hasn't any major distro taken the lead in shaping the future of Linux by including them? Is it because since the Linux market is so fragmented nobody wants to include something that would possibly cause major incompatibilities with other systems and trigger a huge division within the open source community?

---

### Post by movieman on 2010-07-21
> **NMFTM said:**
> Why don't Unix-like systems include ACL's by default and why hasn't any major distro taken the lead in shaping the future of Linux by including them?

I've been using Unix systems since 1985: never once in that time have I needed ACLs.

Given that almost no-one uses them they're kind of pointless to set up by default.

---

### Post by The Cog on 2010-07-22
They are included in all distros. They are just not enabled by default on most systems. For the reason that most people don't feel they need them.

---

### Post by NMFTM on 2010-07-22
> **movieman said:**
> I've been using Unix systems since 1985: never once in that time have I needed ACLs.
 
Given that almost no-one uses them they're kind of pointless to set up by default.
I can understand why home users probably wouldn't need them. But if you were running any kind of company I would think that you'd have enough groups of users with various different needs that you'd pretty much need to use ACL's.

---

### Post by movieman on 2010-07-22
> **NMFTM said:**
> I can understand why home users probably wouldn't need them. But if you were running any kind of company I would think that you'd have enough groups of users with various different needs that you'd pretty much need to use ACL's.

Uh, I've spent much of that time using Unix at work, and running Unix servers around the world (there weren't many people running Unix at home in 1985). We've never had a need for anything beyond standard Unix file permissions.

ACLs are far too complex and easy to screw up to make them the default for users who don't need them... which is pretty much everyone.

---

### Post by lykwydchykyn on 2010-07-22
I don't think it's nearly as crucial as it initially seems.  I can't speak for most places, but where I work we don't have people remoting into *nix boxes running terminal sessions.  When we have a Linux file server, people aren't dealing with local filesystem permissions to enforce security; that aspect is usually handled through the file sharing layer like samba or nfs, or through a CMS.

---

