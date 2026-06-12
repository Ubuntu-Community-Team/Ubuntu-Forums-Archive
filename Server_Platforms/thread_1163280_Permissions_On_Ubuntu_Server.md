---
title: "Permissions On Ubuntu Server"
date: 2009-05-18
forum: Server Platforms
---

### Post by roystreet on 2009-05-18
Hello,
   I have a ubuntu file server up & running.  It's a small home network.  All windows users can view & edit the shares I've made.  Great!  Now my problem I'm having is limiting certain folders to only specific users.  Right now if someone opens up one of the shares they are doing if via the administrators log on.  So they have full permission to do what they want with the folder or files.  I currently setup permissions & configure my server via webmin which is a very, very good product.  I do all modifications I mention below via webmin.

  The problem is when I create a new system user I'm not 100% sure what groups to add them to.  I know that I not only have to limit access on the shares I create, but also in the system files themselves.  So I want a user to have editing access to most of the folders.  I want them to use the shares under their own username.  When I've created another user in the system what permissions do I give them so they can access folders? Is there a way I can completly do this via webmin?  I don't see where webmin shows me how to give specific system permissions to a folder.  I only see samba permissions. 

Thanks,
~roystreet

Quick Note: Most of these folders 'sit' on NTFS partitions. If this makes a difference.

---

