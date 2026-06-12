---
title: "RAID 0 configuration not saved after reboot"
date: 2017-06-13
forum: Server Platforms
---

### Post by yotu-tuy on 2017-06-13
Hello, I have a very similar configuration to this: [https://askubuntu.com/questions/860643/raid-array-doesnt-reassemble-after-reboot](https://askubuntu.com/questions/860643/raid-array-doesnt-reassemble-after-reboot) question, that hasn't been answered. And instead of posting a similar question I though I'd open a forum here.

Basically I set up a RAID 0 array following [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-0-array](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04#creating-a-raid-0-array) this tutorial and everything went fine. 

After that I made sure that if I stopped mdadm the array would assemble afterwards running 
                  - 'mdadm --assemble --scan' it did NOT 
                  - so I tried 'mdadm --assemble /dev/md0' didn't work either. 
                  - finally I tried 'mdadm --assemble /dev/md0 /dev/sda /dev/sdb' which worked. 

Because of those results I checked the /etc/mdadm/mdadm.conf file and modifed the line: ```
#DEVICE devices
``` to ```
DEVICE /dev/sda /dev/sdb
```. after this when trying the previous  commands it worked with the first one. 
BUT after the reboot this is not read, again. and like the question explains the only way to make it 'work' again is to create a new array.... which kind of defeats the point. 

That is a different step I took to try to solve this, but pretty much the question I posted above explains it all.

ANY HELP/SUGGESTION would be greatly appreciated. since I have searched so much and nothing has helped me...

---

### Post by darkod on 2017-06-13
Do you have ARRAY definition in mdadm.conf? It is needed for arrays to be auto-assembled on boot.

---

### Post by yotu-tuy on 2017-06-13
Yes I do. I defined with:
mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf

---

### Post by darkod on 2017-06-13
And do you have separate /boot partition or everything is on the raid0?

---

### Post by yotu-tuy on 2017-06-13
I have a separate partition for the system (it is on an ssd) including /boot

---

### Post by darkod on 2017-06-13
Not sure why it doesn't assemble to be honest. Can you post the output of:
```
sudo blkid
cat /etc/mdadm/mdadm.conf
cat /proc/mdstat
```

Also, in the Digital Ocean tutorial, there is a step to update the initramfs after creating the array. I assume you executed it, right?

---

### Post by yotu-tuy on 2017-06-15
hi, sorry for the late reply. In the end we decided to change to hardware RAID since we had the possibility to do so, but this will bug me until I have the chance to mess up with it again.
of what I can remember when blkid showed all of the disks, including mdX BEFORE reboot but after mdX was not there.
I had the ARRAY line defined in mdadm.conf
as with mdstat it was the same story as with blkid, it showed the disk there before the reboot. 

Sorry I cant show you the actual results, but as I said, we had to move on. So I no longer have the setup.

---

