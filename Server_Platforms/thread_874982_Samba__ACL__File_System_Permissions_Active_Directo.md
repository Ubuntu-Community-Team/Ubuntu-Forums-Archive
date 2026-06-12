---
title: "Samba / ACL / File System Permissions Active Directory"
date: 2008-07-30
forum: Server Platforms
---

### Post by ksudbury on 2008-07-30
Hi Guys,

I have a windows 2003 SBS handling domain logins, I also have an Ubuntu machine being used as a file server this is using winbind and is on the domain I can chown dirs etc with Active Directory users.

However I have the following problem, I need to allow certain users to access some dirs and not others... for example.

"folder1"  would  need to be accessed by "user1" "user2" and  "user3"  

Now my understanding of this would be to add users 1,2 & 3 to a group say for example "group1" then chown folder1 with that group?

"chown -R  :"DOMAIN\Domain Users"  folder1"

Thats fine but then when user 1,2 or 3 access folder1 and write to the folder and there primary group is "Domain Users" for example it will make it unreadable for other users?

I could force it to take permissions from the parent directory using sticky bit? but what if the users creates a dir and then another dir would it still take its permissions from its parent directory then?

It must be fairly common to want to set a bunch of users that are not in the same primary group access to one dir that no other users can access?


If any one has any ideas / feedback at all on how they have done this it would be great as im melting my brain thinking a way around this if im honest...



Many Thanks
Keith

---

### Post by ginjabunny on 2008-07-30
I asked something similar, see [http://ubuntuforums.org/showthread.php?t=576907](http://ubuntuforums.org/showthread.php?t=576907)

netlogic wrote (I didn't try it, but it sounds like to should work)

First, you want to change all the permissions of the group from the parent directory level and apply the Recursive function

chmod -R 750 directory

After that you want to set setgid to the folder by
chmod +s name.of.the.group directory

[http://en.wikipedia.org/wiki/Chmod#Special_modes](http://en.wikipedia.org/wiki/Chmod#Special_modes)

---

### Post by codmate on 2008-07-31
Since you are using AD for authentication (I'm assuming you have "security=ads" in your smb.conf), then you shouldn't have to worry about Linux permissions, unless some users are being authenticated to the box through means other than AD.

You should be able to chmod 777 the folders and then set read/write permissions in the smb.conf.

Place the below parameters in your share definition where READ_LIST and WRITE_LIST are AD groups:

```

valid users=@WRITE_LIST @READ_LIST
write list=@WRITE_LIST
read list=@READ_LIST
public=No
browseable=No

```

If you don't want to leave the folders open on the Linux side, and winbindd is working well, you should be able to chgrp them using AD groups.

```
chgrp WRITE_LIST /shares/data
```

This is OK if you just have a 'WRITE_LIST' to worry about. Any more complex permissions will probably require the use of setfacl:
[http://linux.die.net/man/1/setfacl](http://linux.die.net/man/1/setfacl)

You might also look into sticky bits:
[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)
...and various types of symlinks:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?ln](http://unixhelp.ed.ac.uk/CGI/man-cgi?ln)

Personally I try and keep things as simple as possible.

I don't allow any other users (apart from other admins) to get a terminal on my Linux fileservers, and there is very little installed on the boxes other than samba.

The only way of accessing the boxes is via SSH with the admin password, or via an AD/samba/kerberos/winbindd authenticated smb session.

Absolutely no Apache, sendmail, desktop gui or anything extraneous is allowed (I don't even have man pages on these boxes).

I've yet to have a security problem, despite my 'open' drwxrwxrwx share folders (touches wood)...

---

### Post by ksudbury on 2008-07-31
Ah I see, 

Currently I have one "share" and then folders below... 


Do i need to create each folder a share? then set perms for it in smb.conf? 

I guess the easy way would be to create a group for each folder and  include each user i want to be able to access it in the group for that folder?


Thanks!
Keith

---

### Post by codmate on 2008-07-31
> **ksudbury said:**
> Ah I see, 

Do i need to create each folder a share? then set perms for it in smb.conf? 

I guess the easy way would be to create a group for each folder and  include each user i want to be able to access it in the group for that folder?


Thanks!
Keith

That's exactly what I do  :)

---

### Post by ksudbury on 2008-07-31
I see so what happens if a user is in two or three groups and they write to different folders? Do the items the users write / create inhert perms from the above dir or va there username / primary group? or does samba take care of the group that writes to that dir?

---

### Post by codmate on 2008-07-31
> **ksudbury said:**
> I see so what happens if a user is in two or three groups and they write to different folders? Do the items the users write / create inhert perms from the above dir or va there username / primary group? or does samba take care of the group that writes to that dir?

It depends on what you have in nsswitch.conf

I have these settings:
```
passwd:     files winbind
shadow:     files
group:      files winbind
```

With this nsswitch, Linux permissions don't figure, as long as the AD group/AD user has permissions to the share folder itself. If my share is in /shares/data, the permissions on /shares *should* be of no relevance (unless it has 'special stuff' like an ACL or a sticky bit, or something else I didn't think of). Experiment. Sometimes it seems to matter - sometimes it doesn't.

I have both totally open in the linux world (set to 777), as it seems to cause less problems.

If winbindd is working correctly with your smb share, then the rest will be up to AD and how its OUs are set up.

In my corporation's AD tree, we have an OU /Users, followed by another OU, DOMAIN USERS.

Files created in the smb shares are owned by the user which created them, and by the group 'DOMAIN USERS'. I'm guessing that this depends on how the AD tree is set up. I think that in my case, it uses the topmost group of the tree that it can find.

The way my AD tree is set up is great for me, as the multiple shares are locked down by samba - but if you have access to a samba share, you have access to everything in it. This is why I go the route of having multiple shares for differing permission requirements.

It prevents users complaining that they can't see into a folder another user has created in a share that they both have access to.

Don't forget that it is also possible to map AD users (and possibly groups) to Linux users (and possibly groups) using the smbusers file in /etc/samba.

There are probably hundreds of ways of doing what you want to do - finding the most simple and maintainable is the mission!

For me it's multiple shares with SMB and AD permissions. If you have a more complex model, then you may need a more complex solution!

I think the best thing for you to do is to set up your share and experiment!

---

### Post by seryeb on 2009-08-25
Hi guys!

Solution that worked for me! (in the case of a group in AD 2k3)

In the file /etc/samba/smb.conf I have the options:

```
   idmap uid = 10000-20000
   idmap gid = 10000-20000
[folder]
   path = /folder
   ...
   valid users = @"DOMAIN+Domain Admins"
   inherit acls = yes
   inherit permissions = yes
   ...

```You can view the gid of the group by the command:
```
wbinfo --group-info="DOMAIN+Domain Admins"

   DOMAIN+Domain Admins:x:**10007**
```Once you have the GID, you mount the partition with the acl option, and use setfacl:
```
setfacl -m g:**10007**:rwx /folder
```Then the Domain Admins group has total rights in /folder.

Bye!

---

