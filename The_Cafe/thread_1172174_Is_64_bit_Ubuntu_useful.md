---
title: "Is 64 bit Ubuntu useful ?"
date: 2009-05-28
forum: The Cafe
---

### Post by praveesh on 2009-05-28
Hi guys,
I have a 64 bit processor . Is there any use if I use 64 bit Ubuntu . Any improvement in performance and responsivity .  From wikipedia I came to know that Ubuntu packages are optimised for pentium 2 . 64 bit packages might be optimised for core2 ,I Think. My computer's specification :Intel core2duo E4600 2.4Ghz(per core) ,945GC motherboard chipset ,1Gb ram ,GEFORCE 7200 GS graphics,

---

### Post by _Purple_ on 2009-05-28
You might find this thread helpful:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by gn2 on 2009-05-28
Simple answer: Yes.

---

### Post by Mehall on 2009-05-28
Simple answer: he only has 1GB of RAM, meaning the MAIN advantage is lost. Refer to previous link to see if it's still worth it.

---

### Post by gn2 on 2009-05-28
> **Mehall said:**
> Simple answer: he only has 1GB of RAM, meaning the MAIN advantage is lost. 

What you mean by "main advantage"?

---

### Post by jespdj on 2009-05-28
He means that the main advantage of a 64-bit OS is that you can use more than 3.5 GB RAM.

Many people think that a 64-bit OS is only really useful if your computer has 4 GB or more RAM - a 32-bit OS is limited to a 4 GB address space (and part of the address space is reserved for communication with devices, so that at most about 3.5 GB RAM is useable). A 64-bit OS does not have such a limitation.

However, that's not the only advantage of 64-bit. If you want to know the details, study the [x86-64](http://en.wikipedia.org/wiki/X86-64) architecture in more detail. The CPU has more and larger internal registers available in 64-bit mode, which makes programs run more efficiently. Also, a different [calling convention](http://en.wikipedia.org/wiki/Calling_convention) is used (parameters for subroutines are passed in registers instead of on the stack), which is more efficient. Also, the CPU has twice as many [SSE](http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions) registers available.

In short, you will notice that especially CPU-intensive applications run faster on 64-bit.

---

### Post by gn2 on 2009-05-28
> **jespdj said:**
> He means that the main advantage of a 64-bit OS is that you can use more than 3.5 GB RAM.

Nope, Mehall hasn't confirmed that yet, therefore you can only be *assuming* that's what is meant.

---

### Post by Mehall on 2009-05-28
> **jespdj said:**
> He means that the main advantage of a 64-bit OS is that you can use more than 3.5 GB RAM.

Many people think that a 64-bit OS is only really useful if your computer has 4 GB or more RAM - a 32-bit OS is limited to a 4 GB address space (and part of the address space is reserved for communication with devices, so that at most about 3.5 GB RAM is useable). A 64-bit OS does not have such a limitation.

However, that's not the only advantage of 64-bit. If you want to know the details, study the [x86-64](http://en.wikipedia.org/wiki/X86-64) architecture in more detail. The CPU has more and larger internal registers available in 64-bit mode, which makes programs run more efficiently. Also, a different [calling convention](http://en.wikipedia.org/wiki/Calling_convention) is used (parameters for subroutines are passed in registers instead of on the stack), which is more efficient. Also, the CPU has twice as many [SSE](http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions) registers available.

In short, you will notice that especially CPU-intensive applications run faster on 64-bit.


It is still the main advantage for the average "I'll just go on youtube while I'm typing something in oo.o" users.

Also, the 64-bit pointers result in larger memory use, be it cache, RAM, or on your HDD, as they use larger blocks, which is how they use more RAM (well.. one of the reasons)

If OP currently uses a lot of his 1GB of RAM (e.g. Compiz is on with many effects AND running OO.o, for example) then space would be that little bit tighter, resulting in more swap usage.

---

### Post by Mehall on 2009-05-28
> **gn2 said:**
> Nope, Mehall hasn't confirmed that yet, therefore you can only be *assuming* that's what is meant.

That is what I meant, actually.

For most users, the main advantage is gaining use of all of their RAM.

---

### Post by gn2 on 2009-05-28
> **Mehall said:**
> That is what I meant, actually.

For most users, the main advantage is gaining use of all of their RAM.

Thanks for the clarification.

Addressing huge amounts of RAM can be done in both 32-bit and 64-bit Linux, so it's no advantage at all.

Encoding tasks complete significantly faster in 64-bit. 
Now *that's* an advantage.

---

### Post by Mehall on 2009-05-28
> **gn2 said:**
> Thanks for the clarification.

