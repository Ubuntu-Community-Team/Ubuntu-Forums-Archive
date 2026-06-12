---
title: "Question about RKHunter results"
date: 2009-07-26
forum: Security
---

### Post by iwc5893 on 2009-07-26
When I ran RKHunter, I saw these comments in the results log.  I've searched for the files to see what they could be used by, but haven't had any luck.  Anyone have any idea what they're for?

> [09:57:54] Warning: Suspicious file types found in /dev:
[09:57:54]          /dev/shm/pulse-shm-2035844333: data
[09:57:54]          /dev/shm/pulse-shm-2491132049: data


---

### Post by wojox on 2009-07-26
/dev/shm is nothing but implementation of traditional shared memory concept. It is an efficient means of passing data between programs. One program will create a memory portion, which other processes (if permitted) can access. This will result into speeding up things on Linux.

---

### Post by iwc5893 on 2009-07-26
Thanks for the quick response.

---

### Post by HermanAB on 2009-07-27
Sadly, Rkhunter and similar old tools basically don't work anymore, so you are wasting your time...

---

### Post by cariboo on 2009-07-27
I have to agree with HermanAB, I installed a rootkit on one of my test system, and none of the usual tools found it.

---

