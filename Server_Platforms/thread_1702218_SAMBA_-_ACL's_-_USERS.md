---
title: "SAMBA - ACL's - USERS"
date: 2011-03-07
forum: Server Platforms
---

### Post by yield_ on 2011-03-07
Hi there,

I am currenly building a file server with Ubuntu 10.10 and Samba.
I have ACL enabled on the file system I want to share.
I also have a bunch of test users.(Nancy and Simon)

They both have access to the share and able to write in it.
However, if one user write a file or folder, the other(s) are not able to edit it 
as the user who wrote the file is the owner as wall as the group of it in rwxrwx...

How can I make user writing in that folder being able to modify other uers folder(s) and file(s) ?

I would actually like to use a group... Like... (shareread and sharewrite) for user who can read or read and write....

I tought only adding that group in the ACL would fix that but it look like I would need to use the ''mask'' feature or something like that ?

Here is my samba config :

[share]
	comment = Permission
	path = /DATA/smb_share/Permission
	write list = simon nancy sharewrite shareread
	writable = yes
	nt acl support = yes


Here are the ACL for that folder :



# file: Share/
# owner: root
# group: root
user::rwx
user:simon:rwx
user:nancy:rwx
group::rwx
group:sharewrite:rwx
mask::rwx
other::---

Thanks !

---

### Post by bsntech on 2011-03-07
If the user is creating a brand new file and wanting to save it, you'll need to add this to the /etc/samba/smb.conf file (I'm assuming that is where the above information is being pulled out of):

create mask = 0775
directory mask = 0775

The above directives will set the initial permission to full access for the user that created it, the groups that the user belongs to, and read-only/execute to everyone else.

This is how I have a home directory setup:

[Home]
path = /home
browseable = yes
read only = no
guest ok = no
create mask = 0774
directory mask = 0775


Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/clients.html")

---

### Post by Morbius1 on 2011-03-07
Don't know anything about ACL's but:
> if one user write a file or folder, the other(s) are not able to edit it 
as the user who wrote the file is the owner as wall as the group of it in rwxrwx...If your user's files are saving as 770 anyway and both are members of the sharewrite group then force the saved file to have the sharewrite group instead of the user's group:
> [share]
    comment = Permission
    path = /DATA/smb_share/Permission
    write list = simon nancy sharewrite shareread
    writable = yes
[COLOR=Blue]**force group = sharewrite**[/COLOR]
    nt acl support = yes

---

### Post by yield_ on 2011-03-07
It does exactly what I needed to.
The mask also helped ;-)

Thanks guys !

---

