---
title: "Ununstalling Ubuntu One"
date: 2011-10-12
forum: Ubuntu One (CLOSED)
---

### Post by cheatos on 2011-10-12
Hi,

I had ubuntu one installed and have uninstalled it now as I have seen that it is also possible to upload and download files via the internet.
What I have done in the first step is using the Software Center and chose remove.
Afterwards I found out that the Ubuntu One folder still exists, so I thought I'd better try it with the Synaptics Package Manager and, as estimated I still found some stuff installed in there. Now I have uninstalled all the stuff listed in the synaptics manager, too but still there is the folder of ubuntu one, I know I could just push it to the bin but how can I ensure that really everything is uninstalled, because I have the feeling that if I remove the U1 folder, I still have some stuff on my computer (I'm sorry, I've been a windows user for a long time and there you learn stuff like that ;) )

I hope you have understood my problem, as I think I wouldn't if I would read this for the first time, but good luck...

Thanks in advance for all your help

---

### Post by TeoBigusGeekus on 2011-10-12
First try
```
sudo apt-get purge ubuntuone*
```
and then remove the U1 folder.

---

### Post by oldos2er on 2011-10-12
Thread moved to Ubuntu One.

---

### Post by cheatos on 2011-10-12
Hi, here I have a screenshot from what happened, I think I have really uninstalled everything via synaptics...
So the only thing left to do is deleting the folder in my home folder and then it'll all be gone, right?

---

### Post by TeoBigusGeekus on 2011-10-12
I guess so, yeah.
At least that's the way I do it in every new ubuntu installation I do (gwibber, ubuntu one and computer janitor are the first things to remove).

---

### Post by cheatos on 2011-10-12
okay, thank you very much and sorry for posting this in the wrong forum.

---

