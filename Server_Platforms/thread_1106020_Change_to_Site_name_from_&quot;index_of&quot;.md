---
title: "Change to Site name from &quot;index of&quot;"
date: 2009-03-25
forum: Server Platforms
---

### Post by dantattoo on 2009-03-25
I probably did this the wrong way but I have dual desktop environments gnome and kde and decided to use lighty instead of apache because of system demands 

My question is simple how do I get my site to read as anything other than index of

I know that this is probably in the conf. for lighttpd but if anyone could shed some light on this I would appreciate it.

my site as is: 65.65.68.212 but I dont care for all to know what its running on just the pages any help...PLEASE

---

### Post by albandy on 2009-03-25
We aren't here to do your job but
set server.dir-listing to disable in lighttpd.conf

---

### Post by dantattoo on 2009-03-25
ok I will try that and this is completely new to me thank you for the help and the quick reply

---

### Post by BkkBonanza on 2009-03-25
You also need to have some content, like index.html. If no content then the server may show a listing for the directory.

---

### Post by albandy on 2009-03-25
> **BkkBonaza said:**
> You also need to have some content, like index.html. If no content then the server may show a listing for the directory.

except if you disable it in server configuration, as said before

---

