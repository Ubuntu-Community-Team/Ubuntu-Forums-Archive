---
title: "Windows home server drive extender technology is being removed from beta"
date: 2010-11-29
forum: The Cafe
---

### Post by garethsimpsonuk on 2010-11-29
I just thought I'd share this with you guys.

[http://www.wegotserved.com/2010/11/23/microsoft-abandons-development-windows-home-server-drive-extender/]("http://www.wegotserved.com/2010/11/23/microsoft-abandons-development-windows-home-server-drive-extender/")

Windows home server V1has a cool technology called DE )drive extender) which allows you to pool disks together into one logical volume. This allows you to duplicate the data across multiple drives at a folder level among other feature. 

WHS v2 beta (codename Vail) is 8 months into a public beta and MS have just decided to drop the DE functions. In my opinion, and most other users this has removed the primary benefit from WHS and there has a been lots of complaints on MS connect. I think removing this will be the end of WHS.

Now I'm on the lookout for an alternative solution. I know there are some good projects out there and was wondering what you guys think can fill then void that MS will leave.

I look forward to hearing your thoughts...

---

### Post by cariboo on 2010-11-29
Try Ubuntu server with LVM, it does essentially the same thing, and it doesn't need as many resources as wha.

---

### Post by crl0901 on 2010-11-29
This is probably the only reason why I use WHS.  If they don't re-think this, I'll probably just use a Linux solution for my next server.

---

### Post by garethsimpsonuk on 2010-11-30
Yes LVM looks pretty cool but is it expandable? Also, WHS has a ton of other features that the stock ubuntu doesn't do. I think there is a place for a Ubuntu home server project, I know its been tried before at ubuntuhomeserver.org which looks like it didn't work out.

crl0901: I'm not sure if I could make a 100% switch (although I would love to!) there are some windows server programs that I just can't live/work without. As much as I hate to admit it, I probably will still buy WHS v2 as I need a 64 bit OS for VMs.

I guess I will have to buy an expensive RAID card that supports OCE.

---

### Post by cariboo on 2010-11-30
What features/programs can't you do without? I tried a demo copy of WHS a while back, there wasn't anything I could see that you can't do with Ubuntu.

---

### Post by garethsimpsonuk on 2010-11-30
- Remote file access
- Simplified user management & permissions
- MS media center integration
- Media streaming to anywhere using ORB
- Dynamic DNS
- Health notifications

Do you know of a similar project which has good storage management but also a fully fledged desktop enviroment? Thanks

---

### Post by Spice Weasel on 2010-11-30
CentOS

Don't forget to check the servers you want enabled and the GUIs installed when installing it.

---

### Post by NCLI on 2010-11-30
> **garethsimpsonuk said:**
> - Remote file access
SSHFS for Linux systems and Samba for Windows systems.
> - Simplified user management & permissions
Ubuntu seems simple to me.
> - MS media center integration
Just install one of the many DLNA-compatible server applications available from the USC.
> - Media streaming to anywhere using ORB
Read the above.
> - Dynamic DNS
Works fine in Ubuntu.
> - Health notifications
Easy to set up using various tools, or you can just pay Canonical to use Landscape(Though it's very expensive ATM, and only meant for big business)
> Do you know of a similar project which has good storage management but also a fully fledged desktop enviroment? Thanks
Ubuntu Server + ubuntu-desktop.


About Drive Extender, why not just use mdadm to set up RAID in Ubuntu? It's fully expandable, and very stable.

---

### Post by NightwishFan on 2010-11-30
I run a lot of file and music server tasks for my local network so I run my machine with the server kernel and ubuntu desktop, then just install server packages (server kernel is just optimized for some things, generic kernel is fine).

---

### Post by Sporkman on 2010-11-30
> **garethsimpsonuk said:**
> 
Do you know of a similar project which has good storage management but also a fully fledged desktop enviroment? Thanks

You could try one of the Turnkey Linux packages ([link]("http://www.turnkeylinux.org/")) - not a desktop environment, but it does have a nice web UI apparently. Or you could try webmin on a standard Ubuntu Server install...

---

### Post by crl0901 on 2010-11-30
The major draw for me, besides drive extender, is the ease of use for WHS.  There's very little configuration to get it working like you want.  I just wanted something that I wouldn't have to mess with too much or take hours trying to configure it to do everything I wanted.  I really like the backup system too.  However, as I said before, if they remove DE, it's useless to me.

---

