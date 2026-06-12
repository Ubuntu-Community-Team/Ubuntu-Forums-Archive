---
title: "help getting started with apache2(where is the local host found on my HD)"
date: 2009-06-17
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-06-17
(i new to ubuntu, i've been using windows xp)
i just installed apache2 using the code:
sudo apt-get install apache2

when i got to "http://localhost/"
it says "it works"

i just want to know where is the folder that I can put php files in so they will show up is the localhost


on windows i had put a folder called "mypages"in the correct folder, and now when i goto  "http://localhost/mypages" i can see a directory list in that folder, and run php scripts from that folder

how do i do this in ubuntu?

---

### Post by hictio on 2009-06-17
The default location is the '/var/www/' directory.
If I might suggest something, without being a ball breaker, you should read the [Ubuntu Server Guide](https://help.ubuntu.com/9.04/serverguide/C/), or at least, the [chapter on Apache](https://help.ubuntu.com/9.04/serverguide/C/httpd.html) ;)

---

