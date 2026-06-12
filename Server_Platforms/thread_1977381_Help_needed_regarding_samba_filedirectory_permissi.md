---
title: "Help needed regarding samba file/directory permissions"
date: 2012-05-10
forum: Server Platforms
---

### Post by loongyh on 2012-05-10
Hi I have set up a samba file share on Ubuntu Server 11.10 x64, and have assigned various users with group 'users' access to it. I have set the default file/directory creation masks to 770, and have verified the permissions of created files/directories (i.e. in Windows: New > Text Document in the context menu) to be 770 in the share.

However, when users perform a file copy, i.e. drag and drop, the files/directories inherited a 755 permission. This resulted in User A not being able to write to files created by User B under the same group 'users'. I have tried other smb.conf parameters like "force (directory) security mode = 770" and "force create mode = 0770" to no effect.

As I understand, this could be due to source file/directory permissions being transferred over too during a "drag-and-drop" copy. However, aren't the 'force' parameters supposed to mask those permissions? For now I can only think of implementing a cron job to manually chmod -R 770 the share directory as a workaround. But does anyone know of a proper solution to this? Any advice will be greatly appreciated :)

---

### Post by wiggy1977 on 2012-05-10
I get a similar problem, we scan files to a shared folder with a mask 0775 but the scanned files end up with 0755 permissions, if we have to over scan a file I have to manually either delete file or change permission.

---

### Post by bab1 on 2012-05-10
> **wiggy1977 said:**
> I get a similar problem, we scan files to a shared folder with a mask 0775 but the scanned files end up with 0755 permissions, if we have to over scan a file I have to manually either delete file or change permission.

Your problem could be cured by setting the system umask to 002.  I think you will find that it is 022 right now.  This changes the **default file creation** from 644 to 664 and directories from 755 to 775.  You can change this in /etc/profile.

@loongyh -  This *may* work for you, but I can't be sure.  If a file is already created then I believe the permissions will stay as they are.  I have a situation where I am copying file that have 600 permissions.  I have found nothing short of creating a script that will provide a change of permissions on already existing files and directories.

In all conditions the *Linux file system trumps any Samba settings*.  The answers are not going to be fiddling with Samba settings unless the underlying file system also allows it.

---

### Post by SeijiSensei on 2012-05-10
When user joe creates a file through samba, what group does that file have?  By default Ubuntu creates a group for each user with the same name as that person's username.  What you probably want is for files created by joe to be assigned groups "users" rather than "joe".  

I don't think changing the umask by itself will resolve this problem since even if joe has umask 002, the group read/write privileges will apply to group joe.  One possible solution is to enable "force group = users" in Samba.  That may be sufficient, along with the change in umask, to give everyone in the users group read/write permissions to all the files.  The other, more painful, process is to make the users group be each user's primary group rather than unique group now assigned.  That means changing all the entries in /etc/passwd so the primary group value equals the group id of group users.  In /etc/passwd, you'll see entries like this:

```
joe:x:1000:1000:Joe,,,:/home/joe:/bin/bash
```

The second numerical entry is the group id.  You can put all the users in group users by setting that value to the group ID found in /etc/group.  You'd have to make sure you assign any new users to the users group when they are created as well.

If it really doesn't matter to you to keep track of which users own which files, then you can add the "force user" and "force group" parameters to smb.conf.  Then all the files written to the share will have the same user and group IDs.

---

### Post by bab1 on 2012-05-10
> **SeijiSensei said:**
> When user joe creates a file through samba, what group does that file have?  By default Ubuntu creates a group for each user with the same name as that person's username.  What you probably want is for files created by joe to be assigned groups "users" rather than "joe".  

I don't think changing the umask by itself will resolve this problem since even if joe has umask 002, the group read/write privileges will apply to group joe.  One possible solution is to enable "force group = users" in Samba.  That may be sufficient, along with the change in umask, to give everyone in the users group read/write permissions to all the files.  The other, more painful, process is to make the users group be each user's primary group rather than unique group now assigned.  That means changing all the entries in /etc/passwd so the primary group value equals the group id of group users.  In /etc/passwd, you'll see entries like this:

```
joe:x:1000:1000:Joe,,,:/home/joe:/bin/bash
```

