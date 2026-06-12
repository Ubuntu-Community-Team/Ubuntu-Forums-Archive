---
title: "What does GET HIT and IGN mean"
date: 2006-08-07
forum: Repositories &amp; Backports
---

### Post by benjaminwr on 2006-08-07
i just have a quick question, everyone seems to get some IGN message instead of GET or HIT from now and then when updating repositories but I would like to know how that affects being able to download from that repository.

Could someone be so nice as to tell me what 

IGN and HIT mean... (I suppose GET is everything ok)

Cheers

---

### Post by eXisor on 2006-08-07
Could be talking rubbish here... But this is what I think.
Updates are done only for entries in your sources.list, so when you do a apt-get update a compare is done between those archives and what you have installed. So, from obervation, this is what I think they mean:

1) IGN: Ignored. This seems to say you have an entry in sources.list which has been superceded by a later version/archive, so the check of the archive is ignored. I find this happens for my iso install entry.

2) Hit: The archive version you have is the latest.

3) Get: There is a newer version of the archive. Depending on what you have installed, this may/may not contain an upgrade to your software.

---

