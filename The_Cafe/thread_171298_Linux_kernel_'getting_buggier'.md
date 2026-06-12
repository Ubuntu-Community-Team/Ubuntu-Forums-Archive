---
title: "Linux kernel 'getting buggier'"
date: 2006-05-06
forum: The Cafe
---

### Post by YourSurrogateGod on 2006-05-06
> Andrew Morton, the lead maintainer of the Linux production kernel, is worried that an increasing number of defects are appearing in the 2.6 kernel and is considering drastic action to resolve it.

"I believe the 2.6 kernel is slowly getting buggier. It seems we're adding bugs at a higher rate than we're fixing them," Morton said, in a talk at the LinuxTag conference in Wiesbaden, Germany, on Friday.

Morton admitted he hasn't yet proved this statistically, but has noticed that he is getting more emails with bug reports. If he is able to confirm the increasing defect rate, he may temporarily halt the kernel development process to spend time resolving bugs.

"A little action item I've given myself is to confirm that this increasing defect rate is really happening. If it is, we need to do something about it." he said. "Kernel developers will need to reapportion their time and spend more time fixing bugs. We may possibly have a bug-fix only kernel cycle, which is purely for fixing up long-standing bugs." 

_One problem is that few developers are motivated to work on bugs, according to Morton. This is particularly a problem for bugs that affect old computers or peripherals, as kernel developers working for corporations don't tend to care about out-of-date hardware, he said._ Nowadays, many kernel developers are employed by IT companies, such as hardware manufacturers, which can cause problems as they can mainly be motivated by self-interest.

-snip-

During his talk, Morton discussed the 2.6 kernel development process, explaining that if people want to get their code into the kernel they should send it to him, not Linus Torvalds, who maintains the development kernel. Morton manages the "-mm" code branch, which is where patches are tested before being added to the development kernel.

"The way an individual can get their code into the kernel is by sending it to me. I will buffer it in my [mm] tree and send it to Linus. It's fairly rare for a person to send patch to Linus and get it in. In fact Linus is fairly random at patches at the best of times. Generally, Linus will cc: it to me because he knows I'll pick it up," said Morton. 

-snip-

[http://news.zdnet.co.uk/0,39020330,39267255,00.htm](http://news.zdnet.co.uk/0,39020330,39267255,00.htm)

Interesting, but hardly surprising.

The kernel has gotten more complex lately, so this is to be expected. There are 2 ways to lessen/reduce this problem.
1) Shrink the size of the kernel.
2) Implement methods from the get-go that reduce the size of the kernel.

It would be pretty far-fetched to even suggest that the kernel would sink down to the level of some Windows operating systems (please no flame-war.) Plus, one has to take into account the fact that as more and more people contribute source to Linux, not everyone is a flawless programmer (or close to it), as a result, there will be more problems (one solution would be to look at what Vista is attempting to do, have drivers run away from the kernel in user mode, so that if something does fail, it won't take down the OS.)

Sorry, about that, went on a little rant there :) .

---

### Post by Lovechild on 2006-05-06
My take on Andrews larger number of bugreports is basically that many more people use vanilla kernels now, as well as the general number of users having gone up - which would naturally result in more bug notices from users. Nothing to worry about, the kernel has had a history of having good peer review and quick critical fix releases, I suspect it will continue that way without foricng developers to cease active development in favor of pure bugfixing.

Another thing to consider is that stablity of users is not an upstream issue, they will never get the amount of testing vendors get done - upstream does the rough edges but they can't possbily hit all the corner cases, active distro development makes sure we hit the non-obvious bugs in the first place. Meaning that forcing developers to look over code that they already wrote to the best of their ability for bugs is rather fruitless, some bugs simply only occure on a certain configuration that the upstream developer might not have access to and he will never suspect it untill someone hit the bug in the first place.

I think the biggest benefit we could get would be from having automated buildfarm running benchmarks and tests, as well as extensive use of tools like sparse, Ingo' lock checker and coverity.

---

