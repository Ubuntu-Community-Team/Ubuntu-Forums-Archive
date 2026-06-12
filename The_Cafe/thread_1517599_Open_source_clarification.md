---
title: "Open source clarification"
date: 2010-06-25
forum: The Cafe
---

### Post by MerlinCoder on 2010-06-25
Hi guys, this is going to be a very stupid noobie question, but its always something that has puzzled me.

If you release the source code to an application, such as apache web server, could  a hacker find out exactly how it interfaces with with your connection and the internet and be able to fine tailor an exploit program for it? 

It has always supprised me that firefox is a stronger browser than IE when anyone can see exactly how it works.

I just think that if windows became open source, the amount of hacks and viruses out there would explode.

---

### Post by warfacegod on 2010-06-25
> I just think that if windows became open source, the amount of hacks and viruses out there would explode.

This may or may not be correct but it seems like a reasonable assumption to me. We'll almost certainly never find out. Windows seems to be tailor made for viruses* and Linux isn't. Just because something is Open Source doesn't mean that it's easier to write viruses for. Allot of it depends on how the app's or OS's code is written in the first place. I can't really give you a better explanation than that because I'm stretching my knowledge as it is.



**Generic term guys. I'm not interested in getting into another argument about what is and is not a virus. The average user thinks of all of these things as viruses and for the sake of simplicity, that's good enough.*

---

### Post by philinux on 2010-06-25
Moved to Café.

---

### Post by Sporkman on 2010-06-25
> **MerlinCoder said:**
> If you release the source code to an application, such as apache web server, could  a hacker find out exactly how it interfaces with with your connection and the internet and be able to fine tailor an exploit program for it? 


Yes.

There needs to also be a bunch of "good guys" who also look for exploits, and close them in the code.

---

### Post by mk1w86 on 2010-06-25
> If you release the source code to an application, such as apache web server, could a hacker find out exactly how it interfaces with with your connection and the internet and be able to fine tailor an exploit program for it? 


If you look at it another way, sure people with malicious intent can see the code but at the same time all the people reporting or fixing the bugs and security holes can also see it.  This is one of the great strengths of open source, the number of eyes that see the code, a piece of open source software can be seen by many people whereas at Microsoft as you give in your example a far smaller proportion of people will see the code, let alone fix it because so few know about it. ;)

---

### Post by MindSz on 2010-06-25
A crude example would be to look at these forums. Many posts are about 'How do I get this to work in Ubuntu?' and you see tons of replies from different users with different ways to achieve the task you require.

Some of them work, some of them don't, but most of the time, just looking at the feedback they got you can tell which is which.

---

### Post by MerlinCoder on 2010-06-25
Cool!

I have so much to learn with programming and I've never worked on anything where security is required so I have a bit of a blind spot when it comes to this kind of thing.

Hopefully Linux will get me looking at source code and understanding how things work a little better :D

Thanks for the clarification guys!

---

### Post by undecim on 2010-06-25
Yes, a hacker can look at the source code and see how a program works

However, in order to write an exploit that would allow them to attack your computer, they will first need to find a flaw in the source code that allows them to do that.

Meanwhile, thousands of others review the same source code looking to fix such flaws. In most cases, for high-profile applications like the Linux kernel and Apache, a fix will be available within a day or two, leaving a very small window for an attacker to find a flaw, write an exploit, and make use of it.

