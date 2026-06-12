---
title: "Samba remote home directories"
date: 2009-11-16
forum: Server Platforms
---

### Post by PinkyTr4ffic on 2009-11-16
The situation is as follows:

I have a samba + openldap server to which clients can authenticate.

Smb.conf:

[Homes]
      comment = Home Directories
      browseable = no
      guest ok = no
      valid users = %S
      
With the above statements i want to be able to log in on the client computer and automatically mount the home share of the correct user.

I have a couple of problems with this situation:

1. When i try to reach the home directory of the user i get the following error:

administrator@Abit:/home$ smbclient  \\\\lodo\\bart -U bart
Enter bart's password: 
Domain=[LODO] OS=[Unix] Server=[Samba 3.3.2]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

2. What are you expected to do on the client side?
    
   Is samba automatically going to mount the home share or do i have to   create a directory for it in the /home of the client?

thx in advance

---

