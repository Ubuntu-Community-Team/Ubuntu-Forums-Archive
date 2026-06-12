---
title: "What Partition &quot;Block Size&quot; is better ?"
date: 2007-11-02
forum: The Cafe
---

### Post by medya on 2007-11-02
hey I just found out , unlike windows, in linux you can have variable block sizes...

and I found out the bigger your block size be , the bigger your partition cn be .. (am I right ?)


what block sizes are availbe in linux partion  formats and each one is good for what ?


I guess a large block size is good for a partition which has Big Files in it 
(like DVD movies)  and it would access it faster

and for a partiton full of Programs  (binary) you better have smaller block size ...

thats what I guess... I havent found a book or something to read ...

what do u think about block size ?

---

### Post by LaRoza on 2007-11-02
If you use EXT3 with the defaults, you will have a good setup.

-You can have variable block sizes in Windows formats.

---

### Post by anaconda on 2007-11-02
ext3 can have 4 different block-sizes. 1k, 2k, 3k and 4k

And even the 4k block size is quite small so I dont think it really matters which you use.

The max partition sizes of ext3 fs are
2TB-8TB debending of the selected block size. So if you have bigger than 2TB partition then, you have to select bigger block size.

---

### Post by medya on 2007-11-02
I heared Bigger Block Size, uses more cpu but it is so much faster in accessing -reading and writing-

by the way what is the Fat32 and NTFS default block size ?
and how can you change them ? I don think u can change block size in windows parttiion

---

### Post by anaconda on 2007-11-02
fat32 has a 32k block size (for big partitions)

and the default blocksize of ntfs is 4k, but If I remember correctly it can be selected when you format a partition. and you can make it even as big as 64k. 

I dont think that you can change the block size of fat32, ntfs or ext3 partition without destroying data, but you can reformat and select a new blocksize when formatting.

hmm. sounds strange that bigger blocksize would use more cpu. I would think that it uses less cpu, but a LOT more harddisk space... Because with big blocks you waste a lot of space..

---

### Post by Polygon on 2007-11-02
if you have a bigger block size, if you have a bunch of small files your actually wasting space as only one file can occupy a block (i think they are called sectors however..not blocks)..so if you have like a 1 kb file and 4 kb block size...then the 1kb file uses up that block/sector/whatever and nothing else can use it, so youve just wasted 3 kb. etc etc

but even 4kb is pretty  small so i dont think anyone needs to worry about it

---

