---
title: "Best tutorial/guide to learn Linux"
date: 2017-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by elsmandino2 on 2017-04-10
I have spent the last few months having a go with Linux and, for some reason, I just don't seem to be making any progress.

I have posted on numerous sites for help and although the advice has been really helpful, I just don't ever seem to fully understand the advice/instructions given.

It seems that I really need to start from absolute scratch.

Is there a comprehensive, single source guide or tutorial that takes someone as clueless as me and takes them through everything that I might need to know or understand Linux?

I have tried searing on the net but, as always, there is too much information out there.

Is there a go-to guide that all beginners should use?

Thanks

---

### Post by TheFu on 2017-04-10
No. > takes them through everything that I might need to know or understand Linux? is a tall order. Doesn't exist.

It also depends on what you want to become in 5 yrs.  Training to be a programmer is different from training to be a systems admin, cloud admin, or end-user.

Plus different people learn most effectively in various different ways.  I learn by doing, then less so by reading it. Even less by seeing it done by someone else and worst by hearing someone else explain it.  Other people only learn by hearing it, not reading or doing.

So - where do you want to be in 5 years (what do you want to be competent in doing?) and how do you learn best?

---

### Post by elsmandino2 on 2017-04-10
Given that I appear to have learnt so little so far, just by playing with Linux, I reckon that reading instructions with explanations is going to be best for me.

In terms of long-term goals, I just want to be an end-user - i.e. I just want to be able to reach the point where I don't have any reliance on Windows any more (examples - I want to be able to understand how to troubleshoot driver issues, compile (and understand what that is), maintain a headless server etc.)

---

### Post by vasa1 on 2017-04-10
Moved here because the issue is quite broad and not a specific support question about Ubuntu or any of its official flavors.

---

### Post by Habitual on 2017-04-10
I found the far best guide for learning Linux was daily use.

---

### Post by #&amp;thj^% on 2017-04-10
> **Habitual said:**
> I found the far best guide for learning Linux was daily use.

+1...Agreed.
And the very helpful folks here @ Ubuntu Forums..
You will find just like any other system...the more you use it the more comfortable you will become.:)

---

### Post by Morbius1 on 2017-04-10
If you wrote a book about the care and feeding of Windows XP when it first came out it would have been valid 10 years later. Some of the things mentioned would be valid in Windows 10.

Linux is not Windows. In a 10 year time frame desktop environments have come and gone, init systems have come and gone, even the default filesystem used has changed. Whatever book you may find on Linux became obsolete by the time it reached the publisher. Except maybe Linux permissions - that has pretty much stayed as it was when UNIX was invented 45 years ago.

---

### Post by TheFu on 2017-04-10
> **elsmandino2 said:**
> Given that I appear to have learnt so little so far, just by playing with Linux, I reckon that reading instructions with explanations is going to be best for me.

In terms of long-term goals, I just want to be an end-user - i.e. I just want to be able to reach the point where I don't have any reliance on Windows any more (examples - I want to be able to understand how to troubleshoot driver issues, compile (and understand what that is), maintain a headless server etc.)

Ok, that gives us a place to begin, but those are wildly different levels of skill, so you want to be a little-bit programmer, lots of "power user", but mostly point-n-click user.  For that level, googling answers isn't helpful early on. Many answers found make assumptions which just aren't true, mainly assuming you understand things that become more obvious with more experience.

