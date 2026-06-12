---
title: "apache ram usage too high"
date: 2011-05-06
forum: Server Platforms
---

### Post by cakka on 2011-05-06
hello,

i am learning to using ubuntu as my server and learning using vps too :)

now i getting consfuse about my server memory usage
i just have 3 sites , 1 blog site and 2 company profile
but apache memory usage is more than 300MB and total of memory use in my server is more than 500 MB (maximum 512MB burst memory)

i am using drupal for my website
is this normal ?
because in last week, memory consumption in my server no more than 380 MB

thanks

---

### Post by a2j on 2011-05-06
not sure about apache using 300mb, but Linux server will eventually use ALL of the RAM for caching. That is normal.

---

### Post by dtfinch on 2011-05-06
Apache's actual usage is less than the sum of what's reported. Apache forks into multiple processes, and all its memory is shared until written to. I could never find how to determine exactly how much it's using apart from killing it and seeing how much free memory increases though.

You could try lowering MaxSpareServers in apache2.conf. I wouldn't go below 6+MinSpareServers though even for a low traffic site, or else it'll start forking and killing instances for every new visitor, since most browsers will use up to 6 connections loading a page. You could also set MaxRequestsPerChild to some large non-zero amount (like 1000-10000) to occasionally recycle processes for a small gain.

Another option for a more dramatic reduction in memory use is to use a single-process front-end server like nginx or lighttpd for serving static content, and either using fastcgi for php or forwarding dynamic requests to Apache (but configured with a much lower max spare servers).

---

