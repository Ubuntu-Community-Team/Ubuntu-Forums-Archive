---
title: "Word to the wise when using Samba! Recycle Bin!!!!"
date: 2020-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2020-04-03
Make sure to set up the recycle bin feature. I accidentally deleted the wrong file from my Windows 10 computer on the network share. Now I'm waiting for the vet to email me my dog's vaccination records. It could have been much worse, maybe taxes or the like? The configuration is simple. Here is an example.

This is my configuration at the moment. As I am the only Windows capable computer in the house it is set only for my user. This package should be installed. If not then run this.

```
apt install samba-vfs-modules
```

The tail end of my /etc/samba/smb.conf

```
[server]
 path = /snapraid/pool
 directory mask = 0755
 create mask = 0644
 valid users = jason
 read only = no
 browseable = yes
 vfs objects = recycle
 recycle:repository = /snapraid/pool/.windowsrecycle
 recycle:keeptree = yes
 recycle:versions = yes
```

Restart Samba and it should work. At the moment I had to manually create the folder and chmod it 777 (don't do this normally.) If someone can advise me how to make this proper please do. I likely had to do this as I am using my user, and not root for the share. As this is a home environment it isn't a big deal but not good practice I am aware. Maybe using a group would be better?

Throw in a root crontab to clear the folder after so many days. I set mine with this line

```
00 01 1 * * find /snapraid/pool/.windowsrecycle/ -mindepth 1 -mtime +90 -exec rm -r {} \;
```

And you now have a safe place that will hold files for 90 days or so in case you screw up like I did. Obviously you can set to whatever mtime you wish. I figure if I don't miss it in 3 months, I probably never will.

---

