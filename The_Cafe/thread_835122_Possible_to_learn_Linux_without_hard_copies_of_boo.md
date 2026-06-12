---
title: "Possible to learn Linux without hard copies of books?"
date: 2008-06-20
forum: The Cafe
---

### Post by meindian523 on 2008-06-20
Is it possible to learn linux as in how it works,memory,how bits and bytes are transferred from one place to another,the kernel,system calls,etc relying solely on free books on the internet and personal experience?Also assuming that you want to finish it in about 3 years?Ambitious,isn't it?:):guitar::lolflag:

---

### Post by Bloch on 2008-06-20
Most of what you mention is "learning about copmputers and IT" rather than learning linux.

"Learning Linux" means different things to different people. For many users moving from Windows XP it means getting familiar with the Gnome interface, learning the range of software available and how to install it, learning a little bit about permissions and simple commands like ls.

What you are talking about is very high level stuff that most users of linux don't know about. If you are into that you would probably love one of the more hardcore distros like slackware or gentoo.

---

### Post by meindian523 on 2008-06-20
True,but I'm new(not very) to Linux(don't look at those beans) and I tried Gentoo,it seems it didn't like my motherboard(Intel D101GGC) which,supposedly,Gentoo supported first.It refused to install.

Also,I hardly know any programming except the courses in C and C++ taught us at college,which is actually an insult to the courses in C and C++ available out there.Plus I'm doing Engineering,so the only time I get to really concentrate is between semesters.

I'm looking to try and get into kernel programming.

---

### Post by FFighter on 2008-06-20
Everything is possible. 

And the impossible just delays a little more :P

But really, of course you can, why not?

---

### Post by meindian523 on 2008-06-20
Ah,ok,so could you recommend some good resources.I've been looking at tldp.org,but I honestly feel the content is a bit dated.And I need a source for learning C proper,over and above the apology which was taught us.

---

### Post by jomiolto on 2008-06-20
> **meindian523 said:**
> Ah,ok,so could you recommend some good resources.I've been looking at tldp.org,but I honestly feel the content is a bit dated.And I need a source for learning C proper,over and above the apology which was taught us.

If you really want to understand the kernel internals, you should know C well and some Assembler would help too (it is needed for some of the very low level stuff). Then you should also have some knowledge about operating system theory (multitasking, memory management, etc.), and finally, if you want to understand drivers and the other stuff that interfaces with the hardware, it would also be useful to get some documentation about the hardware in question (Intel has great documentation for their processors, but I'm not so sure about all the other stuff).

There is also some documentation with the kernel source, but I don't really have any idea how good/easy to understand that documentation is. If that documentation is good, it would naturally be a great resource for learning about the kernel. (There is also a Kernel Hackers Guide at Linux Documentation project, but that seems quite antiquated and might be quite obsoleted.)

Decent books are always good for learning, but you can also find all of this stuff from the Internet, if you bother to search for it (Google is your friend, as always). If you search for "operating system development", you will find plenty of resources on the subject, but quite a lot of those are about writing a new operating system from scratch, which is quite different from hacking an already existing system.

With quick Googling I found, for example, this book about C: [http://publications.gbdirect.co.uk/c_book/]("http://publications.gbdirect.co.uk/c_book/"). I only took a quick look at it, but it seems decent. This might be worth checking out too: [http://www2.its.strath.ac.uk/courses/c/]("http://www2.its.strath.ac.uk/courses/c/").

Here's also an Assembler tutorial that seems good: [http://drpaulcarter.com/pcasm/]("http://drpaulcarter.com/pcasm/").

For operating system theory I don't know of any good, extensive resource on the web, but you could probably find something about that too. At least you can check out the [Operating System Development]("http://en.wikipedia.org/wiki/Operating_system_development") page at Wikipedia, and follow the references to information about Memory Management, Multitasking, Task Management and Scheduling (those are some of the core features of an OS). This page about Linux memory management in particular seems interesting: [http://linux-mm.org/]("http://linux-mm.org/").

I wish you good luck on your research! Operating system development isn't exactly the easiest branch of computer science, but you don't need to be a superhuman for it, if you just have the perseverance and will to learn.

---

### Post by meindian523 on 2008-06-20
Thanks!Google is a friend to be true,but only when you ask it the right questions.Unfortunately,I haven't got the tricks to get the best results out of Google just yet,but I still don't want to be spoon fed.I shall find out and keep coming back with questions.

---

### Post by original_jamingrit on 2008-06-20
You might be interested in checking out this: [http://janitor.kernelnewbies.org/](http://janitor.kernelnewbies.org/)

make sure to read the FAQ

---

### Post by Catharina on 2008-06-20
Maybe you find something to help you here:

[http://www.open-of-course.org/courses/course/index.php]("http://www.open-of-course.org/courses/course/index.php")

---

### Post by Ioky on 2008-06-21
I have to agrees  with the other that what are you saying is more like a computer science/ IT subject matter. But sure, why not? try slackware or Arch Linux, you will learn a lot from those distro. plus, all the sources are there. If you are welling to take your time, and look it up. Plus, all those book you can found, aren't really into deep to anything in general. There is just too much that can't be written in a book.

---

### Post by krokodil on 2008-06-21
If you're interested in how Linux is put together you might try Linux From Scratch as well:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by saulgoode on 2008-06-21
[Linux Kernel In A Nutshell]("http://www.kroah.com/lkn/")

---

### Post by meindian523 on 2008-06-21
Well,actually what I'm interested is everything,like how hardware talks to software,when we save something,how those bits and bytes go from RAM to HDD,Process Management, and I said learn Linux because I'm particularly interested in how Linux accomplishes those tasks.Thanks to all those who replied,I will look through and keep asking questions.

---

### Post by plb on 2008-06-21
Go use slackware for a while. You will learn a lot from using it.

---

### Post by john_spiral on 2008-06-21
Before buying a copy of O'reilly's **Running Linux** I got loads of info from wikipedia.

---

