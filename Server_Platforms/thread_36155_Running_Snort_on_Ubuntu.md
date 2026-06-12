---
title: "Running Snort on Ubuntu"
date: 2005-05-22
forum: Server Platforms
---

### Post by Nikodemis on 2005-05-22
Hello all, I'm trying to run Snort but when I try to start it I get the message Libpcre.so.0 is missing. I've installed libpcre 5.0, so I'm not sure what is wrong. Any help would be great.

Thank You

---

### Post by Nikodemis on 2005-05-26
[QUOTE=Nikodemis]Hello all, I'm trying to run Snort but when I try to start it I get the message Libpcre.so.0 is missing. I've installed libpcre 5.0, so I'm not sure what is wrong. Any help would be great.

Thank You[/QUOTE]

I just wanted to update the post, I had to add /usr/local/lib to the LD_LIBRARY_PATH, and I can now start Snort  ](*,)

---

