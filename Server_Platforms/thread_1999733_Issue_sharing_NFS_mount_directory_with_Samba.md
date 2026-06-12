---
title: "Issue sharing NFS mount directory with Samba"
date: 2012-06-08
forum: Server Platforms
---

### Post by Thedrew87 on 2012-06-08
Hello everyone!  I have an interesting issue with Samba and NFS.  I have been working on this issue for about 1.5 weeks with not much luck.  My current running environment involves 2 Ubuntu 12.04 releases.  What I am trying to do is use Server 1 to mount using NFS on the shared directory in Server 2.  On Sever 1 I am running Samba that is currently sharing out the mounted volume.  I am able to create new files on a Windows 7 box just fine in the Samba share.  But when I try to edit the file and re-save the file I receive an error "This file is currently open with another user".  Any recommendations would be most helpful.  Also if you need additional information please let me know!

Thanks!

---

### Post by SeijiSensei on 2012-06-08
I'm not entirely clear on your intent, but, in general, it's not possible to re-export a remote share for security reasons.  If you could do this, then it would be possible to avoid enforcing permissions on the original filesystem.  Suppose, for instance, you exported a filesystem using Samba to a machine and then tried re-exporting it with NFS.  It would then be possible for a user on the NFS client to authenticate to the NFS server and gain access to files on the Samba machine that he or she might be prohibited from accessing directly via Samba.

There's also the problem that a Samba share has NTFS filesystem primitives, not *nix ones like ext4.  I suspect that can cause all sorts of locking problems.  There's also a problem with NFS file handles described [here]("http://www.gossamer-threads.com/lists/mythtv/users/451005#451005").

Samba re-exports of NFS mounts are equally problematic.

Can the client not mount the shares directly?

---

### Post by Thedrew87 on 2012-06-08
Sorry for not being clear.  Let me start over.  Currently I have two Ubuntu boxes setup in vmware one is running Samba(Server1) the other is running NFS server (Server 2).  What I am trying to accomplish is using Server 1 to mount an NFS share from Server 2 on a local directory on Server 1.  Which I was able to successfully read and write to the mounted drive from Server 1.  Now I am wanting to share that mount point to the windows users using Samba.  I was able to browse to the Samba server from a Windows 7 machine and right click and create a new file.  (I am also able to delete it)  But when I open the file up to edit and try resaving I receive the error - "This file is already in use from another user."  It seems that Microsoft is putting down a temp file before changing the original file.  So after the error I have both the temp file and the main file.  I have also created a lot Samba folder where it works great using word.  But when I start using the mounted NFS share I am getting these issues.  Would there be anything I can do to resolve this or another recommendation to accomplish this?  The reason I have this setup is due from the old Admin and also the samba would have multiple mount points that would have symbolic links to point at different locations that would be shared out.  Any help would be great!  Thanks!

---

### Post by SeijiSensei on 2012-06-08
So let me ask again, what's keeping the clients from connecting directly to server 1?

---

### Post by Thedrew87 on 2012-06-11
Well we currently use two servers that holds all the data.  The old admin setup a samba share and then used symbolic links within the share directory to point to different mount points.  Currently how the setup is I can't think of a way to share straight from server 1 because we still have additional server that holds data.  We would like one share not two separate shares of data.  Hopefully that helps clear up the question you have asked.  We currently have it working with the old samba server (3.0.35).  I'm having troubles trying to upgrade the samba server with this configuration.  Any thoughts or more questions?

---

### Post by Thedrew87 on 2012-06-12
I really need to figure out a way to be about to share out a NFS mount drive.  It is currently working just fine under Samba 3.0.35 but when we upgrade to Samba 3.6.3 we seem to be experiencing these issues.  Any ideas that Samba would have implemented between the two versions that would cause this?

Thanks

---

### Post by bab1 on 2012-06-12
> **Thedrew87 said:**
> Well we currently use two servers that holds all the data.  The old admin setup a samba share and **[COLOR="Red"]then used symbolic links[/COLOR]** within the share directory to point to different mount points...

Samba has changed the way it handles symlinks due to a found exploit.  You still can configure the original behavior though.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.samba.org/samba/news/symlink_attack.html") and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("https://www.google.com/search?q=samba+symlinks&btnG=Go!").

---

### Post by Thedrew87 on 2012-06-12
Thanks for letting me know regarding the symbolic links.  I was able to figure out how to resolve allowing clients to access symbolic links.  Now I am having issues trying to configure oplocks properly.  I found out if I add kernel oplocks = no I am able to resave a Word document within the Samba share.  Now I am worried about multiple users can edit the file and corrupt the data.  Would would be the best recommendation regarding the Word documents issue?

---

### Post by bab1 on 2012-06-12
> **Thedrew87 said:**
> Thanks for letting me know regarding the symbolic links.  I was able to figure out how to resolve allowing clients to access symbolic links.  Now I am having issues trying to configure oplocks properly.  I found out if I add kernel oplocks = no I am able to resave a Word document within the Samba share.  Now I am worried about multiple users can edit the file and corrupt the data.  Would would be the best recommendation regarding the Word documents issue?
What method are you using to mount the share?

---

### Post by Thedrew87 on 2012-06-12
I am using NFS to mount the remote directory to the Samba server.  Then I use the Samba Server to share out the mount.  After couple more hours working on this issue I believe I know what was causing my issues.  Now I am in testing phase now.  I ended up adding "kernel oplocks = no" within my smb.conf file.  

I'll let you know if the problem is resolved with no issues.  But so far so good.

---

### Post by bab1 on 2012-06-12
> **Thedrew87 said:**
> I am using NFS to mount the remote directory to the Samba server.  Then I use the Samba Server to share out the mount.  After couple more hours working on this issue I believe I know what was causing my issues.  Now I am in testing phase now.  I ended up adding "kernel oplocks = no" within my smb.conf file.  

I'll let you know if the problem is resolved with no issues.  But so far so good.

I'm asking you how you mount the share.  Via GVFS or mounting via a script or via fstab.  There is a **nobrl** option in mount.cifs.  From the man pages```
    nobrl
           Do not send byte range lock requests to the server. This is
           necessary for certain applications that break with cifs style
           mandatory byte range locks (and most cifs servers do not yet
           support requesting advisory byte range locks).

```

---