So ... a customized list for you. Read them in order.
* [Linux for Windows Users]("http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html") - get some quick understand of how Linux is different in practical ways.
* [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm") - gain some understanding about the difference in cultures between volunteer workers and paid, commercials, software devs.
* [Ubuntu Desktop Guide]("https://help.ubuntu.com/stable/ubuntu-help/") - this won't be very useful if you don't use Unity. This covers about 10% of what stock Ubuntu can do.
* The [Linux Command Line]("http://linuxcommand.org/tlcl.php") - Gain access to the other 90% of what a Unix system can do that point-n-click users never touch.

Read those, in order, and you'll be well on your way to "power user."  The first 2 should take less than 45 min.  Probably want to flip through every page of the Destktop Guide quickly, to get an idea of what is available and possible.  Reading 10-20% of it.  For the last link, you should probably read up thru about page 135-ish and skim the rest quickly.  Don't skip the Linux file system hierarchy part. There is a reason for all those directories, though many don't apply to single-user, home, desktop, systems.  If you use Linux in a work environment, it is critical to understand why /var/ and /etc/ should always be local and /usr/ can be on network storage.

None of this will get you compiling programs. There are 500 different ways to "build a program" depending on the languages, OS, GUI, and tools involved. There aren't "standard ways" that everyone uses - programmers have their own way of doing things, each is a little different especially if they are volunteers.  I was a professional developer for almost 15 yrs - writing code daily in C/C++, and about 30 other languages across about 15 different platforms. In the old days, Unix programmers all basically did things similar ways, not exactly the same, but similarly.  With the huge influx of Windows devs moving into Linux, we really get a hodge-podge of methods now. Plus many more programs use different scripting languages like Go or Erlang these days, so things have to be different than the old C or perl deployment methods.  It is very common for compiling C/C+ programs to break and a little more knowledge to be necessary to get it working. All the dependencies are YOUR RESPONSIBILITY and aren't always documented. Plus just setting up an environment to do compiling things (software development) can be a 2-16 hour effort when you are new.  As an example, even with all my experience I won't attempt to compile ffmpeg myself anymore. There are about 15 dependencies, each has other dependencies for their development, and it gets nasty quickly. Much easier to find a trusted PPA and use that instead.  OTOH, for self-contained programs, like comskip, the compilation and linking is pretty straight forward (even if the code is really ugly).  Last time I did it, it had lots and lots of automatic type conversions that we'd see in the 1980s as a "feature" of C. Now those are considered type-bugs to be fixed.

Troubleshooting drivers is really all about understanding the OS at a deeper level.  Knowing that almost everything is a file on any Unix system is an important abstract idea. Really there are just 2 things - files and processes. Whenever you see anything on a Unix system it is either a file or a process - there isn't any other choices, period. None.  If it isn't a running program, then it is a file.  Directories are "files", for example.  File systems are files. Devices like modems, keyboards, monitors or speakers are files.  Files are read-from and written-to based on the normal Unix permissions model.  BTW, file permissions ... are files too. ;)  A solid understanding of Unix file and directory permissions will make life much easier. If you work with others on the same machine or run any services like a home photo viewer or media server, that understanding will make access trivial and limiting access to the "adult R rated stuff" easy to setup.

Plus there is a very different way of thinking necessary to get the most from any Linux/Unix system. Having the system do things for me, automatically, saves me time every day.  I don't point-n-click through my top 5 favorite websites for articles. My box pulls all the articles from my favorite 20 sites, stores them in a system locally that I can review or delete quickly.  If I'm going to be offline, but still want to read those things, fine - export to epub or pdf is 1 click from a tablet and I'm gone.  The system estimates how long each article will require to read, so if I'm waiting in a doctors office or for some car work, I can catch up on reading that I've already filtered.  Have a few short sci-fi stories in my list too - between 45-60 min if that is what I'd like.  I wrote an article about this thought shift using a report that my boss wanted a few years ago as an example. I compared the Windows-way and the Unix way.  If I needed to create the report once, the Windows way was clearly better and tool less knowledge/skill. But if I needed to create the report more than once, the Unix way was far more efficient - far more.

It really is a different mindset than "get it now, consume it now" methods.

Ok ... let me go back and fill in those links now.

There are lots of other documents for learning, but if you move around too much early on, there will probably be gaps of knowledge left behind. Avoid the gaps. Work through those in order, to completion.

And if you forget the GUI stuff, the underlying things really don't change all that much over the decades.  I have scripts and aliases created from 25+ yrs ago that I still use daily, constantly. Here's one.
```
alias psg='ps -eaf | grep $*'
```
Today, there is a tool called **pgrep**, but my habit of **psg** is done and provides some more information. Some tools have improved over the years - du, df, sort - these all have more options today than they did 20+ yrs ago.  Mostly "human" readable things and human sortable things. Not really things that most end-users consider, but handy nonetheless.

