---
title: "Infinitely large file on XFS?"
date: 2011-01-24
forum: Server Platforms
---

### Post by ragtag on 2011-01-24
I have a file I've been trying to copy from an XFS formatted raid that is giving me some strange trouble. The file is supposedly 3.6Gb, but when I try to copy it using 'rsync', the destination temp file keeps growing seemingly infinitely, way beyond 3.6Gb. I tried copying using 'cp' and the copy command kept going, while the new file stopped growing at 3.6Gb. I eventually canceled the job, and ran a 'diff' on the files, which turned out that they were different. I've tried using tar on it too, and that just kept going forever too.

I'm not really sure what's going on here. Has anyone seen this before? And is there a solution to it?

  Ragnar

p.s. This is on a CentOS 5.4 server, not Ubuntu, but I figured I'd ask here anyway.

---

