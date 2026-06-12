---
title: "Disk Quota Problem."
date: 2015-01-21
forum: Server Platforms
---

### Post by gardenair on 2015-01-21
I have configure samba server (for testing purpose)  and then implement quota on it. I am facing logical problem in disk quota on user. 

# vi /etc/fstab
 
 
```
/dev/sda4        /office-data               ext4    defaults,usrquota 0 0
```
 
To check that the quota is enable on the partition  or not

```

 
# mount | grep /office-data
 
/dev/sda4 on /office-data type ext4  (rw)

```

Now just refresh the disk label. This means that the command which we give in /etc/fstab is still unknown and it is not till yet implemented .

```
# mount -o remount,usrquota,rw /office-data
/dev/sda4 on /office-data type ext4  (rw,usrquota,usrquota)
```


Now we will create quota files


```
# quotacheck -cum /office-data
```


You can check the quota is implemented or not


```
# ls &#8211;l  /office-data
 
- - -  - - -. 1  root           root      7168    jan       21 08:14          aquota.usr
rwx - - -. 2   root            root      16384  jan       19 09:46          lost+found
rwx r - x. 2   root           pdc      4096     jan       21 04:17          mysamba

```

Now to &#8220;ON&#8221;quota features

 ```
#  quotaon &#8211;auv
/sda [/office-data]: user quota turned on
```

Now implement quota on user

# edquota @-u  smith
 
```
Disk quotas for user smith (uid 501):
  Filesystem         blocks       soft       hard     inodes     soft     hard
  /dev/sda4            4           1024       2048       4        0        0



```


Well the issue is In windows xp on the map the z drive , i right click on the z drive and properties it show capacity 1.00 MB The actual figure for Hard Limit is  is 2 MB which I write in edquota for smith.The question is the soft limit is the capacity which will show in the client computer map drive. For example if I raise teh soft limit 1500 then in windows xp z drive it show me capacity 1.5 MB. 


Please guide me that why it is not showing me 2MB Hard limit  capacity in my windows z drive or it also show the soft capacity.

thanks
gardenair

---

