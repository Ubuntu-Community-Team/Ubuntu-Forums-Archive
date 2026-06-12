---
title: "vhosts and symbolic links"
date: 2009-06-28
forum: Server Platforms
---

### Post by Vegan on 2009-06-28
At present, I simply have the actual file for each site physically in the /etc/apache2/sites-enabled

what I would like is to change that to symbolic links and keep the files in the /etc/apache2/sites-available

---

### Post by LepeKaname on 2009-06-29
Hi,

cd /etc/apache2/sites-enabled
mv * ../sites-available 
ln -s ../sites-available/* .

That's all.

---

### Post by Vegan on 2009-06-30
thanks

---

