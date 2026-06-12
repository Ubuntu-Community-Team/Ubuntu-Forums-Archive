---
title: "Server RAM question?"
date: 2011-02-13
forum: Server Platforms
---

### Post by Nate204 on 2011-02-13
Hey everyone!

I just had a quick question. 

I'm currently running an Ubuntu server 10.10 with the specs below.

I just picked up 4GB of ram to add to the existing two.

My questions is this:
How much RAM can I use with my server? I've talked with a few people about it, but most don't seem to know because I'm the "one friend they know" who works with and around servers. All they seem have info on is with Desktop environments and Windows.

I guess I'm just trying to get my ducks in a row.

It has two Dual Core Xeon processors on board as you'll see below. I figured they both could run a max of 4GB each~ tot total 8GB if needed. Then again, that's why I'm here. I wanted to ask you =D

Thanks in advance everyone!!
-----------------

Operating system	Ubuntu Linux 10.10

Kernel and CPU	Linux 2.6.35-25-generic-pae on i686

Processor information	Intel(R) Xeon(TM) CPU 2.80GHz, 4 cores

Real memory	1.96 GB total, 792.32 MB used

Virtual memory	1.49 GB total, 7.34 MB used

Local disk space	129.59 GB total, 24.16 GB used

---

### Post by volkswagner on 2011-02-13
Most likely your hardware is not limited to 8 gigs on a dual CPU.  You should never assume, and check with the MOBO manufacturer for RAM specs.

You may need [Physical Address Extension]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/"), which I see is enabled in your kernel...pae i686... you should be good to go!

---

### Post by insane_alien on 2011-02-13
if you're going to be using that much RAM i'd suggestgoing for 64-bit unless your xeons are 32-bit.

64-bit handles RAM much better than pae

---

### Post by cascade9 on 2011-02-13
> **volkswagner said:**
> Most likely your hardware is not limited to 8 gigs on a dual CPU. You should never assume, and check with the MOBO manufacturer for RAM specs.

Yeah, good advice. ;) 

> **insane_alien said:**
> if you're going to be using that much RAM i'd suggestgoing for 64-bit unless your xeons are 32-bit.

64-bit handles RAM much better than pae

+1. 

BTW, all the dual-core xeons are 64bit capable AFAIK.

---

### Post by Nate204 on 2011-02-14
Thank you everyone for your help and suggestions!

You right! I got the RAM in today, and Installed it.
It shows under WebMin, that I have 4.9GB of space (I could only get in 5, due to only having 6 slots. The 2GB I had are both 512Mb each....

I tried to install a 64bit on Ubuntu and it wouldn't go. I then tossed in my 32bit OS disc and it started right up.

I'm having more troubles now as well. I'm trying to run application with a java (a game server), and I can't allocate the new RAM?

I know this is a long shot of a question, but does anyone know why?
Here is the command line I toss in, and It spit out an error telling me the size requested is larger than the allowed limit.

I know of other server running this same exact code, but they're not stopped by this message.

Command:
 java -Xmx4096M -Xms4096M -cp mysql-connector-java-bin.jar:craftbukkit-0.0.1-SNAPSHOT.jar org.bukkit.craftbukkit.Main nogui

Here is a snip-it of my server info with Webmin:
[IMG]http://online-self.com/blog/wp-content/uploads/2011/01/server.png[/IMG]
(Note, This is from before Updates and new RAM added)

Thanks everyone for your assistance!
I appreciate it!

---

### Post by Nate204 on 2011-02-14
> **cascade9 said:**
> Yeah, good advice. ;) 



+1. 

BTW, all the dual-core xeons are 64bit capable AFAIK.

Just figured out I'm running x86 :| Doh!

I really don't want to do a re-install of everything just to see if I can run 64 bit.

Do you have a source I could look over first?

---

### Post by The Real Dave on 2011-02-14
> **Nate204 said:**
> Just figured out I'm running x86 :| Doh!

I really don't want to do a re-install of everything just to see if I can run 64 bit.

Do you have a source I could look over first?

