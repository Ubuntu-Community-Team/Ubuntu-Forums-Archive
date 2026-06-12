---
title: "StarDict suddenly appeared"
date: 2008-12-31
forum: Security
---

### Post by brandon88tube on 2008-12-31
I wanted to make sure that this wasn't a security breach or anything. I just added a new language under Ubuntu and now under my Applications > Accessories is a program called StarDict. I never told it to install and was wondering if it installs itself with adding a new language. If not I think I got compromised. I didn't find anything really in the log files except a few blocks with UFW these are not all of them, but the first one pops up multiple times ```
Dec 31 03:32:14 prtbl kernel: [49117.251393] [UFW BLOCK INPUT]: IN=wlan0 OUT= MAC=00:14:a5:4e:39:74:00:0d:72:0b:aa:79:08:00 SRC=69.60.7.199 DST=172.16.1.36 LEN=1420 TOS=0x00 PREC=0x00 TTL=54 ID=46107 DF PROTO=TCP SPT=80 DPT=50889 WINDOW=65520 RES=0x00 ACK URGP=0 
Dec 31 03:32:15 prtbl kernel: [49117.252320] [UFW BLOCK INPUT]: IN=wlan0 OUT= MAC=00:14:a5:4e:39:74:00:0d:72:0b:aa:79:08:00 SRC=69.60.7.199 DST=172.16.1.36 LEN=84 TOS=0x00 PREC=0x00 TTL=54 ID=46363 DF PROTO=TCP SPT=80 DPT=50889 WINDOW=65520 RES=0x00 ACK URGP=0 
```

---

### Post by cariboo on 2009-01-01
There is nothing to worry about, the name of the dictionary file **StarDict** is a leftover from the origional name of OpenOffice, it was origionally called StarOffice, and I guess no-one has gotten around to renaming it.

Jim

---

### Post by brandon88tube on 2009-01-02
I'm curious as to how I got it on my machine though. It wasn't there before.

---

### Post by cariboo on 2009-01-02
Check the dependencies of the language file you installed, go to System-->Administration-->Synaptic Package Manager, highlight the language package you installed and click the properties button, then click the dependencies tab and check to see if the dictioanry is there.

Jim

---

### Post by ubuntu27 on 2009-01-02
Don't worry. Your computer wasn't compromised.

StarDic is a dictonary application.

Here is its homepage: [http://stardict.sourceforge.net/](http://stardict.sourceforge.net/)
You can add different dictionary such as French, Japanese, Russian, etc.


I have enabled Japanese support and StarDic was installed.


StarDic was installed on your system because you told it to install "extra software" while adding support for a specific language.

Take a look at my screeshot:

[[IMG]http://img126.imageshack.us/img126/4302/screenshotlanguagesuppoyr1.th.png[/IMG]](http://img126.imageshack.us/my.php?image=screenshotlanguagesuppoyr1.png)

---

### Post by brandon88tube on 2009-01-02
Yeah, thanks it seems that I did install the extras when installing another language. I didn't realize it though.

---

