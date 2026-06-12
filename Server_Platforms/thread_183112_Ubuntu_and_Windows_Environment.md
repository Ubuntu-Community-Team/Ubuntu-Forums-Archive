---
title: "Ubuntu and Windows Environment"
date: 2006-05-27
forum: Server Platforms
---

### Post by ddoctor on 2006-05-27
Hi,

I run a home network of 5 WinXP desktop PC's and 2 servers. I have a windows 2000 AD domain controller/file server, and a Fedora 3 router/dns/firewall server.

One of the greatest benefits of the windows DC is roaming profiles - I can use any machine on the network and it looks the same, and all my files are in the same place.  

I would like to move some of the desktop PC's to Ubuntu and would like to keep some features of the roaming-profile system. Does Ubuntu have something similar, to keep user settings consistent between machines?

Current thoughts:

I could run samba on the ubuntu machines to auth against Active Directory and mount appropriate CIFS shares. I assume this should be ok... i.e. user boots ubuntu machine, sees login screen, enter's credentials for their AD account...? Or do I have to sync passwords or something? I guess samba docco has the answers to these, and I should be right to figure this one out myself.

Now, i'm still pretty new to Linux, so I don't understand where/how the user data is stored. I'm assuming this is in, like, /user/username/ or something similar. If so, could I just do an NFS-mount in the user's login script, so that /user/username/ maps to part of the user's profile on my AD server? Or can I do that just by tweaking samba settings?


Am I going about this the right way? Any tips for running Ubuntu workstations with windows file servers would be appreciated.


Cheers,

D Doctor

---

