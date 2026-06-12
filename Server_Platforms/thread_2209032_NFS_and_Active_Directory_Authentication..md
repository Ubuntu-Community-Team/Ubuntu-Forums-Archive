---
title: "NFS and Active Directory Authentication."
date: 2014-03-03
forum: Server Platforms
---

### Post by doublez13 on 2014-03-03
So i have a file server set up that is joined to Active directory and uses it for authentication. I joined it the typical way using samba and winbind. I have an idmap_rid backend configured in samba so that a user will have the same UID on all linux computers that they log into. I set it up this way because the file server serves files using both samba and NFS, and the UIDs and GIDs need to match on the NFS server and client. I have it so that when a user logs into a linux computer for the first time, if their home directory (which is NFS mounted), does not exist, then it will create it automatically. I have set this up using pam_mkhomedir. Here's where the issue is. By default, the root_squash option is enabled on all NFS shares, but the pam_mkhomedir tries to create the home directory as root, which then maps to nobody because of root_squash. So changing root_squash to no_root_squash solves the problem, but everyone on the internet seems to say its a bad idea to set no_root_squash. 

I'd love to hear what people have to say about enabling this option, or maybe suggesting a better way to automate the initial home directory creation.

---

