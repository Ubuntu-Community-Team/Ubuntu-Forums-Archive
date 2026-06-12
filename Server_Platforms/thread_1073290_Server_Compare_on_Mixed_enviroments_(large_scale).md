---
title: "Server Compare on Mixed enviroments (large scale)"
date: 2009-02-18
forum: Server Platforms
---

### Post by icq70610 on 2009-02-18
Hi All, 

Ist not a total Ubuntu related Question however Ubuntu has the main part in our server landscape (combined with Debian), 

For years we are struggling to get the system setup into a single shape. We use a self build installation process, together with and automated update system (from a separated build / repository system ). As for Software reasons there are as well Solaris systems in the landscape. Over time and regardless of the effort we drove into the systems come out of sync. And we can not rebuild them each time, the application is just to complex, as well we are running 24/7 -- People change permissions, on local file systems, files are not kept up-todate or redistributed only to certain servers, (after the a failover the system than hangs as settings are not there etc) This is going on for months. Finally a separated group has been established in order to get this somehow under control. 

As anybody ever heard of a application which actually compares Server Setups? E.g 

On Solaris / ubuntu using various tools to gather system configuration, checking, entries of system files, permission settings on specific directories, is a directory a real directory or is it a link. Number of max open process etc. 

Im now that comparing diff Unix flavors gets kind of tricky but I like to start with a existing application, before I redefine the world and rebuild the whole scheme from sratch just to finds in 6 months someone has already done it &#61514;

Any Ideas?

Thanks

Joe

---

