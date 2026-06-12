---
title: "OCFS2 datavolume option"
date: 2006-07-19
forum: Server Platforms
---

### Post by hillrudy on 2006-07-19
I waited for a long time for the datavolume option to mount OCFS2 volumes, but 6.06 server kernel 2.6.15 doesn't have it yet.
I think this is due to old OCFS2 modules; despite Oracle site says to get the 1.2 version (the one with the datavolume option) from oss.oracle.com, Ubuntu has the OCFS2 build version 1.3.3, but old source version, I think.

I'll rebuild the kernel, but 1.2 OCFS2 has been available for more than one year, so why not include it in the next kernel build?

---

### Post by aalmenar on 2007-09-21
I also would like the ocfs2 version on dapper be updated, since 1.1.5 that is available on dapper its kinda unstable(no matter what i do, my nodes fence each other even using heartbeat over bonded interfaces and STP). Also asked on Oracle OSS forums, and they told me to use the last version or at least sionce 1.2.3.

Cheers.

---

### Post by Brazen on 2007-09-21
Though I am typically a staunch advocate of only using the LTS releases for production servers... this might be a situation where you might consider using Feisty, or even waiting till next month and using Gutsy.

You might at least check to see what version is in Gutsy as that version or later should be what goes in the next LTS release (confirmed for release next spring).

---

### Post by Brazen on 2007-09-21
And you could also compile the new version into a deb and submit it to the backports repo.

---

