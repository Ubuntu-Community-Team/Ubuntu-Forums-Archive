---
title: "Mysteries of Linux"
date: 2010-10-18
forum: The Cafe
---

### Post by madmax.santana on 2010-10-18
How would I define Linux? I was writing a research paper regarding it and there is confusion all over internet.

- Is it a **kernel**?
- Is it an **operating system**?
- Is it a ***minimal* operating system** which needs other applications to work fully?
- Why do we call it *monolithic* when I can still see *processes running in separate threads*?
- If Linux *itself* is an **operating system**, why do I need *other **packages*** to use Ubuntu and not be done with just installing Linux?
- If Linux is just a **kernel**, why does *Wikipedia* call it an **operating system**?
- **Torvalds** defined it as an **operating system** in his initial posts. Why did it need **GNU *applications*** then?

---

### Post by kio_http on 2010-10-18
1. Kernel

---

### Post by JackNocturne on 2010-10-18
Definitely a kernel;)

---

### Post by Simian Man on 2010-10-18
It's confusing, but the name "Linux" refers to both the kernel and a full system built with that kernel.

As to the monolithic question, Linux is very modular.  Monolithic doesn't mean that everything is one giant process, but that the whole of the kernel runs is privileged mode - that is it's allowed to do anything it wants.

---

### Post by Spice Weasel on 2010-10-18
Linux is the kernel, GNU/Linux (or ulibc+BusyBox/Linux) is the operating system.

---

### Post by LowSky on 2010-10-18
Don't use Wikipedia as an information source.

Linux is a Kernel
GNU is an instruction set
GNU/Linux is an operating system
Ubuntu is a distrobution which is basically just a prepackaged form of Gnu/Linux usually based around a package manager.
X11 is graphic user interface in which other GUI are built upon.
Gnome/KDE are Desktop enviroments built to run on top of X11

Linux is monolithicc, which means process start one at a time. It doesn't mean it cannot run job simultaniously. Especially with the advent of Multi-core processors

---

### Post by Bölvaður on 2010-10-18
1. we are not allowed to do your homework... but this will help you a LOT


Linux is the kernel.
But the definition of an operating system varies depending on who you talk to. It can range from just the kernel to the entire ecosystem of applications.
You will need to explain all of those different, or most popular definitions of operating systems briefly and pick one that you will use in the rest of the paper.

---

### Post by TNT1 on 2010-10-18
[http://www.linux.org/info/index.html](http://www.linux.org/info/index.html)

Seems a shame that we should have to do the research for you though...

---

### Post by Simian Man on 2010-10-18
> **LowSky said:**
> 
GNU is an instruction set
What?  No, x86 and Sparc are instruction sets.  GNU is a collection of programs.

> **LowSky said:**
> Linux is monolithicc, which means process start one at a time. It doesn't mean it cannot run job simultaniously. Especially with the advent of Multi-core processors
That has nothing to do with it, it has to do with kernel vs. user mode as I explained.

> **LowSky said:**
> 
GNU/Linux is an operating system
That is a view put forth by Richard "Sour Grapes" Stallman.  In actuality "Linux" refers both to the kernel and a full OS built on it.  That has been the nomenclature for years.

---

### Post by limestone on 2010-10-18
Linus calls it an operating system because it uses GNU utilities. Only then it's an OS.
But Linux itself is just a **Kernel.**
Most Linux distros are GNU/Linux because they all uses alot of GNU tools.

---

### Post by CraigPaleo on 2010-10-18
> **Spice Weasel said:**
> Linux is the kernel, GNU/Linux (or ulibc+BusyBox/Linux) is the operating system.

That may be the rule but in my experience, most people refer to the kernel as the Linux kernel and refer to the OS as Linux. 

The former is [prescriptive]("http://en.wikipedia.org/wiki/Linguistic_prescription") while the latter is [descriptive]("http://en.wikipedia.org/wiki/Descriptive_linguistics"), linguistically speaking.

---

### Post by madmax.santana on 2010-10-19
> **Bölvaður said:**
> 1. we are not allowed to do your homework... but this will help you a LOT.

Hey! That's offending! I am very egoistically self reliant when it comes to homework... :p

I am writing this research paper for fun. Just a hobby. Man, I am a communication systems engineer in the making. I don't have vaguely anything to do with operating systems. Well, maybe, RTOS sometimes, and that is when I have to do extra work to replace the missing software engineer.

There was a call for research papers in some seminar and I thought as I am attending it anyway, why not do a little research and let people know there's world beyond Windows...

---

### Post by madmax.santana on 2010-10-19
> **CraigPaleo said:**
> That may be the rule but in my experience, most people refer to the kernel as the Linux kernel and refer to the OS as Linux. 

The former is [prescriptive]("http://en.wikipedia.org/wiki/Linguistic_prescription") while the latter is [descriptive]("http://en.wikipedia.org/wiki/Descriptive_linguistics"), linguistically speaking.

Boy oh boy... That's how Wikipedia says it. But I am talking about the technical terminology, not alias.

---

### Post by madmax.santana on 2010-10-19
> **Simian Man said:**
> It's confusing, but the name "Linux" refers to both the kernel and a full system built with that kernel.

As to the monolithic question, Linux is very modular.  Monolithic doesn't mean that everything is one giant process, but that the whole of the kernel runs is privileged mode - that is it's allowed to do anything it wants.

I get the monolithic-thingy...
And indeed, names are very confusing... In fact that is the topic. :)