The second numerical entry is the group id.  You can put all the users in group users by setting that value to the group ID found in /etc/group.  You'd have to make sure you assign any new users to the users group when they are created as well.

If it really doesn't matter to you to keep track of which users own which files, then you can add the "force user" and "force group" parameters to smb.conf.  Then all the files written to the share will have the same user and group IDs.

As I said Linux file ownership and permissions trump Samba.  I would change the group on the root directory of the share and sgid to the group I wanted on that share 9I use smbusers).  Anything created in that directory or below will have that group ID.

But, permissions are not ownership.  The original question asked by @ wiggy1977 was about permissions.

---

### Post by loongyh on 2012-05-17
Thank you all for your reply. Sorry to have not clarified initially, but the issue does not lie with ownership, but with permissions. All the samba users are sync-ed with their respective unix user, and all unix users are created under the unix group 'users', thus all files transferred to the share regardless of user inherits the 'users' group.

The issue: Any pre-existing files on another computer that are copied over to the share through samba does not have write permissions under group. i.e. the permissions appear as rwxr--r--. The goal is to ensure every file that exist in the share has the permissions rwxrwx---. Although further reading convinced me that all files under the share should have rw-rw---- instead, as they should not be allowed to be executed in the server.

[Another thread]("http://ubuntuforums.org/showthread.php?t=1980548") created just yesterday appears similar, if not, identical to the issue this thread brings up. I have been reading up on umask, and it appears that 12.04 has the default umask set to 002.

I have obtained and installed 12.04 x64 Server on a virtual machine and somewhat recreated the issue. The copied files appear in 12.04 as 760, while the directories as 750. As before, new file and directories created appear as 770 as set in the smb.conf create masks.

It appears this is not a samba issue but a filesystem one. Is there a method to force permissions for all files/subdirectories in a directory? The default umask 002 in 12.04 apparently partially fixed this issue, as pre-existing files transferred now inherits 760 instead of 755. However, pre-existing directories transferred still appears as 750.

---

### Post by Morbius1 on 2012-05-17
I have a tendency towards the simplest solutions so I have a question: Do you have a need to preserve the ownership of the transferred file?

If you have a share set up this way:
> [share]
path = /path-to-directory
read only = no
guest ok = noYou can add a parameter to force all remote user's to look like the same user. For example, if this is a true server then you can change it to this:
> [QUOTE][share]
path = /path-to-directory
read only = no
[COLOR=Blue]force user = nobody[/COLOR]
guest ok = no[/QUOTE]After the samba client passes accreditation his user name will be converted to "nobody" which is a default user account on your system. Since it will apply to all remote users then everyone will be able to write to everything new that is saved since all new files will have owner = nobody. 

It doesn't have to be "nobody" of course. It can be any Linux user that matches your requirement and has linux access to the shared folder.

[COLOR=Blue]**EDIT**[/COLOR]: Another alternative is bindfs which will absolutely force all new and old files to have specific permissions which will become immutable but that is available only on 12.04 or prior to 11.10.

---

### Post by doogy2004 on 2012-05-17
In your smb.conf, under the specific share you need to set the "create mask" and "directory mask".  These parameters tell Samba what to set the permissions to on new files and directories.

[https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Create mask: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK)

Directory mask: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK)

---

### Post by bab1 on 2012-05-17
> **loongyh said:**
> Thank you all for your reply. Sorry to have not clarified initially, but the issue does not lie with ownership, but with permissions. All the samba users are sync-ed with their respective unix user, and all unix users are created under the unix group 'users', thus all files transferred to the share regardless of user inherits the 'users' group.

The issue: Any pre-existing files on another computer that are copied over to the share through samba does not have write permissions under group. i.e. the permissions appear as rwxr--r--. The goal is to ensure every file that exist in the share has the permissions rwxrwx---. Although further reading convinced me that all files under the share should have rw-rw---- instead, as they should not be allowed to be executed in the server.

[Another thread]("http://ubuntuforums.org/showthread.php?t=1980548") created just yesterday appears similar, if not, identical to the issue this thread brings up. I have been reading up on umask, and it appears that 12.04 has the default umask set to 002.

I have obtained and installed 12.04 x64 Server on a virtual machine and somewhat recreated the issue. The copied files appear in 12.04 as 760, while the directories as 750. As before, new file and directories created appear as 770 as set in the smb.conf create masks.

