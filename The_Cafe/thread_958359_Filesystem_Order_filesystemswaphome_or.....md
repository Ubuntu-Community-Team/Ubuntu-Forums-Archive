---
title: "Filesystem Order: /filesystem/swap/home or...."
date: 2008-10-25
forum: The Cafe
---

### Post by BGFG on 2008-10-25
/filesystem/home/swap

Gonna start from scratch with Intrepid. Performance wise, any thoughts ?

---

### Post by Bölvaður on 2008-10-25
If you have 2 hdd then have the swap partition on different one than your /home.

If it is one then it is / , /home, /swap

And perhaps you should have /data partition instead of /home, because when you move to different distro or upgrate, you will not take config from different programs along with you.

---

### Post by iKonaK on 2008-10-25
I have /swap , / , /home .

@Bölvaður : maybe he wants to take config, i do :popcorn:

---

### Post by BGFG on 2008-10-25
My reason for this setup as you guys indicated, is that i'd like to try a sudo apt-get distribution upgrade come 9.04 

So yes, i'd keep the config files and see how the system behaves.
I acutally have 3 drives, my primary, an ext3 media dump and an ntfs taht i never bothered to convert because it works so smoothly. The ntfs isn't too active, can i place an ext3 there ?

I wonder, because i'm not sure if i'll get one contiguous section for my swap.
As for the media ext3 drive, i always have torrents active on that drive so i dont think the swap there would be practical.

One question on /swap /, /home. How does that affect the system booting, if at all? I had read in terms of the disk heads,the swap is best placed on the outer end of the disk. 

thanks guys.

---

### Post by iKonaK on 2008-10-25
> **BGFG said:**
> One question on /swap /, /home. How does that affect the system booting, if at all? I had read in terms of the disk heads,the swap is best placed on the outer end of the disk. 

Boots perfectly fine any where you put it, eighter is on the first partition, the third or, if many, the last. After i upgraded my RAM to 1GiB i haven't used swap at all, only once when i was using VirtualBox but the rest of the time just sits empty :|

---

### Post by BGFG on 2008-10-25
I use VB and have 1 gig ram also. I thinking of upgrading to 2gigs 800 mhz. VB pulls a lot of resources.
Great info. i'll decide on my format once i get my Intrepid iso.

---

### Post by snova on 2008-10-25
> **BGFG said:**
> One question on /swap /, /home. How does that affect the system booting, if at all? I had read in terms of the disk heads,the swap is best placed on the outer end of the disk.

It shouldn't affect booting at all, but that the order matters is new to me. Fortunately I don't go into swap very often (rarely).

I have /, swap, and /home. But if I ever reinstall I'm going to do:


[LIST]
[*]/
[*]/tmp /etc /var /home
[*]swap
[/LIST]
And keep the second and third partitions encrypted. (I'm not sure if this is possible.)

---

### Post by BGFG on 2008-10-25
Yeah,
I think the order matters in terms of performance, but only in cases where you use resource intensive apps.
I'm not as inclined to partition my temp,etc and var folders. Think i'll just allow them all to exist in the filesystem partition. I'm thinking about 13gigs for /.

---

### Post by snova on 2008-10-25
Well, the advantage to my design is that the encrypted partition encompasses not only /home, but also configuration, temporary files, and things used at runtime. This was anything even *potentially* sensitive is encrypted. The only thing left open is installed programs, which are the least of my concerns.

Of course, nothing is encrypted at the moment, but these are my eventual plans. First I have to repartition, since / is about twice as large as I need it to be. And now I've discovered that swap is best at the end of the drive, so I'll move that too.

You learn something every day...

---

### Post by BGFG on 2008-10-25
Don't know if you already googled it but here:

[http://lissot.net/partition/partition-04.html#SwapPlacement](http://lissot.net/partition/partition-04.html#SwapPlacement)

Kinda cool. I plan to do the same

---

### Post by markp1989 on 2008-10-25
my current desktop partiton scheme

sda: 80gb
ext 2 : 25gb : /
ext 2 : 50gb : /home

sdb: 160gb
ext 3 : 160gb : /media/data

i dont have a swap, because since i upgraded to 2gb ram, it wasnt used so i removed it

---

### Post by BGFG on 2008-10-25
I want to go to 2 gigs 800 mhz but i think only at three would i feel safe withoug a swap. VB always takes up some swap as it is right now.

---

### Post by ezsit on 2008-10-25
I've always done

sda1 = Swap
sda2 = /
sda3 = /home

figuring the beginning of the drive is usually faster to access than the interior of the drive. However, with 1-2GB of RAM, the swap almost never gets used anyhow.

---

### Post by snova on 2008-10-25
> **BGFG said:**
> Don't know if you already googled it but here:

[http://lissot.net/partition/partition-04.html#SwapPlacement](http://lissot.net/partition/partition-04.html#SwapPlacement)

Kinda cool. I plan to do the same

I only have one drive, so that's already decided for me. But I don't know anything about disk geometry- what would "outer tracks" mean? The ends?

Oh, and I have 1 GB of ram, and I rarely exceed it- but I keep swap around anyway. Even if I had double that, I'd keep some around.

On the other hand, using that much memory is probably fairly abnormal for what I do, so maybe letting the OOM killer reap such processes is for the better to let me know that something is going wrong.

---

### Post by ezsit on 2008-10-28
> I have 1 GB of ram, and I rarely exceed it

If you rarely exceed your RAM and swap is rarely used, then its placement is irrelevant. No one is going to notice the speed difference of a swap area rarely utilized.

Thanks for the article link. I did not realize that newer drives are faster as the heads move towards the outer edge of the platters, I always thought it was the opposite.

---

