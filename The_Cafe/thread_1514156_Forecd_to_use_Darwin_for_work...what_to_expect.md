---
title: "Forecd to use Darwin for work...what to expect"
date: 2010-06-20
forum: The Cafe
---

### Post by wannabegeek on 2010-06-20
hey folks...

I have to use Darwin at my new job. I have little experience with Macs and 
will be doing system admin stuff for the first time. We use macs to analysis
CODAR data. 

I'm having trouble parititoning the HD in my box and have gotten pretty frustrated...
no pgrep wtf ?

the bash seems limited compared to Karmic's...
What do you all think about Darwin and so you have any suggestions ?

tia
wbg

---

### Post by jrusso2 on 2010-06-20
Darwin?  Do you mean OS X?

---

### Post by cariboo on 2010-06-20
If you are installing OSX on non apple branded hardware, don't expect any help here, as the forum doesn't support illegal activities. Thread closed.

---

### Post by cariboo on 2010-06-20
Due to my own confusion and not using my google fu, this thread is reopened.

---

### Post by Bachstelze on 2010-06-20
Thank you. :)

So I was going to say:

Darwin provides the basic UNIX tools like fdisk and mkfs for disk partitioning, that should be all you need. Your distribution might or might not provide a graphical tool.

pgrep is part of the procps package, which is not ditributed in any Darwin disribution I know of. You might or might not be able to compile it, I haven't tried. Either way, you should be able to do the same thing with ps and grep.

Bash should be the same in every OS, so any difference you find should only be a matter of configuration, and fixable by doing some bashrc magic.


> **jrusso2 said:**
> Darwin?  Do you mean OS X?

Not necessarily. That's like saying "Linux? Do you mean Ubuntu?"

---

### Post by DeadSuperHero on 2010-06-20
I would like to recommend looking into trying out [DarwinPorts,]("http://darwinports.com/") or [PureDarwin]("http://www.puredarwin.org/") if you want to try a Darwin distribution. It would at least give a bit more insight into how the system is laid out.

DarwinPorts might work on non-MacOSX systems. Haven't tried it though.

---

### Post by witeshark17 on 2010-06-20
Please keep us posted on your progress... :guitar:

---

### Post by wannabegeek on 2010-06-21
Thanks for the replies..Monday is a few hours away, will check out the Darwin Ports..
I saw something about Darwin-GNU  as well...

I will read about bashrc and hopefully do some magic...I am hoping to get access to the command line programs I am familiar with on my Karmic machine., sed, curl, awk....I haven't been able to resize my partitions yet, just getting the Quad Core to boot into the CD ROM is a hassle...

thanks again,
wbg

---

