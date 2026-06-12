---
title: "possible to get cups maxcopies to work on windows?"
date: 2008-07-16
forum: Server Platforms
---

### Post by opportunity on 2008-07-16
Hi all,

I have large toshiba copier shared via cups + ubuntu server and trying to get the maxcopies directive to work for windows clients but it doesnt seem to work cross platform. Is there a work-around?

Ive even tried printing vis samba + cups with no luck.

Is there alternative methods to limit number of prints for a linux or windows printer share if the printer embedded OS is inadequate?

---

### Post by opportunity on 2008-07-16
The issue may be settled by a JobPatchFile inserted into the printer's PPD
which restricts the number of copies by PostScript means to a given
upper limit.

---

