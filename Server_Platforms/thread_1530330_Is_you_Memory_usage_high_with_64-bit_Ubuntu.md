---
title: "Is you Memory usage high with 64-bit Ubuntu?"
date: 2010-07-13
forum: Server Platforms
---

### Post by R.Bucky on 2010-07-13
I had a quad core Xeon 3200 series in my Ubuntu Server 8.04 32-bit box. It was utilizing around 700MB RAM most of the time. 

I have since built an Intel i7 box with 8GB RAM operating Ubuntu Server 10.04, 64-bit. I am using the same services and have the same software as my other box. However, I am using around 2.1GB RAM. 

Does the 64-bit version use more RAM or is their potentially a memory leak somewhere? Top, HTOP, and free all show the same RAM usage with nothing out of the ordinary. Any ideas on the RAM usage?

---

### Post by ruffEdgz on 2010-07-13
I have been using the 64 bit version of 10.04 for awhile now and I haven't noticed anything that would resemble a memory leak. 

I'm no RAM or memory export but depending on what you picked to be installed on that first setup, you could just have processes that are running in the background or there might be cached processes still stored in memory.

This is an old article but it has helped me some to understand how memory is used on a linux system: [http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html](http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html)

To answer your question though, no, I haven't seen any memory issues or leaks on 64 bit OS. I also install on the 'ubuntu-minimal' package to get me going then install what I need from there.

---

### Post by arrrghhh on 2010-07-13
Hrm, I kinda thought that if Linux had more RAM available, it would utilize it basically.

Not sure if that makes you feel any better, but for what it's worth R.Bucky if you're not experiencing any performance degredation, I wouldn't worry about it.

---

### Post by R.Bucky on 2010-07-13
I know that Linux will utilize the max memory it needs for applications. Since I moved to this new server build, it is really eating up the RAM. Performance is stellar! At one point it jumped to 3.6GB+ RAM usage, but then dropped back down with the surge of web site visitors dissolved. Hey, if it is happy, I am happy...

---

### Post by arrrghhh on 2010-07-13
Yea, like I said... if it has more RAM available, it'll consume more of it.  Kinda how humans are with money ;)

---

### Post by ruffEdgz on 2010-07-13
> **arrrghhh said:**
> Yea, like I said... if it has more RAM available, it'll consume more of it.  Kinda how humans are with money ;)

Now that is an interesting analogy ;)

Glad to hear that the server is working well and it must be alot better then the older box :D

---

### Post by R.Bucky on 2010-07-13
I have no complaints with the Xeon 3200 series quad core. But, the i7 absolutely blows it out of the water. Here are the specs and some images [http://blog.markimoore.com/completed-a-new-i7-server-build/]("http://blog.markimoore.com/completed-a-new-i7-server-build/").

---

