---
title: "Setting Up Homelab Server With Plex"
date: 2022-12-01
forum: Server Platforms
---

### Post by calerid2 on 2022-12-01
Hello Community (Ubuntu),

I am working on setting up a home server for my family. I am learning volume management and container systems. I know there are probably a few better forums, but I wanted to reconnect with these forums. 

I am running 20.04 LTS Server, and I have 3 volumes for data. 1 TB WD, and 2 4TB WD (RAID0). I have tried running Plex in a Docker container, and also from source. I have tried with Docker to set the PID/GID to 1000, and then add /mnt/devicename to the permissions.

 I can't get Plex to recognize the data on these drives. Does anyone have any idea how I would go about this?

Thank you!

---

### Post by TheFu on 2022-12-02
I can't help with docker stuff.  I don't use it for a number of reasons.

RAID0 on spinning disks is asking for all data to be lost.  I speak from experience.  1 disk failed slightly.  I lost all the data on every disk in the RAID0 set.  You've been warned.

If you aren't married to Plex (i.e. you care about privacy), then I can strongly recommend Jellyfin instead.  Jellyfin is based on Emby, but is 100% F/LOSS and respects our privacy, unlike Plex.   Jellyfin finds more accurate metadata than Plex ever did and Jellyfin supports OTA recorded TV using HDHomerun network tuners really easily.  There are jellyfin clients for every platform, if you like, or DLNA clients can be used.
```
sudo apt install jellyfin
``` then point your browser at http://{server-ip}:8096/ to configure.  Normal Unix permissions matter. This is the same for Plex, BTW.  And Kodi and well, all files on the system.

Remote jellyfin access is possible using a full VPN like wireguard.  There are 3rd party services that will spoof IPs so that 2 wireguard systems can connect without opening any internet ports on either system, if you are into trusting a 3rd party (I'm not).  Opening 1 port on the system providing a full VPN seems a minor risk. Client systems don't need any open ports.  Wireguard is supported by all the platforms too.

---

### Post by slickymaster on 2022-12-02
*Thread moved to **Server Platforms**.*

---

### Post by naufrsb on 2023-03-16
Hi there, you can try the following: 

[LIST=1]
[*]Make sure that your drives are mounted properly and that the file system is recognized. You can use the "lsblk command" to check which drives are available and the "mount" command to see which file systems are mounted.

[*]Ensure that your Plex user has permission to access these mounted drives. TRy adding the user to the appropriate group > do this with >(sudo usermod -aG disk <username>) and then make sure the group has the necessary permissions on the mount point... for example: sudo chgrp disk /mnt/devicename.

[*]Plex in a Docker container? Just make sure that the container has access to these mounted drives. You can use the -v flag when starting the container to mount the necessary volumes (docker run -v /mnt/devicename:/data <image>). 

[*]And finally, verify that the file paths for your media libraries are correct within Plex. 

I hope that helps!
[/LIST]

---

