---
title: "pam mount a subfolder in a folder"
date: 2010-08-31
forum: Server Platforms
---

### Post by beeboob on 2010-08-31
Hey all

I want to use Ubuntu 10.04 on some clients whit likewise-open5 for the WinAD and pam_mount to mount user folder, share etc. 

Is there a way, where i can use pam_mount. So a user can get access and auto mouont a subfolder in a folder on a random client

THe path to the subfolder, looks like:

\\Domain\server\share\folder\subfolder1
\\Domain\server\share\folder\subfolder2
\\Domain\server\share\folder\subfolder3

But how can i get User C to mount only Subfolder3. 

There is set some permissions on the folder and subfolder on the win2008 server.

Miniadmins permissions:
\\Domain\server\share\folder\

User permissions:
\\Domain\server\share\folder\subfolder1
\\Domain\server\share\folder\subfolder2
\\Domain\server\share\folder\subfolder3

I have be using the [http://manpages.ubuntu.com/manpages/intrepid/man5/pam_mount.conf.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/pam_mount.conf.5.html) Where the example    

<volume  user="joe"  fstype="cifs"  server="fsbox"  path="sharede/%(USER)" mountpoint="~/HOME/%(USER)" />

works great. 

I have also try to look on [http://ubuntuforums.org/showthread.php?t=1239209](http://ubuntuforums.org/showthread.php?t=1239209)

Hope u can point me in a direction

Best regards

---

