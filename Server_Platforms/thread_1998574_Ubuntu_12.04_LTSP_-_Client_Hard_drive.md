---
title: "Ubuntu 12.04 LTSP - Client Hard drive"
date: 2012-06-07
forum: Server Platforms
---

### Post by slicknick5181 on 2012-06-07
Hello,
   I have been checking out LTSP installs since 9.04 and had a few running, But still a bit of a noob at this. 12.04 LTSP (64 bit) was pretty easy to set up but I can not for the life of me figure out how to access client hard drives. I use this system to recover files from computers a good bit. I have created

/var/lib/tftpdboot/ltsp/i386/lts.conf 

and put the following

LOCALDEV_DENY_INTERNAL_DISKS=false
LOCALDEV_DENY=false

and I have updated the image

ltsp-update-image

And still I can not get access to thin client HDD

Any help would be appreciated,
                                                     Nicholas

---

### Post by snyder.man on 2012-06-30
The beauty of a terminal server is the shared resources. As such your clients are actually working off the "server". Although provisions have been made to be able to utilize local devices on your client system, what is at heart is the host system. To ensure compatibility the only "system" drive your client will see is in the host system and local hard drives are ignored (CD-ROM's and usb are not necessarily considered system drives).

If your client system has a hard drive consider installing Ubuntu on it and reconfigure your network for fat client access.

---

### Post by spynappels on 2012-07-01
I'm not sure how to accomplish what you want to do through LTSP, but I've done the same thing in a different way if this may help?

I've used a USB live install, but a LiveCD should also work with some modification. 

What I did was to add a script which runs at boot which mounts a folder on my server to a mount point I n the live session, and I transfer anything required from the original HDD to that. NFS works with some fiddling, but SSHFS worked best for me.

---

