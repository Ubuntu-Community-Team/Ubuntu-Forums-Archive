---
title: "Ubuntu 18.04 Limits the Loading Speed of nvme SSD?"
date: 2022-01-19
forum: Server Platforms
---

### Post by xlei38 on 2022-01-19
Hi all, we are facing this strange behavior from our server and would really appreciate some help.

Basically we recently added a new M2 nvme SSD for fast IO, and hdparm test did confirm that the cached read speed is ~17 GB/s and buffered disk read speed is ~1.6 GB/s.
Then we tried to load a series of lmdb files (~20G each) into memory for process, the read speed (of the first file) starts out at ~1.5GB/s, but suddenly dropped to ~300M/s after the first ~15GB file was loaded, and that speed maintained for the rest of the task (including loading of later files). We have enough memory, and this happens even if we just load and don't write the data into memory. We then tried to monitor using iotop, it seems as if the loading speed dropped at the precise moment when iotop detects and lists the task, so we are suspecting it's the system that's limiting the IO speed.

I'm wondering is there such automatic throttling mechanism in Ubuntu? If so, how to get around it? If not, maybe you have suggestions of what other things I should look for? I'm more that happy to provide more detailed information if needed.

btw, here is the unlimit -a output
```
$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 257224
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 257224
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

### Post by howefield on 2022-01-19
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by MAFoElffen on 2022-01-19
This is not an Ubuntu Problem, but rather a hardware issue problem that has just started to hit the tech news services last week. I just read an article in the Tech News about this behavior in "some" new NVMe drives... I can't remember who reported it. 

There are several diffrences in NVMe types, and there ratings on what they will be used for. Seems that some brands and models have a problem with their caches... One of the examples was wiht the same compnay, showing a difference in Samsung NVMe drives, in the difference in their cache technology between their EVO and QVO series drives. One is rated beetr for large files transfers and Video Editting. (The higher priced model, of course.)

What it said was the lower model's cache, had great speeds, until the large file size in the transfer, fills the cache to it's maximum, then that rate stalls to a crawl... Still higher than SATA, but at a highly reduced speed.

That's is what I read. It also noted many bargain brand or budget/economy priced NVMe's, you really have to dig into the spec's and reviews on what is relate on how they handle writes on very large files. There are datacenter series NVMe drives, that are rated for handing large file writes... But the costs also follow suit, with their added functionality.

Prices are still falling, as the new wears off.

Where they have great bench marking when dealing with small files

---

### Post by xlei38 on 2022-01-19
I see, thank you so much for the insight! I'll definitely dig into this

if that's the case, could we just break down the large files (22G) to multiple smaller files (say 2G each) and loading them that way? what also baffles me a little is the fact that, since I'm loading multiple of these large files back to back, the loading speed of the following files started at the lower rate, which is not the case for the first file. Is this consistent with the NVME cache problem you mentioned?

Thanks again!

---

### Post by MAFoElffen on 2022-01-20
A majority of people say that with very large writes with SSD and NVMe's that if you disable the write cache, that you can get back to almost full speed on those very large data transfer writes. On the other side of that, some people think turning that off will slow the drives down. I think those are talking about on the smaller files, where the cache would not be filled, and then, would be faster in returning to accept whatever was the next transaction. It has been demonstarated to help with the Samsung Pro, NVMe.

I haven't tested this, so cannot confirm personally. You would have to test this to see if it helps. SATA SSD's are a different set of commands... For NVMe, they are:
```

# Adjust the NVMe's device name to the appropriate drive...

nvme get-feature -f 6 /dev/nvme0n1 get-feature:0x6 (Volatile Write Cache), Current value:0x000001 
nvme set-feature -f 6 -v 0 /dev/nvme0n1 set-feature:06 (Volatile Write Cache), value:00000000 
nvme get-feature -f 6 /dev/nvme0n1 get-feature:0x6 (Volatile Write Cache), Current value:00000000 

```
Tell me how it goes...

Also what seems to help is on large file writes is, just before, you use trim (or on Sansung drives, Samsung Magician Quick Erase), to bypass the garbage collection process in that transfer... to have the system installed on another drive... have the swap on another drive.

If this drive does these kinds of jobs often, then I would add the above to a script. If this disk's primary job is dedicated to this, then I would add it to this disk, as a UDEV Rule:
```

ACTION=="add", KERNEL=="nvme*", RUN+="nvme set-feature -f 6 -v 0 %N"

```
If that does not work... And you split files into smaller pieces, then what you do in between those files, is to ensure you write what is still in the cache to disk, then clear the cache...
```

sudo sync && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches

```

---

