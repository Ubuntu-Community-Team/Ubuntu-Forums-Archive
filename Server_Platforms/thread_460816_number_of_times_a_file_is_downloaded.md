---
title: "number of times a file is downloaded"
date: 2007-06-01
forum: Server Platforms
---

### Post by twistedtwig on 2007-06-01
Hi all,

I am going to be releasing a new program in a while and was curious if it is possible to monitor how many times the file is downloaded?

This could be downloaded from either my ubuntu server or a windows 2003 server depending on which is able to track the downloads.

Thanks for your help and advice in advance.

---

### Post by MJN on 2007-06-01
How is it being downloaded? Via a web server? If so, the logs will reveal that info (at the most basic level grep for the filename and pipe the output to wc to count the number of occurances)
 
Mathew

---

