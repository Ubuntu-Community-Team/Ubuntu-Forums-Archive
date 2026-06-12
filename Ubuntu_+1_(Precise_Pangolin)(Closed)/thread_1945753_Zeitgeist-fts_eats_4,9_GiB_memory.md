---
title: "Zeitgeist-fts eats 4,9 GiB memory"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Abandon on 2012-03-23
After using search in Dash (finding application) memory spikes to 5,9 GiB. That's due to Zeitgeist-fst which is using 4,9 GiB. 

System information:
Ubuntu 12.04 Beta 1

3.2.0-20-generic #32-Ubuntu SMP Thu Mar 22 02:22:46 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Intel Core i7 2600 3,4 Ghz

8 GB memory

Can't think of any reason why this should need so much memory. Is there a solution or is this a bug?

---

### Post by Abandon on 2012-03-30
The problem is still eating my memory. The strange thing is that I don't have zeitgeist-extension-fts installed but it takes almost all memory. Can't be right. 

[IMG]http://www.linuxweblogs.nl/zeitgeist.geschaald.png[/IMG]

---

### Post by dino99 on 2012-03-30
I dont like that kind of package (ZG) on my system, you can mostly remove all of them (or file a bug)

---

### Post by Abandon on 2012-03-30
Installed Ubuntu 12.04 Beta 2 and issue is gone. Must have been a leftover from an dist-upgrade or something.

---

