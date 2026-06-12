---
title: "Apache2 Directory Listings"
date: 2009-03-30
forum: Server Platforms
---

### Post by cantdrive55 on 2009-03-30
I'm trying to change my listings from the default which is sorted by name to where it will list folders first and then files by name after. I believe I have found that I need to add this somewhere but dont know where that is. Possibly /etc/apache2/mods-available/autoindex.conf  ?

C=S sorts the directory by size, then file name.

I found out a page that shows where i can make a header.html file that lets me select my options and then it will sort it correctly but I want this to be the default setting.

Thanks,
Jeff C.

---

### Post by cantdrive55 on 2009-04-04
No ideas??

---

### Post by cantdrive55 on 2009-04-07
Figured it out myself. Simply add "FoldersFirst" to the index options of autoindex.conf

---

