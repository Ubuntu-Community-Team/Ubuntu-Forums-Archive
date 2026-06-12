---
title: "LTSP and Active Directory Homes"
date: 2013-11-21
forum: Server Platforms
---

### Post by DommerD on 2013-11-21
Looking for a hint in the right direction.  I assist in running a small gradeschool that is primarily a windows envionment.  We're running Windows Server 2003 as our domain controller, network shares, DHCP, DNS, etc...  We do have a scattering of Ubuntu installs, and the teachers like those over Windows XP (yes, we're still on XP).

 So, I just installed a few weeks ago Ubuntu Server 12.04 and configured it as an LTSP for fat clients ( using the edubuntu desktop).  Everything is running great.  I followed a few guides on the web on setting it up.  I have printing configured, active directory logon using likewise-open, all the apps they need, etc...  I did this so they can netboot into Linux, and if needed, can boot windows from the local drive.  Plus, it makes updates easier.  However, the one thing I'm rattling my brain against is the home directories, and maybe I'm just confusing myself.  

I have two issues that I could use some assistance/clarification on.
I configured pam-mount on the main server, LTSP-SRV1, setup to mount the user's home directory on our Windows server to the Documents folder in their home directory (~/Documents) on the ltsp-srv1 server.  If a user logs into LTSP-SRV1 using ssh, pam-mount doesn't mount any directories.  However, if I su to the domain user, pam mounts the home directory correctly.  Am I missing a setting somewhere to allow this over ssh?

Second, I'd like to do the same thing for my fat clients.  Right now, they log in fine using active directory credentials.  Their home directory is mounted using sshfs.  I'd like to have the ~/Documents folder mounted to their windows home directory.  I installed pam-mount and set it up the same way as the servers inside the chroot, and rebuilt the image using ltsp-update-image.  It doesn't seem to mount.

Does this make sense and doable?  Any downsides to this?  Reason I'd like to do this is so that any saved docs would be available to them if the went to a windows machine.

I can post my config files tonight when I am able to log into the server.

Any help is appreciated!  Thanks.

Dom

---

