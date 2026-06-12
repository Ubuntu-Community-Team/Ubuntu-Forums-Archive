---
title: "Linux curiosities"
date: 2011-03-26
forum: The Cafe
---

### Post by leviathan8 on 2011-03-26
As you may already think, this thread is all about curiosities regarding to the Linux operating system. Anyone can feel free to post their curiosities, and the veteran users may share their responses with us.

I will start:

If you noticed, the cache memory on RAM goes up whenever file managing is issued. For example, I have 4 GiB of RAM memory installed, and let's say I copy a file that is 3 GiB big somewhere. At this point, the RAM's cache is filled up. I do know that this is not a problem, but I wonder why is this done? In order to preserve the files somewhere if by any means the copy action gets corrupted? 

I would like to hear your questions too. :P

---

### Post by d3v1150m471c on 2011-03-26
your machine reads the file to be copied, puts a copy of it into ram, and then reads the file in the ram to be placed elsewhere on the hdd. it's way easier for a system to read from ram than to read from a harddisk so for various reasons it will do something of this nature. IE, you ever wonder why you can play a song while it's downloading? the computer doesn't always need to read an entire file to do what it needs to do. it will load sections of it or all of it at a time depending on the program and do what it does best.

---

### Post by ssam on 2011-03-26
when you read or write a file it get cached in RAM. if you need to read it again it is already in RAM so this is much faster. if a program needs the RAM it gets priority over cached files.

try this.

reboot your computer, or run:
echo 1 > /proc/sys/vm/drop_caches
to clear the cache

start a large application eg firefox or openoffice
quit the application
start it again

notice how fast it was the second time. thats because all the files it needed were already in the cache

---

### Post by Legendary_Bibo on 2011-03-26
My question is why is Compiz like the most amazing thing when you're drunk? Also, why is it that when I'm drunk the video tearing with the ATI drivers stops happening, and the animation of "Teh Cubez"  is so much smoother.

---

### Post by Random_Dude on 2011-03-26
> **Legendary_Bibo said:**
> My question is why is Compiz like the most amazing thing when you're drunk? Also, why is it that when I'm drunk the video tearing with the ATI drivers stops happening, and the animation of "Teh Cubez"  is so much smoother.

This raises another question: why are you playing around with compiz while drunk? :biggrin:

---

### Post by Dustin2128 on 2011-03-26
> **Random_Dude said:**
> This raises another question: why are you playing around with compiz while drunk? :biggrin:
It's the only way to play around with compiz.

---

### Post by debiansu on 2011-03-26
> **dustin2128 said:**
> it's the only way to play around with compiz.

:? ??

---

### Post by 3Miro on 2011-03-26
- Only in an alternative state of mind can one appreciate the real beauty of Compiz.

- RAM not used is RAM wasted, Linux will take as much RAM as it needs and then use the rest to cache the HDD. Large file manipulations are smoother in Linux than Windows or OSX.

- Linux curiousily, even though there are so many graphial environments, there is an undelying standard. You can run Plasam desktop with KDE applets under Gnome and you an run KDE with Metacity.

---

### Post by d3v1150m471c on 2011-03-27
> **Dustin2128 said:**
> It's the only way to play around with compiz.
+1
lmfao

---

### Post by d3v1150m471c on 2011-03-27
> **3Miro said:**
> Linux curiousily, even though there are so many graphial environments, there is an undelying standard. You can run Plasam desktop with KDE applets under Gnome and you an run KDE with Metacity.

you'll notice, if you install a kde app for the first time, or a gtk app for the first time whilst using the opposite manager, it will also download the libraries and what not for it. while kde, or gnome, etc. will takeover the app still runs and calls the rest of the gui from the proper library.

---

### Post by leviathan8 on 2011-04-15
Here's one for you: what was the first Linux distro that offered a live CD to test the os and in which year it appeared?

---

### Post by jerenept on 2011-04-15
> **leviathan8 said:**
> Here's one for you: what was the first Linux distro that offered a live CD to test the os and in which year it appeared?

Knoppix...i think in 1995?

I dunno the year, but i'm fairly sure it's  knoppix

---

### Post by leviathan8 on 2011-04-22
This is rather Ubuntu related, but, here you go. Summing up all the programs in repositories that users can **directly** interact with, what would be the total number of them? When I talk about applications that the end-user directly interacts with, I DO NOT include libs, kernel stuff, dependencies, back-ends, and such.

tl;dr: the number of all applications a user can download and use, not including libs, dependencies, kernel stuff, modules, cli utilities, etc. You get my point. :)

---

### Post by barbedsaber on 2011-04-22
> **leviathan8 said:**
> This is rather Ubuntu related, but, here you go. Summing up all the programs in repositories that users can **directly** interact with, what would be the total number of them? When I talk about applications that the end-user directly interacts with, I DO NOT include libs, kernel stuff, dependencies, back-ends, and such.

tl;dr: the number of all applications a user can download and use, not including libs, dependencies, kernel stuff, modules, cli utilities, etc. You get my point. :)

over NINE THOASAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAND

---

### Post by leviathan8 on 2011-04-25
It seems like I'm the only one posting here. :c
Ok, I've got 2 more curiosities. 

What Linux distro's do those supercomputers use?

And the second:

