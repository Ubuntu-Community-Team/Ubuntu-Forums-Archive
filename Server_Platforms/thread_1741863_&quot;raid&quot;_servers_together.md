---
title: "&quot;raid&quot; servers together?"
date: 2011-04-28
forum: Server Platforms
---

### Post by Wej on 2011-04-28
I have 3 servers I built, each with 33TB of usable disk space using xfs and a linux software raid6. Currently I just have samba setup to share each partition individually, so to store data on the servers, I connect to each one, i.e. //data-01/shared, //data-02/shared, //data-03/shared. Is there a way to "raid" or cluster the servers together so that they would show up to Windows clients as just a single shared folder? I've tinkered with nfs, but I can only have sub-directories (that are really mounted across the network using nfs) under the samba share, and there is still no way for a single dataset to span all three servers.

Is it possible?

---

### Post by arrrghhh on 2011-04-28
Heh, we were just discussing this in [another thread.](http://ubuntuforums.org/showthread.php?t=1740754)

See this [How-to Geek](http://www.howtogeek.com/howto/36458/9-alternatives-for-windows-home-servers-drive-extender/) post.

---

### Post by rubylaser on 2011-04-28
That article covers most of the cluster filesystems that would be useful in this example. But the one that interested me the most from a simplicity point of view was mhddfs in the comments.
[http://romanrm.ru/en/mhddfs]("http://romanrm.ru/en/mhddfs")

This look extremely easy to implement if you wanted to test it out.

---

### Post by arrrghhh on 2011-04-28
> **rubylaser said:**
> That article covers most of the cluster filesystems that would be useful in this example. But the one that interested me the most from a simplicity point of view was mhddfs in the comments.
[http://romanrm.ru/en/mhddfs]("http://romanrm.ru/en/mhddfs")

This look extremely easy to implement if you wanted to test it out.

I don't think this is what the OP is looking for - does mhddfs apply to multiple servers?  Seems to apply to multiple drives, on the same local server.

Does seem slick tho, if that's what you want.  I'm thinking I just need to do LVM on my server, but again that only works locally.

---

### Post by rubylaser on 2011-04-28
It works with mount points, so there's no reason, you couldn't combine multiple mountpoints from various servers and export them.  You could export via ISCSI or NFS from the 3 servers, combine them with mhddfs and export the share via CIFS.

As I said earlier, I've never used this and though it was interesting. I can confirm from personal experience that Gluster or MogileFS will do this fine.  With 99TB to share, I'd be using a real cluster filesystem, I was just thinking about using this with smaller data sets (home servers).

---

### Post by Wej on 2011-04-28
> **rubylaser said:**
> That article covers most of the cluster filesystems that would be useful in this example. But the one that interested me the most from a simplicity point of view was mhddfs in the comments.
[http://romanrm.ru/en/mhddfs]("http://romanrm.ru/en/mhddfs")

This look extremely easy to implement if you wanted to test it out.

Awesome, this worked perfectly. To answer arrrghhh's question, I was already using NFS on the back end to mount the second and third servers in a location on the first server. I was able to then pass those mount points as well as my locally mounted disk and it shows up as a single 90TB device. Then I just shared that device using samba and the Windows boxes can now map that drive and drop their files on there and mhddfs figures out which mount point to drop the actual file. It's pretty ingenious and exactly what I was looking for! The best part is that nothing is split up, so even if one of my raid arrays goes offline for whatever reason, I can just remount my storage pool without that array included and only the data stored on that array will be unavailable until I fix the issue with the offline array.

---

### Post by rubylaser on 2011-04-28
Thanks for the update.  I'll have to test mhddfs out now.  I love finding new tools like this. Just for my own info, if you don't mind running a few tests, what type of read/write speed to you see with this setup both via SMB and with dd tests on the host machine?

---

### Post by arrrghhh on 2011-04-29
Hrm... you guys are tempting me to try this.  I was thinking I should do LVM, but this seems like a lot less work... and almost achieves the same thing.  Obviously there's a lot of flexibility with LVM, but I'm not sure that really matters in my environment.  I don't know if the benefits of LVM would be worth the pain of setting it up :p.

---

### Post by rubylaser on 2011-04-29
LVM is not hard at all, but I've never tried to use it to join multiple exports from different hosts into one large volume.  I guess, I'd probably just do ISCSI or NFS shares to to host, and aggregate them from there.  Just off the top of my head, you could potentially do the same thing with mdadm (I'd have to experiment with that one).

mhddfs seems to be very easy to implement, I'm just wondering how it performs.  Personally, in a professional environment, I'd still be using a proven cluster filesystem to do this task.

---

### Post by arrrghhh on 2011-04-29
> **rubylaser said:**
> LVM is not hard at all, but I've never tried to use it to join multiple exports from different hosts into one large volume.  I guess, I'd probably just do ISCSI or NFS shares to to host, and aggregate them from there.  Just off the top of my head, you could potentially do the same thing with mdadm (I'd have to experiment with that one).

mhddfs seems to be very easy to implement, I'm just wondering how it performs.  Personally, in a professional environment, I'd still be using a proven cluster filesystem to do this task.

Yea, my 'environment' is just a single server at home.  I'm just constantly running out of disk space, and I'm looking at the dreaded 'multiple disk' solution for what I really want just one folder for.

I was hoping to avoid formatting, and it seems this utility will circumvent that.  I'm not sure if I'll need the ability to re-allocate raw space as LVM allows, but I guess it would be nice to be able to logically shuffle things without physically changing anything ;).

---

### Post by collisionystm on 2011-04-29
> **Wej said:**
> I have 3 servers I built, each with 33TB of usable disk space using xfs and a linux software raid6. Currently I just have samba setup to share each partition individually, so to store data on the servers, I connect to each one, i.e. //data-01/shared, //data-02/shared, //data-03/shared. Is there a way to "raid" or cluster the servers together so that they would show up to Windows clients as just a single shared folder? I've tinkered with nfs, but I can only have sub-directories (that are really mounted across the network using nfs) under the samba share, and there is still no way for a single dataset to span all three servers.

Is it possible?

Share just the one and have the others rsync off the main box durring the lunch hour and after hours.

---

### Post by Wej on 2011-04-29
> **rubylaser said:**
> 
Personally, in a professional environment, I'd still be using a proven cluster filesystem to do this task.

What would be a good proven cluster file system for this task? I am new to this stuff, I haven't had to store terabytes of data like this in the past.

---

### Post by Wej on 2011-04-29
> **rubylaser said:**
> Thanks for the update.  I'll have to test mhddfs out now.  I love finding new tools like this. Just for my own info, if you don't mind running a few tests, what type of read/write speed to you see with this setup both via SMB and with dd tests on the host machine?

```

root@data-01:/# dd if=/dev/zero of=/mnt/virtual/testfile.bin bs=1024 count=1M
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 25.862 s, 41.5 MB/s

```

And when copying via the SMB share both directly to the file and through the virtual device created by mhddfs from an NFS connected server, I got the same results copying that 1GB file to my desktop over a 100mbit link. It saturates the link at about 11MB/s. The servers are linked via gigabit on the backend, so it seems like the virtual device can pass data quicker than my 100mbit switch at least.

---

### Post by rubylaser on 2011-04-29
> What would be a good proven cluster file system for this task?
MooseFS or Gluster would be a couple examples.

> root@data-01:/# dd if=/dev/zero of=/mnt/virtual/testfile.bin bs=1024 count=1M
1048576+0 records in
1048576+0 records out
1073741824 bytes (1.1 GB) copied, 25.862 s, 41.5 MB/s

Those are decent with a 10/100 network.  I assumed with massive storage that you'd be using at a minimum a gigabit network with bonded interfaces, so it's hard to see what the potential throughput could be.  Still, thank you for providing the feedback :)

---

### Post by Wej on 2011-04-29
> **rubylaser said:**
> MooseFS or Gluster would be a couple examples.



Those are decent with a 10/100 network.  I assumed with massive storage that you'd be using at a minimum a gigabit network with bonded interfaces, so it's hard to see what the potential throughput could be.  Still, thank you for providing the feedback :)

They're on gigabit, but my workstation isn't linked to them through gigabit. They are storing a lot of map imagery data, and the data is accessed remotely over slower cellular EVDO links, so even the gigabit is overkill. The only reason they even have gigabit is because our GIS expert processes the data from his workstation (which is on the gigabit switch with the servers) and transfers back and forth on a regular basis.

---

### Post by elico on 2011-04-30
you can use ISCSI instead of this setup and make every server as ISCSI node.
then the main server can use 3 ISCSI server using LVM as one storage space.

---

### Post by rubylaser on 2011-04-30
> you can use ISCSI instead of this setup and make every server as ISCSI node.
Yes this will work fine. I should be much faster than ~40MB/s.

---

### Post by Lars Noodén on 2011-04-30
> **Wej said:**
> What would be a good proven cluster file system for this task? I am new to this stuff, I haven't had to store terabytes of data like this in the past.

I've seen [gluster](http://www.howtoforge.com/high-availability-storage-with-glusterfs-on-ubuntu-10.04-automatic-file-replication-mirror-across-two-storage-servers) used in production, though have not used it myself.

---

