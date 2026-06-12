---
title: "Rsync over ssh - failed: permission denied"
date: 2020-04-10
forum: Server Platforms
---

### Post by aljames2 on 2020-04-10
rsync over ssh to remote server returns "failed: permission denied".  My ssh user is not root.  My server won't allow rsync to write files to the destination unless root does it, or sudo is used.

My sshd_config has:  PermitRootLogin no

Therefore, I am trying to get rsync to write to the server without ssh'ing in as root.

Perhaps I should set up authentication keys for root and use: PermitRootLogin prohibit-password
This way I could ssh in as root and rsync will succeed.

Here is my command format:
```
rsync -avz -e "ssh -p 12345" /home/usr/Projects/ remtusr@192.168.10.24:/backups/storage-mnt/Projects/
```

--dry-run on this command shows perfectly what will happen, but removing the --dry-run returns permission denied when the actual write attempt occurs.

---

### Post by darkod on 2020-04-11
I am not sure in these cases if rsync tries to do the copy as the local user or as the remote remtusr user. The message is clear, the user that is considered doing the copy has no permissions that allow the operation in the destination folder.

I would try to match the users both in the source and the destination. Make them to have the same username and UID.

Of course, make sure remtusr has the necessary permissions in the destination folder on 192.168.10.24.

---

### Post by spjackson on 2020-04-11
Is /backups/storage-mnt a native Linux filesystem, i.e. not Fat32, NTFS etc.?
How is it mounted?
Can you write to Projects? e.g.
```
ssh remtusr@192.168.10.24 /usr/bin/touch /backups/storage-mnt/Projects/a_dummy_file
```

---

### Post by aljames2 on 2020-04-11
The filesystem is LVM+ext4.  the ssh touch try did not work returning the same permission denied.  Good to know, it clearly is a user permission issue.

I am working on setting my remtusr with sudo permissions.  Perhaps this requires on the server sshd_config:  AllowUsers remtusr
And, adding remtusr as a sudoer on the server.

---

### Post by aljames2 on 2020-04-11
I can SSH with keys from my server into the client desktop as a regular (non-root) user.  Rsync pull fails because on my server, Root owns the destination.  If I run sudo rsync then SSH connection fails because root login is not allowed & keys are not set up for root access.  I thought there might be a way to rsync ssh as a regular user and then invoke sudo for the read & write process on the destination.  This way my data drive could remain owned by root.

Permissions are 755 on everything at the destination, with ownership currently being root:root

might this work, or not:
```
sudo chown -R $USER:$USER Projects
```

The tricky part is that some of the data needs to stay root:root  :???:

---

### Post by darkod on 2020-04-12
Well, how you organize your ownership and permissions is up to you. In theory you shouldn't serve data as root owner. There are always ways to plan users and groups to achieve what you need without involving root as owner.

Since the destination is also owned by root it makes sense that you get permissions error.

---

### Post by The Cog on 2020-04-12
Rather than changing the login user to root, why not give the login user you are using the permissions needed to write to that directory? Create a group specifically for that user and directory if necessary.

---

### Post by aljames2 on 2020-04-12
More complicated than I thought it would be but got it working, and learned a lot of stuff..

The first part was to change the owner:group of the destination directory on my Server's backup drive1 to the same as my rsync user as suggested here. On drive1 everything normally lives as root:root

I ended up using this command from the Server to pull binary changes while leaving ownership, group, & permission syncing out.  These are not OS files we're talking about, just stuff, I'd be using rdiff-backup for OS directories/files
```
rsync -rltDvz -e "ssh -p 12345" usr@192.168.10.21:/home/usr/Projects/ /backups/storage-mnt/Projects/
```

This command leaves ownership, group, & permissions unchanged on destination and only syncs the binary data.  I didn't want to pull over the desktop credentials to my backup drive #1, which -a would do.  Instead with -rltDvz changed files come over and inherit the permissions of the original files on the Server.  Now of course new files/directories created on the desktop will have the desktop user credentials which I don't want on the backup server.  This is fixed after the rsync by using a careful chmod on those specific new files that pulled over.

I could chown the destination directory back to root:root if I want but for this directory the standard user:user is fine, especially since I always leave my backup drives umounted until I need to do a retrieval or backup.

Thanks again folks!! :cool:

---

### Post by TheFu on 2020-04-12
For the last 15+ yrs, rsync uses ssh by default, no need to add those options.  With a proper ~/.ssh/config file and port and user and ip can be filled in too, so you don't need to complicate any ssh-based connection with it again.

```
$ rsync -rltDvz  remote-box:/home/usr/Projects/ /backups/storage-mnt/Projects/
```

Add this stanza to the ~/.ssh/config
```
host  remote-box
  user  usr
  hostname  192.168.10.21
  port  12345
```

i didn't look at any of the other options.  See how you can clean up the rsync command?  That same setup will be used for ssh, scp, sftp, rdiff-backup, x2go, or any other ssh-based connection is you use "remote-box" where the hostname goes in the command.  No more trying to recall -p or -P or what the alternate username is on some remote system or what the ip is if you can't recall.  The hostname can be an ip, dns or /etc/hosts entry.  Tab completion for those commands knows to check this config file too.

---

### Post by aljames2 on 2020-04-13
Great tip, thanks!

---

