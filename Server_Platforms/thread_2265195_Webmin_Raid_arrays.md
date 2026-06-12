---
title: "Webmin: Raid arrays"
date: 2015-02-13
forum: Server Platforms
---

### Post by jake53 on 2015-02-13
Hello everyone
 
I am having issues with webmin. On my HP ML350 G5 server I have installed Ubuntu 14.04.1 and accidentally managed to merge my raid 1 and raid 5 array by adding it to the file server- VG file. I think this was an accident or is this what I am meant to do? I have completely reinstalled Ubuntu to try and solve the issue.
Also how do I access the raid 5 array? I can&#8217;t find any folders for the array.
Thanks

Ps if you need any more screen grabs just ask.
[ATTACH=CONFIG]259952[/ATTACH][ATTACH=CONFIG]259954[/ATTACH][ATTACH=CONFIG]259953[/ATTACH][ATTACH=CONFIG]259951[/ATTACH]

Also I keep getting:

[h=3]Failed to save volume group :  Device /dev/cciss/c0d11 not found (or ignored by filtering).[/h]

---

### Post by darkod on 2015-02-13
First, this seems like hardware raid, created with the HP raid card (or onboard raid, which ever). Usually with linux server you would use linux software raid (mdadm).

When you say VG, is that Volume Group? Are you using LVM?

If you added anything into the LVM by mistake the correct way would be to try to remove it from the LVM while there is still no data on it (no extents are used). But by reinstalling you probably lost that chance.

If your server only had raid1 and raid5, where did you reinstall ubuntu? Does it have other disk(s) apart from the raid?

---

### Post by MAFoElffen on 2015-02-13
Yes, I recognize HP SmartRaid as hw RAID. But... Not at home at the moment, so I can boot up that server. As I remember, doing blkid on them (or in a partioner), the SmartArray logical members don't show as /dev/sdX. They show as ccis something...

But logically, yes you can do things like that (LVM) whether it's software or hw RAID. Just like you can take mdadm and combine logical containers into something else. Logically, with LVM, you can combine one extent to another... It will work-- but why do it? Sort of defeats what you usually do those for by mixing the types right?

---

### Post by jake53 on 2015-02-18
Sorry for not responding.
I used HP raid not linux raid

VG is volume group. Im not sure about using LVM or I dont know if I have

There are no other hard drives apart from the raid arrays.

Raid 1 contains two disks for ubuntu 14.04

Raid 5 is 3 disks for the main storage.

Hope this helps

---

### Post by darkod on 2015-02-18
Can you login to the server using ssh and post the output of the following commands:
```
df -h
sudo pvdisplay
sudo vgdisplay
```

I know webmin is interesting to some people because it's GUI interface, but I think you should try learning using the command line too. Plus I have read somewhere that sometimes webmin does the settings in its own way which in the long run can even mess up the server. Maybe this issue wouldn't have even happen if not using webmin because the command line helps you avoid drag&drop, wrong click and similar mistakes...

---

### Post by jake53 on 2015-02-18
I havent setup ssh does it have to be via ssh ?

---

### Post by jake53 on 2015-02-18
Here you go

---

### Post by darkod on 2015-02-18
Did you have any important data on the raid5 array? Or you are still setting up the server and it was empty?

---

### Post by jake53 on 2015-02-18
Nope its all empty

---

### Post by darkod on 2015-02-18
In that case I think it's better you start from scratch. Just reinstall ubuntu on the raid1 array, and use the raid5 for data with or without LVM. You actually don't need LVM especially if you are not planning to expand storage later. You can make the 2TB raid5 a single big data partition, and a mount point for it anyway you want, like /data for example.

Since you have no data to rescue, I think that's best. Webmin probably is using LVM for Logical Volumes option it shows on your first images. So unless you want to use LVM you don't need to create any logical volumes in that tab.

---

### Post by jake53 on 2015-02-18
ok thanks

---

