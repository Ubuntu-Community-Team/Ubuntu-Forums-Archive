---
title: "NFS mount as UID not working"
date: 2014-07-09
forum: Server Platforms
---

### Post by m0rph3us0306 on 2014-07-09
Having some user/permission issues with NFS, and I want to simply user a nodbody:nogroup as the default.   I'm looking through help/docs, etc. and getting an error when using the UID in the options/fstab.

Server has the following export;
```
/export       10.1.0.0/16(rw,fsid=0,insecure,anonuid=65534,anongid=65534,sync)

```
Note that the 65534 is nobody:nogroup

The remote server which mounts has the following in the /etc/fstab;

```
10.1.1.1:/export   /mount    nfs    auto,uid=65534,rw 0 0

```
Now, I had the above loaded with the other options I wanted (auto, rw, etc.) but narrowed it down to the uid that causes the error;
"mount.nfs: an incorrect mount option was specified"

If I remove that UID and mount it as the user, then write to the file, it's being written as that user.   So the question comes down to how do I mount the device as the user I want above?

Thanks for read/replies.

---

### Post by capscrew on 2014-07-09
> **Lace said:**
> Having some user/permission issues with NFS, and I want to simply user a nodbody:nogroup as the default.   I'm looking through help/docs, etc. and getting an error when using the UID in the options/fstab.

There is no UID setting in fstab.  Why would you want to do this?  Do you want all users in a common group and that group setting to be inherited bu all files and subdirectories?
> 

Server has the following export;
```
/export       10.1.0.0/16(rw,fsid=0,insecure,anonuid=65534,anongid=65534,sync)

```
Note that the 65534 is nobody:nogroup

The remote server which mounts has the following in the /etc/fstab;

```
10.1.1.1:/export   /mount    nfs    auto,uid=65534,rw 0 0

```
Now, I had the above loaded with the other options I wanted (auto, rw, etc.) but narrowed it down to the uid that causes the error;
"mount.nfs: an incorrect mount option was specified"

If I remove that UID and mount it as the user, then write to the file, it's being written as that user.   So the question comes down to how do I mount the device as the user I want above?

Thanks for read/replies.
What are the permissions set on the directory that the user is creating a file?  Have you added the user to the nogroup group?

I believe you will find that the PERMISSIONS not the *ownership* of the directory is the reason a user can create files and directories.  The user creates files and directories in that directory as user:user regardless of whether the user is in a secondary group such as nogroup.  The permissions on created files are: 664=files and 775=directory.  The umask determines the permissions.

---

### Post by m0rph3us0306 on 2014-07-09
ok "Why would I want to do this?"
 - this is a central storage location where data get's put in numerous ways, email processing will dump files there, web uploads, etc. but that is irrelevant to the question/issue as this did work in older versions.  Even looking at a ubuntu forum post  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) you can see an example;

 NTFS ~ Use ntfs-3g for write access (rw) 
[FONT=inherit][/FONT]# /dev/hda1
[FONT=inherit][/FONT]UUID=12102C02102CEB83  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
The user on the NFS server is on the local system, and yes, all users should be owned and permissions should all be the same (644). 

Looking at your last statement of the user that creates the files regardless is I think the core answer.  I wanted something like the web-upload once saved to be saved as that nobody user 644 perms, it's currently coming in owned as www-data and 600.   

So the root answer is I can't mount it and have the files written as that user.  I can either script a change on the fly, cron change, etc. OR have the process run as that user it seems. 

Thanks for the time and help.

---

### Post by SeijiSensei on 2014-07-09
Those options apply to *ntfs-3g*, not NFS.  Read "man nfs" for the options that apply to NFS; uid is not one of them.

---

### Post by capscrew on 2014-07-09
> **Lace said:**
> ok "Why would I want to do this?"
 - this is a central storage location where data get's put in numerous ways, email processing will dump files there, web uploads, etc. but that is irrelevant to the question/issue as this did work in older versions.  Even looking at a ubuntu forum post  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) you can see an example;

 NTFS ~ Use ntfs-3g for write access (rw) 
