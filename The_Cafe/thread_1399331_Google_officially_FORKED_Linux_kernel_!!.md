---
title: "Google officially FORKED Linux kernel !!"
date: 2010-02-05
forum: The Cafe
---

### Post by mickie.kext on 2010-02-05
[http://www.kroah.com/log/linux/android-kernel-problems.html?seemore=y](http://www.kroah.com/log/linux/android-kernel-problems.html?seemore=y)

[QUOTE=excerpt]As the Android kernel code is now gone from the Linux kernel, as of the 2.6.33 kernel release, I'm starting to get a lot of questions about what happened, and what to do next with regards to Android. So here's my opinion on the whole matter...

First off, let me say that I love the Android phone platform. Until last week, I used my developer G1, that I bought, every day. It worked wonderfully for me, and as a user, I was more than happy.[/QUOTE]
[http://www.theregister.co.uk/2010/02/03/android_driver_code_deleted_from_linux_kernel/](http://www.theregister.co.uk/2010/02/03/android_driver_code_deleted_from_linux_kernel/)
[http://lwn.net/Articles/372419/](http://lwn.net/Articles/372419/)

---

### Post by SuperSonic4 on 2010-02-05
tl;dr

also open source lets you do that. As far as I know won't google have to release the code of their fork?

---

### Post by pwnst*r on 2010-02-05
I don't know the technical aspects of the kernel, but I'm not seeing anything official in someone's blog.

---

### Post by Paqman on 2010-02-05
> **pwnst*r said:**
> I'm not seeing anything official in someone's blog.

The "someone" in question would be [Greg Kroah-Hartman]("http://en.wikipedia.org/wiki/Greg_Kroah-Hartman"), a senior kernel dev.

---

### Post by mickie.kext on 2010-02-05
> **SuperSonic4 said:**
> tl;dr

also open source lets you do that. As far as I know won't google have to release the code of their fork?
Actualy, that is not a problem code is ok. Tt is GPL and it is available. Problem is in deliberately making fork incompatible with upstream so Linus can not merge Android stuff in his tree anymore. Not without mayor pain, anyways. That action is really not needed and Google is just being mean. 

There is another fork used internally by Google. It is called Goobuntu and they use that on their servers.  They do not give source for that, but they do not give binaries either so they do not brake GPL. 

They are legit, just their "Don't be evil" mantra is pure BS, like Steve Jobs said. I never imagined that I will agree with Steve Jobs' opinion once in a lifetime.

> **pwnst*r said:**
> I don't know the technical aspects of the kernel, but I'm not seeing anything official in someone's blog.

"Official" means that it is no longer microfork, Android stuff is removed, so now Android is real fork. Maybe "offical" is not right word...

---

### Post by Tibuda on 2010-02-05
> **mickie.kext said:**
> There is another fork used internally by Google. It is called Goobuntu and they use that on their servers.  They do not give source for that, but they do not give binaries either so they do not brake GPL.

Goobuntu is not really a fork. It is just a LiveCDs based on Ubuntu just like Crunchbang and Masonux.

---

### Post by fromthehill on 2010-02-05
> **danielrmt said:**
> Goobuntu is not really a fork. It is just a LiveCDs based on Ubuntu just like Crunchbang and Masonux.
don't you mean Gos?

---

### Post by mickie.kext on 2010-02-05
> **danielrmt said:**
> Goobuntu is not really a fork. It is just a LiveCDs based on Ubuntu just like Crunchbang and Masonux.

You probably think on some freely available distro...

Goobuntu (that is just nickname, it is not realy released, so it does not have a name) is used by google for years and nobody outside Google can get it. It has some features (like [GFS]("http://en.wikipedia.org/wiki/Google_File_System"), the cluster file system) that are not present in mainline Linux kernel. So not really a regular distro. Google hired Teodor Tso to help with porting GFS to Ext4 [http://www.tuxmachines.org/node/42455](http://www.tuxmachines.org/node/42455)

---

### Post by gletob on 2010-02-05
> **fromthehill said:**
> don't you mean Gos?

No

[http://en.wikipedia.org/wiki/GOS_%28operating_system%29](http://en.wikipedia.org/wiki/GOS_%28operating_system%29)

[http://en.wikipedia.org/wiki/Goobuntu](http://en.wikipedia.org/wiki/Goobuntu)

---

### Post by mickie.kext on 2010-02-05
^Yeah that is the one, but it hardly a regular distribution. Neither sources or binaries are available outside of Google.

---

### Post by pwnst*r on 2010-02-05
> **Paqman said:**
> The "someone" in question would be [Greg Kroah-Hartman]("http://en.wikipedia.org/wiki/Greg_Kroah-Hartman"), a senior kernel dev.

> **mickie.kext said:**
> 
"Official" means that it is no longer microfork, Android stuff is removed, so now Android is real fork. Maybe "offical" is not right word...

Thanks.

---

### Post by Giant Speck on 2010-02-05
Pfft... and some of you actually think Google cares about Linux.

---

### Post by Icehuck on 2010-02-05
> **Giant Speck said:**
> Pfft... and some of you actually think Google cares about Linux.

They do no evil!

---

### Post by Sporkman on 2010-02-05
> **Icehuck said:**
> They do no evil!

...or do they [boll weevil]("http://en.wikipedia.org/wiki/Boll_weevil")...?

---

### Post by Icehuck on 2010-02-05
> **Sporkman said:**
> ...or do they [boll weevil]("http://en.wikipedia.org/wiki/Boll_weevil")...?

Crazy spork people and their crazy spork ideas.

---

### Post by Sporkman on 2010-02-05
> **Icehuck said:**
> Crazy spork people and their crazy spork ideas.

Don't judge us. We are a peaceful, multi-purpose folk.

---

### Post by Islington on 2010-02-05
> **Giant Speck said:**
> Pfft... and some of you actually think Google cares about Linux.
Considering they use it internally, I would say they do care.

---

### Post by DeadSuperHero on 2010-02-05
Whelp, time to go find an Android-compatible FreeBSD-based phone stack. I'll call it...Cylon.

In all seriousness, it does kinda suck that the code is now incompatible. Doesn't mean that it can't be merged back in with some major doing.

---

### Post by blur xc on 2010-02-05
> **Mr. Psychopath said:**
> Whelp, time to go find an Android-compatible FreeBSD-based phone stack. I'll call it...Cylon.

In all seriousness, it does kinda suck that the code is now incompatible. Doesn't mean that it can't be merged back in with some major doing.

Why do we want it merged back in?  As I understand it, and I admit that I may have it all wrong, is that the Android bits of code in the Linux kernel serve no purpose on our x86 desktop computers.  All the x86 bits of code don't do anything on Android hardware (cell phones).  So, why should either carry junk code that serves no purpose except to take up space?

Doesn't it just make more sense for the Android kernel to strip out everything non-Android from the source code?

BM

---

### Post by beastrace91 on 2010-02-05
> **blur xc said:**
> Why do we want it merged back in?  As I understand it, and I admit that I may have it all wrong, is that the Android bits of code in the Linux kernel serve no purpose on our x86 desktop computers.  All the x86 bits of code don't do anything on Android hardware (cell phones).  So, why should either carry junk code that serves no purpose except to take up space?

Doesn't it just make more sense for the Android kernel to strip out everything non-Android from the source code?

BM

There is piles of code in your default *nix kernel used by most distros that you will never use on your own system - this is so they can support the largest range of hardware.

That being said just because code is in the main kernel tree does not mean it gets compiled into every distro's kernel. Also a user can always feel free to compile a custom kernel toggling any and all features they wish to remove...

Regarding the topic at hand - just one more reason I am glad I went with Nokia's N900 (Maemo operating system) instead of Android.

~Jeff

---

### Post by jwbrase on 2010-02-05
They forked it. So what? One of the wonderful things about free software is that it can be forked so easily. Would that the Windows Kernel were so easily forkable...

---

### Post by mickie.kext on 2010-02-05
> **blur xc said:**
> Why do we want it merged back in?  As I understand it, and I admit that I may have it all wrong, is that the Android bits of code in the Linux kernel serve no purpose on our x86 desktop computers.  All the x86 bits of code don't do anything on Android hardware (cell phones).  So, why should either carry junk code that serves no purpose except to take up space?

Doesn't it just make more sense for the Android kernel to strip out everything non-Android from the source code?

BM
No, that is not the reason. 

What Google changed are internal APIs and security model. They did not striped anything non-Android (they would end-up striping everything in that case), kernel devs removed Android from mainline because Google is uninterested to maintain it and play nice with others. Google did not removed x86 (or anything, Android kernel is still heavily based on Linux) because they will need it when Chrome OS comes out. We all know that Linux's security model is superior to anything, so it is unclear why they changed that. But what is clear is that they do not want to share drivers with anyone. That is why they changed internal APIs. They got vendor support because they are big company, so now they want to abuse it. They will roll out Android tablets, Phones, netbooks. Vendors will make all possible drivers for that, but Google want to be sure that only their OS work on that devices and that peripherals made for that device do not work with ordinary Linux. They do not want to see Ubuntu powered Laptop with ARM Cortex A9, using drivers that Imageon Tehnologies/Qualcom/Whatever wrote and contributed to Android. That is the whole point. They want to take, do not want to give back and do not want to share. So they are quirking up their kernel to make it unattractive to Linus and kernel team. They are no better than Apple.

---

### Post by beastrace91 on 2010-02-05
> **mickie.kext said:**
> They want to take, do not want to give back and do not want to share. So they are quirking up their kernel to make it unattractive to Linus and kernel team. They are no better than Apple.

Well said. +1

~Jeff

---

### Post by jflaker on 2010-02-05
> **SuperSonic4 said:**
> tl;dr

also open source lets you do that. As far as I know won't google have to release the code of their fork?

any updates to the Kernel will need to be released but utilities and other things developed AROUND said Kernel can remain closed source.

---

### Post by Mr. Picklesworth on 2010-02-05
> **mickie.kext said:**
> What Google changed are internal APIs and security model. They did not striped anything non-Android (they would end-up striping everything in that case), kernel devs removed Android from mainline because Google is uninterested to maintain it and play nice with others. Google did not removed x86 (or anything, Android kernel is still heavily based on Linux) because they will need it when Chrome OS comes out. We all know that Linux's security model is superior to anything, so it is unclear why they changed that.

I would be interested to know what kernel-level stuff needed to be changed for Android's security model, actually. It is, if one looks past personal bias, an *incredibly *awesome security model. (Yes, amazingly enough, Linux in its current state is not the be-all-end-all and the state of the desktop is really unimpressive compared to the innovation we're seeing in the mobile space).

The bit I do know is that applications on Android have very limited file system access; basically their own config database and files passed to them by the user. The only time an application has access to a specific file or another application's data is if a trusted component grants that permission. This means personal security; not just system integrity.

That particular chunk, though, isn't getting into kernel changes as far as I'm aware. (That kind of resource access control can go through SELinux). So, I would love to know what they've done in some more detail :)

---

### Post by earthpigg on 2010-02-05
> They want to take, do not want to give back and do not want to share. So they are quirking up their kernel to make it unattractive to Linus and kernel team. They are no better than Apple.

this is only relevant if you are a Linux advocate and not a Free Software advocate.

if *BSD or something based on Android becomes more attractive to me than Linux, ill switch in a heartbeat.

my loyalty is to the Four Freedoms, not any particular license or piece of software.

---

### Post by Zoot7 on 2010-02-05
> **Giant Speck said:**
> Pfft... and some of you actually think Google cares about Linux.
Haha true indeed. Google only care about one thing - profit.

---

### Post by forrestcupp on 2010-02-05
> **Zoot7 said:**
> Haha true indeed. Google only care about one thing - profit.+1
Google doesn't care about Linux; they care about their bottom line.

> **earthpigg said:**
> this is only relevant if you are a Linux advocate and not a Free Software advocate.

if *BSD or something based on Android becomes more attractive to me than Linux, ill switch in a heartbeat.

my loyalty is to the Four Freedoms, not any particular license or piece of software.
I think I'm more loyal to Linux than I am to the FSF.  And Google doesn't give a rat's backside about the Four Freedoms, other than that it helps their wallets and they don't have to pay license fees.  If they could find a way to not pay license fees and not have to worry about the Four Freedoms, I'm sure they would.

---

### Post by DLM955 on 2010-02-06
After reading this thread I just had to find the OS.....I installed gOS 3.1 in a virtual box.It's based on ubuntu 9.04  uses all the same repositorys for upgrades, just uses a bunch of Google wigets....it did 348 updates on first boot. So far so good in virtual world..some glitches but I'am thinking being in virtual box caused them....It states its for portable devices.......I'am using it to write this post.

---

### Post by earthpigg on 2010-02-06
> **forrestcupp said:**
> I think I'm more loyal to Linux than I am to the FSF. 

i have no particular loyalty to the FSF as an organization. they are useful for now. this may not always be the case.

blind loyalty to an institution tends to blind folks to the faults of said institution.

---

### Post by Paqman on 2010-02-06
> **DLM955 said:**
> After reading this thread I just had to find the OS.....I installed gOS 3.1 in a virtual box.

gOS is not affiliated with Google in any way.

---

### Post by Ric_NYC on 2010-02-06
If they did it... I think it's not a good thing.
The open source has a lot of things to improve. Forking is not going to help.

---

### Post by Regenweald on 2010-02-06
Edit; doesn't really matter.

---

### Post by forrestcupp on 2010-02-06
> **earthpigg said:**
> i have no particular loyalty to the FSF as an organization. they are useful for now. this may not always be the case.

blind loyalty to an institution tends to blind folks to the faults of said institution.

Well said.

---

### Post by mickie.kext on 2010-02-09
Here is more light on the issue 
[http://www.h-online.com/open/features/Android-versus-Linux-924563.html](http://www.h-online.com/open/features/Android-versus-Linux-924563.html)

> **earthpigg said:**
> this is only relevant if you are a Linux advocate and not a Free Software advocate.

if *BSD or something based on Android becomes more attractive to me than Linux, ill switch in a heartbeat.

my loyalty is to the Four Freedoms, not any particular license or piece of software.

No, I like free software and Linux equally and I also think that Four Freedoms beats any licence (exept maybe AGPLv3 :D). But what I do not like is unneeded fragmentation. Forking Linux spells more problems for everyone including Google, and they will realize that eventually when their R&D costs go through the roof.

I think my next phone will be Symbian powered. And I am not tinkering with Android SDK anymore.

---

### Post by Gallahhad on 2010-02-09
[QUOTE=http://lwn.net/Articles/372419/]Posted Feb 3, 2010 20:58 UTC (Wed) by **morrildl** (guest, #63330)        [[Link]("http://lwn.net/Articles/372667/")]     
      > Maybe I'm reading too much into this
 You are.

 > Perhaps Google isn't comfortable with the compromising and reduced
> control that would necessarily be involved in sharing responsibility
> with the mainline developers?

 Wow, what is it with Linux people automatically jumping on the "control" 
meme? This is purely a pragmatic thing.

 It's true that Android does a few unusual things in the kernel, and it's 
perfectly reasonable that some of what we contributed was viewed with some 
skepticism. For example, the concept (and code) of wakelocks is something 
that is pretty mobile-specific (and arguably even Android-specific), and 
it's quite reasonable for the upstream kernel folks to proceed cautiously 
in accepting the code. The vast majority of their users run Linux on 
hardware where wakelocks are unnecessary, so it is utterly unsurprising 
that the kernel folks are not falling all over themselves to merge in our 
new paradigm.

 For our part, meanwhile, we have working code that's running on millions of 
devices, and we (also quite reasonably) are not eager to do extensive 
modifications to it simply for the goal of upstreaming it. If the upstream 
folks had enthusiastically endorsed it but added "...but there's a few 
changes we'd like you to make first", then it might be a different story. 
But they didn't, and that's just fine.

 And anyway, what's the hurry? Are we trapped in some hellish game where the 
goblins will devour us if we don't meet our quota for adding upstream code?
Since we have working code, and it's not "less open-source" just because it
lives in a different repo, why is this even an issue?.[/QUOTE]

An interesting post from the [http://lwn.net/Articles/372419/](http://lwn.net/Articles/372419/) link.

---

### Post by Eclipse. on 2010-02-09
Google wanted their code in the mainline kernel however its not possible because of the changes it would require, it will take some time but the code will get in the mainline eventually.

---

