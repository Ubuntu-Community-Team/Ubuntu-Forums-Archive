---
title: "samba - create public folder (no auth) and user folder (auth)"
date: 2008-01-01
forum: Server Platforms
---

### Post by Opsive on 2008-01-01
Hello,

I am running Ubuntu server 7.10 and I have setup samba and that went fine.  But I am editing the smb.conf file and here is what I want:

1. One directory called public that the user does not need to login to
2. The user directories to show and only the owner of that directory can login
3. A directory that isn't specific to any one user but only a list of users can login, and is not public

Is this possible?  I have been able to modify the smb.conf file so that number 2 works (by uncommenting the homes directory).  But if I try to get number 1 to work by adding 

[public]
   comment = Public folder
   path = /home/public
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777

this causes only the public folder to work and the user directories don't appear anymore.  I haven't been able to get number 3 to work at all.

I am setting security = share (because I don't want to have to login when you initially access the server), is that correct?

---

### Post by andol on 2008-01-01
II'm no expert at Samba, but somehow my gut tells me that "security = share" might be the problem. How about trying with "security  = user". instead? If nothing else, just for debuging.

---

### Post by rsw686 on 2008-01-01
Try the following

   security = user
   map to guest = Bad User

[public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  force user = public
  create mask = 644

[homes]
   comment = Home Directories
   browseable = no
   writable = yes

[group]
  comment = Group Folder
  path = /home/group
  public = no
  writable = no
  force user = group
  create mask = 644
  write list = bob joe sally

---

