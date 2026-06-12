---
title: "Mount Degraded Windows RAID 5"
date: 2009-10-21
forum: Server Platforms
---

### Post by mattmill30 on 2009-10-21
Hi Everyone,

OK, we have a windoze server (I know, i'm sorry), and we came in this morning, to be met with a STOP screen, fun.

Anyway, lots of cursing later, we come to the conclusion that, two of the HDD's out of our RAID 5 array have failed.

Now, one of the drives seems... intermittent, and i was thinking, perhaps its possible to mount the two HDD's into a software RAID 5 on my ubuntu 9.10 box :D.

So i googled, and googled.. had a brew, and then googled some more, and i could find nothing, except this:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Woop!

However, i got half way through, and realised that this is aiming at me creating a new array.. not using my old one :(

So, now i'm confused.

Am i correct in thinking that linux only supports software RAID? (HP told me, maybe i'm just gullible).

If i am, how would i go about mounting the two hard drives, as a degraded RAID 5 array, from a Windows Hardware Controlled RAID 5 array?

Essentially, our entire student data is held on the array, and although we have backups, we've tried recovering from them and yeh... i wouldn't be here if they'd worked :P

Anyway, my plan was:

1) start live session off usb stick.
2) do some magic with fstab or mdadm?
3) mount the RAID as degraded, and pray it holds up, for me to get the database off.

Now, i'm sure this'll complicate the situation to an extreme degree, however, i've been asked not to play with the RAID HDD's, as we might send them off to have the database professionally recovered.

So i thought maybe i could dd the data off them, as single drives, into 2 seperate imgs, then mount the imgs using losetup, and then use them as I would a normal RAID 5 HDD.

So those were my theories :). However, i've not got enough experience with terminal to be able to put my theories into action, so i was wondering if someone might be able to point me in the right direction?

The HOWTO linked above, seemed perfect, until it started talking about formatting the HDD's using the "Linux RAID autodetect".

Essentially, i don't fully understand what this "Linux RAID autodetect" is, and i'm not confident enough that i know what i'm doing to trust myself on live equipment without having done some grovelling for information first. :P

Any feedback would be greatly appreciated

---

### Post by mattmill30 on 2009-10-21
Actually, could someone tell me.

On the guide i found, if i were to just ignore the section about formatting.

Would i be able to see one hard drive in computer, with the original data of all three hard drives?

or do i need to do the "Linux raid autodetect" step?

If i need to do the "Linux raid autodetect" step, would i set all the partitions on ball three drives to "Linux raid autodetect", as its the drives which are configured to RAID 5, not specific paritions.

Or do i just remove the numbers from the mdadm command under "Create the RAID set?" to say that the drives should be the RAID?

If i havn't made sense please ask, because i'm shattered, and so will probably make alot more sense in the morning.

Thanks,

Matthew Millar

---