Addressing huge amounts of RAM can be done in both 32-bit and 64-bit Linux, so it's no advantage at all.

Encoding tasks complete significantly faster in 64-bit. 
Now *that's* an advantage.

I've heard of issues with the PAE kernel. it also requires more than a little effort.

At this time, for the average desktop user who isn't likely to be encoding stuff, then it is generally a case of "DO I have more than 3.5GB of RAM? Yes? 64 bit. No? 32bit"

---

### Post by gn2 on 2009-05-28
> **Mehall said:**
> At this time, for the average desktop user who isn't likely to be encoding stuff, then it is generally a case of "DO I have more than 3.5GB of RAM? Yes? 64 bit. No? 32bit"

That's flawed, because it depends on a stereotype and fails to realise that installed RAM amount is no basis for selecting which version to use.

With 1gb RAM in my desktop PC, the tasks that take longest, i.e. encoding, complete signficantly faster in 64-bit.

There is no longer any disadvantage to having 64-bit that I can see, only advantage.

---

### Post by praveesh on 2009-05-28
Is there any advantage in virtualisation . When I tried to use kvm , Ubuntu replied that hardware based virtualisation is not supported . I also tried opensuse and Yast replied that my hardware does not support hardware based virtualisation . I have used 32 bit versions of both . I think Core2Duo supports vt

---

### Post by gn2 on 2009-05-28
> **praveesh said:**
> Is there any advantage in virtualisation .

Depends what you want virtualisation for.

> **praveesh said:**
> When I tried to use kvm , 

KVMs are notoriously problematic in Linux.

---

### Post by praveesh on 2009-05-28
> **gn2 said:**
> Depends what you want virtualisation for.
KVMs are notoriously problematic in Linux.
I want to install 1 or more guest operating systems in linux . I have not only used kvm ,but also  virtualbox , qemu , and visualisation tools in yast . In virtualbox there is an option to enable intel vt but there was no way to know whether vt could be enabled or not. There was no performance improvement . In virtualisation tools of yast , it replied that hardware doesnt support vt. There is no such option in qemu

---

### Post by Dimitriid on 2009-05-28
You'd want more than 3.5gb of ram for either Gaming, Running a Server or running very specific software.

For the better part of Linux users, gaming and very specific software that requires it are propietary and windows so the results if they can be run at all, are less than desirable. So its either cause you want to run some type of server or virtual box or something other than the ram advantage.

So I guess we should focus on giving good examples of Linux applications that really benefit from 64bit processing. Im guessing multithreaded, 64bit optimized video editing/compressing? I haven't got a need for something like that so far though.

---

### Post by hyperdude111 on 2009-05-28
It is a definite yes, the 64 bit version will utilize the full capacity of your processor. You wont notice much difference except with apps that involve maths live video converting etc where there is a massive difference.
I have come across no apps that only support 32 bit now so compatibility is no issue.

In the future 32bit will die out, its old technology. All new processors being made for desktops and now 64 bit.

---

### Post by maflynn on 2009-05-28
I'm going to be a dissenter here.  While 64bit has advantages, I think some of the application compatibility issues outweigh some of those advantages.  If you want or need to access > 3gig of ram, yes go with the 64bit but if you have no special requirements for 64bit apps or have more then 4gig of ram, you're not gaining much but you are incurring more work to get what you do have running, i.e., either finding 64bit versions or working to get 32bit programs to work on a 64bit OS.

---

### Post by 3rdalbum on 2009-05-28
> **maflynn said:**
> I'm going to be a dissenter here.  While 64bit has advantages, I think some of the application compatibility issues outweigh some of those advantages.

We're talking about 64-bit Ubuntu; everything in the repositories is 64-bit or wrapped and tested to work in 64-bit.

On Windows it's an issue as everything is distributed as binary. On Linux there's no issue as source code is always available and your distributor has always recompiled for 64-bit.

Having said that, I wouldn't recommend using 64-bit on a machine with 1GiB of RAM. With that amount of memory you could really do with keeping as much of it free for cache, rather than using it for longer numbers.

---

### Post by gn2 on 2009-05-28
> **maflynn said:**
> I think some of the application compatibility issues outweigh some of those advantages.

Can you name one application with issues?

---

### Post by jespdj on 2009-05-28
> **gn2 said:**
> Addressing huge amounts of RAM can be done in both 32-bit and 64-bit Linux, so it's no advantage at all.
Yes, with PAE, but a single 32-bit process still cannot use more than 3 GB RAM, even with a PAE-enabled kernel. So if you have a program that needs a huge amount of memory, PAE is not really a solution.

