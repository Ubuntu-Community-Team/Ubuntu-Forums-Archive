---
title: "Samab with multiple users accessing different directories"
date: 2010-04-16
forum: Server Platforms
---

### Post by Bauer17 on 2010-04-16
I currently have samba setup and connecting.  What I am trying to do is have multiple users with access to different directories.  

For example , let's say there are folders A B C on my Linux machine. I want one guy to see A and C and another guy to see B and C and a third guy to see them all.  But I want each user to have access to change delete or execute the files within these directories that they have access to.

Any help would be great.

Thanks!

---

### Post by doas777 on 2010-04-16
create user groups for each of the classes of users. then set gid on the folder to force all new files to have the correct group owner.

---

### Post by Bauer17 on 2010-04-16
> **Bauer17 said:**
> I currently have samba setup and connecting.  What I am trying to do is have multiple users with access to different directories.  

For example , let's say there are folders A B C on my Linux machine. I want one guy to see A and C and another guy to see B and C and a third guy to see them all.  But I want each user to have access to change delete or execute the files within these directories that they have access to.

Any help would be great.

Thanks!

Could you go into a little more detail on both the file permission/user group settings with ubuntu and how to lay the smb.conf file out.  Sorry I am new with ubuntu. 

I am looking to set up 1 directory for music (MP3's for the family).  Then have each member of the family have their own directory that only they can make changes to.

Thanks!

---

### Post by Letrazzrot on 2010-04-16
I am new to *nix as well, but using the info found here
 [http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/)
along with other random sources, I managed to cobble together this:

```
netbios name = NBNAME
guest account = nobody
#security = share
map to guest = bad user
[homes]
comment = Private Directories
valid users = %S
read only = no
browseable = no
[public]
comment = Public Data
path = /share
read only = No
guest ok = Yes
force user = miner
force group = users
[backup]
comment = Backup
path = /backup
read only = Yes
valid users = shamus
browseable = no
```Basically it allows each user I add to the server to have their own /home (private) directory (password login), a /share directory for everyone (this is where I keep music and pictures for everyone, anyone can log on without a password), and a /backup directory accessible only to the user shamus (another password login).

It looks like I tried security=share first, but commented it out.  I am assuming that security=user must be the default.

The link I gave gives some explanation about the options, and how to add the users to samba.

Hope it helps!

---

### Post by Bauer17 on 2010-04-28
> **Bauer17 said:**
> I currently have samba setup and connecting.  What I am trying to do is have multiple users with access to different directories.  

For example , let's say there are folders A B C on my Linux machine. I want one guy to see A and C and another guy to see B and C and a third guy to see them all.  But I want each user to have access to change delete or execute the files within these directories that they have access to.

Any help would be great.

Thanks!

Does anyone else have any insight to this?

Thanks!

---