---

### Post by madmax.santana on 2010-10-19
> **LowSky said:**
> Don't use Wikipedia as an information source.

Linux is a Kernel
GNU is an instruction set
GNU/Linux is an operating system
Ubuntu is a distrobution which is basically just a prepackaged form of Gnu/Linux usually based around a package manager.
X11 is graphic user interface in which other GUI are built upon.
Gnome/KDE are Desktop enviroments built to run on top of X11

Linux is monolithicc, which means process start one at a time. It doesn't mean it cannot run job simultaniously. Especially with the advent of Multi-core processors
That's one nice piece of detailed information. Thanks. You're the man.

---

### Post by madmax.santana on 2010-10-19
> **Simian Man said:**
> What?  No, x86 and Sparc are instruction sets.  GNU is a collection of programs.


That has nothing to do with it, it has to do with kernel vs. user mode as I explained.


That is a view put forth by Richard "Sour Grapes" Stallman.  In actuality "Linux" refers both to the kernel and a full OS built on it.  That has been the nomenclature for years.
There, you again blew my concepts leaving me in a muddy confusion

---

### Post by alexan on 2010-10-19
Linux is a kernel..



no wait..




mmmh


no, it's just a kernel after all.

---

### Post by koenn on 2010-10-19
> **madmax.santana said:**
> That's one nice piece of detailed information. Thanks. You're the man.

> **madmax.santana said:**
> There, you again blew my concepts leaving me in a muddy confusion

So, apparently you prefer simple, clear cut information, even if it's incorrect.

That's going to be one interesting research paper ...

---

### Post by norm7446 on 2010-10-19
Hope these link's are of help.