It appears this is not a samba issue but a filesystem one. Is there a method to force permissions for all files/subdirectories in a directory? The default umask 002 in 12.04 apparently partially fixed this issue, as pre-existing files transferred now inherits 760 instead of 755. However, pre-existing directories transferred still appears as 750.

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1980548") for the correct, complete and successful method for achieving this.

---

### Post by Morbius1 on 2012-05-17
Did you actually read the post you quoted? Here let me parse it for you:
> Originally Posted by **loongyh**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11943458#post11943458")                 
                 Thank you all for your reply. Sorry  to have not clarified initially, but the issue does not lie with  ownership, but with permissions. All the samba users are sync-ed with  their respective unix user, and all unix users are created under the  unix group 'users', [COLOR=Blue]thus all files transferred to the share regardless  of user inherits the 'users' group.[/COLOR]2 posts come closest to answering the question: doogy2004's and mine ( I have an SOB ego too you know :wink: ). Although mine is an attempt to circumvent the problem whereas doogy2004's address the problem directly. 

The only problem with using samba ( create mask and such ) to do this sort of thing is the the amount of bit-wise AND'ing and OR'ing going on. You will eventually get it right but not before going insane.

Which is why I suggested bindfs if he is using 12.04. If I bindfs a folder to itself like this:
```
sudo bindfs -o group=users,perms=0660:ug+D "/home/morbius/Test" "/home/morbius/Test"
```Then all existing files will have group=users and permissions of 660. Folders will have 770. Any new file/folder added by any source be it Samba or not will also save with those permissions and group.  It's immutable and independant of the systems umask, original permissions, samba masks, or pretty much anything else you can throw at it.

[COLOR=Blue]*Note: If any of you are playing the home version of this game, to unmount that bindfs mount:*[/COLOR]
```
sudo umount "/home/morbius/Test"
```You will have to set up a upstart job to have this done at boot but it's not that hard and I'd be tickled pink to assist.

---

### Post by loongyh on 2012-05-17
> **doogy2004 said:**
> In your smb.conf, under the specific share you need to set the "create mask" and "directory mask".  These parameters tell Samba what to set the permissions to on new files and directories.

[https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

Create mask: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK)

Directory mask: [https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK](https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK)

Oh that's one of the first things I configured on my smb.conf. I've set both parameters to 770.


> **bab1 said:**
> See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1980548") for the correct, complete and successful method for achieving this.

I quoted that thread in my previous post, thank you for the reaffirmation ;)
It's just that the create masks as mentioned by doogy2004 worked for the thread starter, somehow.. Perhaps during testing he created new files in the share instead of copying existing files to it? If so, he'd be in for a nasty surprise (as I'm experiencing now).


> **Morbius1 said:**
> I have a tendency towards the simplest solutions so I have a question: Do you have a need to preserve the ownership of the transferred file?

If you have a share set up this way:
You can add a parameter to force all remote user's to look like the same user. For example, if this is a true server then you can change it to this:
After the samba client passes accreditation his user name will be converted to "nobody" which is a default user account on your system. Since it will apply to all remote users then everyone will be able to write to everything new that is saved since all new files will have owner = nobody. 

It doesn't have to be "nobody" of course. It can be any Linux user that matches your requirement and has linux access to the shared folder.

[COLOR=Blue]**EDIT**[/COLOR]: Another alternative is bindfs which will absolutely force all new and old files to have specific permissions which will become immutable but that is available only on 12.04 or prior to 11.10.

This is an excellent workaround! However, sadly as it is a production server, with multiple users, I do require file ownership to keep track of accountability. So close.. ](*,)



> **Morbius1 said:**
> Did you actually read the post you quoted? 

Yes I did, it's just that as said, the guy apparently solved his issue by setting the create and directory masks. Which only works for new files and directories created in the share, existing files transferred to the share retain their permissions (I think, as I observed files copied from different locations end up with different permissions in the share).

---

### Post by bab1 on 2012-05-17
Did you set the default umask to 0002?

---

### Post by Morbius1 on 2012-05-17
Sorry, the "Did you actually read the post you quoted?" referenced the previous post to mine not yours.

---

