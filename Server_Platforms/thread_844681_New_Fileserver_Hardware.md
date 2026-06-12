---
title: "New Fileserver Hardware"
date: 2008-06-29
forum: Server Platforms
---

### Post by Tycho7286 on 2008-06-29
Hi Everyone.
I am in the process of building a file server for network.
It will run on 2 Networks through 2 different NICs:
Firstly on my home Network of 5 Computers communicating with GB Lan
Second a business network of roughly 100 computers at 10/100. (I live onsite).
The disk configuration will be as follows:
PATA0 Master: 10 Gig Swap
PATA1 Master: DVD Burner
SATA0: 250 Gig OS Drive
SATA1-3: 3x500 Gig drives in RAID 5 = 1TB
SATA4-7 (on card) Open for RAID expansion.
I was planning on using 7.10x64 (Gutsy Desktop) as the os (is this a good choice)?

The processor I have in this machine is an Athlon X2 soc939 but the motherboard will only recognize one of the two cores. How much difference would it make if I upgraded the motherboard? This system will basically only be a data storage server.
Finally, how much RAM should i put in this system?
Thanks

---

### Post by nix4me on 2008-06-29
I would use the newest ubuntu 8.04 version, no need to use the older version.  As far as ram, i would think 2gig minimum.  I have 4gig in my machine but i never even come close to using 2gig, even with a couple virtual machines running.  As far as recognizing both cores, no clue, thenew version of ubuntu should.  If not, try google, might be a bios thing or something.

---

### Post by PilotJLR on 2008-06-29
I would pick a cheaper / lower-power consumption CPU, like an old Celeron... but if an X2 is on hand, it would certainly work!

Minimal RAM is necessary for just file serving. I'd do 512MB, cause it's very cheap, but you could easily get away with less.

I'm not sure why you'd want a 10G swap drive... this is nothing more than a bottleneck and a point of failure. Less swap should be necessary, and you don't need a dedicated drive.

Also - the OS and boot partitions should be a RAID 1, with GRUB failback configured. With your existing config, you'd be out of luck if EITHER the swap or SATA0 drives fail. If you RAID 1 both swap and OS/boot, then you'd be safe.

---

### Post by Uluen on 2008-06-29
It's impossible to recommend anything without knowing more about your needs.
Will those 100 computer be storing a 4Kb text file every other week or recording HD content to your "server"? ;)

No offense but from your post I get the feeling that you're new to this. How important role will this server have?
Buy a real server from Compaq/Dell/IBM If it's somewhat critical, then someone will come and fix it *when* something goes south.

---

### Post by Tycho7286 on 2008-06-29
Thank you guys for the information you've given me so far.
Just to clear up a few points.

1 The Motherboard is older than dual core technology, that is why it does not support both cores. I ask the question about upgrading because I was wondering if it would be worthwhile / cost effective.

2 As to the purposes of the server, it's primary purpose would be a storage server for my personal files on my home network. The reason I am also putting it on my work network is that I am the only tech on the campus I administer and this campus is roughly 400 acres. there are several servers on this campus for business use, however i would like to be able to access my personal files as well. My server would occasionally be used as a temporary backup point for other peoples documents on the work network, but pretty rarely.

3 A question about Pilot's recommendation. Would it be possible to RAID 1 both OS and Swap with only 2 disks? I thought you were only able to make a single RAID enabled partition per physical disk. Along the same lines, I thought if a SWAP drive failed it could be replaced without any danger to the existing OS / RAID array as long as the new drive had a SWAP enabled partition in the same spot and of the same size on it.

Thanks

---

### Post by PilotJLR on 2008-06-29
You can have multiple RAID partitions per disk, yes.

So it's possible to take 3 drives, for example, and partition them like this:

disk0: 2gb / (RAID1), 100mb /boot (RAID 1), 1GB swap (RAID 1), remainder /storage  (RAID 5)
disk1: 2gb / (RAID1), 100mb /boot (RAID 1), 1GB swap (RAID 1), remainder /storage  (RAID 5)
disk2: 2gb / (hot spare), 100mb /boot (hot spare), 1GB swap (hot spare), remainder /storage  (RAID 5)


Swap can be replaced, yes... but if your swap drive fails while it is in use, the machine will likely crash. RAID 1 on swap allows you to stay up during that failure.

As for an HP / IBM server... I agree that is the best scenario, but it is not always a realistic option. The big 3 server vendors now require SAS as an entry level into hardware RAID 5 (unless you manually setup linux RAID on SATA). Add a Care Pack, and you're talking about a $3500 entry price. 
That's a good deal for a business, but hard to justify for home use or in some budget-constrained operations.

Plus the hardware-independence of linux RAID is pretty useful, should that Care Pack ever lapse!

---

### Post by windependence on 2008-06-30
I have two rack servers running a production web site, mail server, etc. Each of these were built by me using server class hardware. This way you can build WHAT you want instead of taking it in the rear from the big server vendors. This is what I would do......and RAID is no substitute for backup and is not always the best way to go.

-Tim

---

