---
title: "Building a File Server: The More RAM the Better?"
date: 2011-08-10
forum: Server Platforms
---

### Post by mattlach on 2011-08-10
Hi all,

Essentially I have a quick question regarding ym file server build.

I am throwing together an AMD E-350 based system (chosen for its low power use) to serve as a home file server.

I plan on having multiple PC based DVR's write to the drive array in this server, so I am concerned that occasionally the write speed of the drive will not be sufficient for short peak periods.

I plan on using SAMBA as the file sharing protocol, and all machines are connected together using gigabit ethernet with jumbo frame support.

Is SAMBA able to take advantage of large amounts of RAM to cache writes?

Since RAM is so cheap my plan was to max out the E-350 with 8GB if it truly helpful, but I don't want to if I would just be wasting my money.

Much obliged,
Matt

---

### Post by HermanAB on 2011-08-10
Howdy,

A file server doesn't need much RAM.  Mail servers need oodles of RAM.

Samba is sloooow, no matter what you do.  If you want speed, use NFS.  Yes, Windows can do NFS, but you may have to download and install something.

---

### Post by Skadork on 2011-08-10
you can never have too much ram.  Get it, you may expand, later :)

also, I don't have any problems saturating a 1 GigE link using samba ;)

---

### Post by psusi on 2011-08-10
There is absolutely no need for THAT much ram.  2 GB is more than enough.

Also mail servers don't need any more ram as they are basically just small file servers.  Message comes in, write it to a file.  Client connects to read mail, read it from the file... nothing complicated.

And Samba isn't slow.

---

### Post by server_fan on 2011-08-10
What is the core speed of the processor? For every 1GHZ, I would have **at least 768MB** of ram. 

In other words, 2.5GHZ Dual Core Server would be:

768mb x 2.5 = 1920mb = (Round this up..) = 2000mb

Remember though, this is a Dual Core Server, so take the amount above and multiply that by two: 2000mb x 2 = 4000mb.

Since there are 1024MBs in a GB, then I would simply round to the closest common GB amount, which is 4GB.

Hope this helps,
Server_fan

---

### Post by psusi on 2011-08-10
> **server_fan said:**
> What is the core speed of the processor? For every 1GHZ, I would have **at least 768MB** of ram. 

One has nothing to do with the other.  If you are going to be doing a lot of computations, then you need a fast cpu, if you are going to be working with a lot of data at the same time, then you need a lot of ram.  A file server only needs something like 200mb of ram for the system, leaving you with 1.8 GB for caching files when you have 2gb.  That's way more than enough.  No matter what kind of cpu you have, it is going to be 99% idle if you aren't doing anything but serve files.

---

### Post by server_fan on 2011-08-10
"I plan on using SAMBA as the file sharing protocol" This alone should raise some red flags considering that Samba has a tendency to eat up ram.

My formula is simply based on what I have observed the ratio should be based on computations, but everyone has their own way. :)

---

### Post by redmk2 on 2011-08-10
> **server_fan said:**
> "I plan on using SAMBA as the file sharing protocol" This alone should raise some red flags considering that Samba has a tendency to eat up ram...

Says who?  Care to document that?

---

### Post by mattlach on 2011-08-10
So how much RAM is used for write caching?

Lets assume I put 8GB in the server, and the system uses about 200mb.

Now lets say I start a file transfer to the server over gigabit ethernet (which has a theoretical max speed of ~125Mb/s less overhead)but my array can only write at just above 50MB/s.

Can/will the server use the 7.8GB of remaining ram to write cache my large file transfer?   How much of it will it use?  Is there a way to alter this behavior?

Ideally I'd like to use the RAM as a FIFO buffer, so everything is dumped into the RAM first, and then immediately written to the disk, and purged out of ram as soon as it is written.  I would like to make as much of the ram as possible(even all of the available 7.8GB if possible) for this FIFO buffer.

This way I feel I can avoid any performance issues due to data write spikes.

SAMBA has a config feature for write cache (which is deprecated) and may not even be the type of write cache I am looking for.   Would this be something SAMBA would have to do, or is this something the kernel would deal with when interacting with the file system?

Much obliged,
Matt

---

### Post by server_fan on 2011-08-10
Well for instance, I have a media server setup at the house where we can stream our ripped DVDs and MP3 files over the network. When two or three people begin to stream content, Samba has to serve those files and as it does, its memory usage goes up. Funny is that when ram begins to run low, your in house server begins to act like a Youtube Video running on DSLlite. lol :D

In other words, my setup is specific for my needs, but I was just offering a suggestion. Considering how cheap ram is these days, I think it is better to have more then you think you might need. I've found that my ratio seems to work when I build systems, but not everyone has the same results.

---

### Post by server_fan on 2011-08-10
@mattlach Nice computer setup BTW... I bet that desktop is fast.

---