[http://www.youtube.com/watch?v=HDOL7_7DB7k](http://www.youtube.com/watch?v=HDOL7_7DB7k) ( watch this three time's. On the second time just read the word's. )

[http://www.youtube.com/watch?v=EwL0G9wK8j4&feature=related](http://www.youtube.com/watch?v=EwL0G9wK8j4&feature=related) ( I Linux ) 

Linux = Kernel ( As it is always learning ) 

Linux + GUI + Ubuntu = 49

---

### Post by CraigPaleo on 2010-10-19
> **madmax.santana said:**
> Boy oh boy... That's how Wikipedia says it. But I am talking about the technical terminology, not alias.

But you wanted to know about the confusion. The confusion arises because there is the prescriptive definition of Linux and then there is the descriptive definition. 

I rarely see GNU/Linux used and when I do, it's *usually* in reference to that pedantic rule. 

Words are ultimately defined by their usage. "Linux" is used to describe a kernel, or an OS.

Examples: 
"Linux was created by Linus Torvalds". Here, Linux refers to the kernel.

"Linux is ready for the desktop." Here, Linux refers to an OS.

Context is needed to distinguish the two but most people are inclined to insert the word "kernel" rather than add "GNU" to differentiate the two.

---

### Post by hhh on 2010-10-19
Re: Linux kernel vs Linux, language evolves depending on how people use it, which is why irregardless and D'oh are in the Oxford English Dictionary. Since nobody but Stallman refers to Linux as gah-new-lin-uhx, Linux is an OS even if it's not strictly correct. Assuming your paper is for the general public, who don't even know what a kernel is other than popcorn, you can call Linux an OS.

---

### Post by madmax.santana on 2010-10-20
> **koenn said:**
> So, apparently you prefer simple, clear cut information, even if it's incorrect.

That's going to be one interesting research paper ...

LOL yeah!

No I am sorry I forgot to add something. It would be REALLY great if anyone could back his comments with solid references.

But then again, people would say I am looking for someone to do my homework. :p
Seriously, I just want to remove a confusion forever.

---

### Post by madmax.santana on 2010-10-20
> **CraigPaleo said:**
> But you wanted to know about the confusion. The confusion arises because there is the prescriptive definition of Linux and then there is the descriptive definition. 

I rarely see GNU/Linux used and when I do, it's *usually* in reference to that pedantic rule. 

Words are ultimately defined by their usage. "Linux" is used to describe a kernel, or an OS.

Examples: 
"Linux was created by Linus Torvalds". Here, Linux refers to the kernel.

"Linux is ready for the desktop." Here, Linux refers to an OS.

Context is needed to distinguish the two but most people are inclined to insert the word "kernel" rather than add "GNU" to differentiate the two.

I totally agree with everything you say. But you know, as it is supposed to be a research paper, information needs to be coherent with technical terms. You are absolutely right when you say any meaning could be taken depending on the context. But won't it blow the image of the paper if I title it "Linux Operating System" while it is technically known as a kernel in programmers' space? And everyone at the seminar is GONNA BE A PROGRAMMER...

Well, that bugs me a lot and right now my only mission in life is to contact Linus Torvalds himself and ask his views about it. :) By the way, does anyone know how to contact the man? :)

---

### Post by madmax.santana on 2010-10-20
> **norm7446 said:**
> Hope these link's are of help.

