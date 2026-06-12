---
title: "Other users not able to view Microsoft Office installed through wine"
date: 2010-12-06
forum: Wine
---

### Post by ssalman.mansoor on 2010-12-06
I logged in as user A and installed Microsoft Office 2007 and it worked. Now I logged out of user A and then logged in as user B, its not showing Office :'( 
Do I need to reinstall Microsoft Office for every user? Or there is any other way around?
Regards,

---

### Post by alaukikyo on 2010-12-06
the wine data is stored in user's specific home folder and sso i think you will have to reinstall msoffice or you could copy the .wine folder from your home folder (press ctrl+h to see hidden file) to the b users home folder

---

### Post by ssalman.mansoor on 2010-12-06
Thanku alaukikyo.
But problem is that it is my LTSP Cluster setup and users authentication on AD and I have over 2000 users which I am trying to migrate from Windows To Ubuntu. This will not only be a difficult administrative task but will also consume lot of storage. :( Is there any way around?

---

### Post by alaukikyo on 2010-12-07
> **ssalman.mansoor said:**
> Thanku alaukikyo.
But problem is that it is my LTSP Cluster setup and users authentication on AD and I have over 2000 users which I am trying to migrate from Windows To Ubuntu. This will not only be a difficult administrative task but will also consume lot of storage. :( Is there any way around?

I think you should use openoffice on all computers and keep a copy os ms office on just one which can help in conversion.
also you could use linux native and cheap softmaker office for linux it has full 100% support for ms file formats

---