### Post by bab1 on 2012-05-17
> **loongyh said:**
> ...existing files transferred to the share retain their permissions (I think, as I observed files copied from different locations end up with different permissions in the share).
This is not what happens.  The file that is network transferred does not include ownership or permissions.  The receiving host creates a new inode for that information.  It is based on the sum all the settings you have created on the receiving host(i.e. system umask, samba settings and scripted umasks).

---

### Post by loongyh on 2012-05-17
> **bab1 said:**
> Did you set the default umask to 0002?

Yes, 12.04 comes with the default umask of 0002 in fact.. I verified it with ls -l, it is 0002.


> **bab1 said:**
> This is not what happens.  The file that is network transferred does not include ownership or permissions.  The receiving host creates a new inode for that information.  It is based on the sum all the settings you have created on the receiving host(i.e. system umask, samba settings and scripted umasks).

But when new files/directory are created directly in the share their permissions are 770 as set in the samba create/directory masks. When I copy files over however, the permissions vary, but never 770. For example, I get a 750 permissions when copying files that reside in C:\ but 760 permission when copying files residing in C:\Users\User\Desktop.

---

### Post by bab1 on 2012-05-17
> **loongyh said:**
> Yes, 12.04 comes with the default umask of 0002 in fact.. I verified it with ls -l, it is 0002.
The best way to verify the umask is with this command```
umask
```> 

