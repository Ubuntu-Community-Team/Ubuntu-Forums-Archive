---
title: "Over wrote index.html, but old one still is the index"
date: 2006-07-14
forum: Server Platforms
---

### Post by %hMa@?b&lt;C on 2006-07-14
I overwrote my old index.html, with a new one, but when I go to [http://localhost](http://localhost) on my server, it still shows the old one... any ideas?

---

### Post by Paerez on 2006-07-14
hit refresh?

Are you using apache, and where are you putting your files?

---

### Post by %hMa@?b&lt;C on 2006-07-14
I did hit refresh, am using Apache, and am putting my files in /var/www via FTP
the funny thing is that when in go to localhost/index.html, it goes to the new index

---

### Post by Paerez on 2006-07-14
are there any other index files, such as index.php index.htm, etc that may be getting loaded instead of index.html?

---

### Post by %hMa@?b&lt;C on 2006-07-14
no, only that one index.html, I may have to just clear my cahce, the server is not on right now, hope that fixes it.

---

### Post by Paerez on 2006-07-14
yeah it may be the cache. good luck.

---

