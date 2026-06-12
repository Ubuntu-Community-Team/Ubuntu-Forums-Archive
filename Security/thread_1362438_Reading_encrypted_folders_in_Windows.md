---
title: "Reading encrypted folders in Windows"
date: 2009-12-23
forum: Security
---

### Post by Achel4Ever on 2009-12-23
I'm having some strange problem encrypting files with ecryptfs. 

I made an encrypted folder on an USB-stick (2GB-NTFS formatted) works perfectly. Also under windows, they're not readable.

My HD exists out of 3 partitions, one partition with windows XP, one with Ubuntu 9.10 and one where I have data (NTFS formatted), so I can easily access them from both Linux and windows. No problems till there. 
If I now create an encrypted folder on the Data partition, exactly the same way as on the USB-stick, umount the directory, the encrypted directory simply disappears.
Now if I boot windows, the directory still exists, and the files in it still readable!! (I used some textfiles for trying) At the end of the file a block that look likes an encrypted file is added, and here and there some strange signs appears in between the perfectly readable text!
If I boot Linux again, also here the directory is visible again, and the files look like in windows.

Somebody knows what is going on here? 

Thanks for your help

---

### Post by Kobalt on 2009-12-23
So far there is no port of ecryptfs for Windows, and to my knowledge none is planed.

---

### Post by insane_alien on 2009-12-23
if you need interOS compatability then i recommend truecrypt for folder encryption.

---

