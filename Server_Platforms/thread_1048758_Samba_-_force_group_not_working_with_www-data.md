---
title: "Samba - force group not working with www-data"
date: 2009-01-23
forum: Server Platforms
---

### Post by supernicko on 2009-01-23
I have the following setup in my smb.conf
```

[myshare]
   comment = myshare
   path = /my/share/path
   browseable = yes
   read only = no
   writeable = yes
   force group = www-data
   read list = user1, user2
   write list = user1, user2

```

However when trying to connect to the share from a windows machine I get the following error: 
> \\machine\myshare is not accessable. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The group name could not be found.

I have found some other threads about this problem which were either unsolved or where the solution was to remove the "force group" option. Removing that option isn't a solution as I need any files written to be of that group.

I've made sure that the users are added to that group on the server, and I even tried adding the group to my windows machine just in case. The file permissions and ownership are setup ok.

I have two other shares (I copied the config of one of these to create this share) where I use "force group = users" and they both work. 

Any suggestions?

ETA:

I changed my smb.conf so that it read "force group = multimedia" (which is the group on the working share I mention) and it will let me connect. I'm not using a domain or anything of that nature, so I am perplexed.

---

### Post by windependence on 2009-01-24
Why are you allowing share access to your document root? Not a great idea on an internet facing server.

-Tim

---

### Post by supernicko on 2009-01-24
> **windependence said:**
> Why are you allowing share access to your document root? Not a great idea on an internet facing server. 

-Tim
I appreciate the concern, however I don't have any internet facing ports open other than for bittorrent. Access to both apache and samba shares is only available from the local net.

Regarding my issue, it is caused by [this bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411") so at least I've got that sorted.

Nick

---

