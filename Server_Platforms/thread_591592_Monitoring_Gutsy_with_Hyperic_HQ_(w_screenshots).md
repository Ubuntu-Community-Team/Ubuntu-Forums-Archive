---
title: "Monitoring Gutsy with Hyperic HQ (w/ screenshots)"
date: 2007-10-25
forum: Server Platforms
---

### Post by porkrind on 2007-10-25
Just wanted to let folks know that HQ supports Gutsy. You can see a few screenshots here:

[http://www.hyperic.com/blog/hyperic/2007/10/24/hyperic-hq-and-gutsy-gibbon/](http://www.hyperic.com/blog/hyperic/2007/10/24/hyperic-hq-and-gutsy-gibbon/)

And here's the official announcement:
[http://www.hyperic.com/blog/hyperic/2007/10/25/hyperic-first-enterprise-systems-management-vendor-to-support-ubuntus-gutsy-gibbon-release/](http://www.hyperic.com/blog/hyperic/2007/10/25/hyperic-first-enterprise-systems-management-vendor-to-support-ubuntus-gutsy-gibbon-release/)

To set it up, it's a pretty easy command-line install. One problem that I did have, however, is that postgres, which is our default backend DB, was giving me SHMMAX errors, for some reason. I uninstalled + reinstalled, and then it worked fine.

In the blog post above, I noted running into domain lookup lag issues, and I was able to document that with HQ. 

-John Mark
[http://www.hyperic.com/](http://www.hyperic.com/)

---