As seen in the command 'uptime', what does that **Load Average** represent?

---

### Post by 3Miro on 2011-04-25
> **leviathan8 said:**
> 
What Linux distro's do those supercomputers use?


The ones that I have seen, all use Red Hat or CentOS. I am assuming the really big ones use something heavily customized.

> 
As seen in the command 'uptime', what does that **Load Average** represent?

How much was your CPU loaded. If you just idle then Load Average will be small. If you are running heavy tasks (i.e. converting video files, playing games, and/or use scientific software), then LA would be huge.

---

### Post by leviathan8 on 2011-04-26
Hello, I would have another question.
Assuming that I want to upgrade my laptop's RAM memory from 2 GiB to 4 GiB, and I install the -generic-pae kernel, will the update manager continue to update my -generic kernel (the initial install with 2 Gib memory) or the -generic-pae kernel (after the upgrade)?

---

### Post by leviathan8 on 2011-04-26
Hey, I found a new one. Excuse me for such an early bumping, but look at this one.

First of all, **DO NOT EXECUTE THIS COMMAND.** It will crash your computer.
Secondly, what is actually happening when we issue this command, and what does each symbol stand for? Really strange, isn't it?

```
:(){:|:&};:
```

---

### Post by Paqman on 2011-04-26
> **leviathan8 said:**
> Hello, I would have another question.
Assuming that I want to upgrade my laptop's RAM memory from 2 GiB to 4 GiB, and I install the -generic-pae kernel, will the update manager continue to update my -generic kernel (the initial install with 2 Gib memory) or the -generic-pae kernel (after the upgrade)?

Kernel updates are controlled by the meta-packages you mention. When a new kernel is released the meta-package is changed so that it depends on the new kernel, so the package manager grabs the new kernel to satisfy the dependency. If you have both meta-packages installed and allow them both to update, you will continue to get the new kernels they depend on as they're released, even if you never actually boot into them.

This would be a bit of a waste of hard drive space and internet bandwidth, but would have no adverse effect on your system.

---

### Post by 3Miro on 2011-04-26
> **leviathan8 said:**
> Hey, I found a new one. Excuse me for such an early bumping, but look at this one.

First of all, **DO NOT EXECUTE THIS COMMAND.** It will crash your computer.
Secondly, what is actually happening when we issue this command, and what does each symbol stand for? Really strange, isn't it?

```
:(){:|:&};:
```

This defines a function with no name that doesn't take any parameters (I think, but I am not 100% sure). Then the function calls itself twice, creating infinite recursion. Every level of recursion takes memory, so you soon use up all of your memory.

There are strange commands like that in every language. They are not obvious, but they do something. This one breaks the system, other commands can simply be challenging to decipher.

This is one that I like in C++:
```
 int a = 1;
int b = 2;
int c = a+++++b;
```
The question is: what are the values of a, b and c after this code executes (and it will compile and execute). This will not break anything, it is just challenging to predict.

---

### Post by lisati on 2011-04-26
> **leviathan8 said:**
> Hey, I found a new one. Excuse me for such an early bumping, but look at this one.


Have a look here: [http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

---

### Post by leviathan8 on 2011-05-16
Hey again.
This is bit off the topic, but I don't want to open a new thread for a question.

So, what's happening with Ubuntu 10.04? I haven't received updates since 5 days. Is it just me or other people haven't received either? Sorry for this dumb question but I'm being worried whether there is something going wrong with my computer.  :confused:

---

### Post by walt.smith1960 on 2011-05-16
> **leviathan8 said:**
> It seems like I'm the only one posting here. :c
Ok, I've got 2 more curiosities. 

What Linux distro's do those supercomputers use?
........


I was curious about the same thing when the Watson-on-Jeopardy thing was going on.  It was running Suse Enterprise Server, 2880 Power7 cores and 16 terabytes of RAM.  
[http://www.zdnet.com/blog/open-source/what-makes-ibms-watson-run/8208](http://www.zdnet.com/blog/open-source/what-makes-ibms-watson-run/8208)

Another article-I didn't save it- had an interesting perspective by one of the developers.  It was to the effect that "using considerable resources and and a room full of state of the art hardware we have managed to partially duplicate the functions of a body part that will fit in a shoebox and run on a Tuna sandwich"  :lolflag:

---

### Post by leviathan8 on 2011-05-16
> **walt.smith1960 said:**
> I was curious about the same thing when the Watson-on-Jeopardy thing was going on.  It was running Suse Enterprise Server, 2880 Power7 cores and 16 terabytes of RAM.  
[http://www.zdnet.com/blog/open-source/what-makes-ibms-watson-run/8208](http://www.zdnet.com/blog/open-source/what-makes-ibms-watson-run/8208)


I can't actually imagine how those thousands of cores would fit in the System tab in the gnome-system-monitor (just a fictive scenario, I doubt they use any GUI). :lolflag: Oh wow, and 16 terra's of RAM! That would be capable of caching everything on the internet for offline use lol.

---

### Post by leviathan8 on 2011-05-18
Here's a funnier one for you guys.

Why wasn't the precedent version of Ubuntu 4.10 not released?

[COLOR="White"]because Ubuntu 4.04 was not found.[/COLOR]

(hover for answer)

---