[http://www.youtube.com/watch?v=HDOL7_7DB7k](http://www.youtube.com/watch?v=HDOL7_7DB7k) ( watch this three time's. On the second time just read the word's. )

[http://www.youtube.com/watch?v=EwL0G9wK8j4&feature=related](http://www.youtube.com/watch?v=EwL0G9wK8j4&feature=related) ( I Linux ) 

Linux = Kernel ( As it is always learning ) 

Linux + GUI + Ubuntu = 49

I got your point. But it's learning doesn't mean it's a kernel. Operating systems do grow as well, don't they?

---

### Post by madmax.santana on 2010-10-20
> **hhh said:**
> Re: Linux kernel vs Linux, language evolves depending on how people use it, which is why irregardless and D'oh are in the Oxford English Dictionary. Since nobody but Stallman refers to Linux as gah-new-lin-uhx, Linux is an OS even if it's not strictly correct. Assuming your paper is for the general public, who don't even know what a kernel is other than popcorn, you can call Linux an OS.

Oh I must correct you there, pal... My paper is directed to people who write kernels everyday. :p It's a seminar, of PROGRAMMERS...

---

### Post by norm7446 on 2010-10-20
OK. How about this. With out the kernel would it still be Linux ?.

---

### Post by saulgoode on 2010-10-20
> **norm7446 said:**
> OK. How about this. With out the kernel would it still be Linux ?.

OK. How about this? Without GNU would it still be an operating system?*


* if you have the slightest inclination to respond "yes" then I invite you to delete */lib/libc.so.6* (GNU's GLIBC) from your system and see how well it operates.

---

### Post by madmax.santana on 2010-10-21
> **saulgoode said:**
> OK. How about this? Without GNU would it still be an operating system?*


* if you have the slightest inclination to respond "yes" then I invite you to delete */lib/libc.so.6* (GNU's GLIBC) from your system and see how well it operates.
Well I personally think it will work without the GNU software. But you will have to include *glibc* from some other source anyway. However, I think GNU is the only one producing generic libs for C in the open source domain. So it's a +1 for both of you. :)

---

### Post by Spice Weasel on 2010-10-21
> **saulgoode said:**
> OK. How about this? Without GNU would it still be an operating system?*


* if you have the slightest inclination to respond "yes" then I invite you to delete */lib/libc.so.6* (GNU's GLIBC) from your system and see how well it operates.

No such file or directory... I use BusyBox.

Also, there's uclibc.

---

### Post by Simian Man on 2010-10-22
> **saulgoode said:**
> OK. How about this? Without GNU would it still be an operating system?*


* if you have the slightest inclination to respond "yes" then I invite you to delete */lib/libc.so.6* (GNU's GLIBC) from your system and see how well it operates.

If you delete libpng.so your computer isn't going to work right either.  Does every library used get its way into the name of the OS?

And +1 to Spice Weasel.

---

### Post by linux-hack on 2010-10-22
> **kio_http said:**
> 1. Kernel

+1

---

### Post by norm7446 on 2010-10-23
How about this. Hypothetically, you have a newly built PC, with a completely blank H/Drive. You want to put Linux on to this new PC. But you do not have a Distro Disc to hand. So you built it all from source. In this scenario. When could you call what you have built as OS.

---

### Post by Spice Weasel on 2010-10-23
> **norm7446 said:**
> How about this. Hypothetically, you have a newly built PC, with a completely blank H/Drive. You want to put Linux on to this new PC. But you do not have a Distro Disc to hand. So you built it all from source. In this scenario. When could you call what you have built as OS.

You just download the kernel and build it from source?  I'd call the thing I "built as a OS" "worthless because all it will do is boot".

---

### Post by CraigPaleo on 2010-10-23
> **madmax.santana said:**
> I totally agree with everything you say. But you know, as it is supposed to be a research paper, information needs to be coherent with technical terms. You are absolutely right when you say any meaning could be taken depending on the context. But won't it blow the image of the paper if I title it "Linux Operating System" while it is technically known as a kernel in programmers' space? And everyone at the seminar is GONNA BE A PROGRAMMER...

To avoid ambiguity, don't use the word "Linux" by itself. That's when confusion arises. Use the terms "GNU/Linux" and "the Linux kernal." You could also specify at the beginning that for the purpose of your paper, "linux" will refer to the kernal while "GNU/linux" will refer to the OS. 

> Well, that bugs me a lot and right now my only mission in life is to contact Linus Torvalds himself and ask his views about it. :) By the way, does anyone know how to contact the man? :)

I had his number in my phone but I dropped it in the bay while fishing. :P

---

### Post by toupeiro on 2010-10-23
I don't see why everyone gets so up in arms over this.

Yes, Linux is a kernel, but Linux is also used as a reference to operating systems running a Linux kernel.  It has been this way since the inception of the operating system using said kernel, and has been socially accepted across the world.

There was a time when you couldn't find the word "ain't" in any printed English dictionary because it wasn't accepted as a word.  It is now printed, and defined in all currently printed English dictionaries.  In fact, according to Marriam-Webster, its first recorded use was in 1749.  That is a LONG time to protest that a word, isn't a word, when it's used all over the place.  The case with the usage of the word Linux is no different.  Get over it, it's both. :)

---

### Post by madmax.santana on 2010-10-23
> **CraigPaleo said:**
> 
I had his number in my phone but I dropped it in the bay while fishing. :P

LOL... Should I ask the fish?

---

### Post by norm7446 on 2010-10-23
> **Spice Weasel said:**
> You just download the kernel and build it from source?  I'd call the thing I "built as a OS" "worthless because all it will do is boot".


But because it boot's, is it or is it not an OS.

---

### Post by madmax.santana on 2010-10-23
> **CraigPaleo said:**
> To avoid ambiguity, don't use the word "Linux" by itself. That's when confusion arises. Use the terms "GNU/Linux" and "the Linux kernal." You could also specify at the beginning that for the purpose of your paper, "linux" will refer to the kernal while "GNU/linux" will refer to the OS. 


Yes! That's what I am gonna do. Perfect answer. Thank you Paleo.

---

### Post by CraigPaleo on 2010-10-23
> **madmax.santana said:**
> Yes! That's what I am gonna do. Perfect answer. Thank you Paleo.

You're welcome. Do I get a cookie? :)

---

### Post by Spice Weasel on 2010-10-24
> **norm7446 said:**
> But because it boot's, is it or is it not an OS.

It's an OS but a completely useless OS unless you download the GNU or Busy Box userland. Bit like asking if a dead person is still human.

Or calling Windows XP "Windows NT" sine that's the name of the kernel.

---

