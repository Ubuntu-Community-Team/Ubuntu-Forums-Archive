---
title: "Web Server ?"
date: 2007-05-16
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-16
Just to check one thing. I am new to running a web server. It seems to be pretty slow when I pull up the we pages. Is that a setting in the server configs or is it my connection at home?

---

### Post by seamless on 2007-05-16
There is no special setting to make a web server run faster (speaking about Apache2 specifically). If you are hosting it on your home desktop using your home internet connection it is most likely the connection and to a lesser extent the computer.

---

### Post by blmartin777 on 2007-05-17
Well I talked to my ISP and I am getting 512kb upload. Is that very fast. The computer is a AMD Athlon 2600+ with 1.25gb of ram. So is it more my connection or the computer?

---

### Post by blmartin777 on 2007-05-17
> **blmartin777 said:**
> Well I talked to my ISP and I am getting 512kb upload. Is that very fast. The computer is a AMD Athlon 2600+ with 1.25gb of ram. So is it more my connection or the computer?

bump

---

### Post by gaten on 2007-05-18
What is "slow" exactly? Try hosting a sizable file on your webpage (>5mb) and download it from outside your network, and see how fast it is (kb/sec). 

On my webserver, I have a max upload rate of about 35k/s, but for my small webpages that is more than enough. Does your webpage have a alot of graphics and content?

---

### Post by coxy on 2007-06-05
I have a similar issue. I have a wordpress based site that was running fine last week, I could connect to it from work and it loaded the site in around 3 - 5 seconds. I stopped the services for a bit and blocked the port until today. Now the site only loads in text mode.

I have not changed anything so not sure what is the cause!

---

### Post by ixus_123 on 2007-06-05
512 upload speed is plenty for a pictures / text site serving family and friends.

According to speedtest.net I have 384kbp/s upload speed and my site is fast enough for my needs.  I run a standard Apache2 / wordpress2 install with no special speed tweaking.  Computer is a 1Gz Via C3 cpu, 512mb ram, 160gb hard disk running dapper

[http://kieren.demon.co.uk/]("http://kieren.demon.co.uk/")

As long as you don't have large files that need to be called (hi res jpegs / mp3s / video) it should load jus as fast as most other sites.

---

