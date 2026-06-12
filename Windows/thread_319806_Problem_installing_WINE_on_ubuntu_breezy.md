---
title: "Problem installing WINE on ubuntu breezy"
date: 2006-12-16
forum: Windows
---

### Post by godwinoganiru on 2006-12-16
I downloaded wine from [www.winehq.com](www.winehq.com) with windows into my flash disk now I am having problem installing it on my Ubuntu system.

When I issued to following:

sudo dpkg -i my-wine-dir.deb

at the terminal, this is what I get:


(Reading database ... 58582 files and directories currently installed.) 
Unpacking wine (from /home/ogadi/DLD/wine.deb) ... dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy) 
dpkg-deb: subprocess paste returned error exit status 2 
dpkg: error processing /home/ogadi/DLD/wine.deb (--install):  short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/wine/changelog.gz') 
Errors were encountered while processing:  /home/ogadi/DLD/wine.deb 
root@ubuntu001:/home/ogadi# 


Please is there any help?

---

### Post by machoo02 on 2006-12-16
make sure that you are specifying the directory of your flash disk, or move the .deb from your flash disk to /home.

---

