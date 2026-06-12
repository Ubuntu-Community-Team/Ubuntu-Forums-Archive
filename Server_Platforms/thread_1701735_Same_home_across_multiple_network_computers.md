---
title: "Same /home across multiple network computers"
date: 2011-03-06
forum: Server Platforms
---

### Post by Dev0 on 2011-03-06
I'd like to set up a network with a central Ubuntu server and any number of Ubuntu client computers. The goal is to be able to log in from any computer and access the contents of the same home directory. I'm used to Ubuntu desktop but am unsure of how to implement a server to achieve these ends. Any pointers?

---

### Post by bab1 on 2011-03-06
> **Dev0 said:**
> I'd like to set up a network with a central Ubuntu server and any number of Ubuntu client computers. The goal is to be able to log in from any computer and access the contents of the same home directory. I'm used to Ubuntu desktop but am unsure of how to implement a server to achieve these ends. Any pointers?

Use NFS on the Ubuntu server to export a common /home directory.  See [**_here_**]("http://www.google.com/search?q=nfs+shares&btnG=Go!#hl=en&sugexp=ldymls&pq=nfs%20shares&xhr=t&q=nfs+exports&cp=4&qe=bmZzIGU&qesig=8twvLNnirBLmmt3fnF0WhQ&pkc=AFgZ2tnbiwSY0ec84ndTKSwyjhrKftHKyvLPquxQ62XJkQZe3kzqEMqpPY2GjrJkx9p6Ax05zIe-CJnEyola_V93DYj9PBM4Pg&pf=p&sclient=psy&aq=0&aqi=&aql=&oq=nfs+e&pbx=1&bav=on.2,or.&fp=89e96c95c947f3f0") to start.

---

### Post by SeijiSensei on 2011-03-07
You'll also want to a central authentication server.  [NIS]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch30_:_Configuring_NIS") is pretty easy to set up and was designed to work with NFS.

---

