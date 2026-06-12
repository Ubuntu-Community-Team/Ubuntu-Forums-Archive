---
title: "Roaming profiles on dual-boot clients"
date: 2008-07-05
forum: Server Platforms
---

### Post by Bwosc on 2008-07-05
I have setup Mandriva Directory Server and now I'm trying to figure out how to mount home directories to dual-boot clients (WinXP, Ubuntu) that the files would be represented similarly in the different OS environments.

Ubuntu mounts user home folder from */home/joedoe*(Desktop, Documents, Pictures, etc...) with NFS, Windows */home/samba/profiles/joedoe* (My Documents/My Pictures/, Desktop, Send To, etc...). 

Does anybody have any experience what would be the best solution to similarly represent folders Desktop and My Documents (/home) in both operating systems?

---

### Post by promodus on 2008-07-05
Not knowing enough about Mandriva Directory Server to tell you specficis.
Are these systems connected in a domain?

If Mandria Directory Server is using OpenLDAP to store account information for SAMBA and you're on a domain you'll want to set your sambaHomePath and if required create symlinks to map the same directorys between My Documents, Desktop, Send-To, etc.

If this is also for new accounts in the future, modify the skeleton account. In Ubuntu this is /etc/skel, Mandriva may be similar. Mandriva support might have the specific answer on what exactly to change.

---

