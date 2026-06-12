---
title: "defrag tool for ext3"
date: 2008-09-26
forum: Server Platforms
---

### Post by Vegan on 2008-09-26
I was seeking a defrag tool, that can optimize my disk so that Apache can run more expediently. Searching Google did not find much.

I am using the default ext3 file file system.

---

### Post by kino6113 on 2008-09-26
i would be interested to know if such a thing exists in linux,

 as there file systems differ greatly from windows. in linux its more like a bookshelf. when you take a big book out it leaves a space. you can put one big book back or a few small books. unlike windows it will not take a huge book cut it in half and jam half there and another half at the end. it will find a spot for it to fit in its entirety.

---

### Post by windependence on 2008-09-26
Defragging is probably not necessary on Unix file systems. I am sure you will find some people who disagree with me, but I never do this. In fact ever since ntfs, this really doesn't do much for you in Windoze either. People get crazy about this stuff and nonesense like registry cleaners and such. most of the time, this stuff does more harm than good.

-Tim

---

### Post by Vegan on 2008-09-26
I can tell you that as a user of a wide range of systems from PC to Supercomputer etc. ALL file system will fragment eventually.

Linux does not have any special advantage. A badly fragmented server will run significantly slower as time goes by and more and more updates are installed, web sites posted etc.

---

### Post by fjgaude on 2008-09-26
As far as I know Linux and ext3 really doesn't need or have a defragger tool. The filesystem is not like MSDOS and NTFS which do have and need such.

The only warning is to not fill the drives up past about 90%, or pass the largest single file that is on the drive.

---

