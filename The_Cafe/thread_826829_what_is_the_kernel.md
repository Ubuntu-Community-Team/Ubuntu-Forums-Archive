---
title: "what is the kernel"
date: 2008-06-12
forum: The Cafe
---

### Post by gishaust on 2008-06-12
Hi everyone some asked me what is the linux kernel and I could not explain it. 

So is someone able to tell me what the linux kernel is. I need it in a "what the linux kernel is for dummies" format. I have look around the net a got a lot of technical stuff. 

thanks gishaust

---

### Post by sharks on 2008-06-12
This will answer u:
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by karellen on 2008-06-12
a simple answer would be "the core of the operation system"

---

### Post by kaboodle_fish on 2008-06-12
> **karellen said:**
> a simple answer would be "the core of the operation system"


Very much so 

They say a picture is worth a thousand words so 

[http://widefox.pbwiki.com/f/Monolithic_Kernel.png](http://widefox.pbwiki.com/f/Monolithic_Kernel.png)

---

### Post by NovaAesa on 2008-06-12
An easy way of explaining it (and very simlified) is saying that it is "the bits that go on behind the scenes".

---

### Post by jomiolto on 2008-06-12
Like the engine of a car? It's there and it is what makes the car move, but most people never need to bother with it, as long as it is there and does its job.

---

### Post by Trail on 2008-06-12
In very short, the big guy that does the job of managing resources (CPU, RAM, disks, ...) (providing read/write access to, synchronising, scheduling, ...) and also provides related services to 'user' applications.

---

### Post by aaaantoine on 2008-06-12
kaboodle_fish has it right with the picture link.  The kernel is the part of the operating system that deals directly with the hardware.  When kernel modules are loaded in, it is so they can also interface with specific components of hardware.

The kernel is the middle man.  Software sends commands to the kernel, which in turn communicates with the hardware.  It would be impossible to program a piece of software that communicates directly with hardware, unless you have a specific platform in mind, and know all of its intricacies.  The benefit of the kernel is, you program one piece of software, and then you can run it on any platform, as long as the kernel is there.

---

### Post by renzokuken on 2008-06-12
this help?

---

### Post by melrom on 2008-06-12
> 
The kernel

We should point out here that the focal point of any operating system is its 'kernel'. Without going into great detail, the kernel is what tells the big chip that controls your computer to do what you want the program that you're using to do. To use a metaphor, if you go to your favorite Italian restaurant and order 'Spaghetti alla Bolognese', this dish is like your operating system. There are a lot of things that go into making that dish like pasta, tomato sauce, meatballs and cheese. Well, the kernel is like the pasta. Without pasta, that dish doesn't exist. You might as well find some bread and make a sandwich. A plate of just pasta is fairly unappetizing. Without a kernel, an operating system doesn't exist. Without programs, a kernel is useless. 


SOURCE: [http://www.linux.org/lessons/beginner/l1/lesson1b.html](http://www.linux.org/lessons/beginner/l1/lesson1b.html)

---

### Post by KingTermite on 2008-06-12
Here are some diagrams that might put it in perspective better.

[IMG]http://photos.sys-con.com/story/res/38276/Haddad-2-Fig1.jpg[/IMG]


This diagram looks like its for a handheld device, but its the same principles.
[IMG]http://www.openmoko.com/uploaded_images/41.png[/IMG]

Another nice one:
[IMG]http://myy.helia.fi/~karte/media/linux-kernel-os-distro-app.jpg[/IMG]


Hope that helps somewhat. You kind of need a deeper understanding of Operating Systems (and computer architecutre) to fully grasp the concept. The "core" of the operating system is correct, but that makes little sense to somebody who doesn't understand the full import of what an operating system is.

---

### Post by gishaust on 2008-06-12
Thanks for all your great replies I have been looking at the pics and they have been very useful. I have a second question. So the kernel is really only a heap of drivers that work between the software say apache and the board or are drivers different again?

gishaust

---

### Post by KingTermite on 2008-06-12
> **gishaust said:**
> Thanks for all your great replies I have been looking at the pics and they have been very useful. I have a second question. So the kernel is really only a heap of drivers that work between the software say apache and the board or are drivers different again?

gishaust
No...the kernel is more than just a heap of drivers.

Some the really important modules in a kernel are:
**scheduler **- schedules which programs to run, switches between them to give the "appearance" of running simultaneously.

**Memory Manager** - manages memory used by apps, OS, etc.... Swaps when it needs to, pages in more memory when needed, etc...

**Decoder **- decodes instructions, and in some cases rearranges instructions or modules to run more efficiently (pipelining and multi-threading, etc...)


I guess in a sense you could kind of claim these are "motherboard" drivers, but I think they are probably still more than just that.

---

### Post by gishaust on 2008-06-12
Oh now i see, then how do bugs come about in the kernel? If everything has a job and it the kernel acts as the middle man and talks between the software package and the boards, cpu, ram and hard drives( I think). What cause a bug?

I am sorry if these are silly questions I am just trying to understand the fundamentals in layman's terms

---

### Post by Bruce M. on 2008-06-12
> **renzokuken said:**
> this help?

Now that is definitely good! Glad to see the sense of humour.

Interesting thread and one I'll watch as I've learned a few things here.

Funny, I always thought of the kernel for Linux as win.exe is to Windows.

Have a good one.
Bruce

---

### Post by Fedz on 2008-06-12
Nothing actually causes the bug as in a virus bug - it's different.

A bug is like a certain part of the code in the kernal that could or maybe been written better/different to streamline it or work better with various software/hardware ...etc.

As new and or modern hardware and software come available, new implimentations that are need or required are written into the code (kernal) for them to work.

The code's that complete anyway the vast majority is already done for quite a long time, I guess it needs tweaking now and again as time goes on ...

I'm not expert but, that's my understanding in laymens terms ;-)

---

### Post by cardinals_fan on 2008-06-12
> **gishaust said:**
> Oh now i see, then how do bugs come about in the kernel? If everything has a job and it the kernel acts as the middle man and talks between the software package and the boards, cpu, ram and hard drives( I think). What cause a bug?

I am sorry if these are silly questions I am just trying to understand the fundamentals in layman's terms
When a new version of the kernel is written, it has bugs just like any other new software.

---

### Post by Fedz on 2008-06-12
A bit of light reading before bed ;-)

