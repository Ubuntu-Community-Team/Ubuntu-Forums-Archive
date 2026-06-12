---
title: "Mirroring a Directory?"
date: 2008-05-24
forum: Server Platforms
---

### Post by user1234 on 2008-05-24
Hi, I'm posting this in the Server Platforms forum, because I'm guessing SysAdmin's are most likely to know this answer, and I don't know what section would be better....

Because NFS doesn't export NTFS, I've had to cp an entire dir off my usb NTFS 320G drive onto my home dir, so I can get at it on my home LAN server through NFS from the other computers on my home LAN...

Now, I pull the drive once in a while, and add stuff to that directory on the USB drive (it's my personal photo archive).

And, my wife and I edit, update, and add photos to the NFS share from our laptops, with photos off our cameras and phones...

So, I'd like those two directories (on different drives) to always update and sync with one another... so if I add a photo to the NFS share, it copies to the NTFS USB drive.  If the NTFS USB drive has a new file, I'd like it to be copied to the ext3 drive in the right directory so we see it on the NFS share... 

Is that clear?  I think it makes sense, but I'm afraid it sounds a lot more confusing that it really is...  But, to add complication, if I could get it to work at all, I'd prefer to have w only, and no delete... like, not let my wife accidental red-eye correct and image and then save to overwrite the original (instead of renaming it to save).

---

### Post by ArrantSquid on 2008-05-24
You could just setup a Samba server and share it out like that. What I mean specifically is you would be able to access the ntfs drive with samba across your entire network as well as locally on that server using the ntfs-3g driver. Samba is fairly easy to setup as well. 

To answer your question directly, though, you can sync a folder using rsync and if you need a gui you can use grsync. Or you can try Unison. If I remember correctly rsync only does one way syncing whereas Unison does bi-directional.

```

rsync -avuz source/ dest/
rsync -avuz dest/ source/

```

Those two lines will get the newest file and sync them. Obviously you'll want to run whichever one you were working off of last, first.

Again, I really think that this is real overly complex. Setting up samba and sharing out the ntfs drive is going to be the easiest thing to do. If you're only running Linux then you don't need samba. Just mount it in fstab with ntfs-3g (gives write support) and go with it. HTH.

---

### Post by user1234 on 2008-05-24
> **Lotek said:**
> You could just setup a Samba server 

Lotek, totally thanks for the help... I'll try rsync.

But, as for Samba, uhm... It seems "backdoor" to me.  Both laptops accessing the server are Ubuntu, and the server is Ubuntu...  and Samba is traditionally a Windows hack-through...

---

### Post by user1234 on 2008-05-24
> **Lotek said:**
> Just mount it in fstab with ntfs-3g (gives write support) and go with it. HTH.

Oh, sorry, uhm, yes, if it was Linux... but it's Ubuntu.  Bug known for about 9 months, NTFS is not supported in NFS.  Try it and you get:
```
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.2.1/24:/media/disk".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.2.1/24:/home/user".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /media/disk does not support NFS export.

```
NTFS is not supported for NFS.  I guess I should have explicitly stated that is the reason why I posted...  I would have totally loved to do that, it would have made life SOOO simple... but it's not even a module for any of the default Ubuntu kernels.

I considered compiling a kernel myself, but figured there might be an easier way... cron'ing rsync might be easier...  because once you tweak a package (like a kernel) all automatic updates get screwed and you have to pay 10x as much attention instead of letting them happen automagically.

---

### Post by ArrantSquid on 2008-05-24
You are totally correct. I was under the impression you were using a mixed OS environment, so yeah Samba is a waste of time. [DISREGARD THIS]But mounting that drive to the server and connecting it as an external drive to work off of would work, of course unless you're looking for redundancy which rsync will provide you.[/END DISREGARDING]*

I'm glad I was able to help. Hope it works out for you and post back any feedback or information you come upon to help someone else out. =)


*just saw your new post so yeah... =)

---

### Post by user1234 on 2008-05-24
> **Lotek said:**
> 
*just saw your new post so yeah... =)

I think rsync is doing the trick, just slowly, going to have to cron it for like 4am or something...  Thanks Lotek!  Seems to be working.

---

### Post by ArrantSquid on 2008-05-24
WooHoo! I helped! LoL. Glad it's doing what you wanted it to do and glad I was able to help. Pass it on!

---

