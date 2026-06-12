---
title: "Samba give too much permission rights"
date: 2011-03-21
forum: Server Platforms
---

### Post by sumasage on 2011-03-21
I setup samba config using the Samba Server Configuration GUI.  I added my share, /raidmnt, check box writeable and visible, and give access to boxeee (my boxee account) and nguyenl (my actual user account).  When i browse my machine from Win 7 client it show the raidmnt and i can access it but it didnt even ask for a password.     

So this pretty much mean my files are public on the network.  I want to setup so when i browse to the raidmnt folder, it will ask me for a password.  I messed with this and cant seem to get it to work.

 my smb.conf  
[raidmnt] comment = raid5 
path = /raidmnt writeable = yes 
;browseable = yes 
valid users = boxeee, nguyenl  

Permission for everything raidmnt is nguyenl:nguyenl drwx------  Please help.  Thanks.

---

