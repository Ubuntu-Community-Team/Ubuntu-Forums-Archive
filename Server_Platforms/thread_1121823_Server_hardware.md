---
title: "Server hardware"
date: 2009-04-10
forum: Server Platforms
---

### Post by Du27 on 2009-04-10
What is the best hardware to run a ubunto server



thaknks

---

### Post by FrankT-Qc on 2009-04-10
A computer ...

Just kidding... For a home server, anything with at least 100MBit ethernet would do, else, there's no magic answer... 

File server, web server, weather station, caching server, VPN server... time to go shopping !!!

You could go to [eRacks]("http://eracks.com/"). Their hardware is divided into task oriented categories... It could help you make up your mind on what kind of hardware is thrown at different tasks

I bougth an old P3 with 512MiB of RAM (25$) and added a 1000Base-T (12$) to act as a file server and it transacts a nice 45 MB/s up and down to a few drives... We're 15 to 20 people harassing the thing with our backups and our limit is pretty much our hard drives... Unless you're pretty CPU intensive (encryption, rendering...) the slow link is almost always the hard drives... We wish we had more RAM but it's RAMBUS... When it dies, we'll go with something like 2GiB...

Some tunning (man sysctl), dividing the work evenly between hard drives and adding some RAM for caching should make a difference.

Usually, when you're up to the point where hardware makes a big differences, you're already familiar with hardware :-P

Have fun

---

