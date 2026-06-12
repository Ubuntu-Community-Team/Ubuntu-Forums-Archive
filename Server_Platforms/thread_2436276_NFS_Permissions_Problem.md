---
title: "NFS Permissions Problem"
date: 2020-02-03
forum: Server Platforms
---

### Post by clarknova on 2020-02-03
Ubuntu Server 18.04 (nfs server)
Ubuntu Server 16.04 (nfs client)

A local non-root user is able to create and delete files in a directory on the server. A local non-root user on the client gets the error "Permission denied" when attempting to create or delete a file in the same directory. I'm trying to make it so the non-root user on the client is able to create and delete files in the shared directory, but I'm not sure what the problem is.

[LIST=1]
[*]The directory's ownership is 1001:1001
[*]The directory's permissions are drwxrwsr-x
[*]The local user on server and client is a member of group 1001
[*]The directory is shared with options rw,sync,no_subtree_check,no_root_squash
[*]User root is able to create and delete files in the directory on client
[*]I logged out and back in on the client to ensure current permissions are applied
[/LIST]

Can somebody please point out what I've missed?

---

### Post by darkod on 2020-02-03
If it is really true that the same user exists on both server and client, and the password is the same, then it should work.

Basically NFS on the client would react like if the user was on the server itself. But make sure the password is the same, that is important part!!!

---

### Post by clarknova on 2020-02-03
I don't understand what user passwords have to do with NFS. In fact, the user on the client does not exist on the server, but is a member of the group that owns the shared directory.

---

### Post by darkod on 2020-02-03
That's why it doesn't work. The group 1001 on the client is not the same as group 1001 on the server (I think).

Unless I am mistaken you have to match the users and groups (or at least the groups) both on the client and server. Try it like that. Same group name and same group ID. If possible create the same users both on client and server and make their group membership match.

At least that's how I did it for my NFS and works OK.

---

### Post by clarknova on 2020-02-03
I added the user on the server using the same password as in use on the client. I added the user to group 1001, restarted the nfs-kernel-server service and logged out of the client and back in. No change.

---

### Post by SeijiSensei on 2020-02-03
The users must match by ID not name.  You can fix this problem with brute force by editing (as root with sudo) /etc/passwd and /etc/group on both the server and the client. Make sure all the UIDs and GIDs match up.

---

### Post by clarknova on 2020-02-03
> **SeijiSensei said:**
> The users must match by ID not name.

That's what I thought. The user (drs) is already a member of the group, so I'm still not sure why I'm getting the permissions problem.

```
# grep drs /etc/group
ftp:x:1001:drs

# ls -an ./
total 44
drwxrwsr-x 6 1001 1001 10 Feb  3 08:50 .

```

---

### Post by SeijiSensei on 2020-02-03
User drs has to have the same ID on both machines as well, not just a shared group.

---

### Post by TheFu on 2020-02-03
> **clarknova said:**
> I don't understand what user passwords have to do with NFS. In fact, the user on the client does not exist on the server, but is a member of the group that owns the shared directory.

Passwords shouldn't matter on NFS.
Check the userid groups using 'id'.  Rather than describing things, please provide it using ls -al and id commands for the userids involved.

In theory, NFSv4 supports a userid/groupid mapping capability. I've never used it, but have seen forum posts elsewhere saying it doesn't work.

---

