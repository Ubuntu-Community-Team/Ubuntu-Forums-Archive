---
title: "Ubuntu Server 14.04 LTS - NAS + HTPC"
date: 2015-11-16
forum: Server Platforms
---

### Post by warr87 on 2015-11-16
Hi,

I have used linux on and off for a few years now (started off with Red Hat, then Mandriva, and now Ubuntu), but I am now trying my hand in building a ubuntu server using 14.04 LTS. (I'm not afraid of command-line)

I originally wanted only a HTPC, but after some thinking I thought a NAS was more aligned to my needs (though I still want a HTPC) since I have a lot of non-media files that I want to store, periodic backups, and general file-server needs. I have been doing a lot of reading over the last month and I'm still not entirely sure which way I should go with organizing my setup. 

I have a 120G SSD for my OS with a separate 4TB WD RED for my files and media (will be adding on more soon-ish when I manage to pay off the parts I just bought for the project :popcorn:, including RAID setup). On the SSD I was obviously going to go with ubuntu 14.04LTS server with a separate partition for root since I assume I will be making a lot of false starts with this. I also plan on creating a mount point with the 4TB as something along the lines of "/data" (so my /home drive will still be on the SSD), with my files organized accordingly (some shared folders via samba). Now, my main problem with designing all of this right now is should I install ubuntu server and then simply add on mythTV (to pair with my usb dual tv-tuner), or do I separate my HTPC tasks in a VM (VirtualBox?) with another ubuntu server + mythtv or just do a mythbuntu install. The VM/HTPC  would save files to my /data storage area. Is nesting a VM within my server adding too much complexity?

The server is primarily for me, though I will allow some friends access. I'm thinking samba + SFTP + webmin + openSSH + LVM, and NFS for my storage hdd? I've also been looking at FireFly and Twonky for the media server side of things (though I'm less concerned with that right now). I'm also wondering if I install some cloud software so I can sync once of my folders (with university assignments) as another layer of backups (I've had my thesis file corrupted, plus my backups at the same time. Not a good situation .... which has also made me a little paranoid on the subject of assignment backups).

Your advice is appreciated (and will definitely save me a lot of headaches).

[http://au.pcpartpicker.com/user/warr87/saved/DZyPxr](http://au.pcpartpicker.com/user/warr87/saved/DZyPxr)

---

### Post by mastablasta on 2015-11-17
I would say have a look at openmediavault. EDIT - if you feel more at home with RedHat, then maybe have a look at ClearOS or Nethserver. 

and also to stop over complicating the simple things. a descent server should be able to handle multiple tasks at once as long as it is not loaded with too many users.

like for example you have samba, why do you suddenly need cloud software to sync one folder and only for you?! rsync (or grsync if you prefer a gui) should be able to do it just as well. cloud software is meant for multiple users.

---

### Post by darkod on 2015-11-17
I would also say avoid the virtualization taking into account that the few tasks you mention are compatible and easily performed by single physical machine. Plus it will avoid the headache of calculating the dimensioning of the VMs.

I have samba and minidlna running on a small HP Proliant Microserver.

You mention webmin, and also giving your friends access. That would mean giving public access to the server. In such case I would avoid webmin (not that i would use it even if the server was only on the local lan). Going for a web based GUI opens up exploits and attack surface of any "public" server.

I would stick to ssh and sftp (which is using ssh too) and only key based authentication (no passwords), for you and your friends...

PS. Of course, you can configure iptables not to allow connection to webmin from the outside, if it's only for your use. But still, try doing all your tasks over ssh...

PPS. There is also little need to separate / and /home. You mention separate partitions. If all big data including user data goes to the 4TB /data location, nothing big will end up in /home. So you don't really need to complicate it by having /home separate. You would do that mostly on a desktop. The server depends mainly on config files which are not in /home anyway. They are usually in the folders of the respective applications.

---

### Post by warr87 on 2015-11-18
> **mastablasta said:**
> I would say have a look at openmediavault. EDIT - if you feel more at home with RedHat, then maybe have a look at ClearOS or Nethserver. 

and also to stop over complicating the simple things. a descent server should be able to handle multiple tasks at once as long as it is not loaded with too many users.

like for example you have samba, why do you suddenly need cloud software to sync one folder and only for you?! rsync (or grsync if you prefer a gui) should be able to do it just as well. cloud software is meant for multiple users.

You are right. I had just read in one guide that it is best to have the VM with the tv tuner/media server. But it shouldn't be too much of an issue for the server to handle those tasks at all. This is my first server build so I'm not entirely sure what to expect. The case arrives Friday which means I will be attempting to put this all together over the weekend.

Also I was look into openmediavault and rsync/grsync.

> 
I would also say avoid the virtualization taking into account that the  few tasks you mention are compatible and easily performed by single  physical machine. Plus it will avoid the headache of calculating the  dimensioning of the VMs.

I have samba and minidlna running on a small HP Proliant Microserver.

You mention webmin, and also giving your friends access. That would mean  giving public access to the server. In such case I would avoid webmin  (not that i would use it even if the server was only on the local lan).  Going for a web based GUI opens up exploits and attack surface of any  "public" server.

I would stick to ssh and sftp (which is using ssh too) and only key  based authentication (no passwords), for you and your friends...

PS. Of course, you can configure iptables not to allow connection to  webmin from the outside, if it's only for your use. But still, try doing  all your tasks over ssh...

PPS. There is also little need to separate / and /home. You mention  separate partitions. If all big data including user data goes to the 4TB  /data location, nothing big will end up in /home. So you don't really  need to complicate it by having /home separate. You would do that mostly  on a desktop. The server depends mainly on config files which are not  in /home anyway. They are usually in the folders of the respective  applications.


I'll definitely keep that in mind re webmin. I like to think of myself as being fairly secure with my stuff, and the security of my information has definitely been something I have thought about a lot (though still unsure the best way to do things with the safety and security of my server/data. That was going to be further questions here once I had actual got the server running!). I should be able to do everything via ssh, or at least learn quickly! I had read somewhere to put the /home drive on the storage hdd for the NAS/HTPC, but I figured it would be easier and better if I just create a /data mount point and keep everything separate. From your response I can see I was right with that.

---

