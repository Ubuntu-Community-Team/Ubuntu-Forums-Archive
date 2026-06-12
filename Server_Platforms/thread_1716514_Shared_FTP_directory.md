---
title: "Shared FTP directory"
date: 2011-03-28
forum: Server Platforms
---

### Post by Jonathan2007 on 2011-03-28
I am trying to setup 2 individual FTP users. They should both have access to the same directory. They both need to be able to read/write into the directory. But, I want them not to be able to write to each other's files (e.g. delete, remove, rename, etc.).

So let's say the shared directory is: /home/ftp/shared/

UserA needs read/write access to /home/ftp/shared/. UserA should only have write access to his own files.
UserB also needs read/write access to /home/ftp/shared/. UserB should only have write access to his own files.

It would be a unix box of sorts, but that is the only restriction. I could use whatever software. I am currently thinking pure-ftpd or vsftp but I am open to all ideas. 

Any ideas how I can accomplish this?

Thanks.

---

### Post by Jonathan2007 on 2011-03-30
Bump.

Any ideas?

---

