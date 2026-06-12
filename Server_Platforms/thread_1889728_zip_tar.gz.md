---
title: "zip tar.gz"
date: 2011-12-01
forum: Server Platforms
---

### Post by gishaust on 2011-12-01
Hi ubuntu server people, 

I am trying to test my php script I want to decompress zip tar.gz 
these files using php but my local machine ubuntu 11.04 won't work
what do I need to install to get it to work?

Thanks

---

### Post by hawkmage on 2011-12-01
Is the fine extension tar.gz?  If so you can expand it by tar zxf file.tar.gz

---

### Post by jonobr on 2011-12-02
uncommpress them before unzip

gunzip file.tar.gz 
the tar -xvf file.tar.gz

---

