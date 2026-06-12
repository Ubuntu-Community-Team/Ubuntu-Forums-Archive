---
title: "dots and commas"
date: 2011-02-12
forum: Server Platforms
---

### Post by jmvidalvia on 2011-02-12
Hi!
I just set a new server.
I am importing csv files to mysql, but get errors because my system understands  dots as decimal separators, and commas as thousands separators, when I need them in the opposite way.
How can I change this behaviour?
My locales are LANG=es_ES.UTF-8
Thanks a lot.

---

### Post by Vegan on 2011-02-12
you will need to use C++ and data.getline() type functionality and parse it manually

---

### Post by Vegan on 2011-02-12
C++ can connect to MySQL and then you can upload the data as needed

---

### Post by jmvidalvia on 2011-02-12
Thank you.
But I am afraid neither I am skilled enough nor have time to start learning C++ now. :(
Will use following script before importing my data:
```
sed 's/,/./g' <infile >outfile
```
Fortunately the file doesn't have other commas than those in the numbers...

---

