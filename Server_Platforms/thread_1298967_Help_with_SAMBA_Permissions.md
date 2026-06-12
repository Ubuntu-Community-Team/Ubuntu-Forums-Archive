---
title: "Help with SAMBA Permissions"
date: 2009-10-23
forum: Server Platforms
---

### Post by Noah0504 on 2009-10-23
My file server serves media to my media center, hosts a backup for my computer and also acts as a torrent box.

I have been having problems with the permissions for these shares.  When moving media into the media share, I am often unable to rename these files later until I move it back to my Mac, take ownership, rename it and then move it back to the share.  Or I can go the hard route of changing the permissions for all of the files under that share.  Right now I have the create mask rule set to 0777.  I figured this would cover me, but I guess maybe they are not being set when moving a file?

Also, I use Transmission when downloading a torrent.  This works fine.  I have the download directory set in my home directory, which in turned is shared by having that option enabled in my SAMBA config file.  However, if I copy one of these files from the server to my Mac, sometimes I do not have permissions again to rename the file, even though it says I am already the owner.  Here I really have no control.  There is no way for me to change it because it doesn't change anything as I am already the owner...

I guess I am looking to for the best way to share my home directory for BitTorrent and a spot for my back up.  Also, I need to fix the problem with the media share.  I hope this was easy enough to understand.  :)

Thank you in advance for any advice or help.

---

### Post by swerdna on 2009-10-23
Can you post the results of this command: testparm -s
That will give us a condensed look at your configuration file.

Please point out which [stanza] pertains to the "media share".

I also need to see the owner, group and permissions on the shared media directory (not the shared directory's contents, the directory itself, so can you run the "ls -l" command on the shared directory and post here.

---

### Post by Noah0504 on 2009-10-23
> [media]
	comment = Network Share for Media
	path = /srv/media
	read only = No
	create mask = 0777
	directory mask = 0777
	guest only = Yes
	guest ok = Yes

I did guest only so my media center wouldn't have to login.  Could this be part of the problem?

> drwxrwxrwx 6 nobody nogroup 4096 2009-09-06 00:15 media

Now that I am looking at it... I don't remember every changing to ownership to nobody.nogroup.  That may be part of the problem as well, huh?

---

### Post by swerdna on 2009-10-23
Hard to get the mind around all those things.
How about you define a user for ease of admin of the media share, any name you like, e.g. "admin". Create the Linux user admin.

Chown the directory media and all its contents to admin user with this command: ```
sudo chown -R admin:admin /srv/media
```
Then make the share like this:
```
[media]
comment = Network Share for Media
path = /srv/media
read only = No
force user = admin
guest ok = Yes
```
What happens is that a guest gains access and immediately assumes the persona of the user admin, so all permissions problems fall away because additions, edits, creations etc are made by the guest in the name of the owner (admin).

Since that is the case, you can change the permissions on directory media back to the ordinary perms drwxr-xr-x if you like.

If you find that users have to log in then add the line "guest only = yes", but try it without first (I'm not familiar with it).

---

