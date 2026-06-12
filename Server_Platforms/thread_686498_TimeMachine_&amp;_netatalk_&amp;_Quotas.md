---
title: "TimeMachine &amp; netatalk &amp; Quotas ??"
date: 2008-02-03
forum: Server Platforms
---

### Post by Vati-Khan on 2008-02-03
I've just built my "perfect" home server. Or maybe not so perfect .... ?

The server has raid5 with LVM and different partitions for their respective purposes and an additional partition /data  for all my files, fotos , music, video etc. and backup

samba & netatalk fileservers set up correctly and working flawlessly.

so far everything is fine.

now with a little tweak I've set up TimeMachine on my Macs to back up via LAN to one of my netatalk shares. 

Now here comes my problem:

netatalk reports to my macs a disksize of 900GB - which time machine will use up until no free space is left. Only when TM starts to run out of space it will delete old backups and free up space.  Now - **I would like to trick netatalk to give my Macs only say 200GB or so**...

is this possible??

the obvious solution would be to use disk quotas - but they would be valid for the whole partition therefore make problems with my video etc stuff ....

so what can I do ?
I don't want to repartition ... ](*,)
disk quotas - don't work ... :neutral:
different users for backing up different macs so every mac is connected via two accounts - ugly ... :mad:

is there a possibility to apply quotas to a certain directory?? :confused:

I hope you guys can help 

VK

---

### Post by Vati-Khan on 2008-02-06
anyone please ...

---------
DISCLAIMER: I know bumping one's own thread is a no-no. I assure you it only a measure of desperation and won't happen again :oops:

---

### Post by Vati-Khan on 2008-03-03
I've found a solution ...

create a new file - 100GB
```
dd if=/dev/zero of=/data/Timemachine.img bs=10M count=10240
```

make it a filesystem
```
mkfs -t ext2 -b 2048 -v Timemachine.img 
```

insert ist into /etc/fstab 
```
/data/Timemachine.img /data/Timemachine auto loop,auto,rw	0	0

```

mount it
```
 mkdir /data/Timemachine
mount /data/Timemachine
```

share it via SMB, AFP, NFS or whatever - like any other share

now I can mount the Volume read write copy etc. but for some reason TimeMachine is complaining now 

I guess that's gonna be tomorrow's feat


greets VK

---

### Post by bronkeydain on 2008-03-25
Hey Vati-Khan,

Thanks for sharing this information with us. I have a similar setup and might have a play with this next weekend...

---

### Post by jcostom on 2008-03-25
Have you enabled the use of networked volumes for Time Machine?


```
defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1
```

---

