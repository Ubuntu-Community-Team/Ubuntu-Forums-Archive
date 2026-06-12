---
title: "apache symbolic link to mounted drive"
date: 2015-08-28
forum: Server Platforms
---

### Post by couloir0072 on 2015-08-28
For my development laptop I have two drives. My main drive is an ssd, and I'd like to preserve space. What I'd like to do is create a symbolic link to "/media/sean/3599df55-c1af-4211-8165-4638c5e3a5fb/files", and use it in my virtual host webroot to store the gigs of files it contains. I'm able to get symbolic links working from within the same drive, but not from a physically separate drive. Is this even possible?

Thank you,
Sean

---

### Post by TheFu on 2015-08-28
Yes, symlinks work fine.  Check the permissions and ensure the apache process owner has at least read access to files, parent directories all the way up the line.

BTW, /media is for automatic mount points.  You might prefer to create a normal mount for this storage - perhaps using a LABEL instead?

---

