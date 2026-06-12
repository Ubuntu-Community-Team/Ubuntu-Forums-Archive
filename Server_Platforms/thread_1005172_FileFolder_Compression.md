---
title: "File/Folder Compression"
date: 2008-12-08
forum: Server Platforms
---

### Post by Drezard on 2008-12-08
I know that windows has file/folder compression and I think it works great if you have a massive sized file server I can at least shrink the data down to 85%ish. Which when your running a file server of 5TB, its a good 750GB. 

I'm wondering whether there's a Linux alternate to the windows file/folder compression, that doesn't involve tar and untar'ing every file modification.

Daniel

---

### Post by lykwydchykyn on 2008-12-08
I don't know of anything exactly analogous since ext3 doesn't support filesystem compression without a (unofficial and beta) patch. 

You might want to look at [avfs](http://www.inf.bme.hu/~mszeredi/avfs/), though I'm not sure immediately how to make use of it.

---

### Post by insane_alien on 2008-12-08
i think there are some FUSE fileystems that will allow on the fly compression but i'm not sure how good they are and i think throughput is quite poor.

---

