---
title: "Samba share permissions"
date: 2012-11-26
forum: Server Platforms
---

### Post by flycast on 2012-11-26
Sigh...:confused:
I've read multiple times about file permissions and Samba sharing. I am still confused. It seems that what I have learned so far is that what a user can do in a Samba share is affected by both Linux and Samba permission settings. Is this an accurate statement?

> The final permissions will be the most restrictive subset of both the Linux file system permissions and Samba permissions.

If this is so (excluding acl) it seems that we have three choices regarding permissions:

1) Set Samba wide open and use Linux user and group permissions to restrict sharing permissions.

2) Set Linux user and group permissions wide open and use Samba to restrict permissions.

3) A confusing mix of the two.

Before I ask further questions could someone that understands Samba permissions please confirm that I understand this right?

---

### Post by lykwydchykyn on 2012-11-26
> **flycast said:**
> Sigh...:confused:
I've read multiple times about file permissions and Samba sharing. I am still confused. It seems that what I have learned so far is that what a user can do in a Samba share is affected by both Linux and Samba permission settings. Is this an accurate statement?



If this is so (excluding acl) it seems that we have three choices regarding permissions:

1) Set Samba wide open and use Linux user and group permissions to restrict sharing permissions.

2) Set Linux user and group permissions wide open and use Samba to restrict permissions.

3) A confusing mix of the two.

Before I ask further questions could someone that understands Samba permissions please confirm that I understand this right?

What you're saying is correct.  It's pretty much exactly the same as the relationship between Share permissions and NTFS permissions on Windows.

---

### Post by flycast on 2012-11-26
Thanks for your reply.

Sooo......

Here is where I get confused. How best to manage access to shares? I will end up with 3 servers (3 locations), many folders and 30 or 40 users that all have varying degree of access on different folders from no access, read only to read/write.

Does this make most sense?

1) Make a samba group that has 777 permissions on all shared folders.
2) Force samba group
3) Limit individual users by folder/server in samba?

What would be the easiest way to manage users, folder, server?

---

### Post by lykwydchykyn on 2012-11-26
Do you have some kind of directory (LDAP, active directory,etc)?  If you do, I'd look at integrating whatever directory you have with Samba and POSIX ACLs.

I'd say generally, it's best to use one set of permissions or the other; Samba permissions are not as flexible, but if you have some control over the directory structure, they might be workable.

---

### Post by flycast on 2012-11-26
Not sure I want to get into LDAP or ACL's. I am actually looking at webmin to admin the servers because it seems like a good graphical suite of tools. With webmin I can admin the Linux users and sync all the linux users/groups on all servers.

Also, no files in the shared folders need to be executable.

**User:** Obviously needs to be r/w (6) so owners have complete control of their own files.
**Group:** Without acl this needs to be r/w (6) so that users that need to edit other's files could be assigned to this group.
**Others:** ???

This is where I am stuck. I want to allow some users to read files but not write. It seems that I can either open up permissions in linux to 770 and then limit access in samba. This seems like a bad option because the "read only" user could just log in to the server directly (bypass samba) and they would have r/w access to all folders directly that they did not have in samba.

ACL does seem ideal because it is granular. I could truly set permissions by user. The downside is that there doesn't seem to be any graphical acl editors for acl let alone ones that can push the changes to all three servers. Each user would need to be managed using getfacl and setfacl and webmin's ability to execute command lines on all servers using webmin.

---

### Post by lykwydchykyn on 2012-11-26
> **flycast said:**
> Not sure I want to get into LDAP or ACL's. I am actually looking at webmin to admin the servers because it seems like a good graphical suite of tools. With webmin I can admin the Linux users and sync all the linux users/groups on all servers.

Webmin's a good interface, and in a steady state of development.  You'll get told that it's not entirely compatible with Ubuntu, but I've not encountered a problem yet.  Granted, my Samba needs aren't nearly as complex as yours.

> 
Also, no files in the shared folders need to be executable.

Keep in mind "execute" on a folder determines if a user can browse into the folder or not.

> 
**User:** Obviously needs to be r/w (6) so owners have complete control of their own files.
**Group:** Without acl this needs to be r/w (6) so that users that need to edit other's files could be assigned to this group.
**Others:** ???

This is where I am stuck. I want to allow some users to read files but not write. It seems that I can either open up permissions in linux to 770 and then limit access in samba. This seems like a bad option because the "read only" user could just log in to the server directly (bypass samba) and they would have r/w access to all folders directly that they did not have in samba.


If the users have shell/desktop access to the server, then certainly you need to make all restrictions based on Unix permissions, not samba.

There are some good advanced guides on Unix permissions out there, you may want to read up on best practices and some of the advanced features like the sticky bit, set user bit, etc.

Ultimately, though, I think there's a limit to how much complexity you can attain using only Unix permissions.  I don't know the details of what you need to set up, but POSIX ACL's may be the only option.

> 
ACL does seem ideal because it is granular. I could truly set permissions by user. The downside is that there doesn't seem to be any graphical acl editors for acl let alone ones that can push the changes to all three servers. Each user would need to be managed using getfacl and setfacl and webmin's ability to execute command lines on all servers using webmin.

That's where LDAP would come in, but of course that's another can of beans altogether.  I don't have a lot of experience settin up a system in that way; maybe something like Zentyal would be a good option here?

---

### Post by bab1 on 2012-11-27
> **flycast said:**
> ...
**User:** Obviously needs to be r/w (6) so owners have complete control of their own files.
**Group:** Without acl this needs to be r/w (6) so that users that need to edit other's files could be assigned to this group.
**Others:** ???
The owner of the file is not really important as long as that user is part of a group that has RW rights.  If all users belong to a common group that has RW rights, then all will have those rights.  This can be easily done with SGID to provide inheritance (and eliminating the need to use "force user/group" in Samba.  In essence you control access by *group* and *others* permissions.> 

This is where I am stuck. I want to allow some users to read files but not write. It seems that I can either open up permissions in linux to 770 and then limit access in samba. This seems like a bad option because the "read only" user could just log in to the server directly (bypass samba) and they would have r/w access to all folders directly that they did not have in samba.

You can have users that have no login rights.  If you set this up correctly the "others" users will have r (read only rights).  The basic umask sets the default to 775 on folders only and 664 on all files.  This kind of reduces the need for setting Samba "create" parameters.  As you can see a lot of what Samba parameters provide are workarounds for poor file system structure.> 

ACL does seem ideal because it is granular. I could truly set permissions by user. The downside is that there doesn't seem to be any graphical acl editors for acl let alone ones that can push the changes to all three servers. Each user would need to be managed using getfacl and setfacl and webmin's ability to execute command lines on all servers using webmin.
I agree, ACL's can be complex and idiosyncratic to the situation.  I prefer consistency across the filesystem (i.e. /srv/smb).  Your problem with read only documents might be solved with proper file system hierarchy and settings along with Samba share positioning.  At the very least use ACL's for the exceptions to RW permissions.

If you want a directory (share) that is open to all to RW without other users having the ability to delete others files look at how /tmp is set up.  That is exactly how that directories permissions are set.

As a last resort you can change the attributes of a file (to immutable (unchanging)) with the command *chttr*.  That way no user can change the file without changing the attribute and only sudoers can do that by default on Ubuntu hosts.

---