This is usually safer than closed source software, however. With closed source software, any black hats (i.e. bad guys) that would have the skill to be exploiting open source software (i.e. those who understand overflow errors and the like and can write the specific code to exploit that) will also know how to dissect closed source software, watch API calls that it makes, scan its memory, etc. To determine how the software works. The reason that this is less safe than open source software is that it is *illegal*, as outlined in most EULAs (including Microsoft's) to try to figure out how the software works, which means only black hats will be doing that since they don't care about breaking the law.

---

### Post by Sporkman on 2010-06-25
> **undecim said:**
> Meanwhile, thousands of others review the same source code looking to fix such flaws.

In the high-profile case, yes. Not necessarily so with more obscure projects (which nevertheless people are running on pcs & servers).

---

### Post by undecim on 2010-06-25
> **Sporkman said:**
> In the high-profile case, yes. Not necessarily so with more obscure projects (which nevertheless people are running on pcs & servers).

True, but those are less likely to be targeted.

---

### Post by warfacegod on 2010-06-25
> The reason that this is less safe than open source software is that it is illegal, as outlined in most EULAs (including Microsoft's) to try to figure out how the software works, which means only black hats will be doing that since they don't care about breaking the law.

This seems like circular logic to me. Blackhats break the law because what they are doing is illegal because they don't care about breaking the law.

I believe creating viruses* is generally considered illegal regardless of the source code it is aimed at being open or otherwise.

---

### Post by Jay Car on 2010-06-25
> **MerlinCoder said:**
> Hi guys, this is going to be a very stupid noobie question, but its always something that has puzzled me.

If you release the source code to an application, such as apache web server, could  a hacker find out exactly how it interfaces with with your connection and the internet and be able to fine tailor an exploit program for it? 

It has always supprised me that firefox is a stronger browser than IE when anyone can see exactly how it works.

I just think that if windows became open source, the amount of hacks and viruses out there would explode.


I remember wondering about those things too. It takes time to begin seeing things in a different way from what we are used to. I think things became a bit clearer to me when I read this [2004 interview]("http://seattletimes.nwsource.com/html/businesstechnology/2002059632_linus11.html") with Linus Torvalds. 

This question and answer was what I remember most, it's where he explains about security:

> Q. How can Linux avoid the security problems that have affected Windows?

A. Better design and actually caring about them. Having the guts to really fixing fundamental design mistakes, rather than trying to work around them.

Also, if someone knows that the code they create can be seen by the world, especially by others who code, it's a powerful incentive to pay attention to quality. Good work builds trust and a good reputation. 

From an end user's viewpoint, it's truly amazing to have access to some of the worlds most beautiful software. Awesome, indeed.


...

---

### Post by MerlinCoder on 2010-06-25
I find open source a truely fascinating idea, the thought that you open it up to the community to improve on things rather than keeping it locked away in house has always seemed like it could become a very dodgy idea, what with all the hackers out there.
On the flip side it sounds very exciting, the potential for it to grow, well, just look at the firefox addon community!

I guess I need to start looking at the good in people.

I find that these days most of the programs I use on a day to day basis* are all open source, should make my transition into Ubuntu quite easy :)

[SIZE=1]*If you are interested: Firefox, Filezilla, Notepad++ and open office.[/SIZE]

---

### Post by jetsam on 2010-06-25
> **MerlinCoder said:**
> I find open source a truely fascinating idea, the thought that you open it up to the community to improve on things rather than keeping it locked away in house has always seemed like it could become a very dodgy idea, what with all the hackers out there.

Open source projects protect against ill-intended hackers with a code review process, and the distros prevent malicious exploitation of the actual software builds by similar review processes.  

Plus there are a good number of people reporting security vulnerabilities on the most important and exposed packages, like firefox. 

It all seems to work well.  I feel much more secure on the net using  Linux than Windows. By and large, you only get hard core security concerns in Linux if you expose a server to the open internet.

---

### Post by nrs on 2010-06-25
Code isn't magically secured by open sourcing it. Open source software has a reputation for being secure because generally public auditing goes hand in hand with public development. Everything is vulnerable to scrutiny. 

if you didn't have this I think a dam bursting type scenario could happen. This goes for Windows & any large closed software project. I think it'd be pretty disastrous short-term but better long.

---

### Post by mooreted on 2010-06-25
There is also the fact that software is distributed mostly by software repositories rather than downloading files from some fly-by-night website. You would have to get the source code, modify it with your malware tweaks, get it past a code review and hope you can sneak by the repository maintainers who are going to notice the code was modified. 

But then, even in the Windows world, the old-school cracking virus, worm, etc methods of infecting computers is pretty much dead. It's so much easier to offer a clueless user a bouncing bunny screen saver and let them infect the computer for you.

---

### Post by MerlinCoder on 2010-07-05
I found on another post some free books, one of them is: "The Cathedral and the Bazzar". I have been told it is the closest thing the open source community has to a bible so I am going to give it a read later today :)

---

