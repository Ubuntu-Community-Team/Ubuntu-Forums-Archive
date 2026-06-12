---
title: "Problems with Beta alloc_contig_range test_pages_isolated"
date: 2014-08-28
forum: Ubuntu Development Version
---

### Post by Peter09 on 2014-08-28
I am getting a lot of ... 
Aug 28 16:16:15 PCPavilion kernel: [18916.843036] alloc_contig_range test_pages_isolated(13c400, 13c7fb) failed
Aug 28 16:16:15 PCPavilion kernel: [18916.843044] alloc_contig_range test_pages_isolated(13c400, 13c7fc) failed 
Aug 28 16:16:15 PCPavilion kernel: [18916.843052] alloc_contig_range test_pages_isolated(13c400, 13c7fd) failed 
Aug 28 16:16:15 PCPavilion kernel: [18916.843061] alloc_contig_range test_pages_isolated(13c400, 13c7fe) failed

  in syslog - during which time the whole machine grinds to a halt. Any assistance?

---

### Post by lee295012-gmail on 2014-08-29
it's a bug in 3.16 and 3.17, if you add cma=0 to grub that should fix it.

---

### Post by Peter09 on 2014-08-30
> **lee295012-gmail said:**
> it's a bug in 3.16 and 3.17, if you add cma=0 to grub that should fix it.

Thanks for that - I've updated grub to see how it goes. First impressions are that the graphics are a bit quicker - so fingers crossed.

---

### Post by lee295012-gmail on 2014-08-30
it's fixed the ubuntu daily builds so hopefully will be fixed in 3.17-rc3 when linus releases it.

---