But when new files/directory are created directly in the share their permissions are 770 as set in the samba create/directory masks. When I copy files over however, the permissions vary, but never 770. For example, I get a 750 permissions when copying files that reside in C:\ but 760 permission when copying files residing in C:\Users\User\Desktop.
This is not because the file comes with existing permissions or ownership.  In fact NTFS or FAT has no notion of user, group or other permissions or file ownership in EXT.  At this point I can't tell you what is happening with your system (too many variables), but I can tell you that I have verified that the inode data is NOT transferred.  You can check the inode data like this```
stat some_file_name
```
When you login to a samba share you become the owner of any files transferred (unless you suid on the dir).  The permission is set by umask... well you know the rest.  We have been over that part.

Edit: Why do you have 770 set as a file permission?  The umask setting (0002) for files comes out to 0664 should be sufficient.  Or 0660 would be fine.  Again, why 770 for files?

---

### Post by loongyh on 2012-05-17
> **bab1 said:**
> The best way to verify the umask is with this command```
umask
```

Yes, sorry what was I typing, ls -l is for viewing file/directory permissions. umask was the command I meant.


> **bab1 said:**
> Edit: Why do you have 770 set as a file permission?  The umask setting (0002) for files comes out to 0664 should be sufficient.  Or 0660 would be fine.  Again, why 770 for files?

My mistake on that part too, I have recently realized 660 to be more appropriate for files. I'll chmod the files when I finally find a way to force permissions for copied files.

I'm relatively new to Linux in general and still have more to learn, thus please do correct me if at any point I appear to not know what I'm doing, thanks :biggrin:

---

### Post by Morbius1 on 2012-05-17
[1] Create a test folder
```
sudo mkdir /mnt/test
```[2] Install bindfs
```
sudo apt-get install bindfs
```[3] Create a samba share of /mnt/test in a duplicate manner to how you created your other share but with the path of /mnt/test.

[4] Bindfs /mnt/test
```
sudo bindfs -o group=users,perms=0660:ug+D /mnt/test /mnt/test
```Add a file to the folder from within the server itself. Then add a file from any samba client you desire. .

Do all these files not have:
owner = some-user-name
group = users
perms = 660

Do the same thing by adding a new subfolder. Do they all not have:
owner = some-user-name
group = users
perms = 770

[COLOR=Blue]*Note: "some-user-name" will not be the same but be dependent on whoever added the file.*[/COLOR]

---

### Post by bab1 on 2012-05-17
> **loongyh said:**
> Yes, sorry what was I typing, ls -l is for viewing file/directory permissions. umask was the command I meant.




My mistake on that part too, I have recently realized 660 to be more appropriate for files. I'll chmod the files when I finally find a way to force permissions for copied files.

I'm relatively new to Linux in general and still have more to learn, thus please do correct me if at any point I appear to not know what I'm doing, thanks :biggrin:
I ask because I don't always know what you want to achieve in the end.  I'm not a big believer in just giving you something to *cut 'n paste* without you understanding the ramifications.

Learning as you go along is sometimes as important than the destination.  ;-)

Ask if don't have what you have you need.

---

### Post by loongyh on 2012-05-17
Thank you all for your replies! I finally got the group permissions right. The culprit was indeed umask afterall. After some intensive googling I've learnt that 12.04 has the config file with the "global umask" parameter for non-interactive services in "/etc/pam.d/common-session-noninteractive". [All it needed was to append 'umask=007' after the "session optional pam_umask.so" line]("http://muzso.hu/2008/01/22/default-permissions-with-libpam-umask") and the files inherits rwxrwx-w- while the directories drwxrwx-w-. I have no idea how did the extra 'w' end up in the others field, but who cares we can always use the create and directory masks in smb.conf to clean that up.

Thus after applying "create mask = 660" and "directory mask = 770", the final permissions are finally rw-rw---- for files and drwxrwx--- for directories.

Once again, thank you all for your input! :mrgreen:

Edit: bab1 - you are spot-on on the fact that there's no difference between creating a file and copying a file over to a samba share. I've tried creating New>Folder and dragging-and-dropping existing folders from my Windows PC to the 12.04 Server smbshare. No difference in permissions. Special thanks for clearing up the misunderstanding.

---

### Post by Morbius1 on 2012-05-17
If I'm reading that link correctly though the "umask=007" is global so although it works in this particular case for this particular share it might have an impact somewhere else. Does it not work if you set it to a more conventional 002?

EDIT: The parent directory is probably sitting at 770 anyway so if the files within it are sitting at 664 it doesn't really mater since "others" cannot get past the parent directory.

---

### Post by loongyh on 2012-05-17
Do you mean it's possible for someone to go above the samba share directory? i.e. if the samba share 'test' has its directory under '/mnt/test', has a 777 permission, and the samba user can somehow navigate his way to '/mnt' and possibly '/'?

---

### Post by Morbius1 on 2012-05-18
> **loongyh said:**
> Do you mean it's possible for someone to go above the samba share directory? i.e. if the samba share 'test' has its directory under '/mnt/test', has a 777 permission, and the samba user can somehow navigate his way to '/mnt' and possibly '/'?
No, that's not what I meant. 

Based on how you seem to have set things up ( actually we have no idea how you set this share up but ... ) it sounded like "test" was set to 770. That was just an assumption on my part.

If /mnt/test is at 770 and the group was set to "users" and a given file within it is at 664 then the only people who can gain access to that file is the owner of /mnt/test, a member of the "users" group, and root. A given file cannot be accessed in isolation it can only be accessed though it's path. Put up a roadblock anywhere along the path to a given user or group and you have effectively blocked him from gaining access.

It never occurred to me that you set /mnt/test to 777 but that would explain why you were so obsessed with making the files within it 660. But even if you did set it to 777 and allowed the files to save as 664 Samba is still the gatekeeper. If you set up the samba share to allow only members of the users group ( i.e., valid users = @users ) then samba will block everyone except those in the "users" group.

---

### Post by Morbius1 on 2012-05-18
I do have a totally unrelated and perhaps off topic question for you. 

You said in this post that you are new to linux but you also stated that this is a production server. I'm curious as to why you decided to alter a system file especially one in a group that deals with security and authentication.

Don't get me wrong. As an ordained minister in the Church of Whatever Works for You, if this resolved your problem it's fine with me. It just seems inconsistent with where you are at this point in time. In contrast you could have implemented bindfs which would have isolated the experiment to only one directory and then decided that it either worked or what I was suggesting was just a bunch of hooey.

---

### Post by loongyh on 2012-05-18
@Morbius1 Oh I was actually doing all the testing on a virtual Ubuntu server 12.04 I've set up on my laptop. The production server is now still untouched and still running on 11.10. Plan to upgrade it to 12.04 tomorrow and apply the fix, but am seriously considering directory based umask with bindfs or ACL (what's the difference?).

As for your 2nd post, I'm more of a direct-approach kinda guy and prefer to tackle the problem head-on, directly working on the component that is giving trouble, instead of working around the problem installing additional programs like bindfs which in my opinion adds extra complexity to the already overly magnificiently complex OS that is linux and also to satisfy my unverified assumption that there will be performance degradation with these extra layers.

But of course I'm aware that my solution is very extreme as it has a system-wide impact and undeniably may incur collateral repercussions. However if there is a way to set the default umask on a per-user basis so that it can be limited to just the samba users I'd be very interested in knowing ;)

---

### Post by Morbius1 on 2012-05-18
> **loongyh said:**
> Plan to upgrade it to 12.04 tomorrow and apply the fix, but am seriously considering directory based umask with bindfs or ACL (what's the difference?).
You know ACL is another classic way of doing this sort of thing. I tried it once but unfortuantely it was at the very beginning of my Linux jouney and I just couldn't quite get my head around it. I never returned to it.

As for bindfs and the complexity comment, if you think about it it's doing exactly the same thing as what happens when Linux mounts an NTFS partition only at a directory level. When Linux mounts an NTFS partition you can specify ownership and permissions that permeate throughout the entire partition and it creates a "view" of that partition with permissions that Linux interprets as being Linux native permissions. The real NTFS partition has no Linux permissions.

Besides bindfs was a gift from Google so it has to be good :smile:

Plus this part of the bindfs statement:
> group=users,perms=0660:ug+DIs really no different from the classic way of doing things:
** I'm setting the group to users
** Since it will permeate throughout the folder all files will "inherit" the group.
** And I'm effectively setting the umask by forcing all new files ( but also all old files ) to a defined set of permissions.

It just has a terribly unintuitive syntax.

---

### Post by loongyh on 2012-05-18
Can 'bindfs' replace 'mount' in mounting a device?

i.e.
```
sudo bindfs -o group=users,perms=0660:ug+D "/dev/md0" "/media/<md0's UUID>"

