---
title: "Glype with fopen/fread instead of cURL?"
date: 2011-04-16
forum: Server Platforms
---

### Post by Geremia on 2011-04-16
Is there any way to use [Glype]("http://www.glype.com/") without cURL?

Performance comparison:
 10 per minute for fopen/fread for 100 HTTP files
2000 per minute for cURL for 2000 HTTP files

Even though the performance of cURL is much better than fopen/fread, is there a way to make Glype use fopen/fread instead? I am trying to run Glype on a server that is in PHP safe mode and does not have libcurl.

Thanks

---

