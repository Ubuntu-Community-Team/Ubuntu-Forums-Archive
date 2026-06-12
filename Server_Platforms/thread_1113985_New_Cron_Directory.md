---
title: "New Cron Directory"
date: 2009-04-02
forum: Server Platforms
---

### Post by JimmyJam4PHP on 2009-04-02
My company uses a pxe boot for many of its servers.  We are facing an issue now where we have cron jobs that we want to run on some servers, but not others.  Is it possible to set cron up to run cron jobs in a directory other than /etc/cron.d?  For example, could we set it up to run jobs in /<local drive>/cron.local as well?  Any help is greatly appreciated.

Thanks,
~ JimmyJam

---

### Post by shel-hall on 2009-04-02
> **JimmyJam4PHP said:**
> My company uses a pxe boot for many of its servers.  We are facing an issue now where we have cron jobs that we want to run on some servers, but not others.  Is it possible to set cron up to run cron jobs in a directory other than /etc/cron.d?  For example, could we set it up to run jobs in /<local drive>/cron.local as well?  Any help is greatly appreciated.

I had a similar situation, although it was due to my desire to have the same crontabs on all my machines (SGIs back then), rather than to my using PXE booting.

I used the same crontabs for all the machines, but established various "classes" of machines which controlled which activities actually took place.  The classes had names live "bigserver", "tapeless", and other things like that.  I kept the class names in a file, and had the script (run from cron) or the crontab entry itself "grep" the file to see if the activity was suitable for the machine on which it was running.

I felt that this was simpler to maintain than having any sort of multiple crontab scheme.

-Shel

---

