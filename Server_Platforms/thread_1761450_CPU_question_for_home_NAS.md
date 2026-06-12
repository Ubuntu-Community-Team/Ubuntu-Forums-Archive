---
title: "CPU question for home NAS"
date: 2011-05-18
forum: Server Platforms
---

### Post by darkod on 2011-05-18
Hello.

Not sure if the question needed to go under Hardware or Server section.

I am planning to make a home made NAS running ubuntu server 10.04 LTS. Nothing fancy, simple samba with open access for all and openssh for admin access over the network.
The NAS will not have heavy traffic, two home computers with occasional access, just to serve as central location.

I am in doubt which CPU to use and I am after both budget and power saving solution.

1. I have an old Athlon Clawhammer I can use but the TDP of 90W is putting me off. I can also use existing 2x512MB DDR-400 memory with it. The board would be new.

2. I would rather invest in new mini-ITX board with biult-in dual-core Atom D525 (TDP 13W), VGA and Gb ethernet. I would add 2GB DDR3-1333 memory.

Since I would need a new board for the Clawhammer too (current one doesn't have SATA), I am more attracted to option 2.

Any advice? Would the dual-core Atom be enough running this simple home NAS? I think it should but my experience with ubuntu server is limited.

Thanks in advance.

---

### Post by spynappels on 2011-05-18
With the specs you have for option 2, you'll have a rocking little home server. That CPU will not even break a sweat based on your usage description and the 2GB of RAM will allow you to run loads of other services too if you want to.

What hard drive setup were you planning to use? Have a look at mdadm RAID for the actual storage, maybe run the OS on a small hard drive or SSD and have a large RAID array for storage of data.

---

### Post by volkswagner on 2011-05-18
I'd go for the D525 setup.  Sell your DDR-400 on ebay.

The newer setup should be a big performance gain on the AMD setup.

If the board you are looking at has two RAM slots I'd opt to max out the RAM to 4gig.  Your file server won't need it, but if you wanted to play around with VirtualBox, the added RAM will come in handy.

What specific board are you looking at?

I'm happily running SnowLeopard on an older Atom330, so a headless server will happily perform on your proposed D525.

I always say, there's nothing like new!  I just have a bad habit of picking up fixer uppers... LOL

---

### Post by darkod on 2011-05-18
Thanks both of you. I am actually planning to use mdadm RAID1 (software raid) with two 1TB disks. First I considered the WD Green WD10EARS but after finding lots of bad reviews (mostly because they are 5400rpm which I was not aware of) I am starting to change my mind. Other disks which have good reviews seem to be Samsung HD103SJ and I might get two of these.
I was thinking whether to put the OS on the raid or not, but I guess having the OS protected with raid1 couldn't hurt too. My primary objective is the data protection of course.
The board under consideration is Gigabyte D525TUD. And yes, it does have 2 memory slots and that's why I want to buy single 2GB module and leave one slot for future needs.

I guess the next big question is whether to use LVM or not. I have played with it in VB and I generally like the idea. Plus, even though 1TB seems like much space for me right now, LVM would give me an option to add another 2x1TB disks in future without even touching (reinstalling) the OS. Just add them to the LVM.

Any specifics about the filesystem? I have read XFS is very good for large files but this server is for general use. It will have few videos here and there, but I'm not sure using XFS would warrant it. And if it works good with raid1 and LVM.

I guess I might stick with ext4/ext3.

---

### Post by arrrghhh on 2011-05-18
If you're already going to use mdadm, LVM is kinda redundant IMHO...

---

