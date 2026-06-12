---
title: "Samba, can't acess new hdd."
date: 2020-01-19
forum: Server Platforms
---

### Post by Higgins909 on 2020-01-19
I made another thread here about how I couldn't format my 4TB hdd correctly...  I think I "may" have gotten it, but now I can't connect to this HDD.  I have a W10 desktop and I can still connect to my other drives that are on the server.  When editing the fstab, I essentially just changed the UUID with the new HDD's UUID thinking it would be that easy.  I think my mounting location's owner:group got changed, so I fixed that.  Still can't connect.  I ended up making another folder, /srv/four and another Samba share and restarted.  It worked!  Problem was I forgot to change the mounting location in fstab.  As soon as I changed fstab to /srv/four and then command mount -a, it broke...  Could it be because the drive is not formatted correctly still or ?  I had also made a test folder before changing from /srv/one to /srv/four and it carried over, but can only see it on the command line.  My other two shares/drives still work, just not this one I'm trying to setup.

Thanks,
    Higgins909

---

### Post by TheFu on 2020-01-19
It helps to actually SHOW the configs that are causing issues.  More SHOW, less TALK.

What do we need?
The fstab.
The permissions on the mount point - **ls -al**
Something that shows there is a file system - **df -Th** or there are some **lsblk** options which will show it.

Please.  With *code tags*.

---

