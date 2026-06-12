---
title: "How to copy a file from an ubuntu partition to a windows (10) partition"
date: 2015-10-28
forum: Server Platforms
---

### Post by Jake_Simmons on 2015-10-28
I`m currently getting help with another problem, however, i need to paste the text document (network.txt) into my windows partition on my machine to show the output i get. if anyone could tell me how to save a text file from ubuntu (server) to a windows partition on the same machine, that would be great. Thanks.

---

### Post by darkod on 2015-10-28
On the same machine? Windows partition?

Are you dual booting a server?

---

### Post by Jake_Simmons on 2015-10-28
yes, i`m dual booting, just want to have a look at how it works. Thanks.

---

### Post by darkod on 2015-10-28
Lets say the ntfs partition is /dev/sda5 and there is a folder in it called shared. To try mount the partition at temporary mount point, for example /mnt, and then copy the file, you could try:
```
sudo mount -t ntfs /dev/sda5 /mnt
cp /path/document.txt /mnt/shared/
```

I think that should work although I haven't tried mounting ntfs in a server for a long time.

---

### Post by Jake_Simmons on 2015-10-28
it seemed happy to mount the partitions but when i tried to copy it returned
```
cp: cannot create regular file '/mnt/Documents/'
```

Also, as a side note, i could use a USB, if that is easier, as i don`t want to leave the other guy waiting!

Thanks again

---

### Post by darkod on 2015-10-28
It's probably write permissions issue. You can try using sudo in front.

USB stick is also a good option especially if you need to change permissions because that way you would be changing them on the stick and not on the ntfs partition.

---

### Post by Jake_Simmons on 2015-10-28
Ok, ill try both Thanks for the help

Ok, i tried again with the putting it straight onto windows thing, and that still didnt work, then i realized, i still have no clue how to get it onto my USB either, so if you could help, that would be great, Thaks Again!

---

### Post by darkod on 2015-10-28
The same, only use the usb partition instead of sda5. You can unmount with sudo umount /mnt

---

### Post by Jake_Simmons on 2015-10-28
i have finally done it, thanks so much for your help, couldnt have done it without you

---