### Post by mattlach on 2011-08-10
> **server_fan said:**
> @mattlach Nice computer setup BTW... I bet that desktop is fast.

Thank you.   It seems to work for me :)  Though the signature is a little out of date.  I'll see if I can fix it (within the confines of the character limit)

---

### Post by psusi on 2011-08-10
> **server_fan said:**
> 
My formula is simply based on what I have observed the ratio should be based on computations, but everyone has their own way. :)

That sentence does not make sense.  Either you observed something ( what? ), or you computed something ( what? ).  "Observed based on computations" is nonsense.

> **mattlach said:**
> 
Now lets say I start a file transfer to the server over gigabit ethernet (which has a theoretical max speed of ~125Mb/s less overhead)but my array can only write at just above 50MB/s.

Your array should easily be able to handle 125 mb/s and more.  You also aren't going to be generating anywhere near that even recording 8 HD video feeds at once.

> **mattlach said:**
> Can/will the server use the 7.8GB of remaining ram to write cache my large file transfer?   How much of it will it use?  Is there a way to alter this behavior?

Yes, it will, but there is no need since you won't be able to exceed the throughput of the disks.

> **mattlach said:**
> 
SAMBA has a config feature for write cache (which is deprecated) and may not even be the type of write cache I am looking for.   Would this be something SAMBA would have to do, or is this something the kernel would deal with when interacting with the file system?


The kernel caches all disk IO.

> **server_fan said:**
> When two or three people begin to stream content, Samba has to serve those files and as it does, its memory usage goes up.

Define "memory usage goes up".  What process were you measuring, and how much did it go up by?

---

### Post by server_fan on 2011-08-10
> **psusi said:**
> That sentence does not make sense.  Either you observed something ( what? ), or you computed something ( what? ).  "Observed based on computations" is nonsense.



Your array should easily be able to handle 125 mb/s and more.  You also aren't going to be generating anywhere near that even recording 8 HD video feeds at once.



Yes, it will, but there is no need since you won't be able to exceed the throughput of the disks.



The kernel caches all disk IO.



Define "memory usage goes up".  What process were you measuring, and how much did it go up by?

I was measuring the general memory usage of the system when files are transferred, and it does go up when transferring a bunch of files. My personal file server is a LAMP + Samba and FTP. FTP seems to be better on the general speed of the system, and the files move faster, but we are talking about Samba, not FTP. As for the formula, this is something I normally use on desktops... But perhaps it is over-kill for a server. You are probably right, however I tend to be an over-engineer anyway. :)

server_fan

---

### Post by mattlach on 2011-08-10
> **psusi said:**
> 
Your array should easily be able to handle 125 mb/s and more.  You also aren't going to be generating anywhere near that even recording 8 HD video feeds at once.


Thank you, I appreciate it.  Unfortunately my array is far from ideal.  I am currently running a Drobo S.  Dorob's are very sleek little units, but their unique proprietary (boo) RAID alternative which allows for their size mismatching and seamless upgrades, also takes a write time performance hit.   (Had I known this I would never have bought it, but cest la vie)

I have recorded sustained write speeds in the upper 50's MB/s using HDtach when directly connected to my desktop via eSATA.

