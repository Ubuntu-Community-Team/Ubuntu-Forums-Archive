---
title: "Moving the OS to a different Drive."
date: 2017-01-04
forum: Windows
---

### Post by Spud37 on 2017-01-04
I have an Ideapad and am adding an M.2 to it. I would like to move the windows installation (even if its a clean reset of windows) I wanna keep the stupid stuff because i have some of the free anti virus though them. I just want to reset it put it and a copy of ubuntu onto the new M.2 SSD, perhaps keep the HDD for storage or just take it out. Any help would be great I had a friend who mentioned acronis but im hoping that i could put in a Ubuntu thumbdrive and copy the one drive onto the other internally. 

Thanks,
Spud

---

### Post by yancek on 2017-01-04
You will need to post which  version of windows you are using as that will make a substantial difference.  You should be able to do this as long as it is still on the same computer but you may have problems with the difference in hard drives.  You need to make sure the boot files for windows are on a primary partition. Also, are you using UEFI or the older MBR.  Posting the output of 'fdisk -l' or 'gdisk -l' would help.

You might be better off trying a windows forum since you are simply trying to move one windows partition to another partition.

---

### Post by howefield on 2017-01-04
Thread moved to the "*Windows*" forum.

---

### Post by Spud37 on 2017-01-04
Its windows 10. Moving from 1TB HDD, to m.2 SSD 512GB. 
I will post the fdisk -l in a bit. It is bound to be UEFI because it is a newer laptop. I wasn't sure about the forum because its both ubuntu and windows 10. I was hoping I could just shrink then copy win10 over, and install ubuntu on the 512GB SSD as well. 


Thanks for the move.

---

