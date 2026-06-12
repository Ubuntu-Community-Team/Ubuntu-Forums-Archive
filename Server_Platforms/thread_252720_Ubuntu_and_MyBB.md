---
title: "Ubuntu and MyBB"
date: 2006-09-07
forum: Server Platforms
---

### Post by mdelves on 2006-09-07
Hey Folks,
a friend has asked me to setup mybb for a site that I have hosted on my server. Now, I unfortunately can't seem to find this as a package in the 6.06LTS repositories. 

What I would like to know is:
* Has anyone had success setting up mybb on a ubuntu server?
* Are there any .deb packages for mybb?

Thanks,
Matthew Delves

---

### Post by Uluen on 2006-09-07
99% of the forum packages installs like this: Download it, unpack in the correct folder (IE /var/www/whatever), run [http://yourserver/somefolder/install.php](http://yourserver/somefolder/install.php).

Can't be much easier than that :)

---

### Post by az on 2006-09-07
> **mdelves said:**
> Hey Folks,
a friend has asked me to setup mybb for a site that I have hosted on my server. Now, I unfortunately can't seem to find this as a package in the 6.06LTS repositories. 

What I would like to know is:
* Has anyone had success setting up mybb on a ubuntu server?
* Are there any .deb packages for mybb?

Thanks,
Matthew Delves

That application is not free software.  It may be freeware, but it does not meet the criteria to be considerd free-libre open-source software.  Only software that is GPL-compatible (or DFSG-compliant) can be in the main or universe repostories.

Since there are tons of other forum applications that are free-libre, no one has bothered to package that application for debian.

[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)
[https://help.ubuntu.com/community/PunBB](https://help.ubuntu.com/community/PunBB)

Now, can it run in Ubuntu?  I don't see any reason why not.

I can guarantee that phpbb2 is much better supported and has an active community around it.  I beleive punBB is well supported, too.  You can't beat a free-libre application with a large following behind it.

---