If you simply want to see if your machine can run 64 bit Ubuntu run, 

```
sudo lshw > hardware.txt
```

Open up the hardware.txt file, scroll down to your the information on your cpu. It'll list all it's capabilities flags. You're looking for the x86-64 flag.

You can also pop in a 64bit Ubuntu Live CD and see if it boots. If your computer is not 64bit capable, it won't boot.

---

### Post by hawkmage on 2011-02-14
On a 32 bit OS any one process can only see a 4GB memory space without using funky memory mapping techniques that often lead to more issues than they solve.  In this 4GB memory space there is a portion that is reserved  for the Kernel, usually 1GB, and the rest for the process to use leaving your application with 3GB to play with.  

This is way you are getting the command is not allowed to allocate 4GB of memory.  Try it with 3072MB.  

My rule of thumb for choosing between 32 vs 64 bit OS is is there will be any single process that requires more than about 2GB to 2.5GB of ram.  Above 2.5GB I go for 64 bit under 2GB then 32 bit unless there are many processes that will require large memory allocations.

---

### Post by Nate204 on 2011-02-14
> **The Real Dave said:**
> If you simply want to see if your machine can run 64 bit Ubuntu run, 

```
sudo lshw > hardware.txt
```

Open up the hardware.txt file, scroll down to your the information on your cpu. It'll list all it's capabilities flags. You're looking for the x86-64 flag.

You can also pop in a 64bit Ubuntu Live CD and see if it boots. If your computer is not 64bit capable, it won't boot.

I checked out the specs with the code you provided. It seems to me that the CPUs both have a width of 32bits...

I'm really bummed out about this, but I should have checked and double checked. I'm brand new to server hardware and how it works, although 32bit and 64bit are the norm when dealing with builds. I guess I figured all server tech would be running 64bit hardware, but my [Server]("http://www.dealtime.com/Intel-Intel-Corp-Dual-Xeon-7501-DDR266-SE7501WV2S/prices") doesn't seem to make the cut.

I guess I'm stuck until I either get two new CPUs or there is some odd way to get the 32bit of Java to utilize more than 1.5GB of RAM...... I should have known. lol

Thanks again everyone. You all just taught me more here than I feel I've learned so far in my Windows Server 2008 class.

I appreciate it!

---

### Post by Nate204 on 2011-02-14
P.S.

This is what it shows for both CPUs.


     *-cpu:0
          description: CPU
          product: Intel(R) Xeon(TM) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2800MHz
          capacity: 2800MHz
¿½nï¿½ï¿½nwidth: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid x$
          configuration: id=1

---

### Post by cascade9 on 2011-02-15
> **Nate204 said:**
> Just figured out I'm running x86 :| Doh!

I really don't want to do a re-install of everything just to see if I can run 64 bit.

Do you have a source I could look over first?