Currently it is even worse though (and this is why I am building a new server).  My current Athlon server uses a proprietary motherboard and case and has no expansion capabilities. (I bought one of those Dell Zino cubes heavily discounted, starting to wish I didn't.)

My problem now is that the AMD 780 chipset's eSATA implementation refuses to work with port multiplier under Linux, and as such the DROBO will not work.   The only way I have it working now is via USB2, which is a huge bottleneck.   I can only seem to write at about 26MB/s which just so happens to be the practical limit of USB2 once all overhead is taken into account.

I'm hoping the Hudson chipset on Zacate will have better eSATA functionality under Linux, and if it doesn't even a mini-ITX board has one expansion slot for a half height eSATA controller :p

> **psusi said:**
> 
Yes, it will, but there is no need since you won't be able to exceed the throughput of the disks.

The kernel caches all disk IO.


Is there a way to tell the Kernel how much RAM to use for write back cache, vs. other system functions?

Thanks again,
Matt

---

### Post by mattlach on 2011-08-10
> **mattlach said:**
> 
Is there a way to tell the Kernel how much RAM to use for write back cache, vs. other system functions?


also, is there a configuration I need to use to make sure it uses write-back caching, rather than write through cache?

---

### Post by psusi on 2011-08-11
> **server_fan said:**
> I was measuring the general memory usage of the system when files are transferred

How were you measuring is the question.  Keep in mind that you need to look at the count of free ram +/- buffers/cache.  When you are doing a bunch of disk IO, the page cache is likely to grow if it has room to do so, but that does not count as memory used by samba.

> **mattlach said:**
> Thank you, I appreciate it.  Unfortunately my array is far from ideal.  I am currently running a Drobo S.  Dorob's are very sleek little units, but their unique proprietary (boo) RAID alternative which allows for their size mismatching and seamless upgrades, also takes a write time performance hit.   (Had I known this I would never have bought it, but cest la vie)

So you are going to remove the old disks from the drobo and put them in your new server?  Looking back you never did say what disks you were going to use, so I guess I mixed this thread up with another talking about a 3 disk 2tb raid-5 array.

> **mattlach said:**
> I have recorded sustained write speeds in the upper 50's MB/s using HDtach when directly connected to my desktop via eSATA.

This is to one drive?  I thought there was more than one?  Your typical modern TB+ class drive can handle 100+ MB/s, and if you have an array of them, then you can easily handle more than the 125 theoretical max for gigabit ethernet, though you will never get anywhere close to that recording live video without doing a ridiculous number ( 25+ ) of simultaneous channels.

> **mattlach said:**
> My problem now is that the AMD 780 chipset's eSATA implementation refuses to work with port multiplier under Linux, and as such the DROBO will not work.   The only way I have it working now is via USB2, which is a huge bottleneck.   I can only seem to write at about 26MB/s which just so happens to be the practical limit of USB2 once all overhead is taken into account.

What does that matter if you are building a new server?  Ditch the drobo and plug the drives into the server directly.

> **mattlach said:**
> 
Is there a way to tell the Kernel how much RAM to use for write back cache, vs. other system functions?


It uses all otherwise unused ram.

---

### Post by mattlach on 2011-08-11
> **psusi said:**
> 
So you are going to remove the old disks from the drobo and put them in your new server?  Looking back you never did say what disks you were going to use, so I guess I mixed this thread up with another talking about a 3 disk 2tb raid-5 array.

This is to one drive?  I thought there was more than one?  Your typical modern TB+ class drive can handle 100+ MB/s, and if you have an array of them, then you can easily handle more than the 125 theoretical max for gigabit ethernet, though you will never get anywhere close to that recording live video without doing a ridiculous number ( 25+ ) of simultaneous channels.

What does that matter if you are building a new server?  Ditch the drobo and plug the drives into the server directly.

No, I plan on keeping the Drobo.  I am building a new server - in part - so I can have functioning eSATA and not be limited by the ~26Mb/s USB2 connection.

While I am not happy about the proprietary solution on it, and how it limits some speeds, the seamless integration of drives of different sizes, and instant upgrades without rebuilding RAID arrays manually outweighs these penalties to me.

Right now my array contains:

1x 3TB WD Green
3x 2TB WD Green
1x 1TB WD Black

10TB in total.  Any two disks could fail, and I just pop them out and pop any other disk back in, and it recomputes and is good to go.

With this dual disk redundancy I lose the capacity of the two largest disks in the array, which right now means 5TB, but I still have 5TB available.

Its a very sleek, low maintenance system and I like it, particularly the fact that the array can change size without having to copy the data to something else and then copy it back.

When I need my next size upgrade, I'm just going to pop the 1TB drive out and pop a 3TB or whatever the preferred drive size is at the time in.  The array automatically rebuilds without any user input or impact, and the extra space just magically appears in the array.

I feel like ~50MB/s should be sufficient for me, but I just want to add a sizeable write back buffer just in case.

> **psusi said:**
> 
It uses all otherwise unused ram.

My question regarding caching though, has to do with forcing the kernel to use write back cache rather than write through.  is there a way to do this?

Right now from dmesg I have:
```

[     80.322027] sd 5:0:0:0: [sdc] Assuming drive cache write through

```

Is this referring to RAM cache or to the internal drive cache?

If it is RAM cache, I would really like to - if at all possible - force it to use write back cache rather than write through cache.

---

### Post by psusi on 2011-08-12
> **mattlach said:**
> 
10TB in total.  Any two disks could fail, and I just pop them out and pop any other disk back in, and it recomputes and is good to go.

With this dual disk redundancy I lose the capacity of the two largest disks in the array, which right now means 5TB, but I still have 5TB available.

No, redundancy does not work that way.  If you are getting 10tb of usable space with 10tb of disks, then you have zero redundancy, and will loose data if a disk fails.  Redundancy reserves space up front to store duplicate data or checksums.

> **mattlach said:**
> Its a very sleek, low maintenance system and I like it, particularly the fact that the array can change size without having to copy the data to something else and then copy it back.

You can do that with mdadm.

> **mattlach said:**
> My question regarding caching though, has to do with forcing the kernel to use write back cache rather than write through.  is there a way to do this?

Write back and write through are properties of the drive internal cache.  Neither applies to the kernel cache.  It is up to the individual application whether it wants to wait for the data to hit the disk or not ( most of the time, they don't ).  As the cache fills up, samba will start propagating the pressure across the network, slowing down the transfers, which will likely cause the client machine to start buffering up more in its ram.  This will happen slowly at first in an attempt to keep the cache from filling up, and finally will become extreme once there is no more memory.

---

