---
title: "Default download location"
date: 2011-07-18
forum: Server Platforms
---

### Post by Anthonyvu on 2011-07-18
Hi all, 

I have got a question, my fileserver is up and running and is working great but if i want to download something by HTTP using the command wget [url] it does not show up in my server... 

I think this is because my server location is : /Home/samba/ 

How do i change my default download location to /Home/Samba/ so i can see this in my network?

Running ubuntu server 10.04 headless using putty SSH

---

### Post by terazen on 2011-07-18
Try `cd /home/samba` before typing wget.

---

