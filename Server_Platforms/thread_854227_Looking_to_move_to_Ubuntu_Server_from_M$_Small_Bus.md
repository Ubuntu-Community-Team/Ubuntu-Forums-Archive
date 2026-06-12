---
title: "Looking to move to Ubuntu Server from M$ Small Business Server"
date: 2008-07-09
forum: Server Platforms
---

### Post by xanimal on 2008-07-09
We are in the process of upgrading our network with new workstations and a new server. Currently we have a M$ Small Business server acting as a file server. I would like the new server to be running with as a domain, using user authentication, file sharing with user Auth, roaming profiles, and such but using Linux instead. All the workstations will be running XP. I'd love to convert everything to linux but we are going to Quickbooks Enterprise (dumping DACEasy) and I have not seen an easy way to get it to run on linux, if at all. 

Is there a way to handle Windows Domains and user permissions for XP with Ubuntu? Can this be done?
Thanks for the help!!

---

### Post by shizakapayou on 2008-07-09
I'm in a similar position, though my company doesn't have any servers in place yet.  I think you'll find this thread useful:

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

So far I've used it to setup a domain controller and join some XP machines to it.  Ironically joining Ubuntu machines has been a bit more of a chore, but it'll get there.

---

### Post by windependence on 2008-07-09
Check out these articles:

[http://support.quickbooks.intuit.com/support/pages/knowledgebasearticle/1000759](http://support.quickbooks.intuit.com/support/pages/knowledgebasearticle/1000759)

[http://quickbooksenterprise.intuit.com/resources/linux.jsp](http://quickbooksenterprise.intuit.com/resources/linux.jsp)


-Tim

---

### Post by bmathis on 2008-07-09
Use ebox ([http://www.ebox-platform.com/](http://www.ebox-platform.com/)) it'll do all that you have asked, plus. I've set it up at 3 non-profits in my town and have had very few issues with it.

---

### Post by cariboo on 2008-07-09
Samba documentation would be a big help too:

[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

Jim

---

