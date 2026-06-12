---
title: "Tar.gz and tar.bz2."
date: 2009-09-17
forum: The Cafe
---

### Post by dragos240 on 2009-09-17
What's the difference? Tar is uncompressed. Gz and bz2 are compressed and combined into a compressed archive. What is the difference between these two compression formats?

---

### Post by chris4585 on 2009-09-17
I thought .tar's created an archive?  .gz and .bz2 are different compressions.  I'm probably some what wrong.

---

### Post by dragos240 on 2009-09-17
> **chris4585 said:**
> I thought .tar's created an archive?  .gz and .bz2 are different compressions.  I'm probably some what wrong.

I think I misspoke.

---

### Post by snova on 2009-09-17
> **dragos240 said:**
> What's the difference? Tar is uncompressed. Gz and bz2 are compressed and combined into a compressed archive. What is the difference between these two compression formats?

The latter is better, and somewhat slower, due to using a better algorithm (well, in the sense of compression ratio at any rate).

[http://en.wikipedia.org/wiki/Gzip](http://en.wikipedia.org/wiki/Gzip)
[http://en.wikipedia.org/wiki/Bzip2](http://en.wikipedia.org/wiki/Bzip2)

---

### Post by Barrucadu on 2009-09-17
I have found that GZip tends to be better for plain text and Bzip2 for everything else.

Though that's just from what I've seen; the opposite could be true.

---

### Post by chris4585 on 2009-09-17
I guess I missread the question.  I use tar.gz most of the time on my desktop for regular documents, but if I'm dealing with large files like 100mbs or more, I'd use lzma even though it takes longer, its worth the compression.

---

