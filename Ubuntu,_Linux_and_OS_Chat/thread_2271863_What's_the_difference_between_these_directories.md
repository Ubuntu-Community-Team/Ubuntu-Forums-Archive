---
title: "What's the difference between these directories?"
date: 2015-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by KayeNg on 2015-04-02
Hey guys, I don't know if this is the right forum to ask this question but I haven't received any answers in xda-developers, so here goes:

I'm an android veteran but only recently used android kitkat.  

1.  /mnt/sdcard2   ---- and ----  
     /storage/external_SD   -----   
    they are the same, correct?  If I delete the contents of the former, the contents of the latter would be erased? 
    Which means all the files in  my micro sd card will be erased?

2.  /storage/sdcard0 -----and-----  
     /storage/emulated/0   ---and--- 
     /storage/emulated/legacy  --------  
      they seem to be similar with /storage/external_SD  , expect it  does not have the individual files, only folders.  Are they ok to  delete?

3.  /mnt/sdcard  ---------  same with number 2.  Are they ok to delete?

4.  /sdcard ------  same with number 2.  Are they ok to delete?

5. I have a road map application on my phone that forces the map file to be stored INTERNALLY, not on the sdcard.  This was not the case on my old smartphone;  the app can access the map file even if it's saved in the sdcard.

Thank you for your time.

---

### Post by grahammechanical on 2015-04-02
If you remove the SD card you might find that /mnt/sdcard2 disappears. In Linux there is a difference between the mount point of a device and the actual device. If I unmount a partition it does not remove any data from that partition but it does make it more difficult to access the partition.

Just a wild guess.

---

