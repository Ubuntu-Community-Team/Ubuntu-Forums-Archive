---
title: "[SOLVED] Samba groups without ldap, ads, or domain"
date: 2008-06-30
forum: Server Platforms
---

### Post by Ancibit on 2008-06-30
Hi!
I've been searching for days on how to use groups in smb.conf, but keep coming to guides relying on ldap or active directory services. I'm starting a standalone server for a few groups. Each group is a separate department and needs exclusive access to their share. I created the users and groups in Unix and added the users to their appropriate groups through useradd/groupadd, although I used -G for 'supplemental groups'. Could that be the problem? I had tried wiping the user and adding it to a primary group instead, but that didn't fix anything.

I was using the default settnigs for Hardy Heron's smb.conf in terms of passdb backend (tdbsam I think), but I got frustrated and reverted to smbpasswd. After setting that up I can get individual users to access the shares appropriately.

So, I ask, what should I do? Should I abandon using groups and painstakingly enter every user into the appropriate valid user line in smb.conf? Is there a way to get the groups to work? Any other suggestions? :confused: I can post my smb.conf file if needed. Samba is more extensive than I thought.

---

### Post by promodus on 2008-06-30
Would this be similar?
[http://www.bluelightning.org/linux/samba_acl_howto/](http://www.bluelightning.org/linux/samba_acl_howto/)

---

### Post by erolleman on 2008-06-30
I'm not sure how familiar you are with how permissions work in linux.  But all you need to do is make the appropriate users part of the corresponding linux groups then use " chown " and " chmod " to adjust the permissions accordingly.

Example:

Create the user in samba and linux as well as create passwords:
  - "useradd user1"
  - "passwd user1" *assign password
  - "smbpasswd -a user1" *assign the same password

  *repeat for each user you wish to add

Now you need to create your group and add the users to it
  - "groupadd group1"
  - "usermod -G group1 user1"  *repeat this command for each user

Next you will need to adjust permissions on the folder so that only those users have acces. Say the folder being shared is "/shares/folder"
  - "chown -R root:group1 /shares/folder"
  - "chmod -R 770 /shares/folder"

The last two lines are the commands to set permissions.  The first will set the owner to " root " and the group to " group1 ".  The " -R " switch will apply this change to the folder and all files and folders inside that folder.  The second command uses the numbers to set what level of permissions the owner, group and other (everyone else) has. 1 = Execute, 2 = Write, 4 = Read.  You simple add all the numbers together according to what permissions you would like to assign.  Just read and execute would be 1 + 4 being 5 of course.  Full permissions would be 7.  The order of the numbers determine who the permission applies to. The order is as follows: owner, group, other.  So the "chmod -R 770 /share/folder" gives full permissions (7) to the owner (which we set as root in the command before it), 7 to the group (which we assigned to " group1 " in the command before this) and no access what so ever (0) to everyone else.  Now to give another use access to the folder you will just need to add them to the " group1 " group.

I hope this helps.

---

### Post by Ancibit on 2008-07-01
Okay cool. So we are mounting a disk onto /media/fileserver which has 4 different shares. Each one has it's own group, however, some users have more than one group.
```
[ACE]
   path = /media/fileserver/ace
   valid users = @acemembers
   create mask = 660
   directory mask = 770
   writeable = yes

[ESG]
   path = /media/fileserver/esg
   valid users = @esgmembers @acemembers
   create mask = 660
   directory mask = 770
   writeable = yes

[Accounting]
   path = /media/fileserver/accounting
   valid users = @accountants
   create mask = 660
   directory mask = 770
   writeable = yes

[ITRes]
   comment = Technical Files 
   path = /media/fileserver/itres
   create mask = 664
   directory mask = 775
   readonly = yes
   write list = @filemanagers
```
In this example group acemembers can access the ESG share, but when they create a file, the group bit will apply to them and not allow group esgmembers to even read files, right? Would force group = esgmembers resolve that issue if every acemember is also an esgmember? Or wouldn't that just make anyone -- even if they weren't in those 2 groups -- able to access that folder? I think that may have been my problem (although I did forget to chown and chmod those directories ...:-\").

As this is not yet a live server, I'm going to test this. The ACL is a good idea if it works on a standalone server and doesn't require a domain. If this doesn't work out, that may be my next choice. Thank you guys! :D

---

### Post by promodus on 2008-07-01
> Windows NT clients can use their native security settings dialog box to view and modify the underlying UNIX permissions. 

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id396746](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id396746)

---

### Post by erolleman on 2008-07-01
Adding the force group is definately a good way to do it and make sure your create mask gives the appropriate permissions to the group.  To the situation with acemembers and esgmembers, I'd say make the acemember users members of the esgmembers group as well.  So if user1 is a member of the acemembers, make him a member of esgmembers as well.  This way you can still " force group = @esgmembers " and the acemembers will still have access because they will also be members of the esgmembers group.

---

### Post by Ancibit on 2008-07-01
Thank you, erolleman, I was hoping that it could work that way. I'm just concerned that this kind of scenario would cause a security issue with something like the Accounting share. So if I use "force group = accountants" there to make sure it's saving the files as that group (instead of acemembers/esgmembers), would this not give anyone else access to the share under the premises of 'accountants,' even if they do not belong to the group?

---

### Post by erolleman on 2008-07-02
[ACE]
   path = /media/fileserver/ace
   valid users = @acemembers
   **force group = @acemembers**
   create mask = 660
   directory mask = 770
   writeable = yes

[ESG]
   path = /media/fileserver/esg
   **force group = @esgmembers**
   valid users = @esgmembers
   create mask = 660
   directory mask = 770
   writeable = yes

[Accounting]
   path = /media/fileserver/accounting
   **force group = @accountants**
   valid users = @accountants
   create mask = 660
   directory mask = 770
   writeable = yes

With this set up any files created in the ACE share will have the acemember group set, any files created in the ESG share will have the esgmember group set and any files created in the Accounting share will have the Accountants group set.  So the only way a user would be able to access the share and/or edit or change the files is if they are a member of the appropriate group.  So acemember and esgmember users will have no access to the accounting share unless you make each of those users a member of the accountants group.  
Is this not what you are looking for or did I not quite grasp what your worry is?

---

### Post by Ancibit on 2008-07-02
Awesome, nope, you solved it! :D My concern was from the wording of various pages I read that force group would cause a connecting user (even if not from the group) to be able to connect to it as that group, which did sound odd to me. I tested it and it works as it should! Thank you so much for all your help!

---

### Post by alecz20 on 2009-03-08
> **erolleman said:**
> I'm not sure how familiar you are with how permissions work in linux.  But all you need to do is make the appropriate users part of the corresponding linux groups then use " chown " and " chmod " to adjust the permissions accordingly.

Example:

Create the user in samba and linux as well as create passwords:
  - "useradd user1"
  - "passwd user1" *assign password
  - "smbpasswd -a user1" *assign the same password

  *repeat for each user you wish to add

Now you need to create your group and add the users to it
  - "groupadd group1"
  - "usermod -G group1 user1"  *repeat this command for each user

Next you will need to adjust permissions on the folder so that only those users have acces. Say the folder being shared is "/shares/folder"
  - "chown -R root:group1 /shares/folder"
  - "chmod -R 770 /shares/folder"

....


careful about using:
"usermod -G group1 user1"

I did this on my main account and got removed from the admin group. Now I have to figure out how to add myself back to the sudoers.

i suggest using "usermod -a -G group1 user1"
the '-a' appends the user to group1 without removing it from other groups

---

