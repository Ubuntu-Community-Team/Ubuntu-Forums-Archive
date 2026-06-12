---
title: "Ubuntu Server for streaming media file (Video, Music, Photo)"
date: 2015-01-04
forum: Server Platforms
---

### Post by shonick on 2015-01-04
I'm pretty new to ubuntu and ubuntu server, please help me as clear as possible.
 
Current situation: I already installed Ubuntu Server 14.04.1amd64 with the openSSH and samba file server on my old PC (30GB for system file, and about 600GB for swap partition). This is the only OS on this PC. I already installed Putty on one of my window computer to admin this server. On this window computer, I saw this server host name show up on my network in the window explorer.

The problem is:

- Does this mean I have 30GB for the OS? and the rest 600GB for the data storage?
- How can I see the available storage of this server from window explorer like I often see it when I click on the "This PC" to see the available storage for all local partition?
- I tried to copy a file over to this server in the window explorer, but I can't? How can I about to do it?
- How can I give all the user within my home network to have ability to put media file to this server and also be able to delete them? And then be able to stream all these media to their computer, ipod, TV, ect...

Thanks a lot for your help.

---

### Post by TheFu on 2015-01-04
A swap partition is like a pagefile in Windows. 600G is crazy, crazy, crazy large for this.  4G is probably the size you want for swap.  Swap is used for virtual memory - you cannot access that storage as it is today.  Fix this first.

To setup samba, there are many guides.  [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/?PageSpeed=noscript](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/?PageSpeed=noscript) is reasonable and simple.  Samba can be very complex and your situation is not crystal clear. Hopefully that howto is enough.

If you like, you can skip the samba stuff completely and use winscp and putty to manage the files on the server and use plex server to allow any DLNA client access to video/music/photos on the LAN. Plex is awesome and it is definitely worth your time to try out.

---

### Post by shonick on 2015-01-04
well, I guess I was reading wrong then, I set 30GB for the installation when the installer asking me. So I guess 30GB include the system file and the swap?
What is not clear in my situation? I just want to have a streaming server that all the PC, computer, tablet can access to stream media, and are able to put media file there. What is not make sense?

---

### Post by TheFu on 2015-01-05
> **shonick said:**
> well, I guess I was reading wrong then, I set 30GB for the installation when the installer asking me. So I guess 30GB include the system file and the swap?
What is not clear in my situation? I just want to have a streaming server that all the PC, computer, tablet can access to stream media, and are able to put media file there. What is not make sense?

Turn of the swap - use **swapoff**
Use parted or fdisk to resize the swap - probably easiest to delete it and make a new one in the same area that is 4G (correct size depends on many factors, mainly memory and workload-type).
Use parted or fdisk to create the 550G partition for all your data.
Modify the /etc/fstab to mount the new swap and data partitions - put the data partition where you want, perhaps /d?
Reboot to make certain all of this is working.

Running a Linux Server isn't like running Windows. The best way to learn is to practice over and over.  It might be easiest to just reinstall the OS and figure out where the mistake was made last time in the partitioning.  Youtube videos might be helpful to see other setups. I learn by seeing.

---

### Post by mastablasta on 2015-01-07
you are after plex or kodi then for media sharing. these should be easy to setup.

easiest to resolve your swap issue is to reinstall. since you say old PC, how much RAM do you actually have?
if you plan on keeping data separated then create /data partition during install.

```
df -h
``` command on server should show how disk space is distributed in human readable form.

I would use sFTP rather than samba for file upload.

---

