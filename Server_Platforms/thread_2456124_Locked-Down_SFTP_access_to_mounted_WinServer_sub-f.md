---
title: "Locked-Down SFTP access to mounted WinServer sub-folder"
date: 2021-01-04
forum: Server Platforms
---

### Post by Marc-NJ on 2021-01-04
If someone could lend some help with this problem, it would be greatly appreciated!  I have two servers at a site - one running WinServer 2012 and the other running Ubuntu Server 16.04.5.  The Ubuntu server currently has a network share from the WinServer mounted via CIFS.


What I want to do is create a user account on the Ubuntu server that will only have SFTP (not SSH) access to a specific sub-folder on the WinServer.  I used these instructions as a guide initially: [https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04)


Initially I didn't do anything under Step 2, and for Step 3 tried setting the ChrootDirectory to the already mounted WinServer location but with the sub-folder specified in the path (e.g. /media/<WIN_SERVER_NAME>/folder/sub-folder).  I then tried to SFTP in using FileZilla, and was able to connect using the new user ($user) I had created in Step 1, and see contents of the folder, but couldn't upload anything to it.


I then tried messing around with mounting the WinServer sub-folder but telling Ubuntu to mount it with 0757 file and directory permissions, or mount it with $user:$user ownership, but each time I did that and then tried to SFTP in I got fatal errors in FileZilla and couldn't connect.


I thought at this point let me see about asking for some help to see how I can accomplish what I'm trying to accomplish.  Any inside or advice is greatly appreciated!  Thanks.

---

### Post by darkod on 2021-01-05
Instead of trying to set permissions with mount options, have you tried setting up permissions on the specified folder directly with chmod?

In this case I don't know whether they would stay permanent after remount, but you could give it a try.

1. Remove permissions from mount options. Remount it to apply new settings.
2. Set necessary permissions with chmod directly on the folder.
3. Check if upload/create files and modify works.
4. If it does, remount it again and check if it continues working after a remount.

NOTE: For adding write permissions to user or group I prefer 'chmod u+w' and 'chmod g+w'. People in many cases find instructions to use 'chmod 757' or 'chmod 775' but avoid using that because the 7 will set the execute bit on all files too (when used recursive with -R of course). The u+w on the other hand only adds write to files and folders and doesn't touch the execute for files.

---

### Post by The Cog on 2021-01-05
This sounds like a use case for bindfs to me. Bindfs can mount an existing directory into another directory, but changing ownership and permissions at the same time. You can either increase or decrease the effective access to the new bindfs-mounted directory.

---

### Post by TheFu on 2021-01-05
I don't think chmod works with CIFS, backed by NTFS storage.  But I'm assuming that "WinServer" means some sort of normal MS-Windows Server, though that is unclear, at least to me.

---

### Post by Marc-NJ on 2021-01-05
> **darkod said:**
> Instead of trying to set permissions with mount options, have you tried setting up permissions on the specified folder directly with chmod?

In this case I don't know whether they would stay permanent after remount, but you could give it a try.

1. Remove permissions from mount options. Remount it to apply new settings.
2. Set necessary permissions with chmod directly on the folder.
3. Check if upload/create files and modify works.
4. If it does, remount it again and check if it continues working after a remount.

NOTE: For adding write permissions to user or group I prefer 'chmod u+w' and 'chmod g+w'. People in many cases find instructions to use 'chmod 757' or 'chmod 775' but avoid using that because the 7 will set the execute bit on all files too (when used recursive with -R of course). The u+w on the other hand only adds write to files and folders and doesn't touch the execute for files.

I think I tried this and it didn't work.  Even if I set permissions or ownership of the sub-folder in Ubuntu before mounting it, the permissions and ownership are changed when mounting and then I can't use chown or chmod to change them while the mount is in place.  That is what you were getting at above, right?  Thanks though!

---

### Post by Marc-NJ on 2021-01-05
> **The Cog said:**
> This sounds like a use case for bindfs to me. Bindfs can mount an existing directory into another directory, but changing ownership and permissions at the same time. You can either increase or decrease the effective access to the new bindfs-mounted directory.

Any chance you might be able to provide some further info, or point me more in the right direction (although I appreciate the above pointer).  I'm a bit outdated on Ubuntu (haven't really used it heavily in a while) and don't want to risk screwing this up and opening up a security hole or something worse.  Thanks!

