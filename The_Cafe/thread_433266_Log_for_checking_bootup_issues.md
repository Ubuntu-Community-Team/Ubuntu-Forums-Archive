---
title: "Log for checking bootup issues?"
date: 2007-05-04
forum: The Cafe
---

### Post by mlanza on 2007-05-04
On Ubuntu Feisty Fawn, I have used "update-rc.d mongrel_cluster defaults" to setup my machine to automatically start my mongrel_cluster for a Rails app.  When I bootup and attempt to access my localhost website it is unavailable.  A manual invocation of "invoke-rc.d mongrel_cluster start" solves the issue.  What confuses me is that I can invoke this manually and get the expected result, but I am not getting that result on bootup.

I am wondering what logs I can check that would make it clear what daemons the system attempted to start on bootup and their result, that is, so I could spot relevant error messages if any.  I feel as if I am trying to diagnose the issue blindfolded.  

I have disabled the splash screen from the grub menu.lst file in order to catch a glimpse of it, but no luck.
I have searched /var/log/daemon.log but I see no mention of "mongrel_cluster".

Where can one find what daemons were started/attempted upon bootup (per init.d) and the results?

Thanks.
Mario T. Lanza :confused:

---

