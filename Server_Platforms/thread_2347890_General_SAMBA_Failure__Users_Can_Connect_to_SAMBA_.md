---
title: "General SAMBA Failure:  Users Can Connect to SAMBA Share Only With Owner's Credential"
date: 2016-12-29
forum: Server Platforms
---

### Post by ebsf on 2016-12-29
I have noted a general SAMBA failure concerning network share access.

From both Windows and Ubuntu machines, credentialed users can log on and view, but not access, a SAMBA share using their own credentials.  To access the SAMBA share, a credentialed user must instead use the credentials of the owner of the shared directory.

This failure also extends to shared printers.

The configuration is as follows:  Ubuntu 16.04 server.  Three users, A, B, and C who together form a group "team."  User A is the owner of a directory designated as a Local Network Share with "Allow others to create and delete files in this folder" checked.  Permissions are:  Owner, Create and delete files, Read and write files.  Group team, Create and delete files, Read and write files.  Others, None, Access files, Read-only.  The SAMBA configuration is Authentication Mode, User; No password encryption; No guest account.  Three SAMBA users, A, B, and C.  The SAMBA share for the shared directory is Writable, Visible, Only allow access to specific users A, B, C.

Clarifications are welcome but users should beware that this appears to be a general failure.

---

### Post by Morbius1 on 2016-12-31
It would appear that you are using two different methods to create your samba shares.

This sounds like a samba usershare:
> a directory designated as a Local Network Share
And this looks like a classic samba share created from system-config-samba:
> The SAMBA configuration is Authentication Mode, User; No password encryption; No guest account.
[COLOR=#0000cd]*BTW, how any of this works without password encryption is a mystery.*[/COLOR]

I think the only way for anyone here to help you is if you post the output of the following commands so they can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by darkod on 2016-12-31
First, the way you describe the share looks like you are using ubuntu desktop (with a GUI), not the server version. You should specify that because the thread being in the server section most people (myself including) think about advice for the server version automatically. And there might be small differences...

As for samba on linux, there are two sets of permissions: samba share permissions and linux folder/file permissions. On top of that the users need permissions for all folder levels from the top to the shared folders.

1. Since you obviously want to use group membership you should use the parameters 'create mask' and 'directory mask' in the share definition. For example if you use create mask of 660 that will make all new files to be created RW for owner and group, and no access to anyone else. For read-only access to others, use 664 of course. For directory mask add +1 to each number because folders need the X permission (search).
2. The linux folder permissions also need to be 775 (or 770) for folders and 664 (or 660) for files. The ownership needs to be owner:team. All the folder levels above need to have these permissions or more relaxed. For example if your share is /sambashares/share1 then 'share1' needs the above described permissions and 'sambashares' can have 777 because the permissions of the below folders wil lactually determine the access level.

---