---

### Post by Marc-NJ on 2021-01-05
> **TheFu said:**
> I don't think chmod works with CIFS, backed by NTFS storage.  But I'm assuming that "WinServer" means some sort of normal MS-Windows Server, though that is unclear, at least to me.

Yup, sorry for the abbreviation - Windows Server 2012.  Any other thoughts or ideas to accomplish what I'm looking for?  Thanks!

---

### Post by Morbius1 on 2021-01-05
Why not post the cifs mount expression you are using. CIFS from the client perspective is a virtual filesystem and has ownership and permissions that you can set in the mount statement.

---

### Post by Marc-NJ on 2021-01-05
> **Morbius1 said:**
> Why not post the cifs mount expression you are using. CIFS from the client perspective is a virtual filesystem and has ownership and permissions that you can set in the mount statement.

I did the CIFS mount via Webmin.  If you can let me know where I can find it in the filesystem, I can retrieve it and post it here.  Thanks again for your help!

---

### Post by Morbius1 on 2021-01-05
Gosh you're making this hard. Um ... haven't used Webmin for years.

I'm guessing if you have this mount at boot it should be in /etc/fstab.

---

### Post by Marc-NJ on 2021-01-05
> **Morbius1 said:**
> Gosh you're making this hard. Um ... haven't used Webmin for years.

I'm guessing if you have this mount at boot it should be in /etc/fstab.

Sorry about that.  I will hopefully get the information and post it on here later tonight (Eastern Time).  Thanks again for all your help!

---

### Post by The Cog on 2021-01-05
> **Marc-NJ said:**
> Any chance you might be able to provide some further info, or point me more in the right direction (although I appreciate the above pointer).  I'm a bit outdated on Ubuntu (haven't really used it heavily in a while) and don't want to risk screwing this up and opening up a security hole or something worse.  Thanks!

OK, here's an outline:
I assume you can mount the server directory in Ubuntu using CIFS. I can't help you with that, never done it. 
I assume it is mounted at /media/<WIN_SERVER_NAME> and has read/write access for user serveruser.

Create a new folder at e.g. /media/winmiror
As root, run ```
bindfs --force-user=sftpuser --perms=0000:u=rwX /media/<WIN_SERVER_NAME>/folder/subfolder /media/winmirror
```
Leave bindfs running it's a process that does the mirroring.
This makes the contents of your wanted server folder appear in winmirror, read/writable by sftpuser.
The perms might need tweaking with experimenting, and I've never used a chroot. But the basic idea here is to make a mount that mirrors your source folder with changed ownerships and permissions. 

I have used it to mirror a mount that is read-write only to root (not accessible to any other user), and make it read-only to all users. bindfs is very flexible.

---

### Post by Morbius1 on 2021-01-05
I'm not exactly sure what would happen if you used bindfs to remount a cifs mount. I've never done it personally ... I don't think I've ever seen it done .. I'm not sure why you would ever need to do that .... but ...........

Anyhoo, where I was going with my request to see the mount expression goes something like this:

Let's say I want to automount a share on a Win10 machine at boot to say ... /media/Win10Share.

So I put this in /etc/fstab ( there are many more options available - I'm trying to make this generic ):
> //192.168.1.142/share /media/Win10Share cifs username=tim,password=timspw 0 0

What that will do is mount the share with owner=group=root with permissions of 755. Root can write to the share but everyone else can only read.

I have many options here:

** I can replace root with myself by adding **uid=morbius** to the list of options:
> //192.168.1.142/share /media/Win10Share cifs username=tim,password=timspw**,uid=morbius** 0 0

Now morbius can write to the share and everyone else can only read.

** On the opposite end of the spectrum I can keep owner as root but allow everyone ( on the client ) to write to the share by using **dir_mode=0777,file_mode=0666**:
> //192.168.1.142/share /media/Win10Share cifs username=tim,password=timspw**,dir_mode=0777,file_mode=0666** 0 0

Although the internals are different bindfs and mount.cifs are both virtual filesystems which do pretty much the same thing. They both allow setting ownership and permissions that are different from the original or default. They both result in a set of permissions that are immutable and consistent throughout the tree of the mount point. mount.cifs in a way is bindfs used for network filesystems whereas bindfs itself .... and this is just in my experience ... is used for local fileystems.

---