### Post by Stormy Eyes on 2006-05-06
[QUOTE=YourSurrogateGod]The kernel has gotten more complex lately, so this is to be expected. There are 2 ways to lessen/reduce this problem.
1) Shrink the size of the kernel.
2) Implement methods from the get-go that reduce the size of the kernel.[/QUOTE]

I could be wrong, since it's been over a year since I last compiled the kernel (haven't needed to since I switched to Ubuntu, which surprised me at first since I had to compile it when I used SuSE to get acceptable desktop performance), but isn't the kernel implemented in a manner that allows the administrator to compile just about everything as a module, and then only use the necessary modules? If the kernel is "too big", is that really the kernel developers' fault, or the fault of the person building the kernel for not compiling things as modules?

---

### Post by Lovechild on 2006-05-06
[QUOTE=Stormy Eyes]I could be wrong, since it's been over a year since I last compiled the kernel (haven't needed to since I switched to Ubuntu, which surprised me at first since I had to compile it when I used SuSE to get acceptable desktop performance), but isn't the kernel implemented in a manner that allows the administrator to compile just about everything as a module, and then only use the necessary modules? If the kernel is "too big", is that really the kernel developers' fault, or the fault of the person building the kernel for not compiling things as modules?[/QUOTE]


Half right, a lot of the code is modular, however the amount of code that needs to be compiled statically in the kernel has gone up steadily over the years, the 2.6 kernel no longer fits on a floppy disk anymore in any general usable case e.g. but there are good reasons for this, take the scheduler - it went from a 4-5 line algorithm to a monster that is maybe what 1000-1500 lines but the new one scales better and we gain all sorts of fancy interactivity tweaking that we couldn't before with the old scheduler. Sometimes it's a tradeoff for technology.

That being said the developers seem to be very attuned to the size issue and regularly do tweaking to get the most out of the scheduler without loosing performance or features.

---

### Post by YourSurrogateGod on 2006-05-06
[QUOTE=Stormy Eyes]I could be wrong, since it's been over a year since I last compiled the kernel (haven't needed to since I switched to Ubuntu, which surprised me at first since I had to compile it when I used SuSE to get acceptable desktop performance), but isn't the kernel implemented in a manner that allows the administrator to compile just about everything as a module, and then only use the necessary modules? If the kernel is "too big", is that really the kernel developers' fault, or the fault of the person building the kernel for not compiling things as modules?[/QUOTE]
Excellent point. You're right, I believe that you can compile it in modules (it's possible in Gentoo, why not in other distros?)

However, as Ubuntu and other distros are moving more to the desktop, people will want more and more gadgets and the like (not everyone is satisfied with the bare basics, eye-candy will become more prevalent), which will cause things to increase in size and more bugs to pop-up. I believe that this this is one source of an increase in bugs that that developer is seeing.

---

### Post by YourSurrogateGod on 2006-05-06
[QUOTE=Lovechild]I think the biggest benefit we could get would be from having automated buildfarm running benchmarks and tests, as well as extensive use of tools like sparse, Ingo' lock checker and coverity.[/QUOTE]
What are those tools?

---

### Post by Lovechild on 2006-05-06
[QUOTE=YourSurrogateGod]Excellent point. You're right, I believe that you can compile it in modules (it's possible in Gentoo, why not in other distros?)

However, as Ubuntu and other distros are moving more to the desktop, people will want more and more gadgets and the like (not everyone is satisfied with the bare basics, eye-candy will become more prevalent), which will cause things to increase in size and more bugs to pop-up. I believe that this this is one source of an increase in bugs that that developer is seeing.[/QUOTE]

The important thing here is to differciate between packaged size (the binary kernel package) and the actual size (what gets loaded) - the common tactic is to build the kernel very modular and package every module in the kernel package, but since they are loaded on demand the runtime size is not at all equal to the package size.

---

### Post by YourSurrogateGod on 2006-05-06
[QUOTE=Lovechild]The important thing here is to differciate between packaged size (the binary kernel package) and the actual size (what gets loaded) - the common tactic is to build the kernel very modular and package every module in the kernel package, but since they are loaded on demand the runtime size is not at all equal to the package size.[/QUOTE]
Sorry, I don't understand what you mean by packaged and actual size. Could you explain it to me?

