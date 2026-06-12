---
title: "Big files on server, version control and performance"
date: 2008-11-04
forum: Server Platforms
---

### Post by ragtag on 2008-11-04
Hi,

I'm trying to set up a system where aprox. 10-20 compositors read and write files from/to a server. The basic idea is huge amount of data used by a few (10-20) users, that each uses a good chunk of it at a time.

I'm hoping to achieve a few things:

1. Performance. The data used is huge, it can easily exceed 100-200mb per frame with multiple layers of 1920x1080 12-16bit-per-channel image sequences. The frames are NOT played in real-time (24-25fps), but the compositors frequently step around in the sequence having to read all the input images for that frame. We're currently sharing a server via NFS, but when nearing deadlines, the server performance is pushed hard and it slows us down. I've been looking at ways to either use a cluster type file system or moving the files to a local drive, prior to working on them, and moving changed files back once done....though I'm not sure where to go with it.

2. Backup/retention. When a new set of images is output, I want to keep the previous version for a limited time.

3. Clean. I need the file structure on the server to remain organized and clean. Which is harder when the users can directly mount an nfs share and are let loose with little restrtictions other than me telling them to not make a mess. :)

I'm a huge fan of Subversion, though it's impractical to use it with this amount of data (a project can easily be 1TB or more). But some way of getting a similar workflow using some scripting or existing tools would be great.


I'm just throwing this out, hoping someone has suggestion or ideas that could work.

Thanks in advance,

 ragtag

---

