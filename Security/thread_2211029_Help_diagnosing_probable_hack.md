---
title: "Help diagnosing probable hack?"
date: 2014-03-13
forum: Security
---

### Post by rebeltaz on 2014-03-13
After discussing an issue I was having with files disappear from my web server I have decided that the system was, as it's called, owned?

I ran iftop on my server and noticed a LOT of traffic to what should be a very low volume web site. In the range of 30 mb in less than 10 minutes. While that may not seem like much, it is for my little sever. I reinstalled the server from 12.04 LTS server cd and re-ran iftop. Traffic was about 30 mb over an 8 hour period. On the recommendation of the others here, I ran iftop on both my local systems as well and I see a lot of traffic on those when there should be NONE. 

I configured ufw on both the block everything but ssh and to only allow that from the other computer, but is there any way to find out if/what has been done and to undo it? 

I am not proficient with with Linux hacking to even know where to begin looking so any help or finger pointing in the right direction would be great. Thanks in advance.

---

### Post by tgalati4 on 2014-03-13
It could have been a spider crawling through your web pages collecting and indexing information.  What files were missing?  Check your log files in /var/log/apache and see what is going on.

---

### Post by rebeltaz on 2014-03-13
Those are some of the files missing. Before I am criticized for what I am about to say, I already know how wrong I was, but I haven't really looked at the logs in a while. Almost a year to be exact. Logs and webalizer stats have not been created since last May. ISPConfig no longer worked. Webcrawlers I could understand, but not on the continuous basis I was seeing, nor should there have been any traffic to or from my desktop computer on the same network as the server.

---

### Post by tgalati4 on 2014-03-14
So is it possible that your desktop computer has been compromized and it is using your server as well?

---

### Post by rebeltaz on 2014-03-14
I'm thinking yes.

---

### Post by tgalati4 on 2014-03-14
I would shut both machines down.  Boot a Live Ubuntu DVD, download bitdefender and scan both machines.  Let us know what you find.

---

### Post by rebeltaz on 2014-03-14
Bitdefender? Is that not a windows only product?

---

### Post by sammiev on 2014-03-15
> **rebeltaz said:**
> Bitdefender? Is that not a windows only product?

I use Bitdefender all the time with Linux. Works great.

---

### Post by rebeltaz on 2014-03-15
Hmmm. Where do I get BitDefender for Linux?

---

### Post by sammiev on 2014-03-15
> **rebeltaz said:**
> Hmmm. Where do I get BitDefender for Linux?

[Here]("http://www.ossdoc.com/2013/01/installing-bit-defender-antivirus-on.html").

---

### Post by rebeltaz on 2014-03-15
Well, I'll be darn. That's good to know. I will do this weekend and see what I come up with. Thanks.

---

### Post by gifford on 2014-03-18
Read this link:[http://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/](http://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/)
There is a command to check if your server has been compromised. Apparently, many Linux servers have been.

---

### Post by PartisanEntity on 2014-03-27
> **gifford said:**
> Read this link:[http://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/](http://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/)
There is a command to check if your server has been compromised. Apparently, many Linux servers have been.

That's very interesting thanks for sharing. Sounds quite sophisticated. Quickly checked my server too :)

---

### Post by maglin2 on 2014-03-28
looking at virustotal output over the past few days this is detected by quite a few AVs (17 of 51) - but not Clam or Bitdefender.

---