---

### Post by Lovechild on 2006-05-06
[QUOTE=YourSurrogateGod]What are those tools?[/QUOTE]

Static analysis tools, think of it as a souped up compiler that throws all kinds of warnings by looking at the flow of the code to see if you did things the right way - like take locks in the right order, allocated and deallocated memory right, ensure that you don't have pointer dereference..

It's a means of catching errors in the code without having the overhead of running a constant  information gathering tool in runtime - needless to say it's very hard to get right but even tools with a high false positive rate do catch plenty of errors.

The Department of Homeland security recently paid $250.000 USD to Coverity for them to run their tool on the most used FOSS products like the Linux kernel, GNOME, KDE, VIM, EMACS, etc. Results can be found here: [http://scan.coverity.com/](http://scan.coverity.com/)

Sparse is a similar tool written by Linus I think

Ingo's lock checker basically checks that you grab the locks in the right order to avoid deadlocks and general nastiness.

---

### Post by Lovechild on 2006-05-06
[QUOTE=YourSurrogateGod]Sorry, I don't understand what you mean by packaged and actual size. Could you explain it to me?[/QUOTE]

okay. when you compile a kernel for packaging in say a .deb file, you basically take the output of that and tar it up - right?

This means that every module compiled goes into same package not a seperate one - but this does not affect the size of the kernel you run based on that package since you don't load all the modules.

Say we have the kernel plus modules a, b and c.

You might only need the kernel and module a to use your machine, so that's all that gets loaded, this means that the difference is package size and runtime size for you is the combined size of modules b and c. 

Is that simple enough for you?

---

### Post by YourSurrogateGod on 2006-05-06
[QUOTE=Lovechild]okay. when you compile a kernel for packaging in say a .deb file, you basically take the output of that and tar it up - right?

This means that every module compiled goes into same package not a seperate one - but this does not affect the size of the kernel you run based on that package since you don't load all the modules.

Say we have the kernel plus modules a, b and c.

You might only need the kernel and module a to use your machine, so that's all that gets loaded, this means that the difference is package size and runtime size for you is the combined size of modules b and c. 

Is that simple enough for you?[/QUOTE]
... in retrospect, this was a bad question to ask while I'm hung over.

---

### Post by Lovechild on 2006-05-06
[QUOTE=YourSurrogateGod]... in retrospect, this was a bad question to ask while I'm hung over.[/QUOTE]

No worries I shall just make jokes and belittle you with my superior intellect.

---

### Post by YourSurrogateGod on 2006-05-06
[QUOTE=Lovechild]No worries I shall just make jokes and belittle you with my superior intellect.[/QUOTE]
Hey there, this thing is temporary :) .

---

### Post by Lovechild on 2006-05-06
[QUOTE=YourSurrogateGod]Hey there, this thing is temporary :) .[/QUOTE]

Only if you stop drinking my good friend..

To your health!! cheers

---