[FONT=inherit][/FONT]# /dev/hda1
[FONT=inherit][/FONT]UUID=12102C02102CEB83  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

Just as @ SeijiSensei,  I'm confused too.  I  assumed you were using a NFS EXPORT that resided on a ext4 formatted partition.  Is this what you are asking about?   I was asking how you use the EXPORT not the server in general.
> 
The user on the NFS server is on the local system, and yes, all users should be owned and permissions should all be the same (644). 

I think you need a better grasp of how file creation ownership and permissions work.  The user can be both a local user or a remote user.  No local user would use the NFS EXPORT for everyday use.
> 
Looking at your last statement of the user that creates the files regardless is I think the core answer.  I wanted something like the web-upload once saved to be saved as that nobody user 644 perms, it's currently coming in owned as www-data and 600.

Why the user nobody?  There are easier methods.  What is wrong with the default permissions (not ownership)?
>  
So the root answer is I can't mount it and have the files written as that user.  I can either script a change on the fly, cron change, etc. OR have the process run as that user it seems.
Thanks for the time and help.
The proper way to manage shared data is to create a file system that has a common user group.  I use the group named **users** (gid =100).  The caveat to all of this is that NFS requires that you match the local GID to the remote users GID so you need to make sure that the remote user group named *users* is always gid=100.  There is no reason to use the default Apache web root at all.  I keep my data at /data/www/<each-sub-domain>.  I created a group named www-content and all users that need access can access the data.  If you need more security you can create a user group for each sub-domain.

What formatting is the remote host using?  ext4 or ????

---

### Post by m0rph3us0306 on 2014-07-09
Thanks for that nice reply.  I actually came into this 1/2 setup at a datacenter then moved to amazon, but I do have the ability to change things and like the idea of a central 'users' group (nobody:nogroup is what was in place).

The disk is and LVM setup (formatted ext4) so that is no problem.

I don't need to go to the subgroup level. I just have multiple processes on different machines such as posfix, nginx and even some windows machines that write files over samba, and as you said, want a central user/group so the files can been used by all servers as needed.

So I guess my plan is to get that user setup local, match on the passwd/group file and then make sure the processes use that user.

Again, thanks for the steer in the right direction.

As for the export, forgot to mention, it was set as;
/export       10.1.0.0/16(rw,fsid=0,insecure,anonuid=65534,anongid=65534,sync)   (naturally those id's are nobody:nogroup) so that will be changed as well.

---

### Post by capscrew on 2014-07-09
> **m0rph3us0306 said:**
> Thanks for that nice reply.  I actually came into this 1/2 setup at a datacenter then moved to amazon, but I do have the ability to change things and like the idea of a central 'users' group (nobody:nogroup is what was in place).

The disk is and LVM setup (formatted ext4) so that is no problem.

I don't need to go to the subgroup level. I just have multiple processes on different machines such as posfix, nginx and even some windows machines that write files over samba, and as you said, want a central user/group so the files can been used by all servers as needed.

So you have system users rather than mortal users (humans) that need access.  This should work the same way.
> 
So I guess my plan is to get that user setup local, match on the passwd/group file and then make sure the processes use that user.

All you need is to have the same gid (group).  The system users (processes) need to be in that group. Maybe something like *nfsproc*.
To see all the groups you have try this command```
getent group
```
To see all the users (system and mortal) try this command```
getent passwd
```
> 

Again, thanks for the steer in the right direction.

As for the export, forgot to mention, it was set as;
/export       10.1.0.0/16(rw,fsid=0,insecure,anonuid=65534,anongid=65534,sync)   (naturally those id's are nobody:nogroup) so that will be changed as well.
You don't need to set any anonuid or anongid.  Trust me you need to use a common group instead.  I do this every day.  It's well documented.  Start [here]("https://www.google.com/search?q=ext4+sguid+inheritance&btnG=Go!&gws_rd=ssl#q=ext4+sgid+for+inheritance").

[COLOR="#0000FF"]Edit:  Do you come form a Windows administration background?  Most of what you talk about seems to have that flavor.  Windows thinking will not help you much in this context.[/COLOR]

---

