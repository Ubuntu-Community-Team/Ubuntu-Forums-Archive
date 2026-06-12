---
title: "public folders"
date: 2008-03-09
forum: Server Platforms
---

### Post by aknight_sa on 2008-03-09
good day guys,

i am using samba as a domain controller and file server for users on the network... i have a public folder for everyone to dump and share files.. my question here is how can i keep the folder shared for other people to share files but at the same time i want to make sure that noone except the owner of that file can modify/delete it?.. i have been playing around with the permissions but wasnt able to achive this.

here is the public folder definition in smb.conf

[public]
    comment = Public Folder
    path = /home/public
    public = yes
    writable = yes
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nogroup



thanks

---

### Post by aknight_sa on 2008-03-10
help.. anyone??

---

### Post by mattalexx on 2008-04-14
I would love to see this question answered. Anyone have any ideas?

---

### Post by garfonzo on 2008-04-14
I'd also like to hear the answer to this. I'll be doing the same thing in a few weeks. 

BUMP!

:)

---

### Post by aknight_sa on 2008-04-14
i wasnt able to solve it either.. so i just made another share of the same folder.. then i gave read/write access to certain people.. 
so they write to this other share..
others can only read

---

