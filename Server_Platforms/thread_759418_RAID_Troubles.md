---
title: "RAID Troubles"
date: 2008-04-19
forum: Server Platforms
---

### Post by Kissell on 2008-04-19
okay, i had 11 disks in a software raid-5 array, one of which is a hot spare.

a drive failed, and linux automatically used the hot spare and made the raid-5 whole again.

i plugged in a replacement drive and issued the mdadm -add command and it made the new drive the 11th disk that was a hot spare in a healthy array.

all is good right?

except...  this is a test system for me to get familiar with linux...  so I unplugged a disk, to test if it would e-mail me a notification.  

when i unplugged the disk, "YEAH" it e-mailed me... 

ut oh...

the array was supposed to be redundant, mdadm --detail --verbose said it was, and said it also had a hot spare... BUT...  after i unplugged a disk...  it said that another disk failed as well...

I don't know if I believe it...  the disks were all working fine...  I just ran a full sector check for badblocks on every disk a few days ago.

i understand that if a second disk went out after i unplugged the first one and before the hot spare could be synced, that all data would be lost...  however...  the second drive happened to die within minutes of the time i unplugged the first one, and i just tested all drives recently...  

I think it is lying to me.

Is there a way I can tell linux to fix it's obvious mistake, or do i just have to rebuild the array and blow all the data away?  I'm asking, cause under the circunstances....  I think it's lying to me.

---

