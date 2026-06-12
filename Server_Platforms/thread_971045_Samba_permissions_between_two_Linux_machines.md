---
title: "Samba permissions between two Linux machines"
date: 2008-11-04
forum: Server Platforms
---

### Post by gravyface on 2008-11-04
Hello,

I have two Linux machines: one's called "filebox01" running Debian Sarge (I know, I know) and the other is my webdev server running Feisty called "webdev01".

On filebox01, I have a Samba share (//filebox01/data) and it's working fine: I have two XP machines with mapped drives that work with no issues.

On webdev01, I have installed smbfs and have mounted //filebox01/data.  No issues... until I went to try to write to it (I'm trying backup my Apache webroot to my fileserver).  

Now, I'm mounting using a user that has write permissions on filebox01 (gravyface) it's the same user I use on my XP mapped drives, which have no problems at all writing to the share.  I guess I'm not sure how shared permissions work with Samba mounts from within Linux/Ubuntu/mount -- I assumed that because my mount user ("gravyface") has write permissions, any user on filebox01 would have write permissions as well.  I've tried SSHing into filebox01 and chmod 777 to the data share and then umount/mount again, but no dice.

Can anyone steer me in the right direction?

Thanks

---

