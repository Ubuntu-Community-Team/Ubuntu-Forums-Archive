---
title: "Can see icons in C drive, but not Z"
date: 2010-08-27
forum: Wine
---

### Post by wierzbicki on 2010-08-27
I installed Wine the other day and now anytime I try to save something into a directory in my Z drive, say, saving a zip file from the intertubes to my desktop, the icon does not appear on my desktop.  If I 'ls' in terminal, I can see the files, but the icon does not appear when I open the directory window as you normally would explore directories in Windows.

However, I can see all icons if I explore my C drive.  Am I missing something obvious that Wine is doing (I am not running Wine while all this is happening), or have I done something I'm too stupid to realize?

I had Ubuntu back in the 6.04 and 7.04 days, and didn't have this problem then.  Currently I am running Ubuntu 10.04 and Wine 1.2.  Thanks.

---

### Post by hikaricore on 2010-08-27
Have you mapped drive Z in winecfg?
You may be assuming that wine is using your windows partitions _[U]which it is not_[/U].
If you have not mapped a Z drive in wine it will not exist.

---

### Post by wierzbicki on 2010-08-27
Sorry, not really understanding what you're saying.

When I open up Wine config, my drive mappings are as follows:

Letter ::: Drive Mapping
C: ::: ../drive_c
Z: ::: /

Thanks

---

