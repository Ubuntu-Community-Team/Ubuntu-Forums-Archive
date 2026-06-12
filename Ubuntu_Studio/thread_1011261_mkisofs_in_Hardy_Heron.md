---
title: "mkisofs in Hardy Heron?"
date: 2008-12-14
forum: Ubuntu Studio
---

### Post by NotPhil on 2008-12-14
I had problems creating DVD ISOs after I used the Update Manager to move from Gutsy Gibbon to Hardy Heron. I recently discovered that the problem was with the version of genisoimage distributed with Hardy. 

So, I downgraded to Gutsy's version of genisoimage, and can now make working DVD ISOs, but applications that depend on mkisofs, like DVD95 and xDVDshrink aren't working.

It turns out that mkisofs isn't in Hardy or the Hardy repos, yet apps which needed it were working fine before I downgraded my version of genisoimage.

Does anyone know what's going on and how I could fix this? Should I create a symbolic link to genisoimage named mkisofs? Are there debs of mkisofs floating around somewhere that won't break Hardy? Why did my system think mkisofs was installed earlier?

---

