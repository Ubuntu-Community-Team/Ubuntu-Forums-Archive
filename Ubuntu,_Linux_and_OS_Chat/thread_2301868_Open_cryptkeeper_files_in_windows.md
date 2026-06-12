---
title: "Open cryptkeeper files in windows"
date: 2015-11-05
forum: Ubuntu, Linux and OS Chat
---

### Post by john484 on 2015-11-05
I used cryptkeeper to encrypt some files last year, mainly algorithms that i was working on. I just installed windows 10 on an ssd and swapped my ubuntu drive to a secondary bay. I still know the password used to encrypt, but can no longer boot into the disc do to some f@#$ed up boot override in the uefi. This is a new desktop, my old desktop had some mobo issues. I tried putting the secondary back as the primary in my new computer and no dice with booting. I find this very odd. However in windows I can open and access the contents of the secondary hdd and see the encfs that cryptkeeper left behind.

Any help would be much appreciated! 

Thanks.

---

### Post by mikodo on 2015-11-06
I don't know encfs. I had a situation installing to 14.04 from 12.04 where I couldn't unlock a file in bcrypt. I installed the bcrypt version that was in the repos for 12.04 and was able to open it. Might that be a newer version of encfs that you are using now that could be causing this?

Just a thought.


(That may have been a 10.04  repo version to 12.04, to think about it).

---

### Post by Svouf on 2015-11-06
Could you boot from a live image to decrypt and save your files elsewhere until you manage to solve the boot problem? It might work as a temporary one-off solution.

---

