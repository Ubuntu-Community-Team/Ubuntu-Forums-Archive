---
title: "Apache log analysis GUI"
date: 2006-06-26
forum: Server Platforms
---

### Post by blkish on 2006-06-26
can anyone recommend a good apache log analyser/filterer, ideally for gnome?

i have some huge logs to work on and getting tired of grep'ing! thanks

blkish

---

### Post by MJN on 2006-06-26
It may help if you can specify what sort of info you want out of them - there'll be all manner of solutions out there but the choice of which really depends on your problem(s).

For me, requiring straightforward statistics, page/visitor counts, locations and search robots etc I use AWStats ([http://awstats.sourceforge.net/]("http://awstats.sourceforge.net/")) - you can see a typical output (it's fully customisable) at my site [http://www.newtonnet.co.uk/cgi-bin/awstats.pl]("http://www.newtonnet.co.uk/cgi-bin/awstats.pl").

Might this be along the lines of what you require?

Mathew

---

### Post by blkish on 2006-06-29
hi matthew

thanks for the link - i use awstats in some places, great package :)

i am looking for something that would help when performing more 'forensic' analysis of apache logs.

eg, has the ability to load an entire log file, then filter the results according to criteria such as remote address, content of request string etc.

Ideally also then save these resulting results as individual files.
ability to comment the logs would be a huge bonus too.

the process is more like analysis a package capture with ethereal than seeking general stats about site usage etc. it's very specific parts of the logs which are needed.

cheers 

blkish

---

### Post by MJN on 2006-06-29
Ah, okay. I'm afraid I'm not familiar with any particular tool that would suit (that's certainly not to say one doesn't exist).
 
Given the heavy reliance and significance on your search strings and patterns I can't see what value a high-level tool is going to give. The power of grep and pipes in this instance would surely satisfy your needs?
 
Mathew

---

### Post by blkish on 2006-06-29
i'll have another google :)

yes grep and pipes, but i'm always looking for ways to speed up what i do, and a ethereal-esque GUI would make investigative work on log files easier, i think.

thanks for the ideas though!

blkish

---

