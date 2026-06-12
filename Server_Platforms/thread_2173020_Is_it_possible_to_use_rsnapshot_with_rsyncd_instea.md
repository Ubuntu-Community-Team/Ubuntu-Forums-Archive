---
title: "Is it possible to use rsnapshot with rsyncd instead of ssh?"
date: 2013-09-07
forum: Server Platforms
---

### Post by MakOwner on 2013-09-07
I have been looking at rsnapshot to do some automated backups.  
I have been looking at the docs on the ranspshot.org website and at variosu howtos I have found via google.
None of them mention anythign other than ssh as the transport.  

Is it possible to use rsyncd?  
Or would it be better to just mount the remote filesystem via NFS and treat the backup as if it were local?

---

### Post by markbl on 2013-09-07
> **MakOwner said:**
> 
Is it possible to use rsyncd?  
Or would it be better to just mount the remote filesystem via NFS and treat the backup as if it were local?

Of course it is possible to use rsyncd. You specify it in the url just as if you were using rsync by hand. E.g.
```

rsync -av pc:/tmp/x .

```
would copy remote file x to . using ssh transport.
```

rsync -av rsync://pc:/tmp/x .

```
would copy x using rsyncd on the server. If your server is linux then of course you have to have rsyncd running, i.e. directly or from inetd.

I use rsnapshot to do my home backups to my linux server. To include windows PC's I just install deltacopy (free rsync/rsyncd server for windows) and add "rsync://" in front of the paths in rsnapshot.conf for those PC's.

---

### Post by MakOwner on 2013-09-08
> **markbl said:**
> Of course it is possible to use rsyncd. You specify it in the url just as if you were using rsync by hand. E.g.
```

rsync -av pc:/tmp/x .

```
would copy remote file x to . using ssh transport.
```

rsync -av rsync://pc:/tmp/x .

```
would copy x using rsyncd on the server. If your server is linux then of course you have to have rsyncd running, i.e. directly or from inetd.

I use rsnapshot to do my home backups to my linux server. To include windows PC's I just install deltacopy (free rsync/rsyncd server for windows) and add "rsync://" in front of the paths in rsnapshot.conf for those PC's.


I'm not as smart as your average bear -- Just replace the backup command in the rsnapshot file with this rsync command?
This is linux to linux, no windows involved.

---

### Post by markbl on 2013-09-08
> **MakOwner said:**
> Just replace the backup command in the rsnapshot file with this rsync command?
This is linux to linux, no windows involved.

The rsnapshot server configuration is the same regardless of whether your client is windows or linux. Just put "rsync://" in front of your paths on the "backup" commands in your rsnapshot.conf if you want to connect to rsyncd.

However, I only described using a client side rsync server because you asked about it so I assumed you had windows clients. If you are just backing up linux to linux then why don't you just use rsnapshot in the normal way, i.e. rsync over ssh? Why are you asking about rsyncd/NFS etc? Read "man rsnapshot" and look at rsnapshot.org. Plenty of info there.

---

### Post by MakOwner on 2013-09-08
> **markbl said:**
> The rsnapshot server configuration is the same regardless of whether your client is windows or linux. Just put "rsync://" in front of your paths on the "backup" commands in your rsnapshot.conf if you want to connect to rsyncd.

However, I only described using a client side rsync server because you asked about it so I assumed you had windows clients. If you are just backing up linux to linux then why don't you just use rsnapshot in the normal way, i.e. rsync over ssh? Why are you asking about rsyncd/NFS etc? Read "man rsnapshot" and look at rsnapshot.org. Plenty of info there.

Speed primarily.  rsync over ssh takes a couple of weeks to move 13TB+ of data.  I get about 10MB/s with rsync over ssh on a 1GB link, NFS will give me 40 - 60MB/s over the same link.
Once that amount of data is seeded, incrementals shouldn't be that big of a deal, even at 10MB/s, but the initial load of data is... onerous.

I am testing various ways to manually move the data into the rsnapshot storage area manually for faster initial backup time.  

I assume the encryption on the ssh link is the cause of the slowdown.  Is there any way to disable that _just_ for the rsnapshot sessions?

---

### Post by markbl on 2013-09-08
I would try the rsyncd approach. It's easy to configure and I would guess that it would be quite a bit quicker than via ssh, and maybe also than nfs.

---

