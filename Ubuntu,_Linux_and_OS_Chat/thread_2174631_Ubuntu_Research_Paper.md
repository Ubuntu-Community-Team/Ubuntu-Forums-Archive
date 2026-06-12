---
title: "Ubuntu Research Paper"
date: 2013-09-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Kevin_Marino on 2013-09-15
Hello all. I am a computer science major tasked with writing a 15 page paper about the technical workings of Ubuntu. What I am searching for is not information directly, but rather resources (white papers, technical documentation) about the specifics to Ubuntu. More specifically, I am looking for:

The design principles underlying Ubuntu
Elements of process management (process control, synchronization, concurrency, etc)
Interprocess communication
Memory management (overylays, partitions, virtual memory, thrashing, etc)
Scheduling (deadlock handling, algorithm)
[FONT=sans-serif, Arial][SIZE=2][/SIZE][/FONT]I/O functions handling

[FONT=sans-serif, Arial][SIZE=2]Advantages and disadvantages of Ubuntu[/SIZE][/FONT]
[FONT=sans-serif, Arial][SIZE=2][/SIZE][/FONT]
 Distributed and or virtual capabilities of Ubuntu

 
Again, before you start thrashing me, I am not looking for you to write my paper, I am just asking for a few resources that are Ubuntu specific. I understand it is built off the Linux kernel, so much of the above can be answered through a discussion of Linux (memory management, scheduling, process management), however I am only looking for things that are specific to Ubuntu (ie if Ubuntu implements a different scheduler than the Linux completely fair scheduler). For instance if Ubuntu and Red Hat handle deadlocks the same (they do, as in they pretend that deadlocks don't occur at all), then I don't care, because it is common through the Linux kernel. 

I have tried looking through the documentation, and through a few forums, but haven't found much useful information. It is very possible that I have skipped right over it, which is why I'm turning to you. Even if you have a search suggestion, or a place for me to dig, I would appreciate that.

Thanks for your help,

Kevin

---

### Post by Bashing-om on 2013-09-15
Kevin_Marino; Hi and welcome !
I am pleased to introduce you to the greatest operating system the world has ever known. Anything that I can do advance ubuntu I am more than happy to do.

In my sig at the bottom of the post is a link to "NewDocs", an ever increasing compilation of everything "ubuntu". I suggest it as a great starting point.
After some perusal, by all means ask specific questions..
Someone will respond.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by JDShu on 2013-09-15
The answer is no. Ubuntu doesn't do anything special in the Linux kernel. Everything you list is handled by the core kernel. The only core functionality that a Linux distribution might change in the kernel is the scheduler. (Check out the alternative scheduler written by Con Kolivas: [ Link ]("http://en.wikipedia.org/wiki/Brain_****_Scheduler")). If it's something technically interesting you are looking for, that is probably the best way to go.  Operating System wise, Ubuntu and other mainstream distributions actually aren't very interesting. They JustWork as the saying goes!

---

### Post by JDShu on 2013-09-15
Since I suspect that Ubuntu was not specifically your assignment, might I suggest doing some research into other FOSS operating systems such as GNU Hurd, Haiku OS, or ReactOS?

---

### Post by Kevin_Marino on 2013-09-15
Actually, in the very first line of my post I stated that I have been tasked to write a research paper about the technical workings of Ubuntu, so yes, Ubuntu is the specific topic of my project. Saying "it just works" isn't good enough. There is no "magical code" that "just makes it work." While yes, the base kernel is the same amongst many distros, which again, I think I mentioned if you were going to tell me to just look up Linux's kernel then you should just not post anything. You could have given me some useful information, like I don't know, something about the package manager or included GUI, things that are specific to Ubuntu. There are some distros that patch the kernel to change many aspects of it, for instance Chrome OS stripped the kernel down to bare basics, so Ubuntu and Chrome don't handle things the same way, specifically file management. Again, I am only looking for information specific to Ubuntu, which may explain why I have chosen to seek information within the Ubuntu community, as I currently have more technical documentation about the Linux kernel than any one person should have.

---

### Post by JDShu on 2013-09-16
> **Kevin_Marino said:**
> Actually, in the very first line of my post I stated that I have been tasked to write a research paper about the technical workings of Ubuntu, so yes, Ubuntu is the specific topic of my project.   What program are you in? Your task sounds very strange. Your list of features are lower level operating system concepts that are all handled by the kernel. None of these are done at the distribution level. That's why I suspected that you chose the project youself when your instructor told you to write a paper about a specific operating system, because frankly your assignment doesn't make any sense.  >  Saying "it just works" isn't good enough. There is no "magical code" that "just makes it work." While yes, the base kernel is the same amongst many distros, which again, I think I mentioned if you were going to tell me to just look up Linux's kernel then you should just not post anything.   I told you the answer toy your question is a massive NO. Ubuntu DOES NOT do anything interesting at the kernel level. But fine, I'll stop answering you after this post. Good luck on your assignment.

---

### Post by mikewhatever on 2013-09-18
I think JDShu has a point. Canonical is not exactly a leader in the Linux kernel development. In fact, Mark Shuttlworth had stated that [Canonical is not interested in kernel development]("http://www.theinquirer.net/inquirer/news/2168086/canonical-linux-kernel"). Their effords used to go towards design and desktop (user friendliness and user experience), and now, the focus is primarily on Ubuntu Touch for phones.
What may differ Ubuntu from some other Linux distros is the use of [upstart]("http://upstart.ubuntu.com/") and ureadahead. Then there is also the [Mir display server]("https://wiki.ubuntu.com/Mir/").

So,the kernel mailing list: [https://lists.ubuntu.com/archives/kernel-team/](https://lists.ubuntu.com/archives/kernel-team/)
Design Blog: [http://design.canonical.com/](http://design.canonical.com/)
Unity interface: [http://en.wikipedia.org/wiki/Unity_%28user_interface%29](http://en.wikipedia.org/wiki/Unity_%28user_interface%29)

---

### Post by leg on 2013-09-18
Look at [Linux from Scratch]("http://www.linuxfromscratch.org/") to get a good understanding of how a linux distro can be put together.

---

### Post by Warrior4Christ on 2013-09-29
Advantages and Disadvantages?  I can name a few:

Advantages: Free OS, Very Light and Fast (There's plenty more)
Disadvantages: Not supported by a lot of hardware and apps, but Wine can help with that.  Also, user friendliness.  It can be very confusing to someone who's used to Windows and is about average in their computing skills. (There's a few more)

---

### Post by Petro Dawg on 2013-09-29
The package management in Ubuntu I believe is handled by APT (advance packaging tool).  However, this is not really unique to Ubuntu, as it is found in Debian upon which Ubuntu was based. The thing that really sets Ubuntu apart from other distros is it GUI known as "Unity".  You might be able to find useful links in the Wikipedia references here [http://en.wikipedia.org/wiki/Unity_(user_interface)](http://en.wikipedia.org/wiki/Unity_(user_interface))

Unity was also built using Compiz, for which you can start here to find more info [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

---

