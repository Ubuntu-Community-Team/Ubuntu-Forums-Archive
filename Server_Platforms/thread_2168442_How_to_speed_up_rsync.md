---
title: "How to speed up rsync?"
date: 2013-08-17
forum: Server Platforms
---

### Post by MakOwner on 2013-08-17
I am copying about 12TB of daya from one server to another using rsync via ssh.  At best I can get  9.25MiB over the link according to bmon on both sides of the link.
I issue the rsync command using nice -15 and that's what got me to 9.25 up from about 8.5 before.

I'm pushing this over a bonded pair of 1GB NICs on both servers and I can get other applicaitons to push data at much higher rates - 40 to 60 MiB depending on where on the source the file sits - I suspect most of the time I'm hitting an upper limit on the ability of the source server to read from a software RAID5 array on 5900RPM SATA disks on an eSATA link. The system load on both sides is neglible.

So, at this point, I have been copying data for about 3 days and I'm just over a 25% through. 

Would I gain throughput by breaking the round-robin bond and going to a direct connect crossover between two NICs and use jumbo frames?  Or is rsync via ssh just that big of drag on the transfer that it won't help?
I'm almost at the point of just trying to do NFS over a crossover with jumbo frames -- I have done that before on other hardware (completely differnet everything though) and been able to reach close to saturation point on a 1GB NIC.

What I'm doing is working, but the wait time is killing me...  Any suggestions to make this go faster?

---

### Post by hawkmage on 2013-08-17
For the initial copy of large amounts of data it is best to do it via NFS, the overhead is much less and you can increase the number of NFS threads on both systems to max out the systems disk and network IO.

---

### Post by CharlesA on 2013-08-18
The slowness comes from the encryption. If you have that much data you can either reduce the level of encryption used or use something else like NFS for the initial sync.

See here:
[http://serverfault.com/questions/377598/why-is-my-rsync-so-slow](http://serverfault.com/questions/377598/why-is-my-rsync-so-slow)

---

### Post by nerdtron on 2013-08-18
1GB NIC with only 9.5MB/sec. Quite slow as I can reach 50MB and up from network transfer.
Anyway, some pointer from me:
All all the swicthes that the data passes from server to server all have gigabit interfaces?
Also, the transfer rate of "a lot of files with small file sizes" is significantly slower than "a few files with large file sizes".
The encryption really is a bottleneck. 
Also see this for other alternatives in transferring files over the network. [http://intermediatesql.com/linux/scrap-the-scp-how-to-copy-data-fast-using-pigz-and-nc/](http://intermediatesql.com/linux/scrap-the-scp-how-to-copy-data-fast-using-pigz-and-nc/)

---

### Post by markbl on 2013-08-19
> **MakOwner said:**
> I am copying about 12TB of daya from one server to another using rsync via ssh.
Perhaps try rsyncing directly via rsync protocol (i.e. rsync to/from rsync://) rather than over ssh?

---

### Post by mcapaldo on 2013-08-19
Have you tried using ftp to transfer data?

---

### Post by MakOwner on 2013-08-21
I just went ahead and moved to NFS and was able to push 40 ~ 60 MB/s across the link and synced up that way for the restore.  

So now that I have my data back where I want it, I want to set up a more automated backup process than I had before.

I am looking at rsnapshot and just striaight rsyncd.  

I tried rsyncd first, and it looks pretty straight forward - I have the rsyncd daemon responding to a remote query at the very least.
I can' find any CLI examples for backup TO the rsyncd daemon - only commands to read data from the rsyncd daemon.

I'm using this: [http://nwlinux.com/how-to-configure-and-ubuntu-rsync-server/](http://nwlinux.com/how-to-configure-and-ubuntu-rsync-server/) for rsyncd setup and the example given is this:

```

A working rsync example within Terminal would be

rsync -avh rsync://bbc.nwlinux.com/bbc /home/mark/Desktop/

The above statement would copy the BBC share of bbc.nwlinux.com to your Desktop.

```


I want to push data from the client TO the rsyncd server.  Have I misunderstood the setup?  The rsyncd should be running on the system to be backed up perhaps?

---

### Post by MakOwner on 2013-08-21
I just went ahead and moved to NFS and was able to push 40 ~ 60 MB/s across the link and synced up that way for the restore.  

So now that I have my data back where I want it, I want to set up a more automated backup process than I had before.

I am looking at rsnapshot and just striaight rsyncd.  

I tried rsyncd first, and it looks pretty straight forward - I have the rsyncd daemon responding to a remote query at the very least.
I can' find any CLI examples for backup TO the rsyncd daemon - only commands to read data from the rsyncd daemon.

I'm using this: [http://nwlinux.com/how-to-configure-and-ubuntu-rsync-server/](http://nwlinux.com/how-to-configure-and-ubuntu-rsync-server/) for rsyncd setup and the example given is this:

```

A working rsync example within Terminal would be

rsync -avh rsync://bbc.nwlinux.com/bbc /home/mark/Desktop/

The above statement would copy the BBC share of bbc.nwlinux.com to your Desktop.

```


I want to push data from the client TO the rsyncd server.  Have I misunderstood the setup?  The rsyncd should be running on the system to be backed up perhaps?



OK, got that figured out -- just in case anyone else is looking -- here is a good config and command examples 
[edit] oops -- I meant this:[/edit]
 [http://www.yolinux.com/TUTORIALS/Rsync.html](http://www.yolinux.com/TUTORIALS/Rsync.html)  

Not that this [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html) wasn't good, I just used the other examples... 





This is a minimal rsyncd.conf file that will let you push data to the rsync daemon with minimal security:
```

max connections = 5
log file = /var/log/rsync.log
hosts allow = 192.168.20.7
hosts deny = *
list = true
uid = root
gid = root
timeout = 60
read only = false

[media]
comment = Media Server Backup Path
path = media/md1/rsyncd_test

```


The command(s) I used:
```

 rsync -avh /home/test/ media2::media

```

and 

```

rsync -avh /home/test/ rsync://media2/media

```


I didn't notice any perceptible performance differences in the syntax, anyone know if there are functional differences that may show up over multiple GBs of data?

---

