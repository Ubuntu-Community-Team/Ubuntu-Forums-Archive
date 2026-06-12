---
title: "apt-file fails to find everything due to missing Contents-&lt;arch&gt;.gz"
date: 2007-03-04
forum: Repositories &amp; Backports
---

### Post by Cruncher on 2007-03-04
Hi.

apt-file is a very powerful tool to find the package a certain file belongs to.
However, it seems to draw its sources from the informations found in the Contents-<arch>.gz files, which unfortunately only exist for the main branches (i.e., dapper, edgy, feisty), but not for sub-branches (i.e., edgy-security, dapper-backports, etc.).

Is there a reason for this, and how can this be remedied? Who can create the required Contents-<arch>.gz files on the servers?

Thank you very much,
Cheers,
Cruncher

---

### Post by Cruncher on 2007-03-12
Well? Any ideas/advice?
Should I post this somewhere else?
Otherwise, I'd just sumbit a bug for this.

---

