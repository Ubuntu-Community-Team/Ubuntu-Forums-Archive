---
title: "Postfix question during install"
date: 2010-05-08
forum: Server Platforms
---

### Post by wiz561 on 2010-05-08
Hi,

I downloaded and burned 'ubuntu-10.04-server-amd64.iso' image.  I've done a thousand ubuntu installs before from so many different versions.  

My question is, why is it asking me to configure postfix during the installation?  It pops up with it right before it asks me what services I want to install, and right after I put in my user account to create.  

I've never seen it do this before, and I've even verified the md5 on the image I downloaded with the Ubuntu repo.  I've installed 10.04 server on different machines and it never asked me for the postfix config.  Why now?

Thanks!

---

### Post by wiz561 on 2010-05-08
OK, this is really strange...  I have two hard drives and was doing RAID0 + LVM.  Here's my partitioning scheme...

sda1
512m - /boot - ext4
(rest) - raid0

sda2
(whole) - raid0

raid0 array -> lvm

lvm - two volume groups

2g - swap
(rest) - / (root partition)

If I do this, then it asks me for postfix configuration.  If I leave the software raid out and just use LVM, then it doesn't ask me for it.

So bizarre.  Don't know why, but it does.  I didn't believe it, and I attempted to install with the raid combo again to just verify...and it asks me for the postfix configs.  Strange stuff...

---

### Post by Aearenda on 2010-05-08
For software raid, the mdadm package has a 'recommends' link to postfix or another mail transport, so that you can get maintenance messages by email, I expect. Installing recommended packages is on by default in Ubuntu. You can just uninstall Postfix afterwards.

---

### Post by wiz561 on 2010-05-08
That makes sense....sort of strange, but makes sense.  I would have guessed it would use syslog instead, but mail works too.

Thanks for the response.  Its things like this that makes me scratch my head!

---

### Post by Aearenda on 2010-05-09
It made me wonder too, first time I came across it!

---

