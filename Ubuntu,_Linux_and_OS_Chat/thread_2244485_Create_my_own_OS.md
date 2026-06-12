---
title: "Create my own OS"
date: 2014-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Roelf_Langley_Ruff on 2014-09-16
Hello everyone. Not sure where to start with this so ill just ramble on. I tried Ubuntu a year a go or so and loved it buuuut didn't have time to learn the code and what not. Now im back at it, still in love with it and have time lol. That being said, I have looked into linux itself and it has me fascinated. I want to create my own OS from absolute scratch completely custom for me. I've always loved creating things, I even plan to make my own computer later, so this idea hooked me. Sooo basically, how in the world do I start this? I know absolutely nothing besides having used a computer for years casually and for gaming.

---

### Post by T.J. on 2014-09-16
Try Linux from Scratch or Gentoo Linux if you want to get an understanding of how Linux works without actually being a programmer. =)  You're embarking on a great learning experience.  It won't always be easy, but persevere and you will learn a lot that can be applied anywhere.  I do wish the the best.

---

### Post by grahammechanical on 2014-09-16
Your post reminds me of the man that asked a local person for directions to a certain place. The local man thought about it for a while and then said, "If I was you I would not start from here." This is not the place to start

> [COLOR=#000000]I know absolutely nothing besides having used a computer for years casually and for gaming.[/COLOR]

Have you defined what you mean by "my own OS?" Have you identified the components that make up a Distribution? Are you thinking of taking the software of other developers and bringing it altogether in a Linux distribution? Or do you want to write your own code? You did say, "from absolute scratch."

---

### Post by endlessinstant on 2014-09-16
Truly writing your own OS requires a fairly sophisticated understanding of computer science.  Linux itself was modeled on the older UNIX rather than truly being imagined from scratch.   You can build your own Linux system with a minimum of technical knowledge so long as you are willing to research and learn.  There are many, many great guides on the internet for this purpose.  

I would personally recommend that you build a functional system with an Ubuntu or Debian install before you embark on a more complex install.   Arch Linux is a good choice to move onto from there.  [This guide from Lifehacker]("http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process") is a little old but is quite good if you are a non-technical user.   Ideally you'll have a secondary machine that you can use to troubleshoot as it is very possible you will break something.   Breaking can be good though as it can teach you a lot about what NOT to do which is just as important as knowing what to do.   This is part of the reason I recommend you cut your teeth on a stable Debian or Ubuntu setup.   It's a lot easier to recover from a critical error and get a working system if you have an Ubuntu Live CD/USB ready to go to set your system up if you accidently fry something.   You can also use Debian/Ubuntu to experiment with different components you might be interested in like the different Desktop Environments (KDE, Gnome, Xfce, etc.) and test out the different types of software you might want.   This will help you know what to install when you are ready to build your own system.   

The big advantage that distros like Arch and Slackware have over Ubuntu is that they are very minimal by default so you can add in only the parts you want and can build a very efficient machine, often with software compiled to your specific hardware so everything will be very fast and responsive.  While you don't get this with Ubuntu, you still get the extensive customization you might want in terms of swapping out and configuring DEs and other software packages.   Some of these other distros also use rolling updates instead of targeted updates so you don't have to wait for the next release to use the latest and greatest software.    

Once you've been around Linux long enough to have at least a basic understanding of how it works (things like **packages, desktop environments, **and **file structure**) [Linux From Scratch ]("http://www.linuxfromscratch.org/") is an amazing resource if you want to do EVERYTHING by yourself.

---

### Post by ibjsb4 on 2014-09-16
You being new to this sort of thing, I would suggest something that does the basics for you.

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

That will make it easier than starting with just a terminal (text) only install, but still will not be a walk in the park.  There is a hefty learning curve to this.  Myself, I would say that it took me six months to build something that I like and another six months before I had it tweaked to my satisfaction.  But I don't think the mini-remix was around back then as I started with the mini iso.

If you have a computer with enough resources, I would also recommend doing your build in a virtual machine as you will be changing things around many many times.  A VM will allow you to restore your build by taking snapshots of it.  Kind of like the windows restore feature.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

And setting up a VM is like building your own, a skill in its self.

---

### Post by Roelf_Langley_Ruff on 2014-09-16
Thank you all for your responses.In response to Tj, i'll look into it thank you. In response to grahammechanical, What I mean by my own OS is literally eventually being able to create my own absolutely custom OS with code created by me,inothwerwords as scratch as scratch can possibly get. No,  but I am in the process. As a stepping stone I may very well do that to learn things, but not as the final product or goal no. In response to endlessinstant, ill definitely use that! and in response to ibjsb4, perfect, ^^ I love things that are hard and always have.

---

### Post by Tadaen_Sylvermane on 2014-09-16
> [COLOR=#000000] able to create my own absolutely custom OS with code created by me[/COLOR]

If you got 1300 years to spare with 175 million laying about.. maybe.

From a 2004 article, revised 2011.

[http://www.dwheeler.com/essays/linux-kernel-cost.html](http://www.dwheeler.com/essays/linux-kernel-cost.html)

This is just the kernel. No software.

 > Total Physical Source Lines of Code (SLOC)                = 4,287,449
 Development Effort Estimate, Person-Years (Person-Months) = 1,302.68 (15,632)
  (Basic COCOMO model, Person-Months = 2.4 * (KSLOC**1.05))
 Schedule Estimate, Years (Months)                         = 8.17 (98.10)
  (Basic COCOMO model, Months = 2.5 * (person-months**0.38))
 Estimated Average Number of Developers (Effort/Schedule)  = 159.35
 Total Estimated Cost to Develop                           = $ 175,974,824
  (average salary = $56,286/year, overhead = 2.40).
 SLOCCount is Open Source Software/Free Software, licensed under the FSF GPL.
 Please credit this data as "generated using David A. Wheeler's 'SLOCCount'."

Taking on a project like this is not for the faint of heart. I had the same aspirations as you but in the end I decided I would rather spend my time using my computer than custom building every little thing... combined with my sheer laziness. I've tried all the major distros except gentoo at this point. Am back on Kubuntu now because I just don't have the desire I once had. In the end though if you really want to do it, do it. There is nothing to lose by learning to code, and a great deal to gain. Just don't expect to write your own os from the ground up with new source, at least in your lifetime.


Basically... don't try to reinvent the wheel.

---

### Post by Roelf_Langley_Ruff on 2014-09-17
Thank you for your advice. I will take it into account, i'm still going to try of course. Even if I don't reach my goal, as you and everyone else stated I can still learn a lot. And at the very least I can make a custom OS from using multiple sources already made.

---

### Post by rg4w on 2014-09-17
As entire OS is a lot of work.  Perhaps you might start with one corner of it and see how that goes.  A file manager would be relatively easy to do, and you could use high-level tools like Python, Xojo, LiveCode or other GUI scripting languages to explore your ideas.

---