```

Assuming that it works, will the mount survive reboots?

---

### Post by Morbius1 on 2012-05-18
> Can 'bindfs' replace 'mount' in mounting a device?No. bindfs can only remount a partition or part of a partition that's already mounted. So you would have to do something like this only after /dev/md0 is mounted to /media/<md0's UUID>:
```
 sudo bindfs -o group=users,perms=0660:ug+D "/media/<md0's UUID>" "/media/<md0's UUID>"
```> Assuming that it works, will the mount survive reboots?     A "sudo bindfs" does not survive a reboot. There's three ways to have this done a boot. 

(1) In fstab
The syntax changes but I do not recommend this method. There's a race condition that occurs most of the time in my experience where the bindfs instruction is executed before the device itself is mounted and the whole thing falls apart.

(2) Add it to rc.local 
Add the line just as it is but without the sudo right above the "exit 0" line. There's a better chance it works with this method.

(3) Upstart job.

* Create an upstart job file:
```
gksu gedit /etc/init/bindfs-remounts.conf
```* With this content:
```
# List of bindfs remounts
description "Bindfs Remounts"

start on stopped mountall

script
  bindfs -o group=users,perms=0660:ug+D /mnt/Test /mnt/Test
end script
```You can test to see if it works before an actual reboot by running:
```
sudo initctl start bindfs-remounts
```This is the method I use now because of the line "start on stopped mountall". mountall is the service that mounts everyting in fstab. That line states do not run this upstart job until mountall is finished running. It's the best way I have found to insure it remount successfully.

[COLOR=Blue]*EDIT: It's very late here. I hope I haven't made a typo anywhere in this.*[/COLOR]

---

### Post by phillw on 2012-05-18
to add a networked device to fstab that you need things to settle down for, replace **defaults** with **_netdev** (yes the leading **_** is required). This ensures that the network is up and stable before mountall goes and tries to mount the device. I've never used it with networked SMB drives, (which must also be declared as filetype cifs), but it is required for iSCSI drives else everything will go horribly wrong!

Regards,

Phill.

---

### Post by Morbius1 on 2012-05-19
@phillw, The OP is not talking about mounting a networked device.

This is a very confusing thread because it's talking about many different subjects almost simultaneously. The OP is talking about mounting, or in the latest development [COLOR=Blue]re-mouning[/COLOR], a local partition or part of a local partition not accessing a remote share.

---

### Post by loongyh on 2012-05-22
@Morbius1 I have followed your advice and used bindfs on the production server. Made it persistent by the upstart job method as suggested. It worked like magic and the permissions are forced 660, tested it working by manually sudo chmodding the files in there - no change. Special thanks!! :mrgreen:

Also lastly, thanks to all who have responded too. I have learnt a great deal from y'all. Now I can finally get it over and done with the client \\:D/

---

