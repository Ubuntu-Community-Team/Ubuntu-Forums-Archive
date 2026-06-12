---
title: "Need help with Samba and linux groups"
date: 2011-06-14
forum: Server Platforms
---

### Post by b3nny80y on 2011-06-14
I have been struggling with that some hours this afternoon and I can't find a solution...  I already googled that without finding the right solution...

The facts :
- I have my linux server, running specific custom applications, permissions are set for those applications with a local unix groups (I wall call it "myLocalGroup").
- I can't mess with permissions on the application files and folders.
- Users have to logon via terminal session (ssh).
- Samba / Winbind, etc. are installed, configured and working.
- Local users and Active Directory users have to connect to the server.
- Windows users are part of "myADGroup".

Problem A :
- To work accurately, the users must be in the "myLocalGroup".  I must find a way to map the "myADGroup" to "myLocalGroup" so both, Windows users and locally created users can use the application.

Problem B :
- I have to change the Primary Group for the users in "myADGroup" from "Domain Users" to "myLocalGroup".  I can't change it in the smb.conf, it has to be only for the users in the specific group.

Any help will be greatly appreciated!

---

