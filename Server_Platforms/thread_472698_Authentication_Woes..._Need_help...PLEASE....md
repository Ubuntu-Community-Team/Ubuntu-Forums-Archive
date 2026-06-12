---
title: "Authentication Woes... Need help...PLEASE..."
date: 2007-06-13
forum: Server Platforms
---

### Post by knichel on 2007-06-13
I have wasted many days trying to get my classroom set up. I upgraded my server to feisty in April or early May.  I was using 6.10 on workstations and using NIS for authentication.  All was fine...

When I updated my workstations to feisty, authentication broke.  None of the accounts on the server work on the workstations.  I see the list of users, but none can log in.

I tried to set up ldap.  I got it set up as best I can...
getent passwd returns the list of user accounts local and server.
id usernam returns the ldap info for any user on the server

So, it seems that ldap is working.  

Can someone please help me?  I need my students to be able to log in and creating accounts on all of the workstations is NOT an option I want to explore.  IRC has not offered much help.  I did find a how-to in the forums...
 [https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28pdc%29%7C%28samba%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28pdc%29%7C%28samba%29)

Thanks in advance for any help.
Mike

---

