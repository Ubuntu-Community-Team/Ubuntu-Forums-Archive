---
title: "Programming in Systems Security as a career"
date: 2011-06-05
forum: Security
---

### Post by cdelapena on 2011-06-05
How will learning C++ (or any other language) help me in my career -- Systems Security? If programming does help, which language would be the most useful to know?

---

### Post by 3xp10r3r|X13 on 2011-06-05
You just named it:  C, C++ and maybe java

--> In my opinion those are the most powerful ones (ubuntu itself is about 85% written in C and C++)

---

### Post by Thewhistlingwind on 2011-06-05
> **3xp10r3r|X13 said:**
> You just named it:  C, C++ and maybe java

--> In my opinion those are the most powerful ones (ubuntu itself is about 85% written in C and C++)

For systems security? Really?

I would think you'd be better served by the scripting languages that sysadmins love so much.........

Also LINUX is written in C and C++.

---

### Post by Lars Noodén on 2011-06-05
> **cdelapena said:**
> How will learning C++ (or any other language) help me in my career -- Systems Security? If programming does help, which language would be the most useful to know?

C rather than C++ for systems and networking.  Some Java and C++ would be nice.  Java for web apps.  Perl and a little python is necessary for system administration.

---

### Post by 3xp10r3r|X13 on 2011-06-05
> **Thewhistlingwind said:**
> For systems security? Really?

I would think you'd be better served by the scripting languages that sysadmins love so much.........

Also LINUX is written in C and C++.
So where is your problem?

I mentioned Java and that Linux (including ubuntu) is mostly written in C and C++ ???

(C is quite important as well - not just those scripting languages)
I just don't get your point..

---

### Post by Lars Noodén on 2011-06-05
> **3xp10r3r|X13 said:**
> So where is your problem?

I mentioned Java and that Linux (including ubuntu) is mostly written in C and C++ ???

(C is quite important as well - not just those scripting languages)
I just don't get your point..

The [linux kernel is still written in C](http://www.kerneltrap.org/node/2067), not [C++](http://www.tux.org/lkml/#s15-3).  C++ is for mobile apps.  Java is for mobile apps and web services.  Perl is for web services and system administration.  Python is for some web services and some system administration, and so on.

---

### Post by Kinstonian on 2011-06-05
You can use programming to help with any security related job, and which language(s) depends on what exactly it is you want to do.

If you want to deal with web application security PHP, Javascript, etc.

If you want to do exploit development, penetration testing or malware analysis?  Probably languages like C, assembly and Python.

Want to do security admin work?  To be honest, as a Perl programmer I'd suggest you try Python since everything seems to be moving towards Python for security related scripting, rather than Perl.

---

### Post by Thewhistlingwind on 2011-06-06
> **Lars Noodén said:**
> The [linux kernel is still written in C]("http://www.kerneltrap.org/node/2067"), not [C++]("http://www.tux.org/lkml/#s15-3").

theres like, ten thousand lines of c++ in there, 99.9% of it is C though.

---

### Post by Lars Noodén on 2011-06-06
> **Thewhistlingwind said:**
> theres like, ten thousand lines of c++ in there, 99.9% of it is C though.

It's written in [C](http://www.kernel.org/pub/linux/docs/lkml/#s15-3), not C++.  At [over 13 000 000 lines of code](http://arstechnica.com/open-source/news/2010/12/linux-kernel-13-million-lines-over-5-patches-per-hour.ars), ten thousand would be smaller than 0.08%

---

### Post by cdelapena on 2011-06-06
Perhaps you guys can answer this question: How have UNIX commands evolved since its creation? Does every UNIX-like operating system use UNIX commands?

---

### Post by Kinstonian on 2011-06-06
> **cdelapena said:**
> How will learning C++ (or any other language) help me in my career -- Systems Security? If programming does help, which language would be the most useful to know?

> **cdelapena said:**
> Perhaps you guys can answer this question: How have UNIX commands evolved since its creation? Does every UNIX-like operating system use UNIX commands?

Now I'm starting to get the feeling we're doing your homework for you.

---

### Post by raja.genupula on 2011-06-06
C,C++,Java 

these are best man

i love to use C++ than java

---

### Post by doas777 on 2011-06-06
Op, disregarding the choice of langague, it is useful to have some programming skill in security, because it allows you to see the complete picture. the difference between knowing the definition of a drive-by-download, and really understanding how one works, requires some knowledge of how the related softwares work. 

I'd recommend focusing on a web based platform for learning (php perhaps?), as it's inherent networked nature puts security at the forefront, and exposes you to many of the application vulnerabilities that can be exploited in the modern world (things like sql injection, XSS, CRSF, credential leakage, etc). you'll get an understanding of how the server and the browser work together, helping you understand how to secure both the server and the client.

---

### Post by Thewhistlingwind on 2011-06-06
> **Lars Noodén said:**
>  At [over 13 000 000 lines of code]("http://arstechnica.com/open-source/news/2010/12/linux-kernel-13-million-lines-over-5-patches-per-hour.ars"), ten thousand would be smaller than 0.08%

You know what I meant.

Anyway, to the OP. This really sounds more like an impractical homework question, the GNU utilities are shared by most (If not all.) modern UNIX systems, but for a time AFAIK the different Unices were proprietary, and in many cases had different commands.

(And to anyone who would construe that sentence to mean I somehow think there exist no proprietary Unix implementations, quit trolling.)

---

### Post by Lars Noodén on 2011-06-07
> **cdelapena said:**
>  How have UNIX commands evolved since its creation? 

It's a secret, but there are no commands.  There is just a bunch of small programs that do one single thing very well.  The number vary from system to system because you can always add the ones you want or need.  In a plain vanilla Ubuntu, there are 
[list]
[*]  0115 /bin
[*]  1171 /sbin
[*]  0135 /usr/bin
[*]  0211 /usr/sbin
[*]  
[*]  1632 Total
[/list]

As you customize the system more are added.

> **cdelapena said:**
> Does every UNIX-like operating system use UNIX commands?

As mentioned, most systems share a base of GNU utilities from the GNU project.

---

