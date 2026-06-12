---
title: "force group does not exclude other groups"
date: 2006-08-20
forum: Server Platforms
---

### Post by mihaisofti on 2006-08-20
I have just set up a share called Staff-files.  It looks like this in smb.conf
[staff-files]
        path = /export/staff
        readonly = no
        force group = staff
        force create mode = 0060
        force directory mode = 0070
        create mask = 0770
        directory mask = 0770

Despite this, another user on an XP client who is not a member of the staff group is able to access the share.
Does anyone know why this is.  I can use 'valid users = ..." to stop others, but I would like it to work with the 'force group = ' line.
Can anyone assist me, please.

---

### Post by meng on 2006-08-20
I am no samba expert, in fact I may well be less knowledgable than you are!
My understanding is that force group does not restrict access, but rather treats anyone accessing the share as though they belong to that group.
Have you possibly set "guest ok = yes" in [global]?

---

### Post by dazedandconfused on 2006-08-20
Hiya,

Force group has no effect on the access rights of users, what you need is:

valid groups = @group1 @group2 

and so on (the @ tells it you're naming groups not users). Force group basically forces ownership of any new files/folders created by Samba users to be set to a specified group.

If you want, you can also add Posix Access Control Lists to a shared folder but you need to make sure that the acl package is installed (sudo apt-get install acl) and modify its entry in /etc/fstab by adding the entry acl to its partition's mount options.

An entry in fstab would go from:

/dev/hda5      /shared    ext3    defaults   0 0

to

/dev/hda5      /shared    ext3    defaults,acl   0 0

you can then extend the normal UNIX permissions on that folder to set up access for multiple groups with each group having its own set of access rights and Samba will recognise these settings.


If you want to try this I recommend you search Google for Posix ACLs.

Good luck, post back with any problems.

Cheers,

Jools

---

### Post by mihaisofti on 2006-08-21
Thanks, Meng, but that was not the problem.  
And thanks, Dazedandconfused (I know the feeling), that was exactly the problem, and all is now sorted.  I shall try the thing with Posix ACLs.
Once again, many thanks,
Bungay Mike

---

### Post by dazedandconfused on 2006-08-21
No worries,

All the best,

Jools

---

### Post by mihaisofti on 2006-09-05
Dear Jools
Despite my stating that all is now well, I notice that testparm queries the use of valid users = 
producing:
Processing section "[staff-files]"
Unknown parameter encountered: "valid groups"
Ignoring unknown parameter "valid groups"

so, I must have done something else, too to make this work for me.  Have you any thoughts about the use of valid groups?

regards,

mihai

---

### Post by mihaisofti on 2006-09-05
Okay, I have found the solution; it is this:
"valid groups" is not a valid parameter, however, "valid users =" is okay for users or groups, with the following provisos: (according to Gerald Carter's "Teach yourself samba" isbn 0-672-32269-2, which I recommend)
"Groups can be prefaced by (1)'@' to instruct smbd to look the name up as an NIS/YP netgroup first and as a Unix group if the previous query failed, (2) '+' to inidcate that the group membership should be looked up in the list of Unix groups, and (3) '&' to indicate that the group membership should be expanded by searching the group map for the server's NIS/YP domain"

Thanks again

Mihai

---

