---
title: "Proprietary drivers aren't illegal?"
date: 2007-11-01
forum: The Cafe
---

### Post by bessiambre on 2007-11-01
Hey, I just downloaded Ubuntu and I noticed it now comes with closed source drivers. What's up with that? Isn't this illegal? What stops the transition to a model where companies produce a non free Linux distribution by charging for the included drivers, Consider the following scenario:

Intel develops new closed undocumented architecture with 16 core cpu. Similarly to current 3d accelerated video cards, you need a proprietary driver to enable the super accelerated multicoreness. In order to enable the use of the newer faster computers, Ubuntu does what it did with the video card drivers, label these drivers as "not part of the kernel" and ships with the proprietary drivers which, for now, intel is giving away for free with the hardware. For a while everybody is happy and content. The new 16 cores chip becomes the new standard. There are even 32  core chips on the market and the 64 cores chips are soon to be released all of which rely on proprietary drivers.

Suddenly, we hear that a large company, Linusoft, started by ex MS executives, makes a deal with Intel, a very lucrative deal for Intel, to license the drivers. Intel then says they won't give away the drivers anymore but you are free to buy their brand new Ubuntel Linux distribution. This distribution, which sells for 699$ a piece is all GPL'd except for those drivers that have become so standard that you need them in order for computers to run at a reasonable speed. 

Bearded men scramble to write free replacement drivers that work on their Gnubian distribution but only manage to make drivers that can run the multi core cpu's at 1/20th the speed as Intel won't release documentation or specifications. Linux is rendered mostly useless except for the Ubuntel distro, (which is also available for free and with sourcecode as Ubuntelora exluding the proprietary drivers of course) You can always plug in the Gnubian drivers in the free Ubuntelora project and get a working computer but it will only run at 1/20th the speed of the commercial 699$ a pop version and isn't powerful enough to run the new Mozilaurus browser smoothly.

How can we let anyone close up an obviously derived work based on the kernel just by saying the words "this driver is not part of the kernel"?

Notice that, even today I sometimes need to pay to get a fully working Linux from certain vendors, like Mandriva. (if i don't pay 3d acceleration wont work.) I expect that kind of twisting of the law by commercial vendors. It surprises me Ubuntu is doing it.

---

### Post by happysmileman on 2007-11-01
> **bessiambre said:**
> Hey, I just downloaded Ubuntu and I noticed it now comes with closed source drivers. What's up with that? Isn't this illegal? What stops the transition to a model where companies produce a non free Linux distribution by charging for the included drivers.

Not illegal, and there are already many Linux distributions that cost money, though mainly you pay for technical support or codecs that are restricted in some countries, not usually the software.

Also 3D acceleration works fine for me on Mandriva for free, it's best to install from repositories, the configuration tool never downloaded the file correctly for me.

Also I can't think of the Intel analogy, processors do not require drivers and probably never will, if they tried to lock you out of it like that the processor would most likely end up slower than the competition and then Athlon processors would win. And hardware companies don't make money by selling drivers, they sell hardware, if they started charging for drivers the competition would always just beat them anyway.

---

### Post by kebes on 2007-11-01
> **bessiambre said:**
> I just downloaded Ubuntu and I noticed it now comes with closed source drivers. What's up with that? Isn't this illegal? What stops the transition to a model where companies produce a non free Linux distribution by charging for the included drivers

It's a bit of a grey area when it comes to what the GPL considers a "derivative product" with respect to the kernel. The closed-source, proprietary drivers that you see in Linux (and even shipping with Ubuntu) all use some kind of open-source interface to the kernel, and keep all the closed-source parts in a binary blob.

Some people say that this constitutes a derived product of the kernel code, whereas others view these kind of external modules as separate code that merely interfaces with the kernel. The consensus in most distros is that since they are not interwoven with the kernel itself (the kernel runs just fine without them), these external modules are considered separate products. (And there's nothing illegal about shipping some proprietary product in aggregate with Linux.)

In your hypothetical example, by the way, it is hard to imagine creating a module to take full advantage of additional CPU features. The kernel interfaces with the CPU at a very basic level, and so changes to the kernel code itself would be required to take full advantage of a new CPU architecture. In theory selected acceleration operations could be accessed via some proprietary binary module (like how 3D acceleration can be passed to the graphics card via a closed-source driver), but that would be rather inefficient.

If something like that started happening, I doubt the kernel hackers would wait to reverse-engineer it. They would immediately start incorporating those features into the kernel proper. My personal opinion is that the Linux community should view closed-source drivers as interim solutions only: ultimately all code should be open-source and Free (in part to avoid the kinds of situations you envision).

---

### Post by igknighted on 2007-11-01
Your scenario is far fetched indeed.  What concerns me more is this:

---

### Post by happysmileman on 2007-11-01
> **igknighted said:**
> Your scenario is far fetched indeed.  What concerns me more is this:

Does it?  thought it included proprietary drivers, someone should definitely inform someone with the power to change that

---

### Post by bessiambre on 2007-11-01
> **kebes said:**
> (the kernel runs just fine without them)

Not with regard to 3d acceleration. It seems to me that people think it's not covered by the GPL Just because it's not a critical feature. What if it was a driver for a chipset, a bus, or a cpu as I mentioned?

---

### Post by bruce89 on 2007-11-01
> **igknighted said:**
> Your scenario is far fetched indeed.  What concerns me more is this:

Indeed, Firefox is on the CD - [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/83118](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/83118)

---

### Post by LaRoza on 2007-11-01
Free doesn't mean open source. The statement in the Ubuntu site clearly separates the two concepts. All the software on the cd is FREE, like the statements says, and they *encourage* people to use **free and opensource**

---

### Post by igknighted on 2007-11-01
> **LaRoza said:**
> Free doesn't mean open source. The statement in the Ubuntu site clearly separates the two concepts. All the software on the cd is FREE, like the statements says, and they *encourage* people to use **free and opensource**

In the least it is misleading.  Yes, it can be interpreted as you did, but when I hear the phrase "free software" from a linux company, it carries a certain meaning.  I honestly don't care if Ubuntu includes non-free bits by default.  I use them myself (madwifi, nvidia drivers, etc.).  But the way it is worded rather strongly implies that non-free (as in speech) software is not included.  If this is not the case (it isn't), then just say so.  The people who will think less of you for it already do because the software is there, and the rest either don't care or would welcome it.

---

### Post by popch on 2007-11-01
> **igknighted said:**
> In the least it is misleading.  Yes, it can be interpreted as you did, but when I hear the phrase "free software" from a linux company, it carries a certain meaning.

There are - just as in most professions - several terms (or 'words') which stand for different things (or 'meanings'). Some of those things are quite independent of each other, even if they frequently occur in groups.

Professionals use and need those different words because otherwise they would be unable to sensibly speak to each other about certain things. Just like in anatomy where Teeth and Toes are different things.

If you want to make a contribution to those at times quite difficult discussions, I see no way to avoid learning those terms and what they mean.

---

### Post by Dragonbite on 2007-11-01
Proprietary drivers are not illegal and may actually help with for-profit companies to develop their flagship software to Linux knowing that making it for Linux does not mean they have to open their code.

Your scenario doesn't take into effect the other forces, namely competition.  Microsoft is a monopoly, but I think a lot of people are seeing the rays of competition on the horizon for Microsoft (and it ain't from Apple, though they are doing a good job).

