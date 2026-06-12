---
title: "Drive reliability and standy mode for servers"
date: 2010-10-13
forum: Server Platforms
---

### Post by joseph.piron on 2010-10-13
Hello everyone !

I have some general question with with quite an impact for the system I use :)
I have a media server with 2 raid1 mirrors of 2 1 To disk aggregated with lvm and used by a big 2 To ext3 partition.

A few days ago, munin (awesome!) started to send me notifications about smart attributes of some disks, and i'm not quite worried... :KS

Fyi, here's my hdparm.conf:

/dev/sda {
 spindown_time = 54
}

/dev/sdb {
 spindown_time = 54
}

/dev/sdc {
 spindown_time = 54
}

/dev/sdd {
 spindown_time = 54
}

So the question: regarding reliability and disk longevity, is it recommended to have them spin down while not used (most of the day, as these are storage unit for movies, pictures, documents..) or let them spin whatever.. ?

Those are WD green and according to Tom' Hardware, the consumption is only slightly greater in idle compared to standby.

The other question, (boat one as we say in french :)) what is the best configuration here ? My 2 raid 1 stripes, or a raid 5 ? I know that two disks kill the raid 5, and they have to be of the same stripe to kill the lvm on the raid1, but what are the odds ?

I would really appreciate your opinion and knowledge on this!

Thanks in advance :guitar:

---

