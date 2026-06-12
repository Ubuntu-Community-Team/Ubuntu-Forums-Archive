---
title: "Should You Do Maintenance?"
date: 2006-10-22
forum: The Cafe
---

### Post by robcarr2 on 2006-10-22
Hey, well I have recently switched to Ubuntu and was wondering should I do any maintenance on my system? e,g, on Windows I would defrag and do disk cleanup.

---

### Post by GStubbs43 on 2006-10-22
You don't need to defrag, run anti-virus, anti-spyware etc. anymore! You can download an anti-virus etc. but it isn't needed. Defragger isn't needed for ext3 either.

---

### Post by bigken on 2006-10-22
not as far I know the file system looks after its self no need to defrag 
you could empty the temp folder now and again I suppose ;)

---

### Post by weasel fierce on 2006-10-22
The file system used by linux doesnt fragment much, if at all, so defragging is not a concern.

You should check for, and install updates regularly, It should prompt you automatically, but otherwise, open a terminal and do these two commands

sudo apt-get update (this looks for newer versions of your installed files, in the repositories)
sudo apt-get upgrade (this downloads and installs them)

You can also open up synaptic (system, administration, synaptic package manager) and click "mark all upgrades", then Apply

EDIT: You dont need antivirus for linux, but if you send files to people with windows computers, you may want to look into it, so you dont pass on something nasty to your friends

---

### Post by robcarr2 on 2006-10-22
Thanks for all the replys :)

---

### Post by ~LoKe on 2006-10-22
**$ sudo apt-get autoclean**
**$ sudo apt-get autoremove**

Some small things like that you should do every once in a while.  Contrary to popular...uneducated belief; Linux is low maintenance (so long as you don't screw with something you don't understand).

---

### Post by John.Michael.Kane on 2006-10-22
Should you want to defrag. have a look at this [http://ubuntuforums.org/showthread.php?t=169551&highlight=pyfragtools](http://ubuntuforums.org/showthread.php?t=169551&highlight=pyfragtools)

---

