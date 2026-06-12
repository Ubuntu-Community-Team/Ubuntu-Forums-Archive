---
title: "NFS shares, user rights and security?"
date: 2006-08-17
forum: Server Platforms
---

### Post by Jabran Asghar on 2006-08-17
Hi,

I have setup a NFS server, exported a directory for a client, mounted the directory from the client , and accessed the NFS share from client  --- all OK. 

BUT! Things seem not to be as I want!

Both machines (NFS server and client) are fresh installation, both have only one user (say "usr001")(the one created at installation time, same names and same passwords on both machine). As this is the only user created during installation, so this has same User ID and Group ID on both machines (as setups will pick the user id in same sequence). **This is the problem!**

For example server user (usr001) has rwx rights for the nfs share, now when client user (also user001, with same UID) mounts the nfs share on the client machine, he also has rwx rights on the share due to identification of IDs!

How I should setup to prevent this from happening? This would be a security flaw if local users of client machines having same UID and GID as that of local users on the server machine will have access level that of server local users!

Any hints to do it correctly?

Thanks for reading, and any thoughts for a solution :-)

Regards
Jabran

---

