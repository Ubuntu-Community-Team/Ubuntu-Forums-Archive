---
title: "Ubuntu Domain?"
date: 2008-05-16
forum: Server Platforms
---

### Post by alime on 2008-05-16
I have a small organizational and want to have a way of controlling  the users on the network. Is there a way to have authorization, file sharing, printing for Ubuntu clients to a Ubuntu server?

Can you lead me in the right direction?

Thanks,
Aaron

---

### Post by songshu on 2008-05-16
samba for the file sharing and printing to start with.

you can already control user authentication to the shares with samba, but if you want to have it more complicated you can start adding LDAP, KERBEROS to the mix.

i would start with samba and add the rest later if needed

---