[Kernel Comparison: Linux (2.6.22) versus Windows (Vista)](http://widefox.pbwiki.com/Kernel+Comparison+Linux+vs+Windows).

---

### Post by gishaust on 2008-06-12
So a bug really where the software code has trouble talking with the hardware which then cause the computer to do something unexpected!! would that  be one way you would explain it?

I didn't realize windows had a kernel it is news to me (long time windows user).

---

### Post by cardinals_fan on 2008-06-12
> **gishaust said:**
> So a bug really where the software code has trouble talking with the hardware which then cause the computer to do something unexpected!! would that  be one way you would explain it?

I didn't realize windows had a kernel it is news to me (long time windows user).
1. A bug is any place in the code where something doesn't work properly / needs improvement.  Nothing more, nothing less.

2. All OS's have kernels

A kernel is best summed up by these two sentences from Wikipedia:
> As a basic component of an operating system, a kernel provides the lowest-level abstraction layer for the resources (especially memory, processors and I/O devices) that application software must control to perform its function.and> A seed /&#712;si&#720;d/ (help·info) (in some plants, referred to as a **kernel**) is a small embryonic plant enclosed in a covering called the seed coat, usually with some stored food.

---

### Post by Fedz on 2008-06-12
> **gishaust said:**
> So a bug really where the software code has trouble with the hardware which then cause the computer to do something unexpected!! would that  be one way you would explain it.
In a small way but, something like that scenario is more likely a possible configuration problem with the actual software or the actual software code itself (not the kernel) ...

---

### Post by KingTermite on 2008-06-12
A bug is typically when a programmer makes a mistake in the code. Just like you hear people talk about "gremlins" in a machine that isn't working right, they call them "bugs" in computer world.

The kernel as mentioned earlier has a lot of the basic device drivers in it, so it directly talks to the hardware. So let's give you a small example of what a bug is.

Let's say the application asks the kernel to transfer 15 bytes of data from memory address A to memory address B. A programmer could write a program like this in C:

xfer_mem(fromAddress x, toAddress y, size)
{

for (i=1; i<size; i++)
{
toAddress[i] = fromAddress[i];
}

To call this, the program would have called:
xfer_mem(&A, &B, 15);

Don't worry about A and B...they are just variables. I'm just using them as placeholders as if they were real memory addresses.

Do you see the error this would cause?

i goes from to < 15, so it would only transfer 14 bytes of data.

That would be a BUG!


And cardinal_fan was correct, all Operating Systems have a kernel. It's the core of any OS.

---

### Post by gishaust on 2008-06-13
Wow the response has been fantastic thanks to everyone. But I have been doing some research. When they say the kernel is modular what does this mean? Is it like KingTermite diagram where all the core services are different?

---

### Post by gishaust on 2008-06-13
I have had another thought. If all OS have a kernel then what is so special between say windows, linux and Unix. I am not trying to create a war as the above statement might. I love using linux. But I want to know the fundamentals in layman's terms please.

---

### Post by schauerlich on 2008-06-13
> **gishaust said:**
> Wow the response has been fantastic thanks to everyone. But I have been doing some research. When they say the kernel is modular what does this mean? Is it like KingTermite diagram where all the core services are different?

Modular means that the kernel is written with different sections of code that can be swapped out for difference pieces of code, and for the most part things will work the way they should if everything lines up right. 

> **gishaust said:**
> I have had another thought. If all OS have a kernel then what is so special between say windows, linux and Unix. I am not trying to create a war as the above statement might. I love using linux. But I want to know the fundamentals in layman's terms please.

The kernel is a very small part of an operating system. All of the layers above the kernel are what make up the majority of an operating system and the majority of what most users see.

---

### Post by BrokeBody on 2008-06-13
> **gishaust said:**
> Hi everyone some asked me what is the linux kernel and I could not explain it. 

So is someone able to tell me what the linux kernel is. I need it in a "what the linux kernel is for dummies" format. I have look around the net a got a lot of technical stuff. 

thanks gishaust

In short (roughly),

As the processor is the heart of a hardware, kernel is the heart of a software.

---

### Post by KingTermite on 2008-06-13
> **gishaust said:**
> Wow the response has been fantastic thanks to everyone. But I have been doing some research. When they say the kernel is modular what does this mean? Is it like KingTermite diagram where all the core services are different?

Modular, yes, is somewhat like the diagrams I posted. It means that the code is very modular versus all jammed together. Modular is typically a better style because each "piece" of code is self contained in a very small functionality and therefore less prone to bugs. Also, its easier to read modular code. It does come with overhead though....you have to fill up the stack pointer with a lot more functions (don't worry about that detail).

Example:

Let's say we are calculating the side of a triangle. The formula is h = sine(x)/o. We have to compute sine manually (e.g. Taylor formula)

Non-modular version

h = x - (x*x*x)/(3*2*1) 
h = h + (x*x*x*x*x)/(5*4*3*2*1) 
h = h - (x*x*x*x*x*x*x)/(7*6*5*4*3*2*1)
h = h/o
return h


Modular version:

First make module (function) called sine(x)

sine(x)
{
sine = x - (x*x*x)/(3*2*1) 
sine = sine + (x*x*x*x*x)/(5*4*3*2*1) 
sine = sine - (x*x*x*x*x*x*x)/(7*6*5*4*3*2*1)
return sine
}

Now main (modular version) program becomes:

h = sine(x)/o
return h
-----------------------

Now as for what makes them different if they all have kernels. Well, they all have kernels, but that's like saying all cars have engines. That doesn't make a Ferrari and a Pinto equal cars. The kernels are very different in how they behave, such as how they handle multi-threading, how they handle time slicing the running processes on the cpu, how they manage the memory, etc....

---

### Post by KingTermite on 2008-06-13
> **BrokeBody said:**
> In short (roughly),

As the processor is the heart of a hardware, kernel is the heart of a software.

That's only true for Operating Systems or software that has a "kernel". You can't necessarily say that all software has a kernel as most doesn't.

The kernel is essentially an engine. It's software that runs in and endless loop and "runs" things in that loop.

---

### Post by KingTermite on 2008-06-13
A few wikipedia links were placed, I see, but none generically to an OS kernel. They were Linux specific.

Here's a link to the genereal concept of an OS kernel. A pretty good description from what little I've read. If you're seriously interested in understanding, give it a read.

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29)

---

### Post by gishaust on 2008-06-13
thanks for the info I like the ferri and pino example  I will have a look at the site you gave me 

ta

---

### Post by Frak on 2008-06-13
My own definition:

The core of the Operating System that is responsible for bridging the hardware with the software.

---

### Post by gishaust on 2008-06-14
[http://en.wikipedia.org/wiki/Kernel_(computer_science](http://en.wikipedia.org/wiki/Kernel_(computer_science))

This articles is great and would highly recommend it thanks KingTermite. But if it was not for the underpinning knowledge everyone gave me I would not have understood it. I am now going to try and understand Privilege rings.I think that creates a lot of issues for me. Does anyone have any advice.

---