### Post by prizrak on 2006-05-06
I mostly think that while kernel is getting a bit more buggy (it's a long ways from the first one). However I think the main issue is the fact that there are alot more users on a bigger variety of hardware lately. This of course results in more obscure bugs as well as increase in reports due to sheer number of people.

---

### Post by Lovechild on 2006-05-06
[Dave Jones](http://kernelslacker.livejournal.com/37851.html) chimes in

---

### Post by commodore on 2006-05-06
I don't like this at all. I like how BSDs are made. Especially OpenBSD. No code will be included in the kernel until it's widely tested and fixed. I also don't like how unimportant stuff they have in the Linux kernel.

---

### Post by helpme on 2006-05-06
[QUOTE=commodore]I don't like this at all.
[/QUOTE]
OMG, that will be devastating to the kernel devs.
[QUOTE=commodore]
I like how BSDs are made. Especially OpenBSD.
[/QUOTE]
You must be talking about the friendly head developer...
[QUOTE=commodore]
No code will be included in the kernel until it's widely tested and fixed.
[/QUOTE]
Yes and as we all know, random, untested code gets into the linux kernel all the time...
[QUOTE=commodore]
I also don't like how unimportant stuff they have in the Linux kernel.[/QUOTE]
For example?

---

### Post by Stormy Eyes on 2006-05-06
[QUOTE=commodore]I don't like this at all. I like how BSDs are made. Especially OpenBSD. No code will be included in the kernel until it's widely tested and fixed. I also don't like how unimportant stuff they have in the Linux kernel.[/QUOTE]

If you know so much about what should and should not be included in the Linux kernel, then why aren't you in charge of maintaining the production branch of the kernel?

---

### Post by YourSurrogateGod on 2006-05-07
[QUOTE=Lovechild]Only if you stop drinking my good friend..

To your health!! cheers[/QUOTE]
It's the night before graduation and I have nothing to do, can you blame me?

---

### Post by mips on 2006-05-07
[QUOTE=Stormy Eyes]If you know so much about what should and should not be included in the Linux kernel, then why aren't you in charge of maintaining the production branch of the kernel?[/QUOTE]

He has a point though. Question is, do you want the latest and greatest or do you want stable & secure. Ubuntu is kinda like Debians wild child if I can put it that way. If you want more stable then look at Debian which moves slow for various reasons, including poltics.

All depends on your needs.

---

### Post by Lovechild on 2006-05-07
[QUOTE=mips]He has a point though. Question is, do you want the latest and greatest or do you want stable & secure. Ubuntu is kinda like Debians wild child if I can put it that way. If you want more stable then look at Debian which moves slow for various reasons, including poltics.

All depends on your needs.[/QUOTE]

This assumes that we can't do both.

Which is entirely possible, maintain the same level of peer review we have now and use automated tools to find those hard to spot bugs. I might remind you that sitting and staring at code really has a minimal chance of finding a bug, take the recent image display code security bugs - nobody thought that there were security bugs in such code, yet we had them.. in nearly every library, this was well reviewed code, properly debugged. So you have to know what to look for, we generally for non-obvious security bug don't know what to look for before someone gets a bright idea or the bad guys use the hole.

We have tools to combat security issues, we can protect the stack using several GCC and glibc tricks not only for the kernel but for userspace as well. it's admittance that we will never fix every single bug so instead we put our guard up. Numbers show thus far that this catches and stops roughly half of all security bugs.

To sum up, it would be possible to run a high pace of development but if we do that we will need good static analysis tools, automated stress tests and finally a means of gathering information in runtime (I thinking systemtap maybe). We also need to guard ourselves the best we can instead of arrogantly assuming that we are infalliable coders.

---

### Post by mips on 2006-05-07
[QUOTE=Lovechild]This assumes that we can't do both.
[/QUOTE]

Not really, both are possible but it will just be harder&take a bit longer. If you are only talking about the kernel then it should not be to hard. If we start talking about an entire distro then it is a different story as you will have to get the entire dev community involved.

---

### Post by prizrak on 2006-05-07
I don't think that possible bugginess of the kernel is that much of an issue. 
a) there is still no proof it is true
b) this is open source - if it gets too buggy it can be forked :)

---

### Post by Lovechild on 2006-05-07
[QUOTE=mips]Not really, both are possible but it will just be harder&take a bit longer. If you are only talking about the kernel then it should not be to hard. If we start talking about an entire distro then it is a different story as you will have to get the entire dev community involved.[/QUOTE]


If you build it they will come, make it easy for developers to run automated tests after each change and they will - look at GStreamer, they automated valgrind runs and build tests and it definately shows in the quality of their code.

It is a lot easier than you make it out to be.

Take a simple thing like making sure your code compiles without warnings (if the warning is bogus that is a reason to fix the compiler not turning the option off), or take something like OpenBSD does, play fully legal tricks with the stack and see how much stuff only works because of assumptions made about the layout (Fedora does something similar)..

---