---

### Post by Therion on 2009-05-28
I have, in the past, used both 32-bit and 64-bit versions of Ubuntu on the same computer within hours of each other.  I've used both distros with 4GB of RAM installed and with 2GB of RAM installed.  My experiences tell me on no uncertain terms, hands down, 64-bit all the way.  I don't care if you have one GB of system RAM or eight, if your architecture *supports* 64-bit you *want* 64-bit.

---

### Post by Regenweald on 2009-05-28
Forgive me, but i never understand the argurment: if your are not using more than 4 gigs of memory don't bother. I have only ever used 64 bit, I have 2 gigs of memory, my system idles at 150-210 megs and with VirtualBox, Exaile, and Firefox running, i may hit 1200 megs and that is simply because of the memory i have allocated to VB. 

Even back when i only had 1 gig 667mhz, my system has always been fast and responsive, AND could run VB. This little memory thing aside, 64bit utilizes the full power of your 64bit PROCESSOR, which is why i chose 64bit in the first place. I just think that telling someone to stick to 32bit if they don't have bags of memory is bad advice. To me the advantage lies in the processor usage.

---

### Post by frodon on 2009-05-28
I tend to prefer 32 bit OS for most of us now we don't have real 64bit proscessor (we almost all have x86_64 proscessors) and then the gain in performance is really small compared to 32 bit. As you know some software are still missing in 64 version and it takes more RAM too.

So my personal rule is if i don't have 4Go of RAM i use 32 bit OS.

---

### Post by dspari1 on 2009-05-28
I have 4gb of ram and use 64bit, but I honestly don't notice any speed improvements between either 32bit or 64bit. If there's a difference, it must be negligible. 

The only benefit for me so far is that my OS detects the full 4gb instead of 3.5gb which is worth it IMO.

---

### Post by Mr. Picklesworth on 2009-05-28
Hate to admit, but I just downgraded from 64 to 32 bit on my laptop and found an improvement. Probably not in number crunching capacity, but in memory consumption and the general efficiency of the thing. I suspect there were some bugs affecting the 64-bit builds of apps (maybe drivers) I used.
Also, it helps that Google Gears and Boxee have 32 bit builds :)

---

### Post by frodon on 2009-05-28
64bit OSs use more RAM, this is normal and related to the 64bit adress size.

---

### Post by gn2 on 2009-05-28
[Here are some benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=4"), which demonstrate the difference.

Encoding is up to 50% faster in 64-bit, if you do things like rip CDs or DVDs or convert .avi files to dvd.iso the difference is massive.

---

### Post by gjoellee on 2009-05-28
You should get a lot better performance!

---

### Post by Superkoop on 2009-05-28
If your computer is designed for x86_64, use the 64bit Ubuntu. 
You payed to have a computer as powerful as it is, now don't let your OS hold it back from it's potential. 
IMO, it's silly for people to buy a really impressive computer, and then do nothing but use office applications and the Internet; it's just as silly to buy an x86_64 and then install an OS which doesn't utilize that.

---

### Post by Paqman on 2009-05-28
> **Mr. Picklesworth said:**
> 
Also, it helps that Google Gears and Boxee have 32 bit builds :)

Dunno about Boxee (still Alpha innit?), but there's unofficial 64-bit versions of Gears out there.

---

### Post by Chame_Wizard on 2009-05-28
64 bit is cool to use.:lolflag:

---

### Post by Marlonsm on 2009-05-28
My experience so far with 64-bit is: If you can use it, why not?
I went to 64-bit when I upgraded to Jaunty, so I can't really tell how much performance gains I got from 64-bit, but so far everything is good.

---

### Post by doorknob60 on 2009-05-28
Yes, but unless you have 4 GB of RAM, it's not a big enough difference to need to go reinstall everything. If you ever need to reinstall though or when 9.10 comes out, definately install 64 bit then :)

---

### Post by FuturePilot on 2009-05-28
> **doorknob60 said:**
> Yes, but unless you have 4 GB of RAM, it's not a big enough difference to need to go reinstall everything. If you ever need to reinstall though or when 9.10 comes out, definately install 64 bit then :)

It was enough for me to reinstall Jaunty when it was in Beta and I only have 2GB of RAM.

---

### Post by doorknob60 on 2009-05-28
^

I always use 64 bit (2 GB of RAM BTW) regardless, but I just don't think it's worth taking the time to reinstall everything just for the 32 bit to 64 bit conversion. If you do a lot of things like encoding files and all that stuff pretty often then switcfh ASAP. Otherwise just wait 'till you need to reinstall. OR go break your system and then install 64 bit :D Just my personal opinion.

