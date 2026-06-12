---
title: "Sites enabled links work but absolute path names not found"
date: 2011-09-13
forum: Server Platforms
---

### Post by dbahr00 on 2011-09-13
Old Linux server crashed...moving to new Ubuntu server. I have individuals with home directories and that works fine with the public.server.edu\~username. 

I have a directory of /web/public/departments/  with various dept. sites within it.  The urls resolve fine for those in dns and I've enabled within apache2 sites-enabled, i.e., art.server.edu will resolve.

Within the same directory of /web/public/departments/   I have users who have existing links in publications that point to their sites as:   [http://public.server.edu/departments/directoryname](http://public.server.edu/departments/directoryname)

I can add a site with the name of public.server.edu and then I can get to the those sites; however, then the sites that were working that are in the sites-enabled quit working.  I can get one or the other to work but not both.

---

