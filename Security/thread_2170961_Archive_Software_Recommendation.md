---
title: "Archive Software Recommendation"
date: 2013-08-28
forum: Security
---

### Post by maxxjr on 2013-08-28
I have a back-up / archive scheme in mind, and am looking for recommendations on software that may already have this type of functionality, or at least some of it, before I consider putting together scripts.

I have a set of DVD & CD-ROM ISO images.  I would have a local copy, and an off-site copy.  I may use something like rsync over a VPN to automatically update the off-site copy.  

I want to maintain a set of checksums of the files, and have these compared periodically to the local copy and remote copies.  The idea is to catch a file corruption before the file is rsync'd.  If the local or remote file is corrupt, DON'T do the rsync. 

Is there open source software that does this already?

Thanks!

---

