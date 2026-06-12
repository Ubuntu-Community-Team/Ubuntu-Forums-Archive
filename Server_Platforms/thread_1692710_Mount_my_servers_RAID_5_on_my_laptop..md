---
title: "Mount my servers RAID 5 on my laptop."
date: 2011-02-21
forum: Server Platforms
---

### Post by Coder68 on 2011-02-21
Is there a better way to do this then SSH? It is internal so I do not care about security.  Also, I am unable to mount the .iso files in a way that allows me to play the DVD.

I can do a usb drive using:
sudo mount -o loop /media/data/dvd.iso /media/iso

But this SSH tunnel is an sftp connection. I need to be able to mount the remote filesystem on my filesystem so I can play the DVD.

Thanks,

C68

It looks like NFS will work.  I will have to install it on my server.  I have the client on my laptop now, as I have a WD NAS I use it for. I can't believe I forgot about NFS! I am going to try the instructions at: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by rubylaser on 2011-02-22
Yes, NFS is the easiest way to do this.  Those directions will work great, and are very straightforward.

---

### Post by Coder68 on 2011-02-22
I have it working via Webmin.  I had to export my RAID 5 mount on the server, then on my laptop mount the NFS export and then mount the individual ISO so VLC could play it. A lot of mounting just to play an ISO in Linux! 

Thanks,

C68

---

### Post by rubylaser on 2011-02-22
AFAIK VLC doesn't support playing iso's directly (this could be wrong).  I use XBMC, and it plays back iso's without me having to mount them.  I believe SMplayer supports playing back isos as well.  Glad to hear you got it working via NFS.

---

### Post by Coder68 on 2011-02-23
If you use 
sudo mount -o loop /mnt_path /media/iso

after you have the remote folder mounted, and created  /media/iso, this will mount the ISO directly and you can use VLC without issue. 

Now if I can just figure out why my RAID 5 only comes up for a few boots and then "is not ready" anymore. 

C68

---

