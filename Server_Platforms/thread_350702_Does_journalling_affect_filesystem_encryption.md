---
title: "Does journalling affect filesystem encryption?"
date: 2007-01-31
forum: Server Platforms
---

### Post by kj1h234lkj1234 on 2007-01-31
Hi,

I know that most "modern" filesystems support journalling, but does this affect encryption in any way?

I know that deleting a file from an unencrypted disk may not remove it, as traces my exist in the journal, but are there any drawbacks with using a journalling filesystem (say, ext3) with a fully-encryped system?

Thanks

---

### Post by raul_ on 2007-01-31
I think that these are 2 different and separate things. Journaling basically, keeps a log of your filesystem before actually writing it, preventing data loss/corruption. I don't see how that affects encrypting.

---

