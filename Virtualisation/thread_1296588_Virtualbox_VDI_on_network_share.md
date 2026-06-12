---
title: "Virtualbox VDI on network share"
date: 2009-10-20
forum: Virtualisation
---

### Post by low_mat on 2009-10-20
I can't figure out how to add a virtualbox hard drive that's located on a network share in ubuntu. If I mount or bookmark a share I can't access it at all in the virtualbox hard drive manager. I don't even have access to the network part of ubuntu. This is probably by design but I hope it isn't and there is a way to do it. Any ideas?

---

### Post by chipper_farley on 2009-10-22
I have been able to do this successfully by automounting the share during startup.  My shares were on a Samba server so I edited the /etc/fstab file to add the following at the end of the file:

//server/share /mnt/mntpoint smbfs credentials=/somewhere/credential-file,uid=1000,gid=1000

Here's what each item is:

//server/share is the share to mount.  Change the values according to your setup.

/mnt/mntpoint is the mountpoint where you want to mount the share in your filesystem.  You'll need to create a directory in the /mnt/ directory and call it something useful.  Here, I'm using mntpoint for an example.  Make sure the mointpoint has permissions that work for your normal user id.

credentials=/somewhere/credential-file is the location of a file that contains the credentials for the share.  The format is just two lines.  One with "username=some-user" and the second with "password=some-password".  Be sure to do a "chown root:root" on the file and a "chmod 600" on the file so only root can even read it.  Otherwise you will have your password readable by everyone.  If the share is available to everyone, just leave this part out.

The "uid=1000,gid=1000" set the user and group settings for the share.

Once you do all this, the share will be a part of your regular filesystem every time you boot up.  You should be able to browse the share in the Virtual Media Manager with no problem.

Just remember in doing this that, unless you're on a gigabit network, you probably will get slightly sluggish performance as a 100 Mb ethernet connection to the hard disk for a VM is a pretty small pipe.

Good luck and I hope I actually answered your question.

---

