---
title: "Disk drive for /mnt/hogwarts is not ready yet or not present"
date: 2018-01-07
forum: Server Platforms
---

### Post by meijioro on 2018-01-07
[FONT=arial][COLOR=#111111]**Note:** I'm a hardware and Ubuntu newbie so I may need a lot hand holding.[/COLOR]
[COLOR=#111111][B]
Problem:[/B] I have a RAID 5 that someone (I moved away so they aren't accessible) set up for me. I tried to turn on my server again after moving and now I get the error [B]Disk drive for /mnt/hogwarts is not ready yet or not 
present[/B].
[/COLOR]
[COLOR=#111111]I can see my drive (it's listed under devices as 4.0 TB Volume and there are files in there also when clicking on it the folder name is d5078b38-f7ec-427c-82bf-b2770227415d).[/COLOR]
[COLOR=#111111]
I can see the **hogwarts** directory listed under bookmarks (there's nothing in there). I looked in **/etc/fstab** and see this:[/COLOR]

[COLOR=#ff0000]# / was on /dev/sda1 during installation
UUID=myStringBlahBlah / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=anotherLongStringHere none swap sw 0 0
/dev/md0   /mnt/hogwarts   ext4  defaults 0 0[/COLOR]

[COLOR=#111111]I tried [/COLOR][COLOR=#ff0000]findmnt /dev/md0[/COLOR][COLOR=#111111] but got nothing. If I just do [/COLOR][COLOR=#ff0000]findmnt[/COLOR][COLOR=#111111] by itself I get this.[/COLOR]


[COLOR=#ff0000]TARGET   SOURCE FSTYPE OPTIONS
/dev/pts devpts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000My end goal is to be able to view my videos again on my Plex app.

[/COLOR][/FONT][COLOR=#111111][FONT=arial]My end goal is to be able to view my videos again on my Plex app. [/FONT][/COLOR]:(

---

### Post by darkod on 2018-01-07
Please post the output of these commands (if running as root don't use the sudo in front):
```
sudo blkid
cat /proc/mdstat
```

---

