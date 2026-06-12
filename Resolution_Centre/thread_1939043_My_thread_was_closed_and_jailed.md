---
title: "My thread was closed and jailed"
date: 2012-03-10
forum: Resolution Centre
---

### Post by ic7805reg on 2012-03-10
My thread was closed and jailed - what exactly does that mean?

Please either delete the tread from the system or reopen it without insinuating that I was trying to hack - last post said: "hacking it not supported on this forum"

I was asking questions to be able to load a LiveCD that I got with the book entitled "Hacking the art of exploitation" by Jon Erickson. Please read about it at amazon.com

[http://www.amazon.com/Hacking-The-Art-Exploitation-Edition/dp/1593271441/ref=sr_1_1?s=books&ie=UTF8&qid=1331429744&sr=1-1](http://www.amazon.com/Hacking-The-Art-Exploitation-Edition/dp/1593271441/ref=sr_1_1?s=books&ie=UTF8&qid=1331429744&sr=1-1)

It is not illegal (like one of the post stated but then changed) to learn about hacking. It is illegal to hack but not illegal to learn about it. All IT professionals should learn about hacking so they can protect themselves and others from hackers. You have to know how hackers hack in order to by able to protect yourself from them.

Thank you

---

### Post by cariboo on 2012-03-10
Illegal activities, are against the forum code of conduct. Please review the Code of Conduct available [here]("http://ubuntuforums.org/index.php?page=policy").

If you want advise on hacking, this forum is not the place to ask about it, your thread will remain closed.

---

### Post by Iowan on 2012-03-10
This topic has gotten quite convoluted, both here and IRC. 
First, your thread is tucked quite safely in a holding area that we call "The Jail" (or obvious reasons) - only you and the staff have access to it. 
Second, neither your thread nor the book preview specifically mention(at least that I've seen) whether the 7.04 system is set up as a honeypot (ie. easier to crack) system, or if it is set up as a hacker tool.

 If it is customized, it's going to be harder for others to support. Plus, it is a very old version. Much has changed, and setup is different than current systems. 

In previewing the book, I notice phrases like:

> Corrupt system memory to run arbitrary code using buffer overflows and format strings


Inspect processor registers and system memory with a debugger to gain a real understanding of what is happening


Outsmart common security measures like nonexecutable stacks and intrusion detection systems


Gain access to a remote server using port-binding or connect-back shellcode, and alter a server's logging behavior to hide your presence


Redirect network traffic, conceal open ports, and hijack TCP connections


Crack encrypted wireless traffic using the FMS attack, and speed up brute-force attacks using a password probability matrix Although you have not specifically asked how to do these, the inference is that these are the final goal. You understand why these topics cannot be supported? So, while you think you are asking for assistance loading a 7.04 system, others see you asking for help with hijacking, corrupting, and cracking.

---

### Post by bodhi.zazen on 2012-03-11
This was also discussed with you on IRC.

First, 7.10 is outdated, beyond end of life and not supported here. IMO you are wasting your time with this sort of activity on an outdated, patched version of 7.10. Security and penetration testing evolve far too quickly for that version of Ubuntu to be of much use. You should look to the publisher of the book you purchased for an update of some kind.

Second, this site is not the best for penetration testing. Many of the tools you would use are not in the repositories. You have been referred by multiple community members to backtrack which supports this sort of activity. This sort of activity is a double edged sword and as has been explained to you can be used inappropriately.

Third, a simple google search on the tools included in backtrack will lead you to much more appropriates and up to date information, resources, online communities, and books.

---

### Post by ic7805reg on 2012-03-14
You people seem to jump to conclusions that are incorrect and unjust. I was repeatedly pressed to explain why I wanted help to load Ubuntu 7.04 instead of going straight to Ubuntu 11's supported release. I told you repeatedly why, it came with the book I bought (Ubuntu 7.04 LiveCD). If you go back and read the whole thread, with an open mind, of course, you will see that I was not trying to do anything illegal, only trying to follow the instructions in the book (you might want to read it and take into consideration that I'm new at this and wanted to follow the book instead of someone that may or may-not have read the book or understand where I was coming from - newbie). Seeing as how I got unjustly attacked and labelled, I no longer seek your help in fear I will be treated unjustly in the future. backtrack-linux.org seems to meet my needs, so at least I did get something for the black eye that you gave me. I thank you for the backtrack-linux.org tip but not for the unjustly received black eye. Think about it, did I ask how to do anything illegal - no, I only was asking questions on how to load Ubuntu 7.04 that I got as a LiveCD in a book. I still want to learn Linux because of availability of software at a reasonable cost, mostly free like open-office, CAD, circuit design and etc. but I will seek a different Linux flavor such as Debian or what ever. Hopefully, those people will be more helpful in answering questions instead of attacking someone that bought a book with the word hacking in the title.

The book I bought was "http://www.amazon.com/Hacking-The-Art-Exploitation-Edition/dp/1593271441/ref=sr_1_1?s=books&ie=UTF8&qid=1331701298&sr=1-1" and you people seem to feel it is a crime try to read it and learn from it. Well, maybe it is out dated and the stuff that's in it doesn't work any more - that's exactly why I needed to load Ubuntu 7.04 because on a newer release like Ubuntu 11, you're probably right, it won't work. So in that case I wasted my time and money to try to do something that no longer works. What fun or enjoyment would I get out of that - none! So I pressed to get answers to load Ubuntu 7.04 that should still work.

Do I want this thread re-posted, hell no, not with the NDAA passing. I'm afraid I'll go to jail for your unjustly attacks, if some gov't agent reads your attacks without thinking about it - you didn't so why would I think they might - I'll end up in jail unjustly for asking question on how to load a LiveCD that I got with a book I bought.

Instead of ending the thread with something like "we don't support hacking" will you please end the thread with something like "we don't support old releases"?

PS: If nothing in the book works in a resent supported releases, because things have changed, then why would I want to load Ubuntu 11? I wanted to follow the book with things working and didn't care if they work now in the present with all the changed in the new releases. If you can't understand this, then so be it, for there is nothing to say for you to see or understand my point of view.

---

### Post by bodhi.zazen on 2012-03-14
> **ic7805reg said:**
> you people seem to feel it is a crime try to read it and learn from it. 

What you are doing , reading and learning, is not a crime, but the information certainly can be misuesd.

We do not support Ubuntu 7.10 , it is at end of life, sorry about that, but that is something you need to bring up with the publisher of the book. In the future, be more careful about what you buy.

We support Ubuntu, but not penetration testing. Many of the tools are not in the repositories, and your CD is patched, so not only is it outdated, but it is not the default Ubuntu applications.

For Penetration testing you need more up to date information, and probably stat with backtrack. If you use applications (or patches) that are not in the Ubuntu Repositories, we do not support them here.

So we are happy to assist you with supported versions of Ubuntu , technical difficulties with installing applications in the repos, we are not a training site for how to use and interpret these tools and the information they provide.

---

