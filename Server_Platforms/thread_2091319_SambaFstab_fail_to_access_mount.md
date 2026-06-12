---
title: "Samba/Fstab fail to access mount?"
date: 2012-12-04
forum: Server Platforms
---

### Post by jumping_snake on 2012-12-04
Good Evening,
  Ok, I keep going back to try to fix this issue, but for the life of me I haven't been able to solve it, even with looking at KB articles or other websites, for the last couple of months: I used to have Ubuntu 10.04 setup on a server of mine that has a RAID setup inside of it. The single partition on the RAID is formatted with NTFS (I wanted to make it as easy as possible to share with Windows computers). Users were able to access the mounts without issue (only needed a username/password entered when they tried to access the mount). I should note that I never setup any of the Windows users as a local account on the server. 

  I have since upgraded to 12.04, but now no matter what changes I make to the system, I cannot get the share to be accessible. Here are my current settings:

fstab:
/dev/sdb1       /media/Backup   ntfs-3g         auto,nouser,exec,rw     0       0
# I've also tried the following as well here:
/dev/sdb1      /media/Backup   ntfs-3g         defaults,umask=0022     0       0

smb.conf:
workgroup = WORKGROUP (Windows computers have same workgroup)
security = user
[Books]
   comment = Books
   path = /media/Backup/Books
   browsable = yes
   guest ok = yes
   read only = yes
   create mask = 0755

I have also chown'd the /media/Backup/Books to change from root:root to nobody:nogroup.

I realize that I'm probably missing something obvious here, but I've been trying to fix this for too long and now I'm just hoping someone can see why I'm failing :p Thanks!

---

### Post by darkod on 2012-12-04
First, when using samba shares the share itself is accessible from windows, so you didn't need to format the partition as ntfs. In fact, you should have used linux filesystem like ext4 so that ubuntu can control the ownership and permissions.

You should consider changing this when you get the chance.

Second, unless the users are created as linux users or samba users on the ubuntu server, entering the username/password they were doing means nothing, unless I'm wrong.
Every username not existing in the linux system is equivalented to the so called bad user, or guest. I guess the option you have guest ok = yes was making it possible for them to use the share, and not the username they were entering.

If you want the share open to everybody, in the global section in smb.conf you have to change security = user to security = share. That will not require login details.

If you do want to use login details, the users will have to be created in ubuntu too.

That is what I can notice with my limited samba knowledge. :)

---

### Post by bab1 on 2012-12-04
> **darkod said:**
> First, when using samba shares the share itself is accessible from windows, so you didn't need to format the partition as ntfs. In fact, you should have used linux filesystem like ext4 so that ubuntu can control the ownership and permissions.
+1 for sure!> 

You should consider changing this when you get the chance.

Second, unless the users are created as linux users or samba users on the ubuntu server, entering the username/password they were doing means nothing, unless I'm wrong.
+1 for the idea.  You need a Linux user AND a Samba user.> 
Every username not existing in the linux system is equivalenced to the so called bad user, or guest. 
+1 again.  The *Bad User* is a user that is not a Linux or a Samba user.  A Linux user can't be a *Bad User*.  They're just a user that has not furnished the correct password.  The term guest is really not correct.  it's more like an anonymous user.> 
I guess the option you have guest ok = yes was making it possible for them to use the share, and not the username they were entering.
Yep.  It means *no password needed to access the share*.> 

If you want the share open to everybody, in the global section in smb.conf you have to change security = user to security = share. That will not require login details.
Don't do this.  This causes the Samba daemon to run through a series of convoluted checks that mean nothing with current practice.  I believe it is for compatibility with Samba2 and early windows clients.

It's easy to set up anonymous (guest) user access with *security = user*. > 

If you do want to use login details, the users will have to be created in ubuntu too.
Er, this is what the Bad User is for.  On my system I mapped it to a user named *smbguest*.

---

### Post by jumping_snake on 2012-12-06
Thanks for the help! I have ordered another drive to move all of the data onto so that I can reformat the RAID to ext4. Then I'll try this whole process again using what you two have said.

---

