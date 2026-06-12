---
title: "trigger custom scripts on server via http"
date: 2010-07-17
forum: Ubuntu Dev Link Forum
---

### Post by delete000 on 2010-07-17
so, what i want to do is fairly simple if one wants to do it on their own computer: i want a zip file to get replaced by another, automatically generated zip file every time someone downloads it. the reason is that i would like the zip file to contain a little text file saying "you are the XXXth person who downloaded this file", XXXth being the number of times the file has been downloaded. i'm pretty sure i can write a shell script that would perform the aforementioned task on my laptop.

what i want to do however is to make my server do this every time someone downloads a certain file. i also want to avoid this happening when the file is downloaded only partially. i have a cheap web hosting service (linux server). is it possible to do this and how? if a different kind of server is needed then what kind of service should i look for? finally, what would be a good way to go about programming this?

i realize this may not be entirely on topic here, but i don't know any other specialized forums. if someone knows a better place to ask this question please let me know. thanks in advance.

---

### Post by lkjoel on 2010-07-18
> **delete000 said:**
> so, what i want to do is fairly simple if one wants to do it on their own computer: i want a zip file to get replaced by another, automatically generated zip file every time someone downloads it. the reason is that i would like the zip file to contain a little text file saying "you are the XXXth person who downloaded this file", XXXth being the number of times the file has been downloaded. i'm pretty sure i can write a shell script that would perform the aforementioned task on my laptop.

what i want to do however is to make my server do this every time someone downloads a certain file. i also want to avoid this happening when the file is downloaded only partially. i have a cheap web hosting service (linux server). is it possible to do this and how? if a different kind of server is needed then what kind of service should i look for? finally, what would be a good way to go about programming this?

i realize this may not be entirely on topic here, but i don't know any other specialized forums. if someone knows a better place to ask this question please let me know. thanks in advance.
You would need a PHP file to change the download counts.
Apache would work fine, and for installation instructions, go to: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
A better place would be on Programming Talk, just below Ubuntu Dev Link Forum, but this will work fine.

---

