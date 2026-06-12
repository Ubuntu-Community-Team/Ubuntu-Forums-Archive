---
title: "Server Build"
date: 2009-10-28
forum: Server Platforms
---

### Post by sndnichols on 2009-10-28
Hi all,

I have a nice box that I want to re-vamp. I have (2) 73GB 15K SAS drives and (5) 1TB 7200 SATA drives, dual quad core, 16GB RAM. I want to gt the most out of the SAS drives, since they are fast. The box will be used primarily as a media server using Mythbuntu. I will have a webserver (virtualized using esxi). The webservr is for family pictures and video to get it out to the fily easier. I will be using drupal for the cms (blogs, too). In addition, I want to start using (4) virtual desktops for the family so I can continue to use all the old computers we have laying around. 

My question is, what is the best way to use the drives, and how do I go about it? See if I am on the right track, please. I am thinking that the SAS drives should be in a mirror raid configuration and have about 250MB of /boot. Now I get lost.

 The (5) SATA drives I am thinking Raid 5 and contain all of the movies for myth and pics and videos for the webserver.

I ma not sure where the rest should go. Any assistance is greatly appeciated.

Thanks
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by elvinatom on 2009-10-28
I'm far from an expert, but I'd use the 15K drives mirrored (mdadm) for os (and virtual OSes) as that server will have a lot of responsibility and the 1TB for media storage.  I might suggest also to rethink the idea of remotely using OSes at all, since the graphic speed over remote controlled desktops is somewhat lousy at resolutions over 640x480.

---

### Post by sndnichols on 2009-10-29
Elvin, thanks for the response. Exactly what folders comprise the OS in ubuntu. I thought it was /boot. Do you mean all of the folders except /home? Thanks.

---

### Post by sndnichols on 2009-11-03
My plan is 73.3G SAS in Raid1 with 300MB /boot, 33GB /, 20GB swap, 5GB /tmp, 10GN /srv, 5GB media partitions. 

On the (5)1TB drives raid5, I am thinking 400GB /usr, 50GB /var, the remainder for /home.

Does that make sense?

---

### Post by twisted_steel on 2009-11-03
Is the main operating system going to ESXi or Ubuntu?

Are you planning on using /usr and /var for additional storage (e.g. virtual machines and web pages) besides than the default install?  If not, you can free up a lot of that space and use it for something else.  My /usr directory takes up 2.2 GB right now.  My /var directory is under 1 GB.

---

### Post by sndnichols on 2009-11-04
I woulkd like to use esxi as the hypervisor. At present, I am using vmware server to run the website as a vm and also mythbuntu. /usr has the vm's in the server right now, that is why I have it so large. I was wondering how to do this with esxi. I have been focusing on building the raid and getting it right, but it seems I have the cart before the horse. With my present understanding, even the "main" server will be a virtual server. Is that correct? 

Seems like I better read some more before I pull the trigger on the change. I have found a converter between server and esxi, so the vm's I have now should still work, I hope.

Thanks.

---

### Post by sndnichols on 2009-11-04
After reading some about esxi and comparing to server, it looks like I should stick with server. After reviewing the directory contents, the size I chose for /var was a vm in there. I need to be mor careful. I can shrink var to 2GB and mov the rest to /usr for the vm that should be in there. 

With the amount of ram I have do yall think it is ok to just have swap on 1 drive, or should I still spread it across the raid drives (not in the raid)?

---

### Post by twisted_steel on 2009-11-04
I think just putting swap on one of the standard drives would be fine.  I would look into reducing the size of that swap partition.  I don't think the same rules of swap space apply once you get into that much RAM.  I would also look into reducing the size of the root partition ('/') since you are already moving a large amount of the files into separate partitions.  I'm not sure how far to reduce it though - maybe to 10GB or 20GB.  You might find a use for that extra space in one of the others.

I haven't seen a guide with any hard numbers on these things.  Hopefully someone else will chime in.

Are you going to go with VMware Server then?  I've played around with 1.x and 2.x but haven't really touched ESXi.  I'm just curious on that one, and don't really know if that affects your partitioning scheme :p

---

### Post by sndnichols on 2009-11-05
Yea, I am going to stick with vmware server for now. 
It works well for me. I built the webserver using jeos and drupal with it. Also the mythserver is a vm, and the ftp server. To use esxi, apparently, one needs a windows box. I have the RC of 7 on a laptop, but 9.04 is the primary OS on it. All my other machines also run ubuntu. I don't wnat ot have to buy an OS to use the remote console for esxi. Maybe one day they will come out with a linux console, then I will get into it more again.


For those directories, I was just trying to fill up the SAS drive since they are small. With 4TB of SATA and 6 more SAS ports, I am not too worried about the space on the SAS drives now.

---