[http://ark.intel.com/Product.aspx?id=27202&processor=&spec-codes=SL8MA](http://ark.intel.com/Product.aspx?id=27202&processor=&spec-codes=SL8MA)

Thats the earliest dual core Xeon (paxville MP) . 

As for why you dont get the 'lm' or 'x86_64' tags in the CPU capabilities, and your 64bit CD failed,I dont know for sure. Could be that because its a farily early intel64 version, its missing some instruction needed for x86-64. Or it could be a BIOS settings, or it could be a chipset limitation.

---

### Post by Nate204 on 2011-02-15
[http://www.andovercg.com/datasheets/intel-SE7501WV2-motherboard-specs.pdf](http://www.andovercg.com/datasheets/intel-SE7501WV2-motherboard-specs.pdf)

I can't even figure out how to get into my BIOS for the server to check anything =( I'll keep trying after class, but I wouldn't think there would be a setting for anything like that?

---

### Post by hawkmage on 2011-02-15
It sounds like a chip set issue, from what I remember reading all multi core Xeon CPUs are 64 bit capable but many of the early mother boards did not have the support for it.  

I ran into this with a VMWare server that we wanted to put a 64 bit guest OS on, I looked up the CPU specs on Intel's web site and it said it was 64 bit capable but the system would not run 64 bit code.

---

### Post by cascade9 on 2011-02-15
Thats left me a little confused....

Paxville MP is a 800MHZ FSB CPU, according to that datasheet the SE7501WV2 only suppotrs 533MHZ and 400MHz FSB CPU (page 21 if you want to see yourself). 

The intel page for drivers for the SE7501WV2 only has 32bit OSes, so I'd guess that even if you are running paxville MP CPUs, the 64bit support isnt not there. 

> 64-bit computing on Intel® architecture requires a computer system with a processor, chipset, BIOS, operating system, device drivers and applications enabled for Intel® 64 architecture. Processors will not operate (including 32-bit operation) without an Intel 64 architecture-enabled BIOS. Performance will vary depending on your hardware and software configurations. Consult with your system vendor for more information.[http://ark.intel.com/Product.aspx?id=27202&processor=&spec-codes=SL8MA](http://ark.intel.com/Product.aspx?id=27202&processor=&spec-codes=SL8MA)

I'd just move to a more modern CPU if you have the chance. A Core2Quad, Phenom II, Core i5 (quad) or core i7 would be faster than the paxville, and the reduction in your power bill will pay for the upgrade sooner than you might think.

---

### Post by Nate204 on 2011-02-15
Well this is a bummer...
It's awesome though, in a sense that you all helped me out so much and so quickly!

Due to the fact that I don't feel I have a reliable "hot site" to push my server data too, I think I'll just have to stay put and grind it out. I'd love to reinstall and do another RAID config. I'd love even more to get inside my box and toss in two new CPUs too. 

In the future, I'll know to check and stick with 64 bit specs. I got this server box for cheap just to get some hands on with both Ubuntu and server hardware. It was running Win Server before, but I didn't like it and tossed it out.

For now, I'll just use the 32 bit OS so my members can have fun w/o me tinkering anymore than I currently do (downtime...) I was given a suggestion to run two setups of the server software to use up the ram I have access to. 

Not sure If I like the Idea though, due to all the time I've spent with my desktop being 64bit~ I tend to think any application running is stealing away my resources for what I want to run.

Thanks again for being so helpful guys!
I'll keep checking back! Sooner or later I want to take the dive into linux, but server side is just enough to hold me over for now =P

---

### Post by i.r.id10t on 2011-02-15
The -pae kernel series will see all of your ram - however, until you upgrade to a 64bit system the most any one process could address will be ~3.2gb

---

### Post by Nate204 on 2011-02-15
> **i.r.id10t said:**
> The -pae kernel series will see all of your ram - however, until you upgrade to a 64bit system the most any one process could address will be ~3.2gb

That wouldn't be too bad, but the guys over on a java forum have told me Java (JDK) will only see and use 1.5GB.... That's my biggest let down. As soon as you get 64 though, it seems that the sky is the limit.

---

### Post by tgalati4 on 2011-02-15
And realize that most server hardware is conservative design--not the desktop/workstation performance that you would expect.  So 32-bit Xeons, 32-bit motherboard chipsets and error-checking RAM (which impacts throughput) are the norm.

It will still perform OK for a game server, but if this is an older, business-grade server, then it's really designed for serving files, printing, email, etc.  Server gaming workloads were not in the design specifications!

---

### Post by Nate204 on 2011-02-15
> **tgalati4 said:**
> And realize that most server hardware is conservative design--not the desktop/workstation performance that you would expect.  So 32-bit Xeons, 32-bit motherboard chipsets and error-checking RAM (which impacts throughput) are the norm.

It will still perform OK for a game server, but if this is an older, business-grade server, then it's really designed for serving files, printing, email, etc.  Server gaming workloads were not in the design specifications!

HAHA! Very True!

"Hey bill, we need it to process and store statements, and also be able to work as a print server." Oh ok. , No problem. "Oh, and Bill.... It needs to run a brand new java game and allow for low latency in about 3 years." :shock:

---

### Post by tgalati4 on 2011-02-15
Or it needs to run 6 virtual machines of 4 GB each and split the two network cards 3-and-3.

---