---

### Post by praveesh on 2009-05-29
> **gn2 said:**
> [Here are some benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=4"), which demonstrate the difference.
Encoding is up to 50% faster in 64-bit, if you do things like rip CDs or DVDs or convert .avi files to dvd.iso the difference is massive.
I do rip cds and convert different video formats . With only 1 Gb is there any improvement in encoding? ..But please tell me about virtualisation ; is there any benefit .

---

### Post by gn2 on 2009-05-29
I have very little technical knowledge of how virtualisation works.
I do not know if there is any improvement using 64 rather than 32.

I was wondering what the reason you want to use virtualisation is, what do you want to use a virtual PC for?

EDIT: > With only 1 Gb is there any improvement in encoding?

Yes. When changing an .avi file to dvd.iso with DeVeDe, or ripping a DVD with dvd::rip and browsing the net with Firefox at the same time, my RAM sits around 600mb in use on my 64-bit Ubuntu 8.04.

---

### Post by praveesh on 2009-05-29
> **gn2 said:**
> I have very little technical knowledge of how virtualisation works.
I do not know if there is any improvement using 64 rather than 32.
I was wondering what the reason you want to use virtualisation is, what do you want to use a virtual PC for?
There are several reasons for using virtualisation . 
1. I can test a when new distro comes or when a new release come.
2. I can use windows apps that does not run fine in wine . 
3.I can make my brother and my friends wonder

---

### Post by praveesh on 2009-05-29
When I brought my computer last year , 1 Gb was a luxury . Now everyone speaks about 4 Gb . With 512MB of graphics memory , is there any need of 4 GB .

---

### Post by gn2 on 2009-05-29
> **praveesh said:**
> There are several reasons for using virtualisation . 
1. I can test a when new distro comes or when a new release come.
2. I can use windows apps that does not run fine in wine . 
3.I can make my brother and my friends wonder

If you really want to do those things and do them often, you should seriously consider fitting more RAM, 1gb may not be enough.

You can test distros with a conventional dual-boot, same with running Windows.

Do you *need* to have two operating systems running at the same time?
This is the question you should ask yourself when you're at the counter of the PC components shop about to hand over the rupees for the extra RAM ;)

---

### Post by praveesh on 2009-05-29
Thank you guys , I have decided to move to 64 bit. More comments are always welcome . In my knowledge , canonical doesnt ship free 64 bit cd .  Hum I dont have a fast internet ; let me have a try .

---

### Post by praveesh on 2009-05-29
A

---

### Post by praveesh on 2009-05-29
> **gn2 said:**
> If you really want to do those things and do them often, you should seriously consider fitting more RAM, 1gb may not be enough.
You can test distros with a conventional dual-boot, same with running Windows.
Do you *need* to have two operating systems running at the same time?
This is the question you should ask yourself when you're at the counter of the PC components shop about to hand over the rupees for the extra RAM ;)
Is the currency of scotland rupee . Iam sorry if I have asked a wrong question . With 32 bit opensuse there was no problem running Ubuntu 8.10 and win xp in virtualbox.testing under virtualbox is useful since I dont need to change partition etc(ofcourse I know how to do all of these).

---

### Post by gn2 on 2009-05-29
> **praveesh said:**
> Is the currency of scotland rupee . Iam sorry if I have asked a wrong question . With 32 bit opensuse there was no problem running Ubuntu 8.10 and win xp in virtualbox.testing under virtualbox is useful since I dont need to change partition etc(ofcourse I know how to do all of these).

Currency in Scotland is Pounds Sterling.

You will be able to run an Ubuntu host and a guest virtual PC with 1gb of RAM, but more would be better.

---

### Post by jespdj on 2009-05-29
> **frodon said:**
> I tend to prefer 32 bit OS for most of us now we don't have real 64bit proscessor (we almost all have x86_64 proscessors) and then the gain in performance is really small compared to 32 bit. As you know some software are still missing in 64 version and it takes more RAM too.

So my personal rule is if i don't have 4Go of RAM i use 32 bit OS.
What do you mean with "we don't have real 64bit procesor (we almost all have x86_64 proscessors)"? Do you think that a processor that supports x86_64 is somehow not a "real 64-bit processor"? What do you think a processor must have to be regarded as a "real 64-bit processor"? I think you don't really know what you're talking about.

It is true that the performance difference is probably not noticeable in the majority of software. But for processor-intensive software (audio- or video-encoding, ray tracing, ...) the performance gain can be more than 50%, and this will really be noticeable.

---

