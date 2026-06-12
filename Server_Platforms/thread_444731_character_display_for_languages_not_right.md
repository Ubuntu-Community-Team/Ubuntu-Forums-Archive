---
title: "character display for languages not right"
date: 2007-05-15
forum: Server Platforms
---

### Post by lowdne1 on 2007-05-15
running ubuntu server 6.06  as webserver for my site, everything works great except other languages . tags are set for german ,spanish ,japanese , but come out as ?????? or other symbols, need to correct this somehow,  noob as far as ubuntu , had red hat box before and it shows them fine.  what setting and where do I go to corrct this?

---

### Post by Zootropo on 2007-05-15
This has to do with the encoding of your database / html pages, not with ubuntu.
are your pages static or what do you use?

---

### Post by lowdne1 on 2007-05-15
dk if it helps you, but this is the syntsx at the top of all the (japanese) survey pages that's not working:
 <meta http-equiv="Content-type" content="text/html: charset=shift_jis">

there is a similar instruction specifying the other character sets for all the other languages. I can see it in my code when i view source, but when I view (the Same) page info, it says the encoding is UTF-8

---

