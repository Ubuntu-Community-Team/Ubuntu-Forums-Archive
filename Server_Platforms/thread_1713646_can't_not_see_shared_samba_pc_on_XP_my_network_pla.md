---
title: "can't not see shared samba pc on XP my network places"
date: 2011-03-24
forum: Server Platforms
---

### Post by MatthewEva on 2011-03-24
Hello,

I did set samba server up. 
I just modified only one configuration from default /etc/samba/smb.conf file.
Just workgroup = MSHOME to workgroup = WORKGROUP.
And browseable = yes. 
Beacuse my xp workgroup is WORKGROUP. So I changed as same workgroup name 
both unbuntu and XP. 

But I couldn't find samba pc on network places at XP. 
What's wrong with me? 
I have started smbd and nmbd already. 

There is a ridiculous something. I can access samba at XP only typing \\samba IP address. But why I can't see at network places. 
I REALLY can't figure it out. 

Does anyone has some idea?
Thank you!

p.s) I am using ubuntu 10.04 TL

---

### Post by cariboo on 2011-03-24
You do need to set up some shared folders.

---

