---
title: "NTFS defragmentation approximate time"
date: 2014-06-09
forum: Windows
---

### Post by mastablasta on 2014-06-09
i know there are people running NTFS for data sharing. i was wondering if anyone knows approximatelly how long a defragmentation would take on a 120GB partition? 2,4Ghz single core CPU, with 4 GB ram if that matters.

---

### Post by Bucky Ball on 2014-06-09
How much of the 120Gb is used and what are you using to defrag? A pretty tough question to answer with much degree of accuracy, actually, as there are a few variables. :-k

---

### Post by mastablasta on 2014-06-10
arround 100 GB data, so that leaves about 20 GB free. i was thiking to use default Windows XP tools on that end. unless there is somehting faster. apparently the partition is very fragmented, though i haven't noticed the slowdown. i bet that is true since it used to be FAT32 filesystem that i moved to new disk (along wiht other partitions) and then converted to NTFS. 

so what can i expect? approximatelly. overnight job? last time i defragmented any drive i did it on 10 GB drive :-) and a 500 GB drive that was almost fresh from factory (preloaded OS) with very little use. so i am a bit out of touch with times and all for these sort of jobs.

i plan to move partitions arround a bit to organise them better, and i think it would be better if they are defragmented first before i do any moving/enlargment.

---

### Post by danielr2 on 2014-06-10
Run XP Defrag a couple of times on that volume. Depending on the fragmentation, Defrag might take a while (couple of hours). Let the first defrag run over night, the following runs should complete much faster. Alternatively, get Defraggler. It will run on XP and does a much more thorough job than the standard XP Defrag. I've used it on my XP Notebook with no ill effects, but as usual, do a backup of the volume just to be on the save side.

---

### Post by Bucky Ball on 2014-06-11
> **mastablasta said:**
> 

i plan to move partitions arround a bit to organise them better, and i think it would be better if they are defragmented first before i do any moving/enlargment.

Essential rather than 'better'. ;)

It will take awhile. Not sure about overnight but it's possible and a good time to do it. I'd go three times, but that's me, and the defrags get slightly faster. You'll see by the gui if stuff still needs to be, or at least can be, moved to free up space. 

I used to use this:

[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

It has more grunt than the XP default defragger. The blurb on that link makes interesting reading. ;)

---

### Post by mastablasta on 2014-06-19
3 long sessions: 2 nights (2x10 hours=20) and about 6 hours during the day - still not half way through on the 120GB partition. turned off the screen saver and antivirus. brand new 1TB disk, but files moved to it from 9 year old disk that was never defragmented. i am not sure what is going on. it takes time to go through the various games. so i Will remove some of them. but there is only about 35 GB of them. hmm..

smaller system disk 30 GB in total took about one and a half hour, although Windows is still showing it as fragmented and in need of defragmenting...but it looks better after first session.

i will free up some more space on the large drive (at the moment it has about 24 GB free).

anyway disk is quite red so no wonder things started to slow down here and there... :-)

ugh i just need to fix this then move and enlarge and then put Kubuntu on part of the disk. i am thinking i still need Windows since most games i kile won't run well  on Kubuntu (already researched the wine).

---

### Post by Bucky Ball on 2014-06-19
Are you using Power Defragmenter, as suggested? More aggressive, efficient and possibly faster. Certainly won't take as long on the second pass for defrag.

---

### Post by mastablasta on 2014-06-19
yes power defragmenter. i have to cancel after night session so others can use the mashcine and then i restart and i see it skips the part that it already defragmented and then continues. but it takes looooong. and worst thing is window sis showing it is still quite fragmented. i wonder if somethign make sit stop working or to run less efficinet. hibernation and suspend is off, screenscaver is off. 

i read diskkeeper is fast but who could tell in my case... i guess it just needs time and maybe osme extra space on partition would also be good.

edit: forgot to mention that it did 30 GB partition with 24GB space take in about  one and half hour on firts pass. in wonder why this seocnd one is so fragmanted. it seems save files form games tkae him the longest and strangely enough even from those installed recently. ah it Will finish it eventulaly and then i Will run it again a few more times ot clean it all up. then it Will be good for another 10 years :P

---