Intel has AMD (who just announced[[COLOR="Blue"]new Linux drivers for their video cards[/COLOR]]("http://www.linuxjournal.com/node/1003007")), Microsoft has Linux, Nvidia has ATI, IE has Firefox, etc. etc. etc.

---

### Post by Sp4cedOut on 2007-11-01
At one time it was a real hassle to get video cards to work well with Linux, now it's quite easy.  If it works I'm all for it.  Closed source doesn't mean bad, and open source doesn't mean free.

---

### Post by saulgoode on 2007-11-01
> **LaRoza said:**
> Free doesn't mean open source. The statement in the Ubuntu site clearly separates the two concepts. All the software on the cd is FREE, like the statements says, and they *encourage* people to use **free and opensource**

Are you claiming that in the last part of Ubuntu's Promise they are using the term "free software community" and "free software applications" to indicate that they are "free of charge"? I do not agree. And if you are correct, Ignighted is right that "in the least it is misleading".

> **"The Ubuntu Promise"][list]

    [*] Ubuntu will always be free of charge, including enterprise releases and security updates.
    [*] Ubuntu comes with full commercial support from Canonical and hundreds of companies around the world.
    [*] Ubuntu includes the very best translations and accessibility infrastructure that the free software community has to offer.
    [*] Ubuntu CDs contain only free software applications said:**
> 


---

### Post by YaroMan86 on 2008-08-15
> **Sp4cedOut said:**
> At one time it was a real hassle to get video cards to work well with Linux, now it's quite easy.  If it works I'm all for it.  Closed source doesn't mean bad, and open source doesn't mean free.

Amen. I'm glad I'm not the type of FOSSie who absolutely abhores any and all proprietary software. Otherwise I'd be stuck using crappy open source projects such as Gnash or the nv driver, neither of which come close to working as sofficiently as Flash 9/10 Beta or nvidia-glx-new, both of which are proprietary.

I've attempted use of Gnash, which made me want to tear my hair out because it just didn't render as well, if at all. And nv didn't have even half the capabilities I need for my development projects to take off that nvidia-glx-new has, that and I like Compiz Fusion and it requires the proprietary driver to work, again, because nv is far too limited on a technical level to run Compiz Fusion. (I am a programmer, I'm working on a game project. I need good drivers and nv is not a good driver.)

It goes both ways, though. I absolutely detest Java, especially for 64-bit Linux, (It's not so great for 64-bit Windows or so I heard.). The problem is that IcedTea didn't help as much as it could've, either, and I even spent the better part of an hour compiling it from source after the repository version kept Segfaulting at every load. It worked after I did that, but it still didn't seem to do things as well. For Java as a plugin, I had to finally just give in and install 32-bit Firefox just for Java support. I also dislike Java from a developer perspective: It's not really a good language to make serious software from, and is usually only made by developers too lazy to do some port work. Java is bloated, frequently buggy, and very slow.

Another closed source thing I'm not crazy about is VMWare. It's slow and bloated, I much prefer Virtualbox.

---

### Post by t0p on 2008-08-15
> **LaRoza said:**
> Free doesn't mean open source. The statement in the Ubuntu site clearly separates the two concepts. All the software on the cd is FREE, like the statements says, and they *encourage* people to use **free and opensource**

No, no, no!! The difference between Free and open source software is philosophical - Free software evangelists see it as an ethical choice whereas to open source adherents it is a commercial choice.  The word "free" in Ubuntu bumf does *not* mean "without financial cost" - after all, Ubuntu DVDs are sold, and the CDs can also be sold.  When Ubuntu say "Free" they mean as in free speech.  It's a shame what they say isn't true, but that *is* what they mean.

As for the OP's question about the legality of proprietary drivers: as far as I'm aware, Ubuntu do not exclude proprietary codecs etc because they would be illegal to include - after all, they are included in plenty of other distros that are available for free download.  No, Ubuntu excludes them for *philosophical* reasons.

---

