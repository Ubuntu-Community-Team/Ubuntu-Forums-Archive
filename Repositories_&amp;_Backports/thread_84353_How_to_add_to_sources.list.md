---
title: "How to add to sources.list"
date: 2005-10-30
forum: Repositories &amp; Backports
---

### Post by thinhlegolas on 2005-10-30
I found this website with the latest unrar
[http://mirror.isp.net.au/ftp/pub/ubuntu/pool/multiverse/u/unrar-nonfree/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/multiverse/u/unrar-nonfree/)

Wonder how can I add it to sources.list... thanks

---

### Post by audax321 on 2005-10-30
That doesn't look like a standard apt-get repository. It's just a listing of deb files. To install them all you need to do is download the deb file you want and then in a terminal do:

cd <location where the file is located>
sudo dpkg -i <name of deb file>

Then after the deb file is installed you can uninstall it using synaptic or apt-get.

---

### Post by audax321 on 2005-10-30
Also, the latest deb listed there is 3.4.3, which is already available in the ubuntu multiverse repository:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

---

