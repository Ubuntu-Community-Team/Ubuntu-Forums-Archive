---
title: "how do you measure performance on a computer?"
date: 2011-08-03
forum: Server Platforms
---

### Post by 007casper on 2011-08-03
how do you measure performance on a computer?

I know there are benchmark sites, they do give a general guidance in selection.  However, I want to learn how to build a cluster from commodity parts and want to make sure it is equivalent to a specific server in performance.  

I know clustering is a bit abstract and it will be difficult to measure direct performance and compare it to one specific board.  I am fine with that...

how does one go about this?

thank you.

---

### Post by blind2314 on 2011-08-03
> **007casper said:**
> how do you measure performance on a computer?

I know there are benchmark sites, they do give a general guidance in selection.  However, I want to learn how to build a cluster from commodity parts and want to make sure it is equivalent to a specific server in performance.  

I know clustering is a bit abstract and it will be difficult to measure direct performance and compare it to one specific board.  I am fine with that...

how does one go about this?

thank you.

Err...a cluster of what? VMs? Physical machines? Will this be an active/active cluster with massively parallel applications, or an active/passive (HA) cluster? What clustering software are you going to use?

Comparing a "cluster" in the general sense to a "stand-alone" server is apples to oranges.

---

### Post by Gyokuro on 2011-08-03
Hi,

as blind2314 has already mentioned it depends what you want to achieve. Maybe this page will show you that's not as easy as it seems ([http://www.clusterconnection.com/](http://www.clusterconnection.com/)) and can take some time to validate all equipment. And that's only the hardware, have fun with the software stack :-) but I think a specific high performance newsgroup is better suited for such questions.

---

### Post by 007casper on 2011-08-04
thanks for the link gyokuro

cluster of what? VMs? Physical machines? 
Physical machines

Will this be an active/active cluster with massively parallel applications, or an active/passive (HA) cluster? 
active/active

What clustering software are you going to use?
I dont know yet

it is my first attempt in building a cluster server set up from commodity parts.  

yes, I have been told that clustering is abstract. I guess it is like comparing apples to oranges when you want to compare performance.  

However, there has to be a way to compare... no?

Lets say we are going to build the cluster out of intel N570 boards.  It is horrible in performance, but good in power efficiency as one single board.  Now, I want to figure out how many N570 boards would I need to get the performance of one specific board?

And, we are going to compare N570 board to a specific board, which is E3-1230 Xeon.

Well, it cant be compared because xeon does 3x the encryption, decryption, has ECC ram set up etc.  So, N570 cant be compared to xeon.  Then, the next chip that has similar architecture is i7 2600k, or 990X EE; 980X etc.

I figured maybe I can figure out gigaflops on a cluster and compare that to a specific i7.

constructive criticism welcome.

---

### Post by 007casper on 2011-08-09
bump

---

### Post by blind2314 on 2011-08-09
> **007casper said:**
> thanks for the link gyokuro

cluster of what? VMs? Physical machines? 
Physical machines

Will this be an active/active cluster with massively parallel applications, or an active/passive (HA) cluster? 
active/active

What clustering software are you going to use?
I dont know yet

it is my first attempt in building a cluster server set up from commodity parts.  

yes, I have been told that clustering is abstract. I guess it is like comparing apples to oranges when you want to compare performance.  

However, there has to be a way to compare... no?

Lets say we are going to build the cluster out of intel N570 boards.  It is horrible in performance, but good in power efficiency as one single board.  Now, I want to figure out how many N570 boards would I need to get the performance of one specific board?

And, we are going to compare N570 board to a specific board, which is E3-1230 Xeon.

Well, it cant be compared because xeon does 3x the encryption, decryption, has ECC ram set up etc.  So, N570 cant be compared to xeon.  Then, the next chip that has similar architecture is i7 2600k, or 990X EE; 980X etc.

I figured maybe I can figure out gigaflops on a cluster and compare that to a specific i7.

constructive criticism welcome.

You can compare it sure, but it's a garbage comparison. There are not many programs that will fairly judge both parallel and non-parallel setups, without being biased in some way or another to one of them (whether on purpose or by the sheer nature of the tests).

You're either approaching this problem from the wrong direction, or "clustering" is the new buzzword these days (news to me, but I hope that's not the case).

---

### Post by markseger on 2011-11-03
I recommend using collectl - why?  because I wrote it.  But seriously, it's a very powerful monitoring tool.  You just install and start if and it collects almost everything there is to know about what your system is doing every 10 seconds AND at about 0.1% of the cpu load.  Then you can go back and playback the data it collectl to see exactly what was going on at any point in time.

Naturally you can run it interactively as well.

-mark

---