Plus, if you learn the shell/CLI way to do things, those will work from 20K miles away or for servers, which can be very handy.

Hopefully, this is helpful.

---

### Post by bcbuch on 2017-04-14
> **Habitual said:**
> I found the far best guide for learning Linux was daily use.

I couldn't agree more!!

When I started using linux back in the early 90s there wasn't all the forums and online resources that there are now. My first successful install required me going out and purchasing a RedHat boxed set that came with a book and 14 disks. It took a week of trial and error from a cli installer to get a functioning system, along with the purchase of a US Robotics external modem to get online connectivity. These days it is just a matter of downloading an iso and burning it to a DVD or using a USB drive and working through a graphical install.

Keep in mind everybody's system needs, program and environmental preferences will differ. The first things you need to do is decide what you will use your system for, what you types of programs you will want to be able to use, and how you would like the desktop environment to function. Remember in very simplistic terms linux is like a child having a box of legos. You take the different pieces available and build or shape the system to suit your needs and likes. The other thing to keep in mind is that just because many might say it can't be done doesn't make it so.

---

### Post by DuckHook on 2017-04-15
If OP is still tracking this thread, the link in my sig: ***Resources for Newcomers*** is useful.

I have found that irrespective of learning style, it is useful to approach the process systematically. Start with the easy stuff. The harder stuff will come up naturally as you ask more questions based on your use and knowledge of the easy stuff. To that end, I have found the following websites to be especially good because they introduce you to Ubuntu and Linux gently, but yet are sufficiently meaty that they don't stop at just a superficial level:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Trusty](http://ubuntuguide.org/wiki/Ubuntu:Trusty)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://linuxjourney.com](https://linuxjourney.com)

---

### Post by maclenin on 2017-04-15
Essentially, necessity is the mother of invention. Jump in and start using the system. As you get stuck you go looking for solutions which build your understanding.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) < --- lore-worthy introduction
[https://ubuntuforums.org/](https://ubuntuforums.org/) < --- go-to source
[https://www.google.com/](https://www.google.com/) < --- for all else

---

### Post by jamiehennings on 2017-04-18
There are various websites you can check out Linux tutorials. YouTube is the best platform if you want to learn more efficiently because there are various lectures by experienced person in form of videos to explain the concepts in easy way.

---

### Post by poorguy on 2017-04-19
This may help.

[https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by LastDino on 2017-04-21
> **maclenin said:**
> **Essentially, necessity is the mother of invention**. Jump in and start using the system. As you get stuck you go looking for solutions which build your understanding.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) < --- lore-worthy introduction
[https://ubuntuforums.org/](https://ubuntuforums.org/) < --- go-to source
[https://www.google.com/](https://www.google.com/) < --- for all else

So much this. 

If you're trying to know it all with Linux, it will not be one way approach of either reading book or watching videos. 

At least for me it was
>Faced a problem/wanted to do something/experiment
>Searched for solution (You will be surprised how detailed the Ubuntu Wiki and Ask Ubuntu threads are)
>If failed to get the solution, post a thread on forum
>usually someone with great amount of knowledge comes by and show you direction
>Later I build on it according to my needs

After continuous use of 3 years and many distro's, I've managed  to still be around and all my home computers have Linux installed, had one of my friends converted to Linux and he convinced his boss to have Ubuntu on all his office computers.

---

### Post by elsmandino2 on 2017-04-25
Just wanted to pop back on here and thank everyone for the input - you have clearly put in a lot of time and effort in to your replies and wanted you to know that it is very much appreciated.

I first read all the suggested reading material - some of this didn't make sense but after a lot of googling and rereading, it started to click.

I also started just fiddling with my PC generally as suggested.  In conjunction with the reading material, I started to then learn the new terms that allowed me to start searching for solutions.

All in all I really am starting to get Linux now - this was my fourth attempt in about 10 years but I think I am able to stick with it this time.

Would suggest that anyone else who is struggling with Linux to read all the threads and just stick with it - you will get there in the end.

Thanks again.

---

### Post by LastDino on 2017-04-26
Good luck for your Linux journey!

---

